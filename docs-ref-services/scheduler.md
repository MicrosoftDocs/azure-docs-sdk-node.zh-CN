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
# <a name="azure-scheduler-modules-for-nodejs"></a>用于 Node.js 的 Azure 计划程序模块

## <a name="overview"></a>概述

Azure 计划程序可以通过 HTTP、HTTPS、存储队列或 [Azure 服务总线](/azure/service-bus-messaging/service-bus-messaging-overview)创建、维护和调用计划的工作。

详细了解 [Azure 计划程序](/azure/scheduler/scheduler-intro)。

## <a name="management-package"></a>管理包

使用管理 API 跨各种信道创建、维护和调用计划的工作。

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 计划程序 npm 模块

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>示例

此示例列出当前计划程序。

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

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
