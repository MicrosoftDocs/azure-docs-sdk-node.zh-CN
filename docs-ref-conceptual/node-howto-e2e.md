---
title: 使用 Visual Studio Code 和 Azure 进行 Node.js 开发
description: 演示如何创建、使用 Docker 容器化 Node.js 应用并将其部署到 Azure 的完整端到端教程
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
ms.locfileid: "20908137"
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a>使用 Visual Studio Code 和 Azure 进行 Node.js 开发

本教程演示如何使用 Visual Studio Code 提取现有的 Node.js 应用、将其“容器化”（使用 Docker），然后将其部署到 Azure。

本教程使用 [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular) 创建并发布的简单待办事项应用。 这是一个单页 MEAN 应用，因此，它使用 MongoDB 作为数据库，使用 Node/Express 作为 REST API/Web 服务器，使用 Angular.js 1.x 作为前端 UI。 

## <a name="prerequisites"></a>先决条件

若要遵循本演示教程，需要安装以下软件：

- [Contact.java](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/products/docker)
- [DockerHub 帐户](https://hub.docker.com/)
- [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [Azure 帐户](https://azure.microsoft.com/free/)
- [Yarn](https://yarnpkg.com/en/docs/install)
- [Chrome](https://www.google.com/chrome/browser/desktop/) - 用于调试演示应用的前端。
- MongoDB - 由于演示应用使用 MongoDB，因此，需要在本地运行一个侦听标准 `27017` 端口的 MongoDB 实例。 为实现此目的，最简单的方法是在安装 Docker 之后依次运行 `docker pull mongo` 和 `docker run -it -p 27017:27017 mongo` 命令。

## <a name="project-setup"></a>项目设置

若要开始，请使用以下步骤下载示例项目：

1. 打开 Visual Studio Code。

1. 按 **&lt;F1>** 显示命令面板。

1. 在命令面板的提示符下输入 `gitcl`，选择“Git: 克隆”命令，按 **&lt;Enter>**。

    ![Visual Studio Code 命令面板提示符中的 gitcl 命令](./media/node-howto-e2e/git-clone.png)

1. 系统提示输入“存储库 URL”时，请输入 `https://github.com/scotch-io/node-todo`，按 **&lt;Enter>**。

1. 选择（或创建）要将项目克隆到的本地目录。

    ![Visual Studio Code 资源管理器](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a>集成式终端

由于这是一个 Node.js 项目，因此首先要做的是确保从 npm 安装项目的所有依赖项。  

1. 按 **&lt;Ctrl>`** 显示 Visual Studio Code 集成式终端。 

1. 输入 `yarn`，按 **&lt;Enter>**。  

    ![在 Visual Studio Code 中运行 yarn 命令](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a>集成式 Git 版本控制

通过 Yarn 安装应用的依赖项之后，会创建一个 `yarn.lock` 文件，该文件今后提供可预测的方式在 CI（持续集成）版本、生产部署或其他开发人员计算机上顺利地重新获取确切的依赖项。

以下步骤演示如何将 `yarn.lock` 文件签入源代码管理：

1. 在 Visual Studio Code 中，切换到集成式 Git 选项卡（带有 Git 徽标）。

1. 在“消息”框中输入提交消息，并按 **&lt;Ctrl>&lt;Enter>**。 

    ![将 yarn.lock 文件添加到 Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a>项目和代码导航

为了在代码库中定位，让我们演练一下 Visual Studio Code 提供的某些导航功能的一些示例。

1. 按 **&lt;Ctrl>P**。

1. 输入 `.js` 显示项目中的所有 JavaScript/JSON 文件以及每个文件的父目录 

    ![显示所有 .js* 文件](./media/node-howto-e2e/git-output.png)

1. 选择 `server.js`，即应用的启动脚本。 

1. 将鼠标悬停在 **database** 变量（在第 6 行导入）上，以查看其类型。 在开发项目期间，这种在文件中快速检查变量/模块/类型的功能非常有用。 

    ![发现类型](./media/node-howto-e2e/hover-help.png)

1. 在变量（例如 **database**）的范围中单击鼠标可查看同一文件中对该变量的所有引用。 若要在项目中查看对某个变量的所有引用，请右键单击该变量，并从上下文菜单中选择“查找所有引用”。

    ![查找对变量的引用](./media/node-howto-e2e/word-hilight.png)

1. 除了通过将鼠标悬停在变量上来发现其类型以外，还可以检查变量的定义，即使该变量位于另一文件中。 若要了解这项操作，请右键单击“database.localUrl”（第 12 行），并从上下文菜单中选择“查看定义”。 

    ![查看变量的定义](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a>修改代码并使用自动完成

MongoDB 连接字符串在 **database.localUrl** 的声明中经过硬编码。 本部分修改代码以从环境变量检索连接字符串，并介绍 Visual Studio Code 的自动完成功能。  

1. 打开 `server.js` 文件

1. 将以下代码： 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    替换为此代码：

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

请注意，如果手动键入代码（而不是复制并粘贴），则在 `process` 后面键入句点时，Visual Studio Code 会显示 Node.js **process** 全局 API 的可用成员。

![自动完成功能会自动显示 API 的成员](./media/node-howto-e2e/process-env.png)

之所以能够实现自动完成，是因为 Visual Studio Code 在幕后使用 TypeScript（即使是对于 JavaScript）来提供键入信息，然后，在键入时使用这些信息来显示完成列表。 Visual Studio Code 能够检测到 Node.js 项目，因此，能够自动下载适用于 [NPM 中的 Node.js](https://www.npmjs.com/package/@types/node) 的 TypeScript 键入内容文件。 使用键入内容文件可以获取其他 Node.js 全局变量（例如 **Buffer** 和 **setTimeout**）和所有内置模块（例如 **fs** 和 **http**）的自动完成列表。

除了内置的 Node.js API 以外，这种自动获取键入内容的功能也适用于 2,000 多种第三方模块，例如 React、Underscore 和 Express。 例如，若要禁用 MongoDB 在无法连接到配置的 Mongoose 数据库实例时使示例应用发生崩溃，可在第 13 行中插入以下代码行：

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

在上面的代码中可以看到，不需要采取任何动作就获得了自动完成功能。

![自动完成功能会自动显示 API 的成员](./media/node-howto-e2e/mongoose.png)

可以通过浏览 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) 项目（所有 TypeScript 键入内容定义的社区驱动源）来了解哪些模块支持此自动完成功能。

## <a name="running-the-app"></a>运行应用

稍微了解代码之后，便可以开始运行应用了。 若要从 Visual Studio Code 运行应用，请按 **&lt;F5>**。 通过 **&lt;F5>**（调试模式）运行代码时，Visual Studio Code 会启动应用，并显示“调试控制台”窗口，其中显示了应用的 stdout。

![通过调试控制台监视应用的 stdout](./media/node-howto-e2e/console.png)

此外，“调试控制台”已附加到最近运行的应用，因此，可以键入要在应用中评估的、也支持自动完成功能的 JavaScript 表达式。 若要了解这项操作，请在控制台中键入 `process.env`：

![在调试控制台中键入代码](./media/node-howto-e2e/console-code.png)

之所以能够按 **&lt;F5>** 运行应用，是因为当前打开的文件是 JavaScript 文件 (`server.js`)。 因此，Visual Studio Code 假设项目是 Node.js 应用。 如果在 Visual Studio Code 中关闭所有 JavaScript 文件，再按 **&lt;F5>**，则 Visual Studio Code 会查询环境：

![指定运行时环境](./media/node-howto-e2e/select-env.png)

打开浏览器并导航到 `http://localhost:8080` 以查看正在运行的应用。 在文本框中键入一条消息，并添加/删除几个待办事项来感受应用的工作方式。

![正在运行的待办事项应用](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a>调试

除了能够通过集成控制台运行应用并与之交互以外，Visual Studio Code 还提供直接在代码中设置断点的功能。 例如，按 **&lt;Ctrl>P** 可显示文件选取器。 显示文件选取器后，请键入 `route`，选择 `route.js` 文件。

在第 28 行设置一个断点，用于表示当应用尝试添加待办事项条目时要调用的 Express 路由。 若要设置断点，只需在编辑器中单击行号左侧的区域，如下图所示。

![在 Visual Studio Code 中设置断点](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> 除了标准断点以外，Visual Studio Code 还支持可用于自定义应用何时应暂停执行的条件断点。 若要设置条件断点，请右键单击要暂停执行的行左侧的区域，选择“添加条件断点...”，并指定 JavaScript 表达式（例如 `foo = "bar"`）或执行计数来定义要在哪种条件下暂停执行。
> 
> 

设置断点后，返回到正在运行的应用并添加一个待办事项条目。 添加待办事项条目会立即导致应用在设置了断点的第 28 行处暂停执行：

![Visual Studio Code 在断点处暂停执行](./media/node-howto-e2e/debugger.png)

暂停应用程序后，可将鼠标悬停在代码的表达式上，以查看其当前值，检查局部变量/监视项和调用堆栈，并使用调试工具栏逐步执行代码。 按 **&lt;F5>** 可恢复应用的执行。

## <a name="full-stack-debugging"></a>完整堆栈调试

如本主题前面所述，该待办事项应用是一个 MEAN 应用 - 这意味着，其前端和后端都是使用 JavaScript 编写的。 因此，在当前调试后端 (Node/Express) 代码过程中的某个时间点，可能需要调试前端 (Angular) 代码。 出于此目的，Visual Studio Code 提供庞大的扩展生态系统，包括集成的 Chrome 调试。

切换到“扩展”选项卡上，在搜索框中键入 `chrome`：

![Visual Studio Code 的 Chrome 调试扩展](./media/node-howto-e2e/chrome.png)

选择名为“适用于 Chrome 的调试程序”的扩展，再选择“安装”。 安装 Chrome 调试扩展后，选择“重新加载”关闭再重新打开 Visual Studio Code 以激活该扩展。 

![安装 Chrome 调试扩展后重新加载 Visual Studio Code](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

尽管无需进行任何特定于 Visual Studio Code 的配置即可运行和调试 Node.js 代码，但若要调试前端 Web 应用，需要生成一个 `launch.json` 文件来指示 Visual Studio Code 如何运行应用。 

若要生成 `launch.json` 文件，请切换到“调试”选项卡，单击齿轮图标（顶部应有一个小红点），并选择 **node.js** 环境。

![Visual Studio Code 中用于配置 launch.json 文件的选项](./media/node-howto-e2e/debug-gear.png)

创建的 `launch.json` 文件如下所示，它告知 Visual Studio Code 如何启动和/或附加到应用以便对其进行调试。 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

请注意，Visual Studio Code 能够检测到应用的启动脚本为 `server.js`。 

打开 `launch.json` 文件后，依次选择“添加配置”（右下角）、“Chrome: 使用 userDataDir 启动”。

![将 Chrome 配置添加到 Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

为 Chrome 添加新的运行配置可以调试前端 JavaScript 代码。 

可将鼠标悬停在指定的任何设置上，以查看有关该项设置的功能的文档。 此外请注意，Visual Studio Code 会自动检测应用的 URL。 请 **webRoot** 属性更新为 `${workspaceRoot}/public`，使 Chrome 调试程序知道在何处查找应用的前端资产：

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

若要同时启动/调试前端和后端，需创建一个复合运行配置来告知 Visual Studio Code 要并行运行哪个配置集。 

在 `launch.json` 文件中添加以下代码片段作为顶级属性（现有 **configurations** 属性的同级）。

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

在 **compounds.configurations** 数组中指定的字符串值引用**配置**列表中各个条目的**名称**。 如果已修改这些名称，则需要在数组中进行相应的更改。 若要了解这项操作，请切换到调试选项卡，将选定的配置更改为 **Full-Stack**（复合配置的名称），并按 **&lt;F5>** 运行该配置。

![在 Visual Studio Code 中运行配置](./media/node-howto-e2e/full-stack-profile.png)

运行配置会启动 Node.js 应用（可在调试控制台输出中查看）和 Chrome（配置为导航到 `http://localhost:8080` 上的 Node.js 应用）。

按 **&lt;Ctrl>P**，并输入（或选择）`todos.js`，即应用前端的 Angular 主控制器。 

在第 11 行设置一个断点，这是要创建的新待办事项条目的入口点。

返回到正在运行的应用，添加新的待办事项条目，然后可以看到，Visual Studio Code 现已暂停 Angular 代码中的执行。

![在 Visual Studio Code 中调试前端代码](./media/node-howto-e2e/chrome-pause.png)

与执行 Node.js 调试时一样，可以通过将鼠标悬停在表达式上来查看局部变量/监视项、在控制台中评估表达式，等等。 

请注意两个很棒的功能：

1. “调用堆栈”窗格显示两个不同的堆栈：“Node”和“Chrome”，并指示当前暂停了哪个堆栈。

1. 可在前端代码与后端代码之间逐步调试。 若要进行测试，请按 **&lt;F5>** 运行并命中前面在 Express 路由中设置的断点。

通过此设置，现在可以直接在 Visual Studio Code 中有效调试前端、后端或完整堆栈的 JavaScript 代码。 

此外，复合调试程序的概念并不仅仅局限于两个目标进程，而且也不仅仅局限于 JavaScript。 因此，在微服务应用（可能是 polyglot）中操作时，可以使用完全相同的工作流（前提是安装语言/框架的相应扩展）。

## <a name="dockerizing-the-app"></a>使用 Docker 容器化应用

本部分重点介绍 Visual Studio Code 提供的、用于通过 [Docker](https://www.docker.com/) 进行开发的体验。 Node.js 开发人员可以使用 Docker 来为开发、CI（持续集成）和生产环境提供可移植的应用部署。 由于 Docker 对于某些用户而言有一定的难度，Visual Studio Code 提供了一个扩展来帮助某些用户在应用中简化 Docker 的使用。

切换回到“扩展”选项卡，搜索 `docker`，选择“Docker”扩展。 

安装 Docker 扩展，重新加载 Visual Studio Code。

![安装 Visual Studio Code 的 Docker 扩展](./media/node-howto-e2e/docker-search.png)

Visual Studio Code 的 Docker 扩展包含一条命令用于生成 *Dockerfile* 以及现有项目的 `docker-compose.yml` 文件。 

若要查看可用的 Docker 命令，请通过 **&lt;F1>** 显示命令面板并键入 `docker`。

![Visual Studio 的 Docker 扩展支持的命令 ](./media/node-howto-e2e/docker-commands.png)

选择“Docker: 将 Docker 文件添加到工作区”，选择“Node.js”作为应用平台，并指定应用需公开端口 `8080`。 

Docker 命令会生成可立即开始使用的完整 `Dockerfile` 和 Docker-compose 文件。

![生成的 Dockerfile](./media/node-howto-e2e/docker-file.png)

Docker 扩展还针对 `Dockerfiles` 和 `docker-compose.yml` 文件提供自动完成功能。 

若要了解这项操作，请打开 `Dockerfile` 并将第 2 行：

```docker
FROM node:latest
```

更改为：

```docker
FROM mhart
```

将光标定位在 `mhart` 中的 `t` 后面，按 **&lt;Ctrl>&lt;Space>** 查看 `mhart` 在 DockerHub 中发布的所有映像存储库。

![Docker 扩展自动完成](./media/node-howto-e2e/docker-completion.png)

选择 `mhart/alpine-node`（提供此应用所需的所有内容）。 

一般而言，映像越小越好，因为这样可以尽量加速应用的生成和部署，从而可以更快地完成分发和缩放。

生成 `Dockerfile` 后，需要生成实际的 Docker 映像。 同样，可以使用 Docker 扩展在 Visual Studio Code 中安装的命令。 按 **&lt;F1>**，在命令面板中输入 `dockerb`，选择“Docker: 生成映像”命令。 选择刚刚生成并修改的 `/Dockerfile`。 指定包含 DockerHub 用户名的标记（例如 `lostintangent/node`）。 按 **&lt;ENTER>** 启动集成式终端窗口，其中显示了正在生成的 Docker 映像的输出。

![Docker 映像生成状态](./media/node-howto-e2e/docker-build.png)

请注意，该命令已自动完成 `docker build` 的运行过程（这是可以选择用来提高工作效率的另一个例子）。也可以直接使用 Docker CLI。 

此时，若要使此映像可方便用于部署，只需将它推送到 DockerHub。 为此，请确保已在 CLI 中运行 `docker login` 并输入帐户凭据完成了 DockerHub 的身份验证。 然后，可在 Visual Studio Code 中打开命令面板，输入 `dockerpush`，并选择 `Docker: Push` 命令。 选择刚刚生成的映像标记（例如 `lostintangent/node`），按 **&lt;Enter>**。 该命令会自动调用 `docker push` 并在集成式终端中显示输出。

## <a name="deploying-the-app"></a>部署应用

使用 Docker 容器化应用并将它推送到 DockerHub 之后，需要将它部署到云中，使全球用户都能看到它。 为此，可以使用 Azure 应用服务，这是 Azure 的 PaaS 产品。 应用服务提供两项面向 Node.js 开发人员的功能：

- 支持基于 Linux 的 VM，减少了使用本机 Node 模块生成的应用的不兼容性，以及可能不支持 Windows 和/或行为有所不同的其他工具的不兼容性。
- 支持基于 Docker 的部署，允许指定 Docker 映像的名称，并允许应用服务自动提取、部署和缩放映像。

若要开始，请打开 Visual Studio 终端。 将使用新的 Azure CLI 2.0 来管理 Azure 帐户并预配所需的基础结构来运行该待办事项应用。 （如前面的先决条件中所述）从 CLI 使用 `az login` 命令登录到帐户后，请执行以下步骤来预配应用服务实例并部署待办事项应用容器：

1. 创建一个资源组，可将它视为用于帮助组织 Azure 资源的命名空间或目录。 `-n` 选项用于指定组的名称，可采用任何值。

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > `-l` 选项指示资源组的位置。 在预览期，Linux 上的应用服务支持仅在某些区域可用。 因此，如果你不在美国西部并想要知道其他哪些区域提供此项功能，请从 CLI 运行 `az appservice list-locations --linux-workers-enabled` 来查看数据中心选项。

2. 将新建的资源组设为默认资源组，以便可以继续使用 CLI，而无需在每个 CLI 调用中显式指定资源组：

   ```shell
   az configure -d group=nina-demo
   ```
   
3. 创建应用服务计划，用于管理要将应用部署到的底层虚拟机的创建和缩放。 同样，可为 `n` 选项指定任何所需的值。

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > --is-linux 指示想要使用基于 Linux 的虚拟机。 如果不指定此选项，CLI 会默认预配基于 Windows 的虚拟机。

4. 创建应用服务 Web 应用，用于表示要在刚刚创建的计划和资源组中运行的实际待办事项应用。 可将 Web 应用视为与进程或容器同义，将计划视为与运行该应用的虚拟机/容器主机同义。 此外，在创建 Web 应用的过程中，需将它配置为使用已发布到 DockerHub 的 Docker 映像：

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > 如果想要使用 Git 部署而非自定义容器，请参阅[在 Azure 中创建 Node.js Web 应用](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs)一文。

5. 将 Web 应用设为默认 Web 实例：

    ```shell
    az configure -d web=nina-demo-app
    ```

6. 启动应用，查看将在 `*.azurewebsites.net` URL 上部署的容器：

    ```shell
    az webapp browse
    ```

    ![浏览器中运行的待办事项应用](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > 首次加载应用可能需要几分钟时间，因为应用服务必须从 DockerHub 提取 Docker 映像，然后再启动它。

目前只是部署并运行了待办事项应用。 

现已部署待办事项应用。 但是，旋转的图标指示该应用无法连接到数据库。 这是因为，在开发期间使用的是 MongoDB 的本地实例，显然无法 Azure 数据中心内部访问它。 由于已将应用修改为通过环境变量接受连接字符串，因此，只需启动 MongoDB 服务器并重新配置应用服务实例即可引用环境变量。 下一部分会演示此操作。

## <a name="provisioning-a-mongodb-server"></a>预配 MongoDB 服务器

尽管我们可以自行配置 MongoDB 服务器（或副本集）并管理该基础结构，但也可以使用 Azure 提供的名为 [Cosmos DB](https://azure.microsoft.com/services/documentdb/) 的解决方案。 Cosmos DB 是完全托管的、可异地复制的高性能 NoSQL 数据库，提供 MongoDB 兼容性层。 这意味着，可将现有的 MEAN 应用（或任何 MongoDB 客户端/工具，例如 [Studio 3T](https://studio3t.com/)）指向 Cosmos DB，而无需更改除连接字符串以外的其他任何设置。 以下步骤演示如何执行此操作：

1. 在 Visual Studio Code 终端中运行以下命令，创建 Cosmos DB 服务的 MongoDB 兼容实例。 将 **<NAME>** 占位符替换为全局唯一值（Cosmos DB 使用此名称来生成数据库的服务器 URL）：

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. 检索此实例的 MongoDB 连接字符串：

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. 更新 Web 应用的 **MONGODB_URL** 环境变量，使之连接到新预配的 Cosmos DB 实例，而不是尝试连接到本地运行的 MongoDB 服务器（并不存在！）：

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. 返回到浏览器并刷新。 尝试添加和删除某个待办事项来证明该应用现在是否可正常工作，而无需更改任何设置！ 将环境变量设置为创建的、可完全模拟 MongoDB 数据库的 Cosmos DB 实例。

    ![连接到数据库之后的演示应用](./media/node-howto-e2e/finished-demo.png)

如果需要，可切换回到的 Cosmos DB 实例，并增大（或减小）MongoDB 实例所需的保留吞吐量，然后，即可享受到流量的添加好处，且无需手动管理任何基础结构。

此外，Cosmos DB 可自动为每个文档和属性编制索引。 这样，就不需要分析速度缓慢的查询或手动调整索引。 只需根据需要进行预配和缩放，让 Cosmos DB 处理其余的工作。

## <a name="hosting-a-private-docker-registry"></a>托管专用 Docker 注册表

DockerHub 提供超卓的体验来分发容器映像，但在某些情况下，你可能想要托管自己的专用 Docker 注册表 - 例如，为了获得安全/监管或性能方面的优势。 为此，Azure 提供 [Azure 容器注册表](https://azure.microsoft.com/services/container-registry/) (ACR)，用于启动其后备存储位于 Web 应用所在的同一数据中心内的自有 Docker 注册表（可以加速提取过程）。 ACR 还提供全面的内容控制和访问控制 - 例如，谁可以推送或提取映像。 

可运行以下命令来实现自定义注册表的预配。 （请将 **<NAME>** 占位符替换为全局唯一值，因为 ACR 使用指定的值来生成注册表的登录服务器 URL。）

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> 为方便阐述，本主题的示例使用了**管理员帐户**，但不建议对生产注册表使用该帐户。 

`az acr create` 命令（通过 `LOGIN SERVER` 列）显示可用于在 Docker CLI 中进行登录的登录服务器 URL（例如 `ninademo.azurecr.io`）。 此外，该命令会生成可用于对服务器进行身份验证的管理员凭据。 若要检索这些凭据，请运行以下命令，并记下显示的用户名和密码：

```shell
az acr credential show -n $ACR_NAME
```

借助上一步骤生成的凭据和单个登录服务器，可以使用标准 Docker CLI 工作流登录到注册表。

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

现在，可使用以下命令来标记 Docker 容器，指示它与专用注册表相关联（请将 `lostintangent/node` 替换为容器映像的名称）。

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

最后，将标记的映像推送到专用 Docker 注册表。

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

现已将容器存储在自己的专用注册表中，并且可以像使用 DockerHub 时一样，在 Docker CLI 中顺畅地继续工作。 若要指示应用服务 Web 应用从专用注册表提取数据，只需运行以下命令：

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> 请确保在 `-r` 选项的开头添加 `https://` 前缀。 但是，请不要为容器映像名称添加前缀。

如果在浏览器中刷新应用，所有内容和功能的外观与行为应该相同。 但是，应用现在是通过专用 Docker 注册表运行的。 更新应用后，请按如上所述标记和推送更改，并在应用服务容器配置中更新标记。

## <a name="configuring-a-custom-domain-name"></a>配置自定义域名

尽管 `*.azurewebsites.net` URL 非常适合用于测试，但在某些情况下，你可能想要将自定义域名添加到 Web 应用。 从注册机构购买域名后，只需在其中添加一条指向 Web 应用外部 IP（实际上是一个负载均衡器）的 `A` 记录。 可运行以下命令检索此 IP：

```shell
az webapp config hostname get-external-ip
```

除了添加 `A` 记录以外，还需要在域中添加一条指向目前所用 `*.azurewebsites.net` 域的 `TXT` 记录。 `A` 和 `TXT` 记录的组合可让 Azure 验证该域是否由你拥有。

创建这些记录并传播 DNS 更改之后，请将自定义域注册到 Azure，使 Azure 能够正确处理传入的流量。 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> 只有在传播 DNS 更改之后，该命令才能正常运行。

打开浏览器并导航到自定义域，查看它现在是否能够解析为 Azure 上部署的应用。

## <a name="scaling-up-and-out"></a>纵向和横向扩展

在将来的某个时候，你的 Web 应用可能会变得很受欢迎，以致分配的资源（CPU 和 RAM）并不足以处理流量和操作需求的提高。 前面创建的应用服务计划 (**B1**) 附带 1 个 CPU 核心和 1.75 GB RAM，可能很快就会达到最大用量。 **B2** 计划附带的 RAM 和 CPU 是 B1 的两倍，因此，如果发现应用即将耗尽其中的任何一项资源，可通过运行以下命令来纵向扩展底层虚拟机：

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> 有关 Azure 应用计划的定价详细信息和规范，请参阅[应用服务定价](https://azure.microsoft.com/pricing/details/app-service/)一文

几分钟后，Web 应用即会迁移到请求的硬件，可开始利用相关的资源。 除了扩展资源以外，还可以运行上述同一命令来缩减资源：指定 `--sku` 选项，以更低的价格提供更少的资源。 

除了纵向扩展虚拟机规格以外，只要 Web 应用是无状态的，就还可以选择通过添加更多的底层虚拟机实例进行横向扩展。 前面创建的应用服务计划仅包含单个虚拟机（辅助角色），因此，所有传入流量最终会受到一个实例的可用资源限制的束缚。 若要再添加一个虚拟机实例，可运行上述同一命令，但不要纵向扩展 SKU，而是横向扩展辅助角色虚拟机的数目。

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

以这种方式横向扩展 Web 应用时，传入的流量会在所有实例之间以透明方式进行负载均衡，因此可立即提高容量，而无需进行任何代码更改或考虑所需的基础结构。 

无状态 Web 应用被视为最佳做法，因为它们能够使缩放（纵向扩展、缩减和横向扩展）变得完全有确定性，没有任何虚拟机或应用实例包含正常运行所需的状态。 

> [!NOTE]
> 尽管本主题的教程演示的是如何运行应用服务计划包含的单个 Web 应用，但可以创建多个 Web 应用并将其部署到同一个计划，以便根据单个计划进行预配和演练。 

## <a name="clean-up"></a>清理

为确保未使用的任何 Azure 资源产生费用，请在 Visual Studio Code 终端中运行以下命令，删除学习本教程期间预配的所有资源。

```shell
az group delete
```

> [!NOTE]
> 清理过程可能需要几分钟才能完成。 

完成后，`az group delete` 命令会将 Azure 帐户保持为开始学习本教程之前所处的同一状态。 资源组的主要优点之一就是能够以一个单位的形式组织、部署和删除 Azure 资源。 因此，我们建议将预期具有相同生存期的资源分组到一起。