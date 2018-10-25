---
title: 用于 Node.js 的 Azure 备份模块
description: 用于 Node.js 的 Azure 备份模块参考
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: bf3e66ac8341cebd28dee20b6370ed3e5fbfbfa0
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "49728256"
---
# <a name="azure-backup-modules-for-nodejs"></a>用于 Node.js 的 Azure 备份模块

## <a name="overview"></a>概述

Azure 备份是基于 Azure 的服务，可用于备份（或保护）和还原 Microsoft 云端数据。 Azure 备份将现有的本地或异地备份解决方案替换为安全可靠、性价比高的云端解决方案。 Azure 备份提供多个组件，可将其下载并部署到适当的计算机、服务器或云中。 依据要保护的内容选择部署的组件或代理。 无论是保护本地数据还是云端数据，所有 Azure 备份组件均可用于将数据备份到 Azure 的恢复服务保管库中。 

## <a name="management-package"></a>管理包

### <a name="install-the-modules-with-npm"></a>使用 npm 安装模块

使用 npm 安装用于 Node.js 的 Azure 备份模块

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a>示例

此示例列出给定保管库和资源组的恢复作业。

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

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
