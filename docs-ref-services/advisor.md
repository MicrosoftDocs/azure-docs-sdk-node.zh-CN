---
title: "用于 Node.js 的 Azure 顾问模块"
description: "用于 Node.js 的 Azure 顾问模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: aad3b292c6304159f68a81270e671cd335c972ec
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-advisor-modules-for-nodejs"></a>用于 Node.js 的 Azure 顾问模块

## <a name="overview"></a>概述

Azure 顾问是一种个性化的云顾问，可帮助遵循最佳做法来优化 Azure 部署。 顾问可分析资源配置和遥测使用情况，并推荐解决方案，有助于提高 Azure 资源的经济效益、性能、高可用性和安全性。

使用顾问可以：
- 获取主动的、可操作的以及个性化的最佳做法建议。
- 提高资源的性能、安全性和高可用性，同时确定机会减少总体 Azure 支出。
- 通过提议的内联操作获取建议。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 顾问 npm 模块

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>示例

此示例显示 Azure 顾问提供的建议列表。

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
