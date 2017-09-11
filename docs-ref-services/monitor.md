---
title: "用于 Node.js 的 Azure Monitor 模块"
description: "用于 Node.js 的 Azure Monitor 模块参考"
keywords: Azure,SDK,API,Monitor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="2844a-104">用于 Node.js 的 Azure Monitor 模块</span><span class="sxs-lookup"><span data-stu-id="2844a-104">Azure Monitor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2844a-105">概述</span><span class="sxs-lookup"><span data-stu-id="2844a-105">Overview</span></span>
<span data-ttu-id="2844a-106">云应用程序很复杂，包含很多移动部件。</span><span class="sxs-lookup"><span data-stu-id="2844a-106">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="2844a-107">监视可以为用户提供数据，确保应用程序始终处于健康运行状态。</span><span class="sxs-lookup"><span data-stu-id="2844a-107">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="2844a-108">监视还有助于避免潜在问题，或者解决过去的问题。</span><span class="sxs-lookup"><span data-stu-id="2844a-108">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="2844a-109">此外，还可以利用监视数据深入了解应用程序的情况。</span><span class="sxs-lookup"><span data-stu-id="2844a-109">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="2844a-110">了解这些情况有助于改进应用程序的性能或可维护性，或者实现本来需要手动干预的操作的自动化。</span><span class="sxs-lookup"><span data-stu-id="2844a-110">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="2844a-111">管理包</span><span class="sxs-lookup"><span data-stu-id="2844a-111">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="2844a-112">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="2844a-112">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="2844a-113">示例</span><span class="sxs-lookup"><span data-stu-id="2844a-113">Example</span></span>

<span data-ttu-id="2844a-114">此代码示例列显与资源组关联的所有警报规则。</span><span class="sxs-lookup"><span data-stu-id="2844a-114">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a><span data-ttu-id="2844a-115">示例</span><span class="sxs-lookup"><span data-stu-id="2844a-115">Samples</span></span>

<span data-ttu-id="2844a-116">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="2844a-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
