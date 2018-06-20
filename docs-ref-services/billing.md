---
title: 用于 Node.js 的 Azure 计费模块
description: 用于 Node.js 的 Azure 计费模块参考
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 111ca8d4ed40200a307b608915d71d2fa6944ed2
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260340"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="fffaf-103">用于 Node.js 的 Azure 计费模块</span><span class="sxs-lookup"><span data-stu-id="fffaf-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="fffaf-104">概述</span><span class="sxs-lookup"><span data-stu-id="fffaf-104">Overview</span></span>
<span data-ttu-id="fffaf-105">使用 Azure 计费 API 可以访问 Azure 计费信息和发票。</span><span class="sxs-lookup"><span data-stu-id="fffaf-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="fffaf-106">若要使用此 API，帐户管理员必须通过 Azure 门户启用它。</span><span class="sxs-lookup"><span data-stu-id="fffaf-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="fffaf-107">请参阅[使用角色管理对 Azure 计费的访问](https://docs.microsoft.com/azure/billing/billing-manage-access)。</span><span class="sxs-lookup"><span data-stu-id="fffaf-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fffaf-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="fffaf-108">Install the npm module</span></span> 

<span data-ttu-id="fffaf-109">安装 Azure 计费 npm 模块</span><span class="sxs-lookup"><span data-stu-id="fffaf-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="fffaf-110">示例</span><span class="sxs-lookup"><span data-stu-id="fffaf-110">Example</span></span> 
 
<span data-ttu-id="fffaf-111">此示例列显过去所有发票的列表。</span><span class="sxs-lookup"><span data-stu-id="fffaf-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="fffaf-112">示例</span><span class="sxs-lookup"><span data-stu-id="fffaf-112">Samples</span></span>

<span data-ttu-id="fffaf-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="fffaf-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
