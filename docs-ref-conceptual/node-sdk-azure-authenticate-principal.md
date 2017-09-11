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
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="18fec-104">使用 Node.js 创建 Azure 服务主体</span><span class="sxs-lookup"><span data-stu-id="18fec-104">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="18fec-105">当有某个应用需要访问资源时，可为应用设置一个标识，并使用其自身的凭据对应用进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="18fec-105">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="18fec-106">此标识称为服务主体。</span><span class="sxs-lookup"><span data-stu-id="18fec-106">This identity is known as a *service principal*.</span></span> <span data-ttu-id="18fec-107">实质上，这是为 Azure Active Directory 帐户创建了要提供给 SDK 用于身份验证的密钥，这样就不需要用户的干预或提供用户名/密码。</span><span class="sxs-lookup"><span data-stu-id="18fec-107">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="18fec-108">使用服务主体方法可以：</span><span class="sxs-lookup"><span data-stu-id="18fec-108">The service principal approach enables you to:</span></span>
- <span data-ttu-id="18fec-109">将权限分配给应用标识，这些权限不同于自己的权限。</span><span class="sxs-lookup"><span data-stu-id="18fec-109">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="18fec-110">通常情况下，这些权限仅限于应用需执行的操作。</span><span class="sxs-lookup"><span data-stu-id="18fec-110">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="18fec-111">运行无人参与的脚本时，使用证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="18fec-111">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="18fec-112">本主题介绍三种创建服务主体的方法。</span><span class="sxs-lookup"><span data-stu-id="18fec-112">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="18fec-113">Azure 门户</span><span class="sxs-lookup"><span data-stu-id="18fec-113">Azure portal</span></span>
- <span data-ttu-id="18fec-114">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="18fec-114">Azure CLI 2.0</span></span>
- <span data-ttu-id="18fec-115">用于 Node.js 的 Azure SDK</span><span class="sxs-lookup"><span data-stu-id="18fec-115">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="18fec-116">使用 Azure 门户创建服务主体</span><span class="sxs-lookup"><span data-stu-id="18fec-116">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="18fec-117">请遵循[使用门户创建可访问资源的 Azure Active Directory 应用程序和服务主体](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/)主题中所述的步骤来生成服务主体。</span><span class="sxs-lookup"><span data-stu-id="18fec-117">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="18fec-118">使用 Azure CLI 2.0 创建服务主体</span><span class="sxs-lookup"><span data-stu-id="18fec-118">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="18fec-119">可执行以下步骤，使用 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) 创建服务主体：</span><span class="sxs-lookup"><span data-stu-id="18fec-119">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="18fec-120">下载 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)。</span><span class="sxs-lookup"><span data-stu-id="18fec-120">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="18fec-121">打开终端窗口。</span><span class="sxs-lookup"><span data-stu-id="18fec-121">Open a terminal window.</span></span>

3. <span data-ttu-id="18fec-122">键入以下命令启动登录过程：</span><span class="sxs-lookup"><span data-stu-id="18fec-122">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="18fec-123">调用 `az login` 可生成一个 URL 和一个代码。</span><span class="sxs-lookup"><span data-stu-id="18fec-123">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="18fec-124">浏览到指定的 URL，输入该代码，使用 Azure 标识登录（如果已登录，则此过程可自动完成）。</span><span class="sxs-lookup"><span data-stu-id="18fec-124">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="18fec-125">然后，即可通过 CLI 访问帐户。</span><span class="sxs-lookup"><span data-stu-id="18fec-125">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="18fec-126">获取订阅和租户 ID：</span><span class="sxs-lookup"><span data-stu-id="18fec-126">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="18fec-127">下面显示了输出示例：</span><span class="sxs-lookup"><span data-stu-id="18fec-127">The following shows an example of the output:</span></span>

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

    <span data-ttu-id="18fec-128">**记下订阅 ID，因为步骤 7 中需要用到。**</span><span class="sxs-lookup"><span data-stu-id="18fec-128">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="18fec-129">创建一个服务主体用于获取 JSON 对象，其中包含在 Azure 中进行身份验证时所需的其他信息片段。</span><span class="sxs-lookup"><span data-stu-id="18fec-129">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="18fec-130">下面显示了输出示例：</span><span class="sxs-lookup"><span data-stu-id="18fec-130">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="18fec-131">**记下租户、名称和密码值，因为在步骤 7 中需要用到。**</span><span class="sxs-lookup"><span data-stu-id="18fec-131">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="18fec-132">设置环境变量 - 将 &lt;subscriptionId>、&lt;tenant>、&lt;name> 和 &lt;password> 占位符替换为在步骤 4 和 5 中获取的值。</span><span class="sxs-lookup"><span data-stu-id="18fec-132">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="18fec-133">**使用 Bash**</span><span class="sxs-lookup"><span data-stu-id="18fec-133">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="18fec-134">**使用 PowerShell**</span><span class="sxs-lookup"><span data-stu-id="18fec-134">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="18fec-135">使用用于 Node.js 的 Azure SDK 创建服务主体</span><span class="sxs-lookup"><span data-stu-id="18fec-135">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="18fec-136">若要使用 JavaScript 以编程方式创建服务主体，请使用 [ServicePrincipal 脚本](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal)。</span><span class="sxs-lookup"><span data-stu-id="18fec-136">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="18fec-137">使用服务主体</span><span class="sxs-lookup"><span data-stu-id="18fec-137">Using the service principal</span></span>

<span data-ttu-id="18fec-138">以下 JavaScript 代码片段演示在创建服务主体后，如何使用服务主体密钥通过用于 Node.js 的 Azure SDK 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="18fec-138">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="18fec-139">修改以下占位符：&lt;clientId or appId>、&lt;secret or password> 和 &lt;domain or tenant>。</span><span class="sxs-lookup"><span data-stu-id="18fec-139">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

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
