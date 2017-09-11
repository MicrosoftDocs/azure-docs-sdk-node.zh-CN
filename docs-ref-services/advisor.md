---
title: "用于 Node.js 的 Azure 顾问模块"
description: "用于 Node.js 的 Azure 顾问模块参考"
keywords: "Azure,SDK,API,顾问, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="8f1f9-104">用于 Node.js 的 Azure 顾问模块</span><span class="sxs-lookup"><span data-stu-id="8f1f9-104">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="8f1f9-105">概述</span><span class="sxs-lookup"><span data-stu-id="8f1f9-105">Overview</span></span>

<span data-ttu-id="8f1f9-106">Azure 顾问是一种个性化的云顾问，可帮助遵循最佳做法来优化 Azure 部署。</span><span class="sxs-lookup"><span data-stu-id="8f1f9-106">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="8f1f9-107">顾问可分析资源配置和遥测使用情况，并推荐解决方案，有助于提高 Azure 资源的经济效益、性能、高可用性和安全性。</span><span class="sxs-lookup"><span data-stu-id="8f1f9-107">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="8f1f9-108">使用顾问可以：</span><span class="sxs-lookup"><span data-stu-id="8f1f9-108">With Advisor, you can:</span></span>
- <span data-ttu-id="8f1f9-109">获取主动的、可操作的以及个性化的最佳做法建议。</span><span class="sxs-lookup"><span data-stu-id="8f1f9-109">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="8f1f9-110">提高资源的性能、安全性和高可用性，同时确定机会减少总体 Azure 支出。</span><span class="sxs-lookup"><span data-stu-id="8f1f9-110">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="8f1f9-111">通过提议的内联操作获取建议。</span><span class="sxs-lookup"><span data-stu-id="8f1f9-111">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="8f1f9-112">管理包</span><span class="sxs-lookup"><span data-stu-id="8f1f9-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8f1f9-113">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="8f1f9-113">Install the npm module</span></span>

<span data-ttu-id="8f1f9-114">安装 Azure 顾问 npm 模块</span><span class="sxs-lookup"><span data-stu-id="8f1f9-114">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="8f1f9-115">示例</span><span class="sxs-lookup"><span data-stu-id="8f1f9-115">Example</span></span>

<span data-ttu-id="8f1f9-116">此示例显示 Azure 顾问提供的建议列表。</span><span class="sxs-lookup"><span data-stu-id="8f1f9-116">This example displays the list of recommendations from Azure Advisor.</span></span>

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

## <a name="samples"></a><span data-ttu-id="8f1f9-117">示例</span><span class="sxs-lookup"><span data-stu-id="8f1f9-117">Samples</span></span>

<span data-ttu-id="8f1f9-118">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="8f1f9-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
