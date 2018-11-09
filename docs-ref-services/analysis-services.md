---
title: 用于 Node.js 的 Azure Analysis Services 模块
description: 用于 Node.js 的 Azure Analysis Services 模块参考
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 5214cd2f171074ba330bc639643dfba490540856
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2018
ms.locfileid: "51148976"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a>用于 Node.js 的 Azure Analysis Services 模块

## <a name="overview"></a>概述
此包提供一个 Node.js 模块用于方便管理 Microsoft Azure Analysis Services。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure Analysis Services npm 模块

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a>示例

此示例列出所有可用的 Analysis Service 服务器。

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
