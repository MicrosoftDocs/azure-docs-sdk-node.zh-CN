---
title: "使用 Visual Studio Code 和 Azure 进行 Node.js 开发"
description: "演示如何创建、使用 Docker 容器化 Node.js 应用并将其部署到 Azure 的完整端到端教程"
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
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="4e1e1-103">使用 Visual Studio Code 和 Azure 进行 Node.js 开发</span><span class="sxs-lookup"><span data-stu-id="4e1e1-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="4e1e1-104">本教程演示如何使用 Visual Studio Code 提取现有的 Node.js 应用、将其“容器化”（使用 Docker），然后将其部署到 Azure。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="4e1e1-105">本教程使用 [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular) 创建并发布的简单待办事项应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="4e1e1-106">这是一个单页 MEAN 应用，因此，它使用 MongoDB 作为数据库，使用 Node/Express 作为 REST API/Web 服务器，使用 Angular.js 1.x 作为前端 UI。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="4e1e1-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="4e1e1-107">Prerequisites</span></span>

<span data-ttu-id="4e1e1-108">若要遵循本演示教程，需要安装以下软件：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="4e1e1-109">Contact.java</span><span class="sxs-lookup"><span data-stu-id="4e1e1-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="4e1e1-110">Docker</span><span class="sxs-lookup"><span data-stu-id="4e1e1-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="4e1e1-111">DockerHub 帐户</span><span class="sxs-lookup"><span data-stu-id="4e1e1-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="4e1e1-112">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="4e1e1-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="4e1e1-113">Azure 帐户</span><span class="sxs-lookup"><span data-stu-id="4e1e1-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="4e1e1-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="4e1e1-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="4e1e1-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - 用于调试演示应用的前端。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="4e1e1-116">MongoDB - 由于演示应用使用 MongoDB，因此，需要在本地运行一个侦听标准 `27017` 端口的 MongoDB 实例。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="4e1e1-117">为实现此目的，最简单的方法是在安装 Docker 之后依次运行 `docker pull mongo` 和 `docker run -it -p 27017:27017 mongo` 命令。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="4e1e1-118">项目设置</span><span class="sxs-lookup"><span data-stu-id="4e1e1-118">Project setup</span></span>

<span data-ttu-id="4e1e1-119">若要开始，请使用以下步骤下载示例项目：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="4e1e1-120">打开 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="4e1e1-121">按 **&lt;F1>** 显示命令面板。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="4e1e1-122">在命令面板的提示符下输入 `gitcl`，选择“Git: 克隆”命令，按 **&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Visual Studio Code 命令面板提示符中的 gitcl 命令](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="4e1e1-124">系统提示输入“存储库 URL”时，请输入 `https://github.com/scotch-io/node-todo`，按 **&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="4e1e1-125">选择（或创建）要将项目克隆到的本地目录。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Visual Studio Code 资源管理器](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="4e1e1-127">集成式终端</span><span class="sxs-lookup"><span data-stu-id="4e1e1-127">Integrated terminal</span></span>

<span data-ttu-id="4e1e1-128">由于这是一个 Node.js 项目，因此首先要做的是确保从 npm 安装项目的所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="4e1e1-129">按 **&lt;Ctrl>\`** 显示 Visual Studio Code 集成式终端。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="4e1e1-130">输入 `yarn`，按 **&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![在 Visual Studio Code 中运行 yarn 命令](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="4e1e1-132">集成式 Git 版本控制</span><span class="sxs-lookup"><span data-stu-id="4e1e1-132">Integrated Git version control</span></span>

<span data-ttu-id="4e1e1-133">通过 Yarn 安装应用的依赖项之后，会创建一个 `yarn.lock` 文件，该文件今后提供可预测的方式在 CI（持续集成）版本、生产部署或其他开发人员计算机上顺利地重新获取确切的依赖项。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="4e1e1-134">以下步骤演示如何将 `yarn.lock` 文件签入源代码管理：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="4e1e1-135">在 Visual Studio Code 中，切换到集成式 Git 选项卡（带有 Git 徽标）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="4e1e1-136">在“消息”框中输入提交消息，并按 **&lt;Ctrl>&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![将 yarn.lock 文件添加到 Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="4e1e1-138">项目和代码导航</span><span class="sxs-lookup"><span data-stu-id="4e1e1-138">Project and code navigation</span></span>

<span data-ttu-id="4e1e1-139">为了在代码库中定位，让我们演练一下 Visual Studio Code 提供的某些导航功能的一些示例。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="4e1e1-140">按 **&lt;Ctrl>P**。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="4e1e1-141">输入 `.js` 显示项目中的所有 JavaScript/JSON 文件以及每个文件的父目录</span><span class="sxs-lookup"><span data-stu-id="4e1e1-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![显示所有 .js* 文件](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="4e1e1-143">选择 `server.js`，即应用的启动脚本。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="4e1e1-144">将鼠标悬停在 **database** 变量（在第 6 行导入）上，以查看其类型。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="4e1e1-145">在开发项目期间，这种在文件中快速检查变量/模块/类型的功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![发现类型](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="4e1e1-147">在变量（例如 **database**）的范围中单击鼠标可查看同一文件中对该变量的所有引用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="4e1e1-148">若要在项目中查看对某个变量的所有引用，请右键单击该变量，并从上下文菜单中选择“查找所有引用”。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![查找对变量的引用](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="4e1e1-150">除了通过将鼠标悬停在变量上来发现其类型以外，还可以检查变量的定义，即使该变量位于另一文件中。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="4e1e1-151">若要了解这项操作，请右键单击“database.localUrl”（第 12 行），并从上下文菜单中选择“查看定义”。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![查看变量的定义](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="4e1e1-153">修改代码并使用自动完成</span><span class="sxs-lookup"><span data-stu-id="4e1e1-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="4e1e1-154">MongoDB 连接字符串在 **database.localUrl** 的声明中经过硬编码。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="4e1e1-155">本部分修改代码以从环境变量检索连接字符串，并介绍 Visual Studio Code 的自动完成功能。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="4e1e1-156">打开 `server.js` 文件</span><span class="sxs-lookup"><span data-stu-id="4e1e1-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="4e1e1-157">将以下代码：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="4e1e1-158">替换为此代码：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="4e1e1-159">请注意，如果手动键入代码（而不是复制并粘贴），则在 `process` 后面键入句点时，Visual Studio Code 会显示 Node.js **process** 全局 API 的可用成员。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![自动完成功能会自动显示 API 的成员](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="4e1e1-161">之所以能够实现自动完成，是因为 Visual Studio Code 在幕后使用 TypeScript（即使是对于 JavaScript）来提供键入信息，然后，在键入时使用这些信息来显示完成列表。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="4e1e1-162">Visual Studio Code 能够检测到 Node.js 项目，因此，能够自动下载适用于 [NPM 中的 Node.js](https://www.npmjs.com/package/@types/node) 的 TypeScript 键入内容文件。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="4e1e1-163">使用键入内容文件可以获取其他 Node.js 全局变量（例如 **Buffer** 和 **setTimeout**）和所有内置模块（例如 **fs** 和 **http**）的自动完成列表。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="4e1e1-164">除了内置的 Node.js API 以外，这种自动获取键入内容的功能也适用于 2,000 多种第三方模块，例如 React、Underscore 和 Express。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="4e1e1-165">例如，若要禁用 MongoDB 在无法连接到配置的 Mongoose 数据库实例时使示例应用发生崩溃，可在第 13 行中插入以下代码行：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="4e1e1-166">在上面的代码中可以看到，不需要采取任何动作就获得了自动完成功能。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![自动完成功能会自动显示 API 的成员](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="4e1e1-168">可以通过浏览 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) 项目（所有 TypeScript 键入内容定义的社区驱动源）来了解哪些模块支持此自动完成功能。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="4e1e1-169">运行应用</span><span class="sxs-lookup"><span data-stu-id="4e1e1-169">Running the app</span></span>

<span data-ttu-id="4e1e1-170">稍微了解代码之后，便可以开始运行应用了。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="4e1e1-171">若要从 Visual Studio Code 运行应用，请按 **&lt;F5>**。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="4e1e1-172">通过 **&lt;F5>**（调试模式）运行代码时，Visual Studio Code 会启动应用，并显示“调试控制台”窗口，其中显示了应用的 stdout。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![通过调试控制台监视应用的 stdout](./media/node-howto-e2e/console.png)

<span data-ttu-id="4e1e1-174">此外，“调试控制台”已附加到最近运行的应用，因此，可以键入要在应用中评估的、也支持自动完成功能的 JavaScript 表达式。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="4e1e1-175">若要了解这项操作，请在控制台中键入 `process.env`：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-175">To see this in action, type `process.env` in the console:</span></span>

![在调试控制台中键入代码](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="4e1e1-177">之所以能够按 **&lt;F5>** 运行应用，是因为当前打开的文件是 JavaScript 文件 (`server.js`)。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="4e1e1-178">因此，Visual Studio Code 假设项目是 Node.js 应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="4e1e1-179">如果在 Visual Studio Code 中关闭所有 JavaScript 文件，再按 **&lt;F5>**，则 Visual Studio Code 会查询环境：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![指定运行时环境](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="4e1e1-181">打开浏览器并导航到 `http://localhost:8080` 以查看正在运行的应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="4e1e1-182">在文本框中键入一条消息，并添加/删除几个待办事项来感受应用的工作方式。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![正在运行的待办事项应用](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="4e1e1-184">调试</span><span class="sxs-lookup"><span data-stu-id="4e1e1-184">Debugging</span></span>

<span data-ttu-id="4e1e1-185">除了能够通过集成控制台运行应用并与之交互以外，Visual Studio Code 还提供直接在代码中设置断点的功能。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="4e1e1-186">例如，按 **&lt;Ctrl>P** 可显示文件选取器。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="4e1e1-187">显示文件选取器后，请键入 `route`，选择 `route.js` 文件。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="4e1e1-188">在第 28 行设置一个断点，用于表示当应用尝试添加待办事项条目时要调用的 Express 路由。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="4e1e1-189">若要设置断点，只需在编辑器中单击行号左侧的区域，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![在 Visual Studio Code 中设置断点](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="4e1e1-191">除了标准断点以外，Visual Studio Code 还支持可用于自定义应用何时应暂停执行的条件断点。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="4e1e1-192">若要设置条件断点，请右键单击要暂停执行的行左侧的区域，选择“添加条件断点...”，并指定 JavaScript 表达式（例如 `foo = "bar"`）或执行计数来定义要在哪种条件下暂停执行。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="4e1e1-193">设置断点后，返回到正在运行的应用并添加一个待办事项条目。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="4e1e1-194">添加待办事项条目会立即导致应用在设置了断点的第 28 行处暂停执行：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Visual Studio Code 在断点处暂停执行](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="4e1e1-196">暂停应用程序后，可将鼠标悬停在代码的表达式上，以查看其当前值，检查局部变量/监视项和调用堆栈，并使用调试工具栏逐步执行代码。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="4e1e1-197">按 **&lt;F5>** 可恢复应用的执行。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="4e1e1-198">完整堆栈调试</span><span class="sxs-lookup"><span data-stu-id="4e1e1-198">Full-stack debugging</span></span>

<span data-ttu-id="4e1e1-199">如本主题前面所述，该待办事项应用是一个 MEAN 应用 - 这意味着，其前端和后端都是使用 JavaScript 编写的。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="4e1e1-200">因此，在当前调试后端 (Node/Express) 代码过程中的某个时间点，可能需要调试前端 (Angular) 代码。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="4e1e1-201">出于此目的，Visual Studio Code 提供庞大的扩展生态系统，包括集成的 Chrome 调试。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="4e1e1-202">切换到“扩展”选项卡上，在搜索框中键入 `chrome`：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Visual Studio Code 的 Chrome 调试扩展](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="4e1e1-204">选择名为“适用于 Chrome 的调试程序”的扩展，再选择“安装”。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="4e1e1-205">安装 Chrome 调试扩展后，选择“重新加载”关闭再重新打开 Visual Studio Code 以激活该扩展。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![安装 Chrome 调试扩展后重新加载 Visual Studio Code](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="4e1e1-207">尽管无需进行任何特定于 Visual Studio Code 的配置即可运行和调试 Node.js 代码，但若要调试前端 Web 应用，需要生成一个 `launch.json` 文件来指示 Visual Studio Code 如何运行应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="4e1e1-208">若要生成 `launch.json` 文件，请切换到“调试”选项卡，单击齿轮图标（顶部应有一个小红点），并选择 **node.js** 环境。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![Visual Studio Code 中用于配置 launch.json 文件的选项](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="4e1e1-210">创建的 `launch.json` 文件如下所示，它告知 Visual Studio Code 如何启动和/或附加到应用以便对其进行调试。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

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

<span data-ttu-id="4e1e1-211">请注意，Visual Studio Code 能够检测到应用的启动脚本为 `server.js`。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="4e1e1-212">打开 `launch.json` 文件后，依次选择“添加配置”（右下角）、“Chrome: 使用 userDataDir 启动”。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![将 Chrome 配置添加到 Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="4e1e1-214">为 Chrome 添加新的运行配置可以调试前端 JavaScript 代码。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="4e1e1-215">可将鼠标悬停在指定的任何设置上，以查看有关该项设置的功能的文档。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="4e1e1-216">此外请注意，Visual Studio Code 会自动检测应用的 URL。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="4e1e1-217">请 **webRoot** 属性更新为 `${workspaceRoot}/public`，使 Chrome 调试程序知道在何处查找应用的前端资产：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

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

<span data-ttu-id="4e1e1-218">若要同时启动/调试前端和后端，需创建一个复合运行配置来告知 Visual Studio Code 要并行运行哪个配置集。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="4e1e1-219">在 `launch.json` 文件中添加以下代码片段作为顶级属性（现有 **configurations** 属性的同级）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="4e1e1-220">在 **compounds.configurations** 数组中指定的字符串值引用**配置**列表中各个条目的**名称**。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="4e1e1-221">如果已修改这些名称，则需要在数组中进行相应的更改。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="4e1e1-222">若要了解这项操作，请切换到调试选项卡，将选定的配置更改为 **Full-Stack**（复合配置的名称），并按 **&lt;F5>** 运行该配置。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![在 Visual Studio Code 中运行配置](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="4e1e1-224">运行配置会启动 Node.js 应用（可在调试控制台输出中查看）和 Chrome（配置为导航到 `http://localhost:8080` 上的 Node.js 应用）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="4e1e1-225">按 **&lt;Ctrl>P**，并输入（或选择）`todos.js`，即应用前端的 Angular 主控制器。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="4e1e1-226">在第 11 行设置一个断点，这是要创建的新待办事项条目的入口点。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="4e1e1-227">返回到正在运行的应用，添加新的待办事项条目，然后可以看到，Visual Studio Code 现已暂停 Angular 代码中的执行。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![在 Visual Studio Code 中调试前端代码](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="4e1e1-229">与执行 Node.js 调试时一样，可以通过将鼠标悬停在表达式上来查看局部变量/监视项、在控制台中评估表达式，等等。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="4e1e1-230">请注意两个很棒的功能：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="4e1e1-231">“调用堆栈”窗格显示两个不同的堆栈：“Node”和“Chrome”，并指示当前暂停了哪个堆栈。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="4e1e1-232">可在前端代码与后端代码之间逐步调试。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-232">You can step between front and back-end code.</span></span> <span data-ttu-id="4e1e1-233">若要进行测试，请按 **&lt;F5>** 运行并命中前面在 Express 路由中设置的断点。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="4e1e1-234">通过此设置，现在可以直接在 Visual Studio Code 中有效调试前端、后端或完整堆栈的 JavaScript 代码。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="4e1e1-235">此外，复合调试程序的概念并不仅仅局限于两个目标进程，而且也不仅仅局限于 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="4e1e1-236">因此，在微服务应用（可能是 polyglot）中操作时，可以使用完全相同的工作流（前提是安装语言/框架的相应扩展）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="4e1e1-237">使用 Docker 容器化应用</span><span class="sxs-lookup"><span data-stu-id="4e1e1-237">Dockerizing the app</span></span>

<span data-ttu-id="4e1e1-238">本部分重点介绍 Visual Studio Code 提供的、用于通过 [Docker](https://www.docker.com/) 进行开发的体验。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="4e1e1-239">Node.js 开发人员可以使用 Docker 来为开发、CI（持续集成）和生产环境提供可移植的应用部署。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="4e1e1-240">由于 Docker 对于某些用户而言有一定的难度，Visual Studio Code 提供了一个扩展来帮助某些用户在应用中简化 Docker 的使用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="4e1e1-241">切换回到“扩展”选项卡，搜索 `docker`，选择“Docker”扩展。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="4e1e1-242">安装 Docker 扩展，重新加载 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![安装 Visual Studio Code 的 Docker 扩展](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="4e1e1-244">Visual Studio Code 的 Docker 扩展包含一条命令用于生成 *Dockerfile* 以及现有项目的 `docker-compose.yml` 文件。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="4e1e1-245">若要查看可用的 Docker 命令，请通过 **&lt;F1>** 显示命令面板并键入 `docker`。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="4e1e1-246">Visual Studio 的 Docker 扩展支持的命令</span><span class="sxs-lookup"><span data-stu-id="4e1e1-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="4e1e1-247">选择“Docker: 将 Docker 文件添加到工作区”，选择“Node.js”作为应用平台，并指定应用需公开端口 `8080`。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="4e1e1-248">Docker 命令会生成可立即开始使用的完整 `Dockerfile` 和 Docker-compose 文件。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![生成的 Dockerfile](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="4e1e1-250">Docker 扩展还针对 `Dockerfiles` 和 `docker-compose.yml` 文件提供自动完成功能。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="4e1e1-251">若要了解这项操作，请打开 `Dockerfile` 并将第 2 行：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="4e1e1-252">更改为：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="4e1e1-253">将光标定位在 `mhart` 中的 `t` 后面，按 **&lt;Ctrl>&lt;Space>** 查看 `mhart` 在 DockerHub 中发布的所有映像存储库。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Docker 扩展自动完成](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="4e1e1-255">选择 `mhart/alpine-node`（提供此应用所需的所有内容）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="4e1e1-256">一般而言，映像越小越好，因为这样可以尽量加速应用的生成和部署，从而可以更快地完成分发和缩放。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="4e1e1-257">生成 `Dockerfile` 后，需要生成实际的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="4e1e1-258">同样，可以使用 Docker 扩展在 Visual Studio Code 中安装的命令。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="4e1e1-259">按 **&lt;F1>**，在命令面板中输入 `dockerb`，选择“Docker: 生成映像”命令。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="4e1e1-260">选择刚刚生成并修改的 `/Dockerfile`。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="4e1e1-261">指定包含 DockerHub 用户名的标记（例如 `lostintangent/node`）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="4e1e1-262">按 **&lt;ENTER>** 启动集成式终端窗口，其中显示了正在生成的 Docker 映像的输出。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Docker 映像生成状态](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="4e1e1-264">请注意，该命令已自动完成 `docker build` 的运行过程（这是可以选择用来提高工作效率的另一个例子）。也可以直接使用 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="4e1e1-265">此时，若要使此映像可方便用于部署，只需将它推送到 DockerHub。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="4e1e1-266">为此，请确保已在 CLI 中运行 `docker login` 并输入帐户凭据完成了 DockerHub 的身份验证。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="4e1e1-267">然后，可在 Visual Studio Code 中打开命令面板，输入 `dockerpush`，并选择 `Docker: Push` 命令。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="4e1e1-268">选择刚刚生成的映像标记（例如 `lostintangent/node`），按 **&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="4e1e1-269">该命令会自动调用 `docker push` 并在集成式终端中显示输出。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="4e1e1-270">部署应用</span><span class="sxs-lookup"><span data-stu-id="4e1e1-270">Deploying the app</span></span>

<span data-ttu-id="4e1e1-271">使用 Docker 容器化应用并将它推送到 DockerHub 之后，需要将它部署到云中，使全球用户都能看到它。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="4e1e1-272">为此，可以使用 Azure 应用服务，这是 Azure 的 PaaS 产品。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="4e1e1-273">应用服务提供两项面向 Node.js 开发人员的功能：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="4e1e1-274">支持基于 Linux 的 VM，减少了使用本机 Node 模块生成的应用的不兼容性，以及可能不支持 Windows 和/或行为有所不同的其他工具的不兼容性。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="4e1e1-275">支持基于 Docker 的部署，允许指定 Docker 映像的名称，并允许应用服务自动提取、部署和缩放映像。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="4e1e1-276">若要开始，请打开 Visual Studio 终端。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="4e1e1-277">将使用新的 Azure CLI 2.0 来管理 Azure 帐户并预配所需的基础结构来运行该待办事项应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="4e1e1-278">（如前面的先决条件中所述）从 CLI 使用 `az login` 命令登录到帐户后，请执行以下步骤来预配应用服务实例并部署待办事项应用容器：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="4e1e1-279">创建一个资源组，可将它视为用于帮助组织 Azure 资源的命名空间或目录。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="4e1e1-280">`-n` 选项用于指定组的名称，可采用任何值。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="4e1e1-281">`-l` 选项指示资源组的位置。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="4e1e1-282">在预览期，Linux 上的应用服务支持仅在某些区域可用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="4e1e1-283">因此，如果你不在美国西部并想要知道其他哪些区域提供此项功能，请从 CLI 运行 `az appservice list-locations --linux-workers-enabled` 来查看数据中心选项。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="4e1e1-284">将新建的资源组设为默认资源组，以便可以继续使用 CLI，而无需在每个 CLI 调用中显式指定资源组：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="4e1e1-285">创建应用服务计划，用于管理要将应用部署到的底层虚拟机的创建和缩放。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="4e1e1-286">同样，可为 `n` 选项指定任何所需的值。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="4e1e1-287">--is-linux 指示想要使用基于 Linux 的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="4e1e1-288">如果不指定此选项，CLI 会默认预配基于 Windows 的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="4e1e1-289">创建应用服务 Web 应用，用于表示要在刚刚创建的计划和资源组中运行的实际待办事项应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="4e1e1-290">可将 Web 应用视为与进程或容器同义，将计划视为与运行该应用的虚拟机/容器主机同义。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="4e1e1-291">此外，在创建 Web 应用的过程中，需将它配置为使用已发布到 DockerHub 的 Docker 映像：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="4e1e1-292">如果想要使用 Git 部署而非自定义容器，请参阅[在 Azure 中创建 Node.js Web 应用](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs)一文。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="4e1e1-293">将 Web 应用设为默认 Web 实例：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="4e1e1-294">启动应用，查看将在 `*.azurewebsites.net` URL 上部署的容器：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![浏览器中运行的待办事项应用](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="4e1e1-296">首次加载应用可能需要几分钟时间，因为应用服务必须从 DockerHub 提取 Docker 映像，然后再启动它。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="4e1e1-297">目前只是部署并运行了待办事项应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="4e1e1-298">现已部署待办事项应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-298">You have now deployed the todo app.</span></span> <span data-ttu-id="4e1e1-299">但是，旋转的图标指示该应用无法连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="4e1e1-300">这是因为，在开发期间使用的是 MongoDB 的本地实例，显然无法 Azure 数据中心内部访问它。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="4e1e1-301">由于已将应用修改为通过环境变量接受连接字符串，因此，只需启动 MongoDB 服务器并重新配置应用服务实例即可引用环境变量。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="4e1e1-302">下一部分会演示此操作。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="4e1e1-303">预配 MongoDB 服务器</span><span class="sxs-lookup"><span data-stu-id="4e1e1-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="4e1e1-304">尽管我们可以自行配置 MongoDB 服务器（或副本集）并管理该基础结构，但也可以使用 Azure 提供的名为 [Cosmos DB](https://azure.microsoft.com/services/documentdb/) 的解决方案。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="4e1e1-305">Cosmos DB 是完全托管的、可异地复制的高性能 NoSQL 数据库，提供 MongoDB 兼容性层。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="4e1e1-306">这意味着，可将现有的 MEAN 应用（或任何 MongoDB 客户端/工具，例如 [Studio 3T](https://studio3t.com/)）指向 Cosmos DB，而无需更改除连接字符串以外的其他任何设置。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="4e1e1-307">以下步骤演示如何执行此操作：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="4e1e1-308">在 Visual Studio Code 终端中运行以下命令，创建 Cosmos DB 服务的 MongoDB 兼容实例。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="4e1e1-309">将 **<NAME>** 占位符替换为全局唯一值（Cosmos DB 使用此名称来生成数据库的服务器 URL）：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="4e1e1-310">检索此实例的 MongoDB 连接字符串：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="4e1e1-311">更新 Web 应用的 **MONGODB_URL** 环境变量，使之连接到新预配的 Cosmos DB 实例，而不是尝试连接到本地运行的 MongoDB 服务器（并不存在！）：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="4e1e1-312">返回到浏览器并刷新。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="4e1e1-313">尝试添加和删除某个待办事项来证明该应用现在是否可正常工作，而无需更改任何设置！</span><span class="sxs-lookup"><span data-stu-id="4e1e1-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="4e1e1-314">将环境变量设置为创建的、可完全模拟 MongoDB 数据库的 Cosmos DB 实例。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![连接到数据库之后的演示应用](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="4e1e1-316">如果需要，可切换回到的 Cosmos DB 实例，并增大（或减小）MongoDB 实例所需的保留吞吐量，然后，即可享受到流量的添加好处，且无需手动管理任何基础结构。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="4e1e1-317">此外，Cosmos DB 可自动为每个文档和属性编制索引。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="4e1e1-318">这样，就不需要分析速度缓慢的查询或手动调整索引。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="4e1e1-319">只需根据需要进行预配和缩放，让 Cosmos DB 处理其余的工作。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="4e1e1-320">托管专用 Docker 注册表</span><span class="sxs-lookup"><span data-stu-id="4e1e1-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="4e1e1-321">DockerHub 提供超卓的体验来分发容器映像，但在某些情况下，你可能想要托管自己的专用 Docker 注册表 - 例如，为了获得安全/监管或性能方面的优势。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="4e1e1-322">为此，Azure 提供 [Azure 容器注册表](https://azure.microsoft.com/services/container-registry/) (ACR)，用于启动其后备存储位于 Web 应用所在的同一数据中心内的自有 Docker 注册表（可以加速提取过程）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="4e1e1-323">ACR 还提供全面的内容控制和访问控制 - 例如，谁可以推送或提取映像。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="4e1e1-324">可运行以下命令来实现自定义注册表的预配。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="4e1e1-325">（请将 **<NAME>** 占位符替换为全局唯一值，因为 ACR 使用指定的值来生成注册表的登录服务器 URL。）</span><span class="sxs-lookup"><span data-stu-id="4e1e1-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="4e1e1-326">为方便阐述，本主题的示例使用了**管理员帐户**，但不建议对生产注册表使用该帐户。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="4e1e1-327">`az acr create` 命令（通过 `LOGIN SERVER` 列）显示可用于在 Docker CLI 中进行登录的登录服务器 URL（例如 `ninademo.azurecr.io`）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="4e1e1-328">此外，该命令会生成可用于对服务器进行身份验证的管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="4e1e1-329">若要检索这些凭据，请运行以下命令，并记下显示的用户名和密码：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="4e1e1-330">借助上一步骤生成的凭据和单个登录服务器，可以使用标准 Docker CLI 工作流登录到注册表。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="4e1e1-331">现在，可使用以下命令来标记 Docker 容器，指示它与专用注册表相关联（请将 `lostintangent/node` 替换为容器映像的名称）。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="4e1e1-332">最后，将标记的映像推送到专用 Docker 注册表。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="4e1e1-333">现已将容器存储在自己的专用注册表中，并且可以像使用 DockerHub 时一样，在 Docker CLI 中顺畅地继续工作。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="4e1e1-334">若要指示应用服务 Web 应用从专用注册表提取数据，只需运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="4e1e1-335">请确保在 `-r` 选项的开头添加 `https://` 前缀。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="4e1e1-336">但是，请不要为容器映像名称添加前缀。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="4e1e1-337">如果在浏览器中刷新应用，所有内容和功能的外观与行为应该相同。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="4e1e1-338">但是，应用现在是通过专用 Docker 注册表运行的。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="4e1e1-339">更新应用后，请按如上所述标记和推送更改，并在应用服务容器配置中更新标记。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="4e1e1-340">配置自定义域名</span><span class="sxs-lookup"><span data-stu-id="4e1e1-340">Configuring a custom domain name</span></span>

<span data-ttu-id="4e1e1-341">尽管 `*.azurewebsites.net` URL 非常适合用于测试，但在某些情况下，你可能想要将自定义域名添加到 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="4e1e1-342">从注册机构购买域名后，只需在其中添加一条指向 Web 应用外部 IP（实际上是一个负载均衡器）的 `A` 记录。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="4e1e1-343">可运行以下命令检索此 IP：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="4e1e1-344">除了添加 `A` 记录以外，还需要在域中添加一条指向目前所用 `*.azurewebsites.net` 域的 `TXT` 记录。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="4e1e1-345">`A` 和 `TXT` 记录的组合可让 Azure 验证该域是否由你拥有。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="4e1e1-346">创建这些记录并传播 DNS 更改之后，请将自定义域注册到 Azure，使 Azure 能够正确处理传入的流量。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="4e1e1-347">只有在传播 DNS 更改之后，该命令才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="4e1e1-348">打开浏览器并导航到自定义域，查看它现在是否能够解析为 Azure 上部署的应用。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="4e1e1-349">纵向和横向扩展</span><span class="sxs-lookup"><span data-stu-id="4e1e1-349">Scaling up and out</span></span>

<span data-ttu-id="4e1e1-350">在将来的某个时候，你的 Web 应用可能会变得很受欢迎，以致分配的资源（CPU 和 RAM）并不足以处理流量和操作需求的提高。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="4e1e1-351">前面创建的应用服务计划 (**B1**) 附带 1 个 CPU 核心和 1.75 GB RAM，可能很快就会达到最大用量。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="4e1e1-352">**B2** 计划附带的 RAM 和 CPU 是 B1 的两倍，因此，如果发现应用即将耗尽其中的任何一项资源，可通过运行以下命令来纵向扩展底层虚拟机：</span><span class="sxs-lookup"><span data-stu-id="4e1e1-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="4e1e1-353">有关 Azure 应用计划的定价详细信息和规范，请参阅[应用服务定价](https://azure.microsoft.com/pricing/details/app-service/)一文</span><span class="sxs-lookup"><span data-stu-id="4e1e1-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="4e1e1-354">几分钟后，Web 应用即会迁移到请求的硬件，可开始利用相关的资源。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="4e1e1-355">除了扩展资源以外，还可以运行上述同一命令来缩减资源：指定 `--sku` 选项，以更低的价格提供更少的资源。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="4e1e1-356">除了纵向扩展虚拟机规格以外，只要 Web 应用是无状态的，就还可以选择通过添加更多的底层虚拟机实例进行横向扩展。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="4e1e1-357">前面创建的应用服务计划仅包含单个虚拟机（辅助角色），因此，所有传入流量最终会受到一个实例的可用资源限制的束缚。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="4e1e1-358">若要再添加一个虚拟机实例，可运行上述同一命令，但不要纵向扩展 SKU，而是横向扩展辅助角色虚拟机的数目。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="4e1e1-359">以这种方式横向扩展 Web 应用时，传入的流量会在所有实例之间以透明方式进行负载均衡，因此可立即提高容量，而无需进行任何代码更改或考虑所需的基础结构。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="4e1e1-360">无状态 Web 应用被视为最佳做法，因为它们能够使缩放（纵向扩展、缩减和横向扩展）变得完全有确定性，没有任何虚拟机或应用实例包含正常运行所需的状态。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="4e1e1-361">尽管本主题的教程演示的是如何运行应用服务计划包含的单个 Web 应用，但可以创建多个 Web 应用并将其部署到同一个计划，以便根据单个计划进行预配和演练。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="4e1e1-362">清理</span><span class="sxs-lookup"><span data-stu-id="4e1e1-362">Clean-up</span></span>

<span data-ttu-id="4e1e1-363">为确保未使用的任何 Azure 资源产生费用，请在 Visual Studio Code 终端中运行以下命令，删除学习本教程期间预配的所有资源。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="4e1e1-364">清理过程可能需要几分钟才能完成。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="4e1e1-365">完成后，`az group delete` 命令会将 Azure 帐户保持为开始学习本教程之前所处的同一状态。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="4e1e1-366">资源组的主要优点之一就是能够以一个单位的形式组织、部署和删除 Azure 资源。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="4e1e1-367">因此，我们建议将预期具有相同生存期的资源分组到一起。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>