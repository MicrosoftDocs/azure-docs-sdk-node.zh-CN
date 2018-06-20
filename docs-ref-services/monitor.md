---
title: 用于 Node.js 的 Azure Monitor 模块
description: 用于 Node.js 的 Azure Monitor 模块参考
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8a9411b7979f3130a1aa24fd2a0b294fc7f67718
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259300"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="49bfd-103">用于 Node.js 的 Azure Monitor 模块</span><span class="sxs-lookup"><span data-stu-id="49bfd-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="49bfd-104">云应用程序很复杂，包含很多移动部件。</span><span class="sxs-lookup"><span data-stu-id="49bfd-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="49bfd-105">监视可以为用户提供数据，确保应用程序始终处于健康运行状态。</span><span class="sxs-lookup"><span data-stu-id="49bfd-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="49bfd-106">监视还有助于避免潜在问题，或者解决过去的问题。</span><span class="sxs-lookup"><span data-stu-id="49bfd-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="49bfd-107">此外，还可以利用监视数据深入了解应用程序的情况。</span><span class="sxs-lookup"><span data-stu-id="49bfd-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="49bfd-108">了解这些情况有助于改进应用程序的性能或可维护性，或者实现本来需要手动干预的操作的自动化。</span><span class="sxs-lookup"><span data-stu-id="49bfd-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="49bfd-109">管理包</span><span class="sxs-lookup"><span data-stu-id="49bfd-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="49bfd-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="49bfd-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="49bfd-111">示例</span><span class="sxs-lookup"><span data-stu-id="49bfd-111">Example</span></span>

<span data-ttu-id="49bfd-112">此代码示例列显与资源组关联的所有警报规则。</span><span class="sxs-lookup"><span data-stu-id="49bfd-112">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="49bfd-113">示例</span><span class="sxs-lookup"><span data-stu-id="49bfd-113">Samples</span></span>

<span data-ttu-id="49bfd-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="49bfd-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
