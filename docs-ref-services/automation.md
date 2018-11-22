---
title: 用于 Node.js 的 Azure 自动化模块
description: 用于 Node.js 的 Azure 自动化模块参考
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: f364bb09c97c1262f640a4b48514c6abaee5f14a
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2018
ms.locfileid: "52154892"
---
# <a name="azure-automation-modules-for-nodejs"></a>用于 Node.js 的 Azure 自动化模块

## <a name="overview"></a>概述

借助 Azure 自动化，用户可以自动完成通常要在云环境和企业环境中执行的手动、长时间进行、易出错且重复性高的任务。 自动化可以节省时间，提高常规管理任务的可靠性，甚至可将这些任务安排成按特定的时间间隔自动执行。 可以使用 Runbook 实现这些过程的自动化，或者使用 Desired State Configuration 实现配置管理的自动化。

## <a name="management-package"></a>管理包

### <a name="install-the-modules-with-npm"></a>使用 npm 安装模块

使用 npm 安装用于 Node.js 的 Azure 自动化模块

```bash
npm install azure-arm-automation
```

### <a name="example"></a>示例

此示例列出自动化帐户。

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

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
