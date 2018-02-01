---
title: "用于 Node.js 的 Azure Active Directory 模块"
description: "用于 Node.js 的 Azure Active Directory 模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="74770-103">用于 Node.js 的 Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="74770-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="74770-104">概述</span><span class="sxs-lookup"><span data-stu-id="74770-104">Overview</span></span>

<span data-ttu-id="74770-105">[用于 Node.js 的 Azure Active Directory 身份验证库 (ADAL)](https://www.npmjs.com/package/adal-node) 可让 Node.js 应用程序在 AAD 中进行身份验证，以访问 AAD 保护的 Web 资源。</span><span class="sxs-lookup"><span data-stu-id="74770-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="74770-106">客户端程序包</span><span class="sxs-lookup"><span data-stu-id="74770-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="74770-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="74770-107">Install the npm modules</span></span>

<span data-ttu-id="74770-108">使用 npm 安装 Azure 存储客户端或管理模块。</span><span class="sxs-lookup"><span data-stu-id="74770-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="74770-109">示例</span><span class="sxs-lookup"><span data-stu-id="74770-109">Example</span></span>

<span data-ttu-id="74770-110">此示例摘自[客户端凭据示例](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)，演示如何通过客户端凭据进行服务器到服务器的身份验证。</span><span class="sxs-lookup"><span data-stu-id="74770-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a><span data-ttu-id="74770-111">示例</span><span class="sxs-lookup"><span data-stu-id="74770-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="74770-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="74770-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
