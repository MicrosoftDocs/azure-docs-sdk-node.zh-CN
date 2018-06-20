---
title: 用于 Node.js 的 Azure 逻辑应用模块
description: 用于 Node.js 的 Azure 逻辑应用模块参考
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 2de867fdd0aa31b63b9680cc3f0c2e7f6301e632
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261548"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>用于 Node.js 的 Azure 逻辑应用模块

逻辑应用提供了用于在云中简化并实现可缩放的集成和工作流的方式。 它提供了可视化设计器，用于为流程建模并将流程作为一系列步骤（称为工作流）自动执行。 它在云中和本地提供多个连接器，可跨服务和协议快速集成。 逻辑应用以触发器开头（例如，“当将帐户添加到 Dynamics CRM 时”），在触发之后许多组合操作、转换和条件逻辑才能开始。

使用逻辑应用的优点包括：
- 使用易于掌握的设计工具设计复杂过程可节省时间
- 可无缝地实现用代码很难实现的模式和工作流
- 可以从模板快速入门
- 可以使用自己的自定义 API、代码和操作自定义逻辑应用
- 可连接并同步跨本地和云的不同系统
- 可利用一流集成支持从 BizTalk server、API 管理、Azure Functions 和 Azure 服务总线构建

逻辑应用是完全托管的 iPaaS（集成平台即服务），使开发人员无需担心如何实现托管、可伸缩性、可用性和管理。 逻辑应用会自动纵向扩展以满足需求。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装用于 Node.js 的 Azure 逻辑模块

```bash
npm install azure-arm-logic
```

### <a name="example"></a>示例

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

### <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
