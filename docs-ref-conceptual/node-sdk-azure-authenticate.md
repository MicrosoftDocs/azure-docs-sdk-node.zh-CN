---
title: "使用用于 Node.js 的 Azure 管理模块进行身份验证"
description: "在用于 Node.js 的 Azure 管理模块中使用服务主体进行身份验证"
keywords: "Azure, Node, SDK, API, 身份验证, active directory, 服务主体"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="5b3b7-104">使用用于 Node.js 的 Azure 模块进行身份验证</span><span class="sxs-lookup"><span data-stu-id="5b3b7-104">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="5b3b7-105">在被实例化时，所有服务 API 需要通过 `credentials` 对象进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="5b3b7-105">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="5b3b7-106">可以使用三种方法通过用于 Node.js 的 Azure SDK 进行身份验证和创建所需的凭据：</span><span class="sxs-lookup"><span data-stu-id="5b3b7-106">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="5b3b7-107">基本身份验证</span><span class="sxs-lookup"><span data-stu-id="5b3b7-107">Basic authentication</span></span>
- <span data-ttu-id="5b3b7-108">交互式登录</span><span class="sxs-lookup"><span data-stu-id="5b3b7-108">Interactive login</span></span>
- <span data-ttu-id="5b3b7-109">服务主体身份验证</span><span class="sxs-lookup"><span data-stu-id="5b3b7-109">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="5b3b7-110">基本身份验证</span><span class="sxs-lookup"><span data-stu-id="5b3b7-110">Basic authentication</span></span>

<span data-ttu-id="5b3b7-111">若要使用 Azure 帐户凭据以编程方式进行身份验证，请使用 `loginWithUsernamePassword` 函数。</span><span class="sxs-lookup"><span data-stu-id="5b3b7-111">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="5b3b7-112">以下 JavaScript 代码片段演示如何使用存储为环境变量的凭据执行基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="5b3b7-112">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a><span data-ttu-id="5b3b7-113">交互式登录</span><span class="sxs-lookup"><span data-stu-id="5b3b7-113">Interactive login</span></span>

<span data-ttu-id="5b3b7-114">交互式登录提供一个链接和一个代码让用户从浏览器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="5b3b7-114">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="5b3b7-115">如果同一个脚本使用多个帐户或者希望用户干预，可使用此方法。</span><span class="sxs-lookup"><span data-stu-id="5b3b7-115">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="5b3b7-116">服务主体身份验证</span><span class="sxs-lookup"><span data-stu-id="5b3b7-116">Service principal authentication</span></span>

<span data-ttu-id="5b3b7-117">[交互式登录](#interactive-login)是最简单的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="5b3b7-117">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="5b3b7-118">但是，在使用 Node.js SDK 时，我们可能想要使用服务主体身份验证，而不是提供自己的帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="5b3b7-118">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="5b3b7-119">[使用 Node.js 创建 Azure 服务主体](./node-sdk-azure-authenticate-principal.md)主题介绍了创建（和使用）服务主体的各种方法。</span><span class="sxs-lookup"><span data-stu-id="5b3b7-119">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 