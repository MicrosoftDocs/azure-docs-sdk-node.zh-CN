---
title: "用于 Node.js 的 Azure 流量管理器模块"
description: "用于 Node.js 的 Azure 流量管理器模块参考"
keywords: "Azure,SDK,API,流量管理器, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="cc1ec-104">用于 Node.js 的 Azure 流量管理器模块</span><span class="sxs-lookup"><span data-stu-id="cc1ec-104">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="cc1ec-105">概述</span><span class="sxs-lookup"><span data-stu-id="cc1ec-105">Overview</span></span>

<span data-ttu-id="cc1ec-106">使用 Microsoft Azure 流量管理器，可以控制用户流量在不同数据中心内的服务终结点上的分布。</span><span class="sxs-lookup"><span data-stu-id="cc1ec-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="cc1ec-107">流量管理器支持的服务终结点包括 Azure VM、Web 应用和云服务。</span><span class="sxs-lookup"><span data-stu-id="cc1ec-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="cc1ec-108">也可将流量管理器用于外部的非 Azure 终结点。</span><span class="sxs-lookup"><span data-stu-id="cc1ec-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="cc1ec-109">详细了解 [Azure 流量管理器](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。</span><span class="sxs-lookup"><span data-stu-id="cc1ec-109">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="cc1ec-110">管理包</span><span class="sxs-lookup"><span data-stu-id="cc1ec-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cc1ec-111">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="cc1ec-111">Install the npm module</span></span>

<span data-ttu-id="cc1ec-112">安装 Azure 流量管理器 npm 模块</span><span class="sxs-lookup"><span data-stu-id="cc1ec-112">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="cc1ec-113">示例</span><span class="sxs-lookup"><span data-stu-id="cc1ec-113">Example</span></span>

<span data-ttu-id="cc1ec-114">此示例列出给定资源组的所有流量管理器。</span><span class="sxs-lookup"><span data-stu-id="cc1ec-114">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="cc1ec-115">示例</span><span class="sxs-lookup"><span data-stu-id="cc1ec-115">Samples</span></span>

<span data-ttu-id="cc1ec-116">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="cc1ec-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
