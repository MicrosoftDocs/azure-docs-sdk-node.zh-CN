---
title: 用于 Node.js 的 Azure 事件中心模块
description: 用于 Node.js 的 Azure 事件中心模块参考
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: ff167e911b68b82b880e792e7ff2649cbe5af342
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260380"
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="e5f6f-103">用于 Node.js 的 Azure 事件中心模块</span><span class="sxs-lookup"><span data-stu-id="e5f6f-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="e5f6f-104">Azure 事件中心是高度可缩放的数据流式处理平台和事件引入服务，能够每秒接收和处理数百万事件。</span><span class="sxs-lookup"><span data-stu-id="e5f6f-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="e5f6f-105">事件中心可以处理和存储分布式软件和设备生成的事件、数据或遥测。</span><span class="sxs-lookup"><span data-stu-id="e5f6f-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="e5f6f-106">可以使用任何实时分析提供程序或批处理/存储适配器转换和存储发送到数据中心的数据。</span><span class="sxs-lookup"><span data-stu-id="e5f6f-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="e5f6f-107">由于能够以较低的延迟和极高的规模提供发布订阅功能，事件中心可以充当大数据的“入口”。</span><span class="sxs-lookup"><span data-stu-id="e5f6f-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="e5f6f-108">管理包</span><span class="sxs-lookup"><span data-stu-id="e5f6f-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e5f6f-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="e5f6f-109">Install the npm module</span></span> 

<span data-ttu-id="e5f6f-110">使用 npm 安装用于 Node.js 的 Azure 事件中心模块</span><span class="sxs-lookup"><span data-stu-id="e5f6f-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="e5f6f-111">示例</span><span class="sxs-lookup"><span data-stu-id="e5f6f-111">Example</span></span>

<span data-ttu-id="e5f6f-112">此示例检索有关现有事件中心的信息。</span><span class="sxs-lookup"><span data-stu-id="e5f6f-112">This example retrieves information about an existing event hub.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e5f6f-113">示例</span><span class="sxs-lookup"><span data-stu-id="e5f6f-113">Samples</span></span>

<span data-ttu-id="e5f6f-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="e5f6f-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
