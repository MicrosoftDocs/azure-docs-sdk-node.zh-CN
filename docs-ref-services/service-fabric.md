---
title: 用于 Node.js 的 Azure Service Fabric 模块
description: 用于 Node.js 的 Azure Service Fabric 模块参考
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50340245"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="62831-103">用于 Node.js 的 Azure Service Fabric 模块</span><span class="sxs-lookup"><span data-stu-id="62831-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="62831-104">概述</span><span class="sxs-lookup"><span data-stu-id="62831-104">Overview</span></span>

<span data-ttu-id="62831-105">Azure Service Fabric 是一款分布式系统平台，可方便用户轻松打包、部署和管理可缩放的可靠微服务和容器。</span><span class="sxs-lookup"><span data-stu-id="62831-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="62831-106">详细了解 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)。</span><span class="sxs-lookup"><span data-stu-id="62831-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="62831-107">管理包</span><span class="sxs-lookup"><span data-stu-id="62831-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="62831-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="62831-108">Install the npm module</span></span>

<span data-ttu-id="62831-109">安装 Azure Service Fabric npm 模块</span><span class="sxs-lookup"><span data-stu-id="62831-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="62831-110">示例</span><span class="sxs-lookup"><span data-stu-id="62831-110">Example</span></span>

<span data-ttu-id="62831-111">此示例演示如何列出 Azure 订阅的群集。</span><span class="sxs-lookup"><span data-stu-id="62831-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="62831-112">示例</span><span class="sxs-lookup"><span data-stu-id="62831-112">Samples</span></span>

<span data-ttu-id="62831-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="62831-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
