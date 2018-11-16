---
title: 用于 Node.js 的 Azure 事件中心模块
description: 用于 Node.js 的 Azure 事件中心模块参考
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: cf50d0e69e336dac9addc85625599fbbefd1902e
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51425161"
---
# <a name="azure-event-hub-modules-for-nodejs"></a>用于 Node.js 的 Azure 事件中心模块

Azure 事件中心是高度可缩放的数据流式处理平台和事件引入服务，能够每秒接收和处理数百万事件。 事件中心可以处理和存储分布式软件和设备生成的事件、数据或遥测。 可以使用任何实时分析提供程序或批处理/存储适配器转换和存储发送到数据中心的数据。 由于能够以较低的延迟和极高的规模提供发布订阅功能，事件中心可以充当大数据的“入口”。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块 

使用 npm 安装用于 Node.js 的 Azure 事件中心模块

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a>示例

此示例检索有关现有事件中心的信息。

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
