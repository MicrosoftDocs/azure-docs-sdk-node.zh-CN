---
title: "用于 Node.js 的 Azure Key Vault 模块"
description: "用于 Node.js 的 Azure Key Vault 模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: aacc02088236ee5b6a941dfb266b9b198b04ad3a
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-key-vault-modules-for-nodejs"></a>用于 Node.js 的 Azure Key Vault 模块

Azure 密钥保管库可帮助保护云应用程序和服务使用的加密密钥和机密。 通过密钥保管库，可以使用受硬件安全模块 (HSM) 保护的密钥，来加密密钥和机密（例如身份验证密钥、存储帐户密钥、数据加密密钥、.PFX 文件和密码）。 为了提升可靠性，可以在 HSM 中导入或生成密钥。 如果选择这样做，Microsoft 会在通过 FIPS 140-2 第 2 级验证的 HSM（硬件和固件）中处理密钥。

Key Vault 简化了密钥管理过程，可让我们控制用于访问和加密数据的密钥。 开发人员可以在几分钟内创建用于开发和测试的密钥，然后无缝地将其迁移到生产密钥。 安全管理员可以根据需要授予（和吊销）密钥权限。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块 

安装 Azure Key Vault npm 模块

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>示例

此示例在 Azure 中创建新的 Key Vault 服务。

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a>示例

- [Node.js 中的 Key Vault 入门](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [使用 Node.js 管理 Azure 资源和资源组](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [将 Azure AD 集成到 NodeJS Web 应用程序](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
