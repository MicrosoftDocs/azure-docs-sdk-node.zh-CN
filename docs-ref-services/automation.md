---
title: "用于 Node.js 的 Azure 自动化模块"
description: "用于 Node.js 的 Azure 自动化模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 09e9d2675d49b29881d332e7bbf251a5031e3483
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="1765a-103">用于 Node.js 的 Azure 自动化模块</span><span class="sxs-lookup"><span data-stu-id="1765a-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1765a-104">概述</span><span class="sxs-lookup"><span data-stu-id="1765a-104">Overview</span></span>

<span data-ttu-id="1765a-105">借助 Azure 自动化，用户可以自动完成通常要在云环境和企业环境中执行的手动、长时间进行、易出错且重复性高的任务。</span><span class="sxs-lookup"><span data-stu-id="1765a-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="1765a-106">自动化可以节省时间，提高常规管理任务的可靠性，甚至可将这些任务安排成按特定的时间间隔自动执行。</span><span class="sxs-lookup"><span data-stu-id="1765a-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="1765a-107">可以使用 Runbook 实现这些过程的自动化，或者使用 Desired State Configuration 实现配置管理的自动化。</span><span class="sxs-lookup"><span data-stu-id="1765a-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="1765a-108">管理包</span><span class="sxs-lookup"><span data-stu-id="1765a-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="1765a-109">使用 npm 安装模块</span><span class="sxs-lookup"><span data-stu-id="1765a-109">Install the modules with npm</span></span>

<span data-ttu-id="1765a-110">使用 npm 安装用于 Node.js 的 Azure 自动化模块</span><span class="sxs-lookup"><span data-stu-id="1765a-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="1765a-111">示例</span><span class="sxs-lookup"><span data-stu-id="1765a-111">Example</span></span>

<span data-ttu-id="1765a-112">此示例列出自动化帐户。</span><span class="sxs-lookup"><span data-stu-id="1765a-112">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a><span data-ttu-id="1765a-113">示例</span><span class="sxs-lookup"><span data-stu-id="1765a-113">Samples</span></span>

<span data-ttu-id="1765a-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="1765a-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
