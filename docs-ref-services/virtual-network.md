---
title: "用于 Node.js 的 Azure 虚拟网络模块"
description: "用于 Node.js 的 Azure 虚拟网络模块参考"
keywords: "Azure,SDK,API,虚拟网络, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="fd82a-104">用于 Node.js 的 Azure 虚拟网络模块</span><span class="sxs-lookup"><span data-stu-id="fd82a-104">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="fd82a-105">概述</span><span class="sxs-lookup"><span data-stu-id="fd82a-105">Overview</span></span>

<span data-ttu-id="fd82a-106">通过 Azure 虚拟网络服务可安全地将 Azure 资源连接到具有虚拟网络 (VNet) 的各个资源。</span><span class="sxs-lookup"><span data-stu-id="fd82a-106">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="fd82a-107">VNet 是自己的网络在云中的表示形式。</span><span class="sxs-lookup"><span data-stu-id="fd82a-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="fd82a-108">VNet 是对专用于订阅的 Azure 云进行的逻辑隔离。</span><span class="sxs-lookup"><span data-stu-id="fd82a-108">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="fd82a-109">也可将 VNet 连接到本地网络。</span><span class="sxs-lookup"><span data-stu-id="fd82a-109">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="fd82a-110">详细了解 [Azure 虚拟网络](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)。</span><span class="sxs-lookup"><span data-stu-id="fd82a-110">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="fd82a-111">管理包</span><span class="sxs-lookup"><span data-stu-id="fd82a-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fd82a-112">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="fd82a-112">Install the npm module</span></span>

<span data-ttu-id="fd82a-113">安装 Azure 虚拟网络 npm 模块</span><span class="sxs-lookup"><span data-stu-id="fd82a-113">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="fd82a-114">示例</span><span class="sxs-lookup"><span data-stu-id="fd82a-114">Example</span></span>

<span data-ttu-id="fd82a-115">此示例获取并列显虚拟网络的列表</span><span class="sxs-lookup"><span data-stu-id="fd82a-115">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="fd82a-116">示例</span><span class="sxs-lookup"><span data-stu-id="fd82a-116">Samples</span></span>

<span data-ttu-id="fd82a-117">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="fd82a-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
