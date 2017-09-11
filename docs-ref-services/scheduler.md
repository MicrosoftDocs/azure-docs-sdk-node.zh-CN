---
title: "用于 Node.js 的 Azure 计划程序模块"
description: "用于 Node.js 的 Azure 计划程序模块参考"
keywords: "Azure,SDK,API,计划程序, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 3070612721dc434b8c3d7c3200f0666755fd4ce8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="ea922-104">用于 Node.js 的 Azure 计划程序模块</span><span class="sxs-lookup"><span data-stu-id="ea922-104">Azure Scheduler modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ea922-105">概述</span><span class="sxs-lookup"><span data-stu-id="ea922-105">Overview</span></span>

<span data-ttu-id="ea922-106">Azure 计划程序可以通过 HTTP、HTTPS、存储队列或 [Azure 服务总线](/azure/service-bus-messaging/service-bus-messaging-overview)创建、维护和调用计划的工作。</span><span class="sxs-lookup"><span data-stu-id="ea922-106">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="ea922-107">详细了解 [Azure 计划程序](/azure/scheduler/scheduler-intro)。</span><span class="sxs-lookup"><span data-stu-id="ea922-107">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="ea922-108">管理包</span><span class="sxs-lookup"><span data-stu-id="ea922-108">Management package</span></span>

<span data-ttu-id="ea922-109">使用管理 API 跨各种信道创建、维护和调用计划的工作。</span><span class="sxs-lookup"><span data-stu-id="ea922-109">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ea922-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="ea922-110">Install the npm module</span></span>

<span data-ttu-id="ea922-111">安装 Azure 计划程序 npm 模块</span><span class="sxs-lookup"><span data-stu-id="ea922-111">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="ea922-112">示例</span><span class="sxs-lookup"><span data-stu-id="ea922-112">Example</span></span>

<span data-ttu-id="ea922-113">此示例列出当前计划程序。</span><span class="sxs-lookup"><span data-stu-id="ea922-113">This examples lists the current schedulers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a><span data-ttu-id="ea922-114">示例</span><span class="sxs-lookup"><span data-stu-id="ea922-114">Samples</span></span>

<span data-ttu-id="ea922-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ea922-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
