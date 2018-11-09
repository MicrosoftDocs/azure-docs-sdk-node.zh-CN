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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2018
ms.locfileid: "51062036"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="e6519-103">用于 Node.js 的 Azure DNS 模块</span><span class="sxs-lookup"><span data-stu-id="e6519-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="e6519-104">使用 Azure DNS 在 Azure 中托管域名系统 (DNS) 域。</span><span class="sxs-lookup"><span data-stu-id="e6519-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="e6519-105">可使用与其他 Azure 服务相同的凭据、计费方式和支持合同来管理 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="e6519-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="e6519-106">可将基于 Azure 的服务与相应的 DNS 更新进行无缝集成，简化端到端部署过程。</span><span class="sxs-lookup"><span data-stu-id="e6519-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="e6519-107">管理包</span><span class="sxs-lookup"><span data-stu-id="e6519-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e6519-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="e6519-108">Install the npm module</span></span>

<span data-ttu-id="e6519-109">安装 Azure DNS npm 模块</span><span class="sxs-lookup"><span data-stu-id="e6519-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="e6519-110">示例</span><span class="sxs-lookup"><span data-stu-id="e6519-110">Example</span></span>

<span data-ttu-id="e6519-111">此示例列出 DNS 管理区域。</span><span class="sxs-lookup"><span data-stu-id="e6519-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e6519-112">示例</span><span class="sxs-lookup"><span data-stu-id="e6519-112">Samples</span></span>

<span data-ttu-id="e6519-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="e6519-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
