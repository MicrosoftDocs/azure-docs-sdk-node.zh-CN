---
title: 用于 Node.js 的虚拟机模块 - Azure
description: 用于 Node.js 的 Azure 虚拟机模块参考指南
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259839"
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>用于 Node.js 的 Azure 虚拟机模块

## <a name="overview"></a>概述

使用用于 Node.js 的 Azure 管理模块通过代码定义、配置和部署新的 Windows 与 Linux 虚拟机以及虚拟机规模集。 使用这些模块可以启动和停止现有的虚拟机，以及在 Azure 订阅中已停止的 VM 上附加或分离磁盘。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 计算 npm 模块

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>示例

以下示例演示如何登录到 Azure、创建管理客户端，以及列出指定位置、发布者、产品和 SKU 的所有 VM 映像。

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>示例

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
