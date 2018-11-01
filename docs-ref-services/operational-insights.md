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
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="0e6b4-103">用于 Node.js 的 Azure 操作见解模块</span><span class="sxs-lookup"><span data-stu-id="0e6b4-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="0e6b4-104">使用 npm 安装用于 Node.js 的 Azure 操作见解模块</span><span class="sxs-lookup"><span data-stu-id="0e6b4-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="0e6b4-105">示例</span><span class="sxs-lookup"><span data-stu-id="0e6b4-105">Example</span></span> 

<span data-ttu-id="0e6b4-106">此示例创建一个客户端，连接到操作见解，并根据指定的资源组检索工作区列表。</span><span class="sxs-lookup"><span data-stu-id="0e6b4-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="0e6b4-107">示例</span><span class="sxs-lookup"><span data-stu-id="0e6b4-107">Samples</span></span>

<span data-ttu-id="0e6b4-108">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="0e6b4-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
