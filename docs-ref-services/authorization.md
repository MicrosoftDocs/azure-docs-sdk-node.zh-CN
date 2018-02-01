---
title: "用于 Node.js 的 Azure 授权模块"
description: "用于 Node.js 的 Azure 授权模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 6fbaaeba28cac81d360e93c5066791adfa51bcd5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-authorization-modules-for-nodejs"></a>用于 Node.js 的 Azure 授权模块

## <a name="overview"></a>概述

Azure 应用服务身份验证/授权功能方便应用程序登录用户，避免在应用后端更改代码。 授权可以方便地保护应用程序和处理每个用户的数据。

## <a name="management-package"></a>管理包

使用 npm 安装用于 Node.js 的 Azure 授权模块

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 授权 npm 模块

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>示例

此示例列出所请求的资源组的所有角色分配。

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
