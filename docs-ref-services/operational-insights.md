---
title: "用于 Node.js 的 Azure 操作见解模块"
description: "用于 Node.js 的 Azure 操作见解模块参考"
keywords: "Azure,SDK,API,操作见解, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="87038-104">用于 Node.js 的 Azure 操作见解模块</span><span class="sxs-lookup"><span data-stu-id="87038-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="87038-105">概述</span><span class="sxs-lookup"><span data-stu-id="87038-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="87038-106">管理包</span><span class="sxs-lookup"><span data-stu-id="87038-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="87038-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="87038-107">Install the npm module</span></span>

<span data-ttu-id="87038-108">使用 npm 安装用于 Node.js 的 Azure 操作见解模块</span><span class="sxs-lookup"><span data-stu-id="87038-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="87038-109">示例</span><span class="sxs-lookup"><span data-stu-id="87038-109">Example</span></span> 

<span data-ttu-id="87038-110">此示例创建一个客户端，连接到操作见解，并根据指定的资源组检索工作区列表。</span><span class="sxs-lookup"><span data-stu-id="87038-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="87038-111">示例</span><span class="sxs-lookup"><span data-stu-id="87038-111">Samples</span></span>

<span data-ttu-id="87038-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="87038-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
