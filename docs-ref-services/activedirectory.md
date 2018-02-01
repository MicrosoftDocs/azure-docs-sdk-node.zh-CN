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
