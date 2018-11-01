---
title: 用于 Node.js 的 Azure 服务总线模块
description: 用于 Node.js 的 Azure 服务总线模块参考
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 76d7c615cbe64fa38f9c28ea8dfc6d1c854bb0c9
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50272190"
---
# <a name="azure-service-bus-modules-for-nodejs"></a>用于 Node.js 的 Azure 服务总线模块

Azure 服务总线是一个异步消息传送云平台，可用于在分离的系统之间发送数据。

详细了解 [Azure 服务总线](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

使用 npm 安装用于 Node.js 的 Azure 服务总线模块

```bash
npm install azure-arm-sb
```

### <a name="example"></a>示例

此示例创建一个客户端，然后列出与给定订阅关联的所有服务总线命名空间。

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

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
