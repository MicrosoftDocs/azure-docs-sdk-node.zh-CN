---
title: 用于 Node.js 的 Azure Service Fabric 模块
description: 用于 Node.js 的 Azure Service Fabric 模块参考
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51438401"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a>用于 Node.js 的 Azure Service Fabric 模块

## <a name="overview"></a>概述

Azure Service Fabric 是一款分布式系统平台，可方便用户轻松打包、部署和管理可缩放的可靠微服务和容器。

详细了解 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure Service Fabric npm 模块

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a>示例

此示例演示如何列出 Azure 订阅的群集。

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
