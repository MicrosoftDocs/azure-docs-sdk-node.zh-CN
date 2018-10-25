---
title: 用于 Node.js 的 Azure DNS 模块
description: 用于 Node.js 的 Azure DNS 模块参考
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "49803497"
---
# <a name="azure-dns-modules-for-nodejs"></a>用于 Node.js 的 Azure DNS 模块

使用 Azure DNS 在 Azure 中托管域名系统 (DNS) 域。 可使用与其他 Azure 服务相同的凭据、计费方式和支持合同来管理 DNS 记录。 可将基于 Azure 的服务与相应的 DNS 更新进行无缝集成，简化端到端部署过程。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure DNS npm 模块

```bash
npm install azure-arm-dns
```

### <a name="example"></a>示例

此示例列出 DNS 管理区域。

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
