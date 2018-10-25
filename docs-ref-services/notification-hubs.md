---
title: 用于 Node.js 的 Azure 通知中心模块
description: 用于 Node.js 的 Azure 通知中心模块参考
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 18eae632b41b71bc64b052852b677507da2678e9
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "49720682"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>用于 Node.js 的 Azure 通知中心模块

Azure 通知中心提供易用的多平台扩展式推送引擎。 使用单个跨平台 API 调用，即可轻松地从任意云或本地后端向任意移动平台发送有针对性的个性化推送通知。

通知中心非常适合用于企业和消费者方案。 下面是通知中心的几个客户用例：
- 以较低的延迟向数百万用户发送突发新闻通知。
- 向感兴趣的用户群发送基于位置的优惠券。
- 向媒体/体育/财经/游戏应用程序的用户或组发送活动相关的通知。
- 将促销内容推送到应用，以吸引客户并向其推销。
- 向用户通知企业事件，例如，有新消息和新的工作项。
- 发送多重身份验证的代码。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 通知中心模块 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>示例

此示例列出所有通知中心。

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a>示例

* [Node.js 后端的应用服务移动应用完整快速入门](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [通过推特发送 Azure IoT 服务根据运行 Node.js 的 Intel Edison 发出的数据检测到的振动异常](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
