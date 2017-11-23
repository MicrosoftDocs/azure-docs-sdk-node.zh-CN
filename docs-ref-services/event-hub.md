---
title: "用于 Node.js 的 Azure 事件中心模块"
description: "用于 Node.js 的 Azure 事件中心模块参考"
keywords: "Azure,SDK,API,事件中心, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="efe60-104">用于 Node.js 的 Azure 事件中心模块</span><span class="sxs-lookup"><span data-stu-id="efe60-104">Azure Event Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="efe60-105">概述</span><span class="sxs-lookup"><span data-stu-id="efe60-105">Overview</span></span>
<span data-ttu-id="efe60-106">Azure 事件中心是高度可缩放的数据流式处理平台和事件引入服务，能够每秒接收和处理数百万事件。</span><span class="sxs-lookup"><span data-stu-id="efe60-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="efe60-107">事件中心可以处理和存储分布式软件和设备生成的事件、数据或遥测。</span><span class="sxs-lookup"><span data-stu-id="efe60-107">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="efe60-108">可以使用任何实时分析提供程序或批处理/存储适配器转换和存储发送到数据中心的数据。</span><span class="sxs-lookup"><span data-stu-id="efe60-108">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="efe60-109">由于能够以较低的延迟和极高的规模提供发布订阅功能，事件中心可以充当大数据的“入口”。</span><span class="sxs-lookup"><span data-stu-id="efe60-109">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="efe60-110">管理包</span><span class="sxs-lookup"><span data-stu-id="efe60-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="efe60-111">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="efe60-111">Install the npm module</span></span> 

<span data-ttu-id="efe60-112">使用 npm 安装用于 Node.js 的 Azure 事件中心模块</span><span class="sxs-lookup"><span data-stu-id="efe60-112">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="efe60-113">示例</span><span class="sxs-lookup"><span data-stu-id="efe60-113">Example</span></span>

<span data-ttu-id="efe60-114">此示例检索有关现有事件中心的信息。</span><span class="sxs-lookup"><span data-stu-id="efe60-114">This example retrieves information about an existing event hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="efe60-115">示例</span><span class="sxs-lookup"><span data-stu-id="efe60-115">Samples</span></span>

<span data-ttu-id="efe60-116">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="efe60-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
