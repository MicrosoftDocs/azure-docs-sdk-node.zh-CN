---
title: "用于 Node.js 的 Azure 商务模块"
description: "用于 Node.js 的 Azure 商务模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 0597765543cd838049d3946b90ae128875edd4e5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-commerce-modules-for-nodejs"></a>用于 Node.js 的 Azure 商务模块

## <a name="overview"></a>概述

使用 Azure 商务 API 将用量和资源数据提取到偏好的数据分析工具中。 Azure 资源用量和 RateCard API 可以帮助你准确预测及管理成本。 这些 API 作为资源提供程序实现，属于 Azure 资源管理器公开的 API 系列。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 商务 npm 模块

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>示例

此示例检索最后一个月的估算 Azure 消耗数据。

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
