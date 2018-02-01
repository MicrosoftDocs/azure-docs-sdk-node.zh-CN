---
title: "用于 Node.js 的 Azure Monitor 模块"
description: "用于 Node.js 的 Azure Monitor 模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 37caeb2d7b6d757cbe8bb14b6d4909a7c67a37db
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="eccab-103">用于 Node.js 的 Azure Monitor 模块</span><span class="sxs-lookup"><span data-stu-id="eccab-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="eccab-104">云应用程序很复杂，包含很多移动部件。</span><span class="sxs-lookup"><span data-stu-id="eccab-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="eccab-105">监视可以为用户提供数据，确保应用程序始终处于健康运行状态。</span><span class="sxs-lookup"><span data-stu-id="eccab-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="eccab-106">监视还有助于避免潜在问题，或者解决过去的问题。</span><span class="sxs-lookup"><span data-stu-id="eccab-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="eccab-107">此外，还可以利用监视数据深入了解应用程序的情况。</span><span class="sxs-lookup"><span data-stu-id="eccab-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="eccab-108">了解这些情况有助于改进应用程序的性能或可维护性，或者实现本来需要手动干预的操作的自动化。</span><span class="sxs-lookup"><span data-stu-id="eccab-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="eccab-109">管理包</span><span class="sxs-lookup"><span data-stu-id="eccab-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="eccab-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="eccab-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="eccab-111">示例</span><span class="sxs-lookup"><span data-stu-id="eccab-111">Example</span></span>

<span data-ttu-id="eccab-112">此代码示例列显与资源组关联的所有警报规则。</span><span class="sxs-lookup"><span data-stu-id="eccab-112">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="eccab-113">示例</span><span class="sxs-lookup"><span data-stu-id="eccab-113">Samples</span></span>

<span data-ttu-id="eccab-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="eccab-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
