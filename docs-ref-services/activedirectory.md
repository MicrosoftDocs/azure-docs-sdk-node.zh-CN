---
title: 用于 Node.js 的 Azure Active Directory 模块
description: 用于 Node.js 的 Azure Active Directory 模块参考
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: c356801500aa3ef9038fc27634c8a95debf152b3
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259916"
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="117c2-103">用于 Node.js 的 Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="117c2-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="117c2-104">概述</span><span class="sxs-lookup"><span data-stu-id="117c2-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="117c2-105">强烈建议使用 [Microsoft Graph](https://graph.microsoft.io/)（而非 Azure AD Graph API）访问 Azure Active Directory 资源。</span><span class="sxs-lookup"><span data-stu-id="117c2-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="117c2-106">目前，我们在集中开发 Microsoft Graph，未计划进一步改进 Azure AD Graph API。</span><span class="sxs-lookup"><span data-stu-id="117c2-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="117c2-107">Azure AD Graph API 仍可能适用的方案非常有限；有关详细信息，请参阅 Office 开发人员中心的 [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph)（Microsoft Graph 或 Azure AD Graph）博客文章。</span><span class="sxs-lookup"><span data-stu-id="117c2-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="117c2-108">[用于 Node.js 的 Azure Active Directory 身份验证库 (ADAL)](https://www.npmjs.com/package/adal-node) 可让 Node.js 应用程序在 AAD 中进行身份验证，以访问 AAD 保护的 Web 资源。</span><span class="sxs-lookup"><span data-stu-id="117c2-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="117c2-109">客户端程序包</span><span class="sxs-lookup"><span data-stu-id="117c2-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="117c2-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="117c2-110">Install the npm modules</span></span>

<span data-ttu-id="117c2-111">使用 npm 安装 Azure 存储客户端或管理模块。</span><span class="sxs-lookup"><span data-stu-id="117c2-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="117c2-112">示例</span><span class="sxs-lookup"><span data-stu-id="117c2-112">Example</span></span>

<span data-ttu-id="117c2-113">此示例摘自[客户端凭据示例](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)，演示如何通过客户端凭据进行服务器到服务器的身份验证。</span><span class="sxs-lookup"><span data-stu-id="117c2-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="117c2-114">示例</span><span class="sxs-lookup"><span data-stu-id="117c2-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="117c2-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="117c2-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
