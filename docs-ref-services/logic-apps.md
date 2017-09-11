---
title: "用于 Node.js 的 Azure 逻辑应用模块"
description: "用于 Node.js 的 Azure 逻辑应用模块参考"
keywords: "Azure,SDK,API,逻辑应用, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="48e63-104">用于 Node.js 的 Azure 逻辑应用模块</span><span class="sxs-lookup"><span data-stu-id="48e63-104">Azure Logic Apps modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="48e63-105">概述</span><span class="sxs-lookup"><span data-stu-id="48e63-105">Overview</span></span>
<span data-ttu-id="48e63-106">逻辑应用提供了用于在云中简化并实现可缩放的集成和工作流的方式。</span><span class="sxs-lookup"><span data-stu-id="48e63-106">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="48e63-107">它提供了可视化设计器，用于为流程建模并将流程作为一系列步骤（称为工作流）自动执行。</span><span class="sxs-lookup"><span data-stu-id="48e63-107">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="48e63-108">它在云中和本地提供多个连接器，可跨服务和协议快速集成。</span><span class="sxs-lookup"><span data-stu-id="48e63-108">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="48e63-109">逻辑应用以触发器开头（例如，“当将帐户添加到 Dynamics CRM 时”），在触发之后许多组合操作、转换和条件逻辑才能开始。</span><span class="sxs-lookup"><span data-stu-id="48e63-109">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="48e63-110">使用逻辑应用的优点包括：</span><span class="sxs-lookup"><span data-stu-id="48e63-110">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="48e63-111">使用易于掌握的设计工具设计复杂过程可节省时间</span><span class="sxs-lookup"><span data-stu-id="48e63-111">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="48e63-112">可无缝地实现用代码很难实现的模式和工作流</span><span class="sxs-lookup"><span data-stu-id="48e63-112">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="48e63-113">可以从模板快速入门</span><span class="sxs-lookup"><span data-stu-id="48e63-113">Getting started quickly from templates</span></span>
- <span data-ttu-id="48e63-114">可以使用自己的自定义 API、代码和操作自定义逻辑应用</span><span class="sxs-lookup"><span data-stu-id="48e63-114">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="48e63-115">可连接并同步跨本地和云的不同系统</span><span class="sxs-lookup"><span data-stu-id="48e63-115">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="48e63-116">可利用一流集成支持从 BizTalk server、API 管理、Azure Functions 和 Azure 服务总线构建</span><span class="sxs-lookup"><span data-stu-id="48e63-116">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="48e63-117">逻辑应用是完全托管的 iPaaS（集成平台即服务），使开发人员无需担心如何实现托管、可伸缩性、可用性和管理。</span><span class="sxs-lookup"><span data-stu-id="48e63-117">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="48e63-118">逻辑应用会自动扩大以满足需求。</span><span class="sxs-lookup"><span data-stu-id="48e63-118">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="48e63-119">管理包</span><span class="sxs-lookup"><span data-stu-id="48e63-119">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="48e63-120">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="48e63-120">Install the npm module</span></span>

<span data-ttu-id="48e63-121">安装用于 Node.js 的 Azure 逻辑模块</span><span class="sxs-lookup"><span data-stu-id="48e63-121">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="48e63-122">示例</span><span class="sxs-lookup"><span data-stu-id="48e63-122">Example</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a><span data-ttu-id="48e63-123">示例</span><span class="sxs-lookup"><span data-stu-id="48e63-123">Samples</span></span>

<span data-ttu-id="48e63-124">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="48e63-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
