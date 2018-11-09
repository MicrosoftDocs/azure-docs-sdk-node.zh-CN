---
title: 用于 Node.js 的 Azure 商务模块
description: 用于 Node.js 的 Azure 商务模块参考
author: rloutlaw
ms.author: ROutlaw
manager: angrobew
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 87a0e8d689d8d782a705a4525fdbe9b681403c07
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2018
ms.locfileid: "51111215"
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="0db62-103">用于 Node.js 的 Azure 商务模块</span><span class="sxs-lookup"><span data-stu-id="0db62-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0db62-104">概述</span><span class="sxs-lookup"><span data-stu-id="0db62-104">Overview</span></span>

<span data-ttu-id="0db62-105">使用 Azure 商务 API 将用量和资源数据提取到偏好的数据分析工具中。</span><span class="sxs-lookup"><span data-stu-id="0db62-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="0db62-106">Azure 资源用量和 RateCard API 可以帮助你准确预测及管理成本。</span><span class="sxs-lookup"><span data-stu-id="0db62-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="0db62-107">这些 API 作为资源提供程序实现，属于 Azure 资源管理器公开的 API 系列。</span><span class="sxs-lookup"><span data-stu-id="0db62-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="0db62-108">管理包</span><span class="sxs-lookup"><span data-stu-id="0db62-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0db62-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0db62-109">Install the npm module</span></span>

<span data-ttu-id="0db62-110">安装 Azure 商务 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0db62-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="0db62-111">示例</span><span class="sxs-lookup"><span data-stu-id="0db62-111">Example</span></span>

<span data-ttu-id="0db62-112">此示例检索最后一个月的估算 Azure 消耗数据。</span><span class="sxs-lookup"><span data-stu-id="0db62-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

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

## <a name="samples"></a><span data-ttu-id="0db62-113">示例</span><span class="sxs-lookup"><span data-stu-id="0db62-113">Samples</span></span>

<span data-ttu-id="0db62-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="0db62-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
