---
title: "用于 Node.js 的 Azure IoT 中心模块"
description: "用于 Node.js 的 Azure IoT 中心模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 66a0cad731d8e8dfd5cea64bdc910189a23fc6f0
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>用于 Node.js 的 Azure IoT 中心模块

Azure IoT 中心是一项完全托管的服务，可在数百万个 IoT 设备和一个解决方案后端之间实现安全可靠的双向通信。 Azure IoT 中心：
- 提供了多个设备到云和云到设备的通信选项，包括单向消息传递、文件传输和请求-答复方法。
- 将内置的声明性消息路由到其他 Azure 服务。
- 为设备元数据和同步的状态信息提供可查询存储。
- 使用每个设备的安全密钥或 X.509 证书来实现安全的通信和访问控制。
- 可广泛监视设备连接性和设备标识管理事件。
- 包含最流行语言和平台的设备库。

使用 npm 安装用于 Node.js 的 Azure IoT 中心模块

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure IoT 中心 npm 模块

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>示例

此示例创建并命名 IoT 中心。

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

此示例按名称获取现有的 IoT 中心。

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a>示例

- [Raspberry Pi Azure IoT 初学者工具包入门](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [通过推特发送 Azure IoT 服务根据运行 Node.js 的 Intel Edison 发出的数据检测到的振动异常](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
