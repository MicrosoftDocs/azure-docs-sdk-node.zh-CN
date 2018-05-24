---
title: 用于 Node.js 的 Azure 服务映射模块
description: 用于 Node.js 的 Azure 服务映射模块参考
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: db064603e32446ba2f094da2a1601520b99a7304
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="azure-service-map-modules-for-nodejs"></a>用于 Node.js 的 Azure 服务映射模块

服务映射自动发现 Windows 和 Linux 系统上的应用程序组件并映射服务之间的通信。 服务映射显示 TCP 连接的任何体系结构中服务器、进程和端口之间的连接，只需安装代理，无需任何其他配置。

详细了解 [Azure 服务映射](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 服务映射 npm 模块

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a>示例

此示例列出指定的资源组和工作区的所有服务映射。

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
