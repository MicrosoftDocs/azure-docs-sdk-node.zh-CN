---
title: 使用用于 Node.js 的 Azure 管理模块进行身份验证
description: 在用于 Node.js 的 Azure 管理模块中使用服务主体进行身份验证
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: b665c537bf17d08c44357009552054d6b2e609d2
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="d9156-103">使用用于 Node.js 的 Azure 模块进行身份验证</span><span class="sxs-lookup"><span data-stu-id="d9156-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="d9156-104">在被实例化时，所有服务 API 需要通过 `credentials` 对象进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d9156-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="d9156-105">可以使用三种方法通过用于 Node.js 的 Azure SDK 进行身份验证和创建所需的凭据：</span><span class="sxs-lookup"><span data-stu-id="d9156-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="d9156-106">基本身份验证</span><span class="sxs-lookup"><span data-stu-id="d9156-106">Basic authentication</span></span>
- <span data-ttu-id="d9156-107">交互式登录</span><span class="sxs-lookup"><span data-stu-id="d9156-107">Interactive login</span></span>
- <span data-ttu-id="d9156-108">服务主体身份验证</span><span class="sxs-lookup"><span data-stu-id="d9156-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="d9156-109">基本身份验证</span><span class="sxs-lookup"><span data-stu-id="d9156-109">Basic authentication</span></span>

<span data-ttu-id="d9156-110">若要使用 Azure 帐户凭据以编程方式进行身份验证，请使用 `loginWithUsernamePassword` 函数。</span><span class="sxs-lookup"><span data-stu-id="d9156-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="d9156-111">以下 JavaScript 代码片段演示如何使用存储为环境变量的凭据执行基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="d9156-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="d9156-112">交互式登录</span><span class="sxs-lookup"><span data-stu-id="d9156-112">Interactive login</span></span>

<span data-ttu-id="d9156-113">交互式登录提供一个链接和一个代码让用户从浏览器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d9156-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="d9156-114">如果同一个脚本使用多个帐户或者希望用户干预，可使用此方法。</span><span class="sxs-lookup"><span data-stu-id="d9156-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="d9156-115">服务主体身份验证</span><span class="sxs-lookup"><span data-stu-id="d9156-115">Service principal authentication</span></span>

<span data-ttu-id="d9156-116">[交互式登录](#interactive-login)是最简单的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="d9156-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="d9156-117">但是，在使用 Node.js SDK 时，我们可能想要使用服务主体身份验证，而不是提供自己的帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="d9156-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="d9156-118">[使用 Node.js 创建 Azure 服务主体](./node-sdk-azure-authenticate-principal.md)主题介绍了创建（和使用）服务主体的各种方法。</span><span class="sxs-lookup"><span data-stu-id="d9156-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 