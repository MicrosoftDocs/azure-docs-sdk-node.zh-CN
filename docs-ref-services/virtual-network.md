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
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="2c2b1-103">用于 Node.js 的 Azure 虚拟网络模块</span><span class="sxs-lookup"><span data-stu-id="2c2b1-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2c2b1-104">概述</span><span class="sxs-lookup"><span data-stu-id="2c2b1-104">Overview</span></span>

<span data-ttu-id="2c2b1-105">通过 Azure 虚拟网络服务可安全地将 Azure 资源连接到具有虚拟网络 (VNet) 的各个资源。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="2c2b1-106">VNet 是自己的网络在云中的表示形式。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="2c2b1-107">VNet 是对专用于订阅的 Azure 云进行的逻辑隔离。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="2c2b1-108">也可将 VNet 连接到本地网络。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="2c2b1-109">详细了解 [Azure 虚拟网络](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="2c2b1-110">管理包</span><span class="sxs-lookup"><span data-stu-id="2c2b1-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2c2b1-111">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="2c2b1-111">Install the npm module</span></span>

<span data-ttu-id="2c2b1-112">安装 Azure 虚拟网络 npm 模块</span><span class="sxs-lookup"><span data-stu-id="2c2b1-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="2c2b1-113">示例</span><span class="sxs-lookup"><span data-stu-id="2c2b1-113">Example</span></span>

<span data-ttu-id="2c2b1-114">此示例获取并列显虚拟网络的列表</span><span class="sxs-lookup"><span data-stu-id="2c2b1-114">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="2c2b1-115">示例</span><span class="sxs-lookup"><span data-stu-id="2c2b1-115">Samples</span></span>

<span data-ttu-id="2c2b1-116">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
