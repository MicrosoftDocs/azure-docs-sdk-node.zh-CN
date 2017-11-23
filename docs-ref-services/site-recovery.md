---
title: "用于 Node.js 的 Azure Site Recovery 模块"
description: "用于 Node.js 的 Azure Site Recovery 模块参考"
keywords: Azure,SDK,API,Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="f51bc-104">用于 Node.js 的 Azure Site Recovery 模块</span><span class="sxs-lookup"><span data-stu-id="f51bc-104">Azure Site Recovery modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f51bc-105">概述</span><span class="sxs-lookup"><span data-stu-id="f51bc-105">Overview</span></span>

<span data-ttu-id="f51bc-106">使用 Site Recovery 可以自动在区域之间复制 Azure VM、将本地虚拟机和物理服务器复制到 Azure，以及将本地计算机复制到辅助数据中心。</span><span class="sxs-lookup"><span data-stu-id="f51bc-106">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="f51bc-107">详细了解 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)。</span><span class="sxs-lookup"><span data-stu-id="f51bc-107">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="f51bc-108">管理包</span><span class="sxs-lookup"><span data-stu-id="f51bc-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f51bc-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="f51bc-109">Install the npm module</span></span>

<span data-ttu-id="f51bc-110">安装 Azure Site Recovery 服务 npm 模块</span><span class="sxs-lookup"><span data-stu-id="f51bc-110">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="f51bc-111">示例</span><span class="sxs-lookup"><span data-stu-id="f51bc-111">Example</span></span>

<span data-ttu-id="f51bc-112">此示例列出资源组的 Site Recovery 服务。</span><span class="sxs-lookup"><span data-stu-id="f51bc-112">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a><span data-ttu-id="f51bc-113">示例</span><span class="sxs-lookup"><span data-stu-id="f51bc-113">Samples</span></span>

<span data-ttu-id="f51bc-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f51bc-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
