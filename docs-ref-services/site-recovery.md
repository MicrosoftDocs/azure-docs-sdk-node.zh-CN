---
title: "用于 Node.js 的 Azure Site Recovery 模块"
description: "用于 Node.js 的 Azure Site Recovery 模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: a1f3e1c18be68dd7e68f38e353e0c2ba224fbaa1
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="7a45a-103">用于 Node.js 的 Azure Site Recovery 模块</span><span class="sxs-lookup"><span data-stu-id="7a45a-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="7a45a-104">使用 Site Recovery 可以自动在区域之间复制 Azure VM、将本地虚拟机和物理服务器复制到 Azure，以及将本地计算机复制到辅助数据中心。</span><span class="sxs-lookup"><span data-stu-id="7a45a-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="7a45a-105">详细了解 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)。</span><span class="sxs-lookup"><span data-stu-id="7a45a-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="7a45a-106">管理包</span><span class="sxs-lookup"><span data-stu-id="7a45a-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7a45a-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="7a45a-107">Install the npm module</span></span>

<span data-ttu-id="7a45a-108">安装 Azure Site Recovery 服务 npm 模块</span><span class="sxs-lookup"><span data-stu-id="7a45a-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="7a45a-109">示例</span><span class="sxs-lookup"><span data-stu-id="7a45a-109">Example</span></span>

<span data-ttu-id="7a45a-110">此示例列出资源组的 Site Recovery 服务。</span><span class="sxs-lookup"><span data-stu-id="7a45a-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="7a45a-111">示例</span><span class="sxs-lookup"><span data-stu-id="7a45a-111">Samples</span></span>

<span data-ttu-id="7a45a-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="7a45a-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
