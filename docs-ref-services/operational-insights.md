---
title: 用于 Node.js 的 Azure 操作见解模块
description: 用于 Node.js 的 Azure 操作见解模块参考
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: c8a137c4759982e0551d9048ac271780e6a68afe
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50270970"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a>用于 Node.js 的 Azure 操作见解模块

使用 npm 安装用于 Node.js 的 Azure 操作见解模块

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a>示例 

此示例创建一个客户端，连接到操作见解，并根据指定的资源组检索工作区列表。

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
