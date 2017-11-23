---
title: "用于 Node.js 的 Azure 计费模块"
description: "用于 Node.js 的 Azure 计费模块参考"
keywords: "Azure,SDK,API,计费, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="f1d17-104">用于 Node.js 的 Azure 计费模块</span><span class="sxs-lookup"><span data-stu-id="f1d17-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f1d17-105">概述</span><span class="sxs-lookup"><span data-stu-id="f1d17-105">Overview</span></span>
<span data-ttu-id="f1d17-106">使用 Azure 计费 API 可以访问 Azure 计费信息和发票。</span><span class="sxs-lookup"><span data-stu-id="f1d17-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="f1d17-107">若要使用此 API，帐户管理员必须通过 Azure 门户启用它。</span><span class="sxs-lookup"><span data-stu-id="f1d17-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="f1d17-108">请参阅[使用角色管理对 Azure 计费的访问](https://docs.microsoft.com/azure/billing/billing-manage-access)。</span><span class="sxs-lookup"><span data-stu-id="f1d17-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f1d17-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="f1d17-109">Install the npm module</span></span> 

<span data-ttu-id="f1d17-110">安装 Azure 计费 npm 模块</span><span class="sxs-lookup"><span data-stu-id="f1d17-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="f1d17-111">示例</span><span class="sxs-lookup"><span data-stu-id="f1d17-111">Example</span></span> 
 
<span data-ttu-id="f1d17-112">此示例列显过去所有发票的列表。</span><span class="sxs-lookup"><span data-stu-id="f1d17-112">This example prints a list of all of your past invoices.</span></span>
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a><span data-ttu-id="f1d17-113">示例</span><span class="sxs-lookup"><span data-stu-id="f1d17-113">Samples</span></span>

<span data-ttu-id="f1d17-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f1d17-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
