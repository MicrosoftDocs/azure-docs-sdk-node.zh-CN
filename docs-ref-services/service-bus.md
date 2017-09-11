---
title: "用于 Node.js 的 Azure 服务总线模块"
description: "用于 Node.js 的 Azure 服务总线模块参考"
keywords: "Azure,SDK,API,服务总线, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="9563e-104">用于 Node.js 的 Azure 服务总线模块</span><span class="sxs-lookup"><span data-stu-id="9563e-104">Azure Service Bus Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9563e-105">概述</span><span class="sxs-lookup"><span data-stu-id="9563e-105">Overview</span></span>

<span data-ttu-id="9563e-106">Azure 服务总线是一个异步消息传送云平台，可用于在分离的系统之间发送数据。</span><span class="sxs-lookup"><span data-stu-id="9563e-106">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="9563e-107">详细了解 [Azure 服务总线](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)。</span><span class="sxs-lookup"><span data-stu-id="9563e-107">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="9563e-108">管理包</span><span class="sxs-lookup"><span data-stu-id="9563e-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9563e-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="9563e-109">Install the npm module</span></span>

<span data-ttu-id="9563e-110">使用 npm 安装用于 Node.js 的 Azure 服务总线模块</span><span class="sxs-lookup"><span data-stu-id="9563e-110">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="9563e-111">示例</span><span class="sxs-lookup"><span data-stu-id="9563e-111">Example</span></span>

<span data-ttu-id="9563e-112">此示例创建一个客户端，然后列出与给定订阅关联的所有服务总线命名空间。</span><span class="sxs-lookup"><span data-stu-id="9563e-112">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9563e-113">示例</span><span class="sxs-lookup"><span data-stu-id="9563e-113">Samples</span></span>

<span data-ttu-id="9563e-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="9563e-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
