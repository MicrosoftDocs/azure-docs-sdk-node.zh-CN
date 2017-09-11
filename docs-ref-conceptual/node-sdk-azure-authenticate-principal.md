---
title: "使用 Node.js 创建 Azure 服务主体"
description: "了解如何通过 Node.js 使用服务主体身份验证"
keywords: "Azure, Node, SDK, API, 身份验证, active directory, 服务主体"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: faa97e7a9ab6a8b6e04eeee590c7b642d26ba620
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="create-an-azure-service-principal-with-nodejs"></a>使用 Node.js 创建 Azure 服务主体 

当有某个应用需要访问资源时，可为应用设置一个标识，并使用其自身的凭据对应用进行身份验证。 此标识称为服务主体。 实质上，这是为 Azure Active Directory 帐户创建了要提供给 SDK 用于身份验证的密钥，这样就不需要用户的干预或提供用户名/密码。

使用服务主体方法可以：
- 将权限分配给应用标识，这些权限不同于自己的权限。 通常情况下，这些权限仅限于应用需执行的操作。
- 运行无人参与的脚本时，使用证书进行身份验证。

本主题介绍三种创建服务主体的方法。

- Azure 门户
- Azure CLI 2.0
- 用于 Node.js 的 Azure SDK

## <a name="create-a-service-principal-using-the-azure-portal"></a>使用 Azure 门户创建服务主体

请遵循[使用门户创建可访问资源的 Azure Active Directory 应用程序和服务主体](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/)主题中所述的步骤来生成服务主体。

## <a name="create-a-service-principal-using-the-azure-cli-20"></a>使用 Azure CLI 2.0 创建服务主体

可执行以下步骤，使用 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) 创建服务主体：

1. 下载 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)。

2. 打开终端窗口。

3. 键入以下命令启动登录过程：

    ```shell
    $ az login
    ```

4. 调用 `az login` 可生成一个 URL 和一个代码。 浏览到指定的 URL，输入该代码，使用 Azure 标识登录（如果已登录，则此过程可自动完成）。 然后，即可通过 CLI 访问帐户。

5. 获取订阅和租户 ID：

    ```shell
    $ az account list
    ```

    下面显示了输出示例：

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    **记下订阅 ID，因为步骤 7 中需要用到。**

6. 创建一个服务主体用于获取 JSON 对象，其中包含在 Azure 中进行身份验证时所需的其他信息片段。

    ```shell
    $ az ad sp create-for-rbac
    ```

    下面显示了输出示例：

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    **记下租户、名称和密码值，因为在步骤 7 中需要用到。**

7. 设置环境变量 - 将 &lt;subscriptionId>、&lt;tenant>、&lt;name> 和 &lt;password> 占位符替换为在步骤 4 和 5 中获取的值。 

    **使用 Bash**

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    **使用 PowerShell**

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a>使用用于 Node.js 的 Azure SDK 创建服务主体

若要使用 JavaScript 以编程方式创建服务主体，请使用 [ServicePrincipal 脚本](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal)。   

## <a name="using-the-service-principal"></a>使用服务主体

以下 JavaScript 代码片段演示在创建服务主体后，如何使用服务主体密钥通过用于 Node.js 的 Azure SDK 进行身份验证。 修改以下占位符：&lt;clientId or appId>、&lt;secret or password> 和 &lt;domain or tenant>。

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
