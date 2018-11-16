---
title: 用于 Node.js 的 Azure 流量管理器模块
description: 用于 Node.js 的 Azure 流量管理器模块参考
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 2a32eed460c6076011fdcf31d77200502ef61a3d
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51366451"
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a>用于 Node.js 的 Azure 流量管理器模块

## <a name="overview"></a>概述

使用 Microsoft Azure 流量管理器，可以控制用户流量在不同数据中心内的服务终结点上的分布。 流量管理器支持的服务终结点包括 Azure VM、Web 应用和云服务。 也可将流量管理器用于外部的非 Azure 终结点。

详细了解 [Azure 流量管理器](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 流量管理器 npm 模块

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>示例

此示例列出给定资源组的所有流量管理器。

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
