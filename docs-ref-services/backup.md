---
title: "用于 Node.js 的 Azure 备份模块"
description: "用于 Node.js 的 Azure 备份模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 83ccd48d6f66c49ed6be837384a39cb32919b83c
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="59641-103">用于 Node.js 的 Azure 备份模块</span><span class="sxs-lookup"><span data-stu-id="59641-103">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="59641-104">概述</span><span class="sxs-lookup"><span data-stu-id="59641-104">Overview</span></span>

<span data-ttu-id="59641-105">Azure 备份是基于 Azure 的服务，可用于备份（或保护）和还原 Microsoft 云端数据。</span><span class="sxs-lookup"><span data-stu-id="59641-105">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="59641-106">Azure 备份将现有的本地或异地备份解决方案替换为安全可靠、性价比高的云端解决方案。</span><span class="sxs-lookup"><span data-stu-id="59641-106">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="59641-107">Azure 备份提供多个组件，可将其下载并部署到适当计算机、服务器或云端。</span><span class="sxs-lookup"><span data-stu-id="59641-107">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="59641-108">依据要保护的内容选择部署的组件或代理。</span><span class="sxs-lookup"><span data-stu-id="59641-108">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="59641-109">无论是保护本地数据还是云端数据，所有 Azure 备份组件均可用于将数据备份到 Azure 的恢复服务保管库中。</span><span class="sxs-lookup"><span data-stu-id="59641-109">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="59641-110">管理包</span><span class="sxs-lookup"><span data-stu-id="59641-110">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="59641-111">使用 npm 安装模块</span><span class="sxs-lookup"><span data-stu-id="59641-111">Install the modules with npm</span></span>

<span data-ttu-id="59641-112">使用 npm 安装用于 Node.js 的 Azure 备份模块</span><span class="sxs-lookup"><span data-stu-id="59641-112">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="59641-113">示例</span><span class="sxs-lookup"><span data-stu-id="59641-113">Example</span></span>

<span data-ttu-id="59641-114">此示例列出给定保管库和资源组的恢复作业。</span><span class="sxs-lookup"><span data-stu-id="59641-114">This example lists the recovery jobs for a given vault and resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="59641-115">示例</span><span class="sxs-lookup"><span data-stu-id="59641-115">Samples</span></span>

<span data-ttu-id="59641-116">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="59641-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
