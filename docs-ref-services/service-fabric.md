---
title: "用于 Node.js 的 Azure Service Fabric 模块"
description: "用于 Node.js 的 Azure Service Fabric 模块参考"
keywords: Azure,SDK,API,Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="7fb88-104">用于 Node.js 的 Azure Service Fabric 模块</span><span class="sxs-lookup"><span data-stu-id="7fb88-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7fb88-105">概述</span><span class="sxs-lookup"><span data-stu-id="7fb88-105">Overview</span></span>

<span data-ttu-id="7fb88-106">Azure Service Fabric 是一款分布式系统平台，可方便用户轻松打包、部署和管理可缩放的可靠微服务和容器。</span><span class="sxs-lookup"><span data-stu-id="7fb88-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="7fb88-107">详细了解 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)。</span><span class="sxs-lookup"><span data-stu-id="7fb88-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="7fb88-108">管理包</span><span class="sxs-lookup"><span data-stu-id="7fb88-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7fb88-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="7fb88-109">Install the npm module</span></span>

<span data-ttu-id="7fb88-110">安装 Azure Service Fabric npm 模块</span><span class="sxs-lookup"><span data-stu-id="7fb88-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="7fb88-111">示例</span><span class="sxs-lookup"><span data-stu-id="7fb88-111">Example</span></span>

<span data-ttu-id="7fb88-112">此示例演示如何列出 Azure 订阅的群集。</span><span class="sxs-lookup"><span data-stu-id="7fb88-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="7fb88-113">示例</span><span class="sxs-lookup"><span data-stu-id="7fb88-113">Samples</span></span>

<span data-ttu-id="7fb88-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="7fb88-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
