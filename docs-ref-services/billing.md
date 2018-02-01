---
title: "用于 Node.js 的 Azure 计费模块"
description: "用于 Node.js 的 Azure 计费模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 58eed8996f543e845a53a741f8684d9e7f6cc1e4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-billing-modules-for-nodejs"></a>用于 Node.js 的 Azure 计费模块

## <a name="overview"></a>概述
使用 Azure 计费 API 可以访问 Azure 计费信息和发票。

若要使用此 API，帐户管理员必须通过 Azure 门户启用它。 请参阅[使用角色管理对 Azure 计费的访问](https://docs.microsoft.com/azure/billing/billing-manage-access)。

### <a name="install-the-npm-module"></a>安装 npm 模块 

安装 Azure 计费 npm 模块 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>示例 
 
此示例列显过去所有发票的列表。
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
