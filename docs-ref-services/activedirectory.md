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
# <a name="azure-active-directory-modules-for-nodejs"></a>用于 Node.js 的 Azure Active Directory 模块

## <a name="overview"></a>概述

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
