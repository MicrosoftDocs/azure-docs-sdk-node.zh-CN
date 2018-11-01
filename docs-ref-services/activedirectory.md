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
ms.openlocfilehash: 1189bf084fc7d77a1e5eed7f01f2f9bee2295b45
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406423"
---
# <a name="azure-active-directory-modules-for-nodejs"></a>用于 Node.js 的 Azure Active Directory 模块

## <a name="overview"></a>概述

> [!IMPORTANT]
> 强烈建议使用 [Microsoft Graph](https://graph.microsoft.io/)（而非 Azure AD Graph API）访问 Azure Active Directory 资源。 目前，我们在集中开发 Microsoft Graph，未计划进一步改进 Azure AD Graph API。 Azure AD Graph API 仍可能适用的方案非常有限；有关详细信息，请参阅 Office 开发人员中心的 [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph)（Microsoft Graph 或 Azure AD Graph）博客文章。

[用于 Node.js 的 Azure Active Directory 身份验证库 (ADAL)](https://www.npmjs.com/package/adal-node) 可让 Node.js 应用程序在 AAD 中进行身份验证，以访问 AAD 保护的 Web 资源。

## <a name="client-package"></a>客户端程序包

### <a name="install-the-npm-modules"></a>安装 npm 模块

使用 npm 安装 Azure 存储客户端或管理模块。

```bash
npm install adal-node
```   

### <a name="example"></a>示例

此示例摘自[客户端凭据示例](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)，演示如何通过客户端凭据进行服务器到服务器的身份验证。

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

## <a name="samples"></a>示例

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
