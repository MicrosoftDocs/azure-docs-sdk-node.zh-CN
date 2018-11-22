---
title: 用于 Node.js 的 Azure 流量管理器模块
description: 用于 Node.js 的 Azure 流量管理器模块参考
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 2a32eed460c6076011fdcf31d77200502ef61a3d
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2018
ms.locfileid: "52081622"
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="62643-103">用于 Node.js 的 Azure 流量管理器模块</span><span class="sxs-lookup"><span data-stu-id="62643-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="62643-104">概述</span><span class="sxs-lookup"><span data-stu-id="62643-104">Overview</span></span>

<span data-ttu-id="62643-105">使用 Microsoft Azure 流量管理器，可以控制用户流量在不同数据中心内的服务终结点上的分布。</span><span class="sxs-lookup"><span data-stu-id="62643-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="62643-106">流量管理器支持的服务终结点包括 Azure VM、Web 应用和云服务。</span><span class="sxs-lookup"><span data-stu-id="62643-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="62643-107">也可将流量管理器用于外部的非 Azure 终结点。</span><span class="sxs-lookup"><span data-stu-id="62643-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="62643-108">详细了解 [Azure 流量管理器](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。</span><span class="sxs-lookup"><span data-stu-id="62643-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="62643-109">管理包</span><span class="sxs-lookup"><span data-stu-id="62643-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="62643-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="62643-110">Install the npm module</span></span>

<span data-ttu-id="62643-111">安装 Azure 流量管理器 npm 模块</span><span class="sxs-lookup"><span data-stu-id="62643-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="62643-112">示例</span><span class="sxs-lookup"><span data-stu-id="62643-112">Example</span></span>

<span data-ttu-id="62643-113">此示例列出给定资源组的所有流量管理器。</span><span class="sxs-lookup"><span data-stu-id="62643-113">This example lists all Traffic Managers for a given resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="62643-114">示例</span><span class="sxs-lookup"><span data-stu-id="62643-114">Samples</span></span>

<span data-ttu-id="62643-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="62643-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
