---
title: "用于 Node.js 的 Azure Active Directory 模块"
description: "用于 Node.js 的 Azure Active Directory 模块参考"
keywords: "Azure, Node, SDK, API, 存储, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: d0084faa78986bd5518526c6eb84b9c13fdb10bf
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="3b3d9-104">用于 Node.js 的 Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="3b3d9-104">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="3b3d9-105">概述</span><span class="sxs-lookup"><span data-stu-id="3b3d9-105">Overview</span></span>

<span data-ttu-id="3b3d9-106">[用于 Node.js 的 Azure Active Directory 身份验证库 (ADAL)](https://www.npmjs.com/package/adal-node) 可让 Node.js 应用程序在 AAD 中进行身份验证，以访问 AAD 保护的 Web 资源。</span><span class="sxs-lookup"><span data-stu-id="3b3d9-106">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="3b3d9-107">客户端程序包</span><span class="sxs-lookup"><span data-stu-id="3b3d9-107">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="3b3d9-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3b3d9-108">Install the npm modules</span></span>

<span data-ttu-id="3b3d9-109">使用 npm 安装 Azure 存储客户端或管理模块。</span><span class="sxs-lookup"><span data-stu-id="3b3d9-109">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="3b3d9-110">示例</span><span class="sxs-lookup"><span data-stu-id="3b3d9-110">Example</span></span>

<span data-ttu-id="3b3d9-111">此示例摘自[客户端凭据示例](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)，演示如何通过客户端凭据进行服务器到服务器的身份验证。</span><span class="sxs-lookup"><span data-stu-id="3b3d9-111">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="3b3d9-112">示例</span><span class="sxs-lookup"><span data-stu-id="3b3d9-112">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="3b3d9-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="3b3d9-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
