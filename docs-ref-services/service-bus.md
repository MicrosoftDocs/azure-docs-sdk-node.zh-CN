---
title: "用于 Node.js 的 Azure 服务总线模块"
description: "用于 Node.js 的 Azure 服务总线模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 792e51acf2577649432b26e4b840bc1d40b7abaf
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="3b9e1-103">用于 Node.js 的 Azure 服务总线模块</span><span class="sxs-lookup"><span data-stu-id="3b9e1-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="3b9e1-104">Azure 服务总线是一个异步消息传送云平台，可用于在分离的系统之间发送数据。</span><span class="sxs-lookup"><span data-stu-id="3b9e1-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="3b9e1-105">详细了解 [Azure 服务总线](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)。</span><span class="sxs-lookup"><span data-stu-id="3b9e1-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="3b9e1-106">管理包</span><span class="sxs-lookup"><span data-stu-id="3b9e1-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3b9e1-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3b9e1-107">Install the npm module</span></span>

<span data-ttu-id="3b9e1-108">使用 npm 安装用于 Node.js 的 Azure 服务总线模块</span><span class="sxs-lookup"><span data-stu-id="3b9e1-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="3b9e1-109">示例</span><span class="sxs-lookup"><span data-stu-id="3b9e1-109">Example</span></span>

<span data-ttu-id="3b9e1-110">此示例创建一个客户端，然后列出与给定订阅关联的所有服务总线命名空间。</span><span class="sxs-lookup"><span data-stu-id="3b9e1-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a><span data-ttu-id="3b9e1-111">示例</span><span class="sxs-lookup"><span data-stu-id="3b9e1-111">Samples</span></span>

<span data-ttu-id="3b9e1-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="3b9e1-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
