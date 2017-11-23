---
title: "用于 Node.js 的 Azure IoT 中心模块"
description: "用于 Node.js 的 Azure IoT 中心模块参考"
keywords: "Azure,SDK,API,IoT 中心, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 44d01ceb833d2acbef6f9f22b32d4ad66b1fd5ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="e0d17-104">用于 Node.js 的 Azure IoT 中心模块</span><span class="sxs-lookup"><span data-stu-id="e0d17-104">Azure IoT Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e0d17-105">概述</span><span class="sxs-lookup"><span data-stu-id="e0d17-105">Overview</span></span>

<span data-ttu-id="e0d17-106">Azure IoT 中心是一项完全托管的服务，可在数百万个 IoT 设备和一个解决方案后端之间实现安全可靠的双向通信。</span><span class="sxs-lookup"><span data-stu-id="e0d17-106">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="e0d17-107">Azure IoT 中心：</span><span class="sxs-lookup"><span data-stu-id="e0d17-107">Azure IoT Hub:</span></span>
- <span data-ttu-id="e0d17-108">提供了多个设备到云和云到设备的通信选项，包括单向消息传递、文件传输和请求-答复方法。</span><span class="sxs-lookup"><span data-stu-id="e0d17-108">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="e0d17-109">将内置的声明性消息路由到其他 Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="e0d17-109">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="e0d17-110">为设备元数据和同步的状态信息提供可查询存储。</span><span class="sxs-lookup"><span data-stu-id="e0d17-110">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="e0d17-111">使用每个设备的安全密钥或 X.509 证书来实现安全的通信和访问控制。</span><span class="sxs-lookup"><span data-stu-id="e0d17-111">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="e0d17-112">可广泛监视设备连接性和设备标识管理事件。</span><span class="sxs-lookup"><span data-stu-id="e0d17-112">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="e0d17-113">包含最流行语言和平台的设备库。</span><span class="sxs-lookup"><span data-stu-id="e0d17-113">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="e0d17-114">使用 npm 安装用于 Node.js 的 Azure IoT 中心模块</span><span class="sxs-lookup"><span data-stu-id="e0d17-114">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="e0d17-115">管理包</span><span class="sxs-lookup"><span data-stu-id="e0d17-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e0d17-116">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="e0d17-116">Install the npm module</span></span>

<span data-ttu-id="e0d17-117">安装 Azure IoT 中心 npm 模块</span><span class="sxs-lookup"><span data-stu-id="e0d17-117">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="e0d17-118">示例</span><span class="sxs-lookup"><span data-stu-id="e0d17-118">Example</span></span>

<span data-ttu-id="e0d17-119">此示例创建并命名 IoT 中心。</span><span class="sxs-lookup"><span data-stu-id="e0d17-119">This example creates and names an IoT hub.</span></span>

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

<span data-ttu-id="e0d17-120">此示例按名称获取现有的 IoT 中心。</span><span class="sxs-lookup"><span data-stu-id="e0d17-120">This example gets the existing IoT hub, by name.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e0d17-121">示例</span><span class="sxs-lookup"><span data-stu-id="e0d17-121">Samples</span></span>

- [<span data-ttu-id="e0d17-122">Raspberry Pi Azure IoT 初学者工具包入门</span><span class="sxs-lookup"><span data-stu-id="e0d17-122">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="e0d17-123">通过推特发送 Azure IoT 服务根据运行 Node.js 的 Intel Edison 发出的数据检测到的振动异常</span><span class="sxs-lookup"><span data-stu-id="e0d17-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="e0d17-124">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="e0d17-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
