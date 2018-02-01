---
title: "用于 Node.js 的 Azure 虚拟网络模块"
description: "用于 Node.js 的 Azure 虚拟网络模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: f073c700c8df7f7aa05c93d725051d3a9976bebc
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>用于 Node.js 的 Azure 虚拟网络模块

## <a name="overview"></a>概述

通过 Azure 虚拟网络服务可安全地将 Azure 资源连接到具有虚拟网络 (VNet) 的各个资源。 VNet 是自己的网络在云中的表示形式。 VNet 是对专用于订阅的 Azure 云进行的逻辑隔离。 也可将 VNet 连接到本地网络。

详细了解 [Azure 虚拟网络](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 虚拟网络 npm 模块

```bash
npm install azure-arm-network
```

### <a name="example"></a>示例

此示例获取并列显虚拟网络的列表

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
