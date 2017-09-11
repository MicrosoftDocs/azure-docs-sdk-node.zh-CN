---
title: "用于 Node.js 的 Azure 虚拟机模块"
description: "用于 Node.js 的 Azure 虚拟机模块参考"
keywords: "Azure, Node, SDK, API, 虚拟机, vm, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="1cca9-104">用于 Node.js 的 Azure 虚拟机模块</span><span class="sxs-lookup"><span data-stu-id="1cca9-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1cca9-105">概述</span><span class="sxs-lookup"><span data-stu-id="1cca9-105">Overview</span></span>

<span data-ttu-id="1cca9-106">使用用于 Node.js 的 Azure 管理模块通过代码定义、配置和部署新的 Windows 与 Linux 虚拟机以及虚拟机规模集。</span><span class="sxs-lookup"><span data-stu-id="1cca9-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="1cca9-107">使用这些模块可以启动和停止现有的虚拟机，以及在 Azure 订阅中已停止的 VM 上附加或分离磁盘。</span><span class="sxs-lookup"><span data-stu-id="1cca9-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="1cca9-108">管理包</span><span class="sxs-lookup"><span data-stu-id="1cca9-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1cca9-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="1cca9-109">Install the npm module</span></span>

<span data-ttu-id="1cca9-110">安装 Azure 计算 npm 模块</span><span class="sxs-lookup"><span data-stu-id="1cca9-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="1cca9-111">示例</span><span class="sxs-lookup"><span data-stu-id="1cca9-111">Example</span></span>

<span data-ttu-id="1cca9-112">以下示例演示如何登录到 Azure、创建管理客户端，以及列出指定位置、发布者、产品和 SKU 的所有 VM 映像。</span><span class="sxs-lookup"><span data-stu-id="1cca9-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="1cca9-113">示例</span><span class="sxs-lookup"><span data-stu-id="1cca9-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="1cca9-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="1cca9-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
