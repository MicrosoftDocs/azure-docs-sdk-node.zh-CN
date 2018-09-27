---
title: 用于 Node.js 的 Azure 计费模块
description: 用于 Node.js 的 Azure 计费模块参考
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 20df85ae5e504e460a501737aa07b6692a0da3c7
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2018
ms.locfileid: "47346676"
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
