---
title: 用于 Node.js 的 Azure 计费模块
description: 用于 Node.js 的 Azure 计费模块参考
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 20df85ae5e504e460a501737aa07b6692a0da3c7
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48571585"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="4a3aa-103">用于 Node.js 的 Azure 计费模块</span><span class="sxs-lookup"><span data-stu-id="4a3aa-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4a3aa-104">概述</span><span class="sxs-lookup"><span data-stu-id="4a3aa-104">Overview</span></span>
<span data-ttu-id="4a3aa-105">使用 Azure 计费 API 可以访问 Azure 计费信息和发票。</span><span class="sxs-lookup"><span data-stu-id="4a3aa-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="4a3aa-106">若要使用此 API，帐户管理员必须通过 Azure 门户启用它。</span><span class="sxs-lookup"><span data-stu-id="4a3aa-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="4a3aa-107">请参阅[使用角色管理对 Azure 计费的访问](https://docs.microsoft.com/azure/billing/billing-manage-access)。</span><span class="sxs-lookup"><span data-stu-id="4a3aa-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4a3aa-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="4a3aa-108">Install the npm module</span></span> 

<span data-ttu-id="4a3aa-109">安装 Azure 计费 npm 模块</span><span class="sxs-lookup"><span data-stu-id="4a3aa-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="4a3aa-110">示例</span><span class="sxs-lookup"><span data-stu-id="4a3aa-110">Example</span></span> 
 
<span data-ttu-id="4a3aa-111">此示例列显过去所有发票的列表。</span><span class="sxs-lookup"><span data-stu-id="4a3aa-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="4a3aa-112">示例</span><span class="sxs-lookup"><span data-stu-id="4a3aa-112">Samples</span></span>

<span data-ttu-id="4a3aa-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="4a3aa-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
