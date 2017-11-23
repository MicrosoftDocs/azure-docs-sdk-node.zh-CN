---
title: "用于 Node.js 的 Azure 自动化模块"
description: "用于 Node.js 的 Azure 自动化模块参考"
keywords: "Azure,SDK,API,自动化, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 96861efce8eb95f567aa25f2304cb271d932d949
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="014e5-104">用于 Node.js 的 Azure 自动化模块</span><span class="sxs-lookup"><span data-stu-id="014e5-104">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="014e5-105">概述</span><span class="sxs-lookup"><span data-stu-id="014e5-105">Overview</span></span>

<span data-ttu-id="014e5-106">借助 Azure 自动化，用户可以自动完成通常要在云环境和企业环境中执行的手动、长时间进行、易出错且重复性高的任务。</span><span class="sxs-lookup"><span data-stu-id="014e5-106">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="014e5-107">自动化可以节省时间，提高常规管理任务的可靠性，甚至可将这些任务安排成按特定的时间间隔自动执行。</span><span class="sxs-lookup"><span data-stu-id="014e5-107">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="014e5-108">可以使用 Runbook 实现这些过程的自动化，或者使用 Desired State Configuration 实现配置管理的自动化。</span><span class="sxs-lookup"><span data-stu-id="014e5-108">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="014e5-109">管理包</span><span class="sxs-lookup"><span data-stu-id="014e5-109">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="014e5-110">使用 npm 安装模块</span><span class="sxs-lookup"><span data-stu-id="014e5-110">Install the modules with npm</span></span>

<span data-ttu-id="014e5-111">使用 npm 安装用于 Node.js 的 Azure 自动化模块</span><span class="sxs-lookup"><span data-stu-id="014e5-111">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="014e5-112">示例</span><span class="sxs-lookup"><span data-stu-id="014e5-112">Example</span></span>

<span data-ttu-id="014e5-113">此示例列出自动化帐户。</span><span class="sxs-lookup"><span data-stu-id="014e5-113">This example lists the automation accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="014e5-114">示例</span><span class="sxs-lookup"><span data-stu-id="014e5-114">Samples</span></span>

<span data-ttu-id="014e5-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="014e5-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
