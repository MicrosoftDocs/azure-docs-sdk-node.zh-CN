---
title: 用于 Node.js 的 Azure 计划程序模块
description: 用于 Node.js 的 Azure 计划程序模块参考
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 9a842919fddb3d6448d5a4e951dc58dd0d3211e0
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094262"
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="b437b-103">用于 Node.js 的 Azure 计划程序模块</span><span class="sxs-lookup"><span data-stu-id="b437b-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="b437b-104">Azure 计划程序可以通过 HTTP、HTTPS、存储队列或 [Azure 服务总线](/azure/service-bus-messaging/service-bus-messaging-overview)创建、维护和调用计划的工作。</span><span class="sxs-lookup"><span data-stu-id="b437b-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="b437b-105">详细了解 [Azure 计划程序](/azure/scheduler/scheduler-intro)。</span><span class="sxs-lookup"><span data-stu-id="b437b-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="b437b-106">管理包</span><span class="sxs-lookup"><span data-stu-id="b437b-106">Management package</span></span>

<span data-ttu-id="b437b-107">使用管理 API 跨各种信道创建、维护和调用计划的工作。</span><span class="sxs-lookup"><span data-stu-id="b437b-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b437b-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="b437b-108">Install the npm module</span></span>

<span data-ttu-id="b437b-109">安装 Azure 计划程序 npm 模块</span><span class="sxs-lookup"><span data-stu-id="b437b-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="b437b-110">示例</span><span class="sxs-lookup"><span data-stu-id="b437b-110">Example</span></span>

<span data-ttu-id="b437b-111">此示例列出当前计划程序。</span><span class="sxs-lookup"><span data-stu-id="b437b-111">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b437b-112">示例</span><span class="sxs-lookup"><span data-stu-id="b437b-112">Samples</span></span>

<span data-ttu-id="b437b-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b437b-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
