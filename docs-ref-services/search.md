---
title: 用于 Node.js 的 Azure 搜索模块
description: 用于 Node.js 的 Azure 搜索模块参考
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: 895281acd2359240f3d483e4205c628e1f85f724
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="0bd90-103">用于 Node.js 的 Azure 搜索模块</span><span class="sxs-lookup"><span data-stu-id="0bd90-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="0bd90-104">Azure 搜索是一种搜索即服务云解决方案，它将服务器和基础结构的管理委托给 Microsoft，提供随时可用的服务。可在填充数据后使用此服务将搜索添加到应用程序。</span><span class="sxs-lookup"><span data-stu-id="0bd90-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="0bd90-105">详细了解 [Azure 搜索](https://docs.microsoft.com/azure/search/search-what-is-azure-search)。</span><span class="sxs-lookup"><span data-stu-id="0bd90-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="0bd90-106">管理包</span><span class="sxs-lookup"><span data-stu-id="0bd90-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0bd90-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0bd90-107">Install the npm module</span></span>

<span data-ttu-id="0bd90-108">安装 Azure 搜索 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0bd90-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="0bd90-109">示例</span><span class="sxs-lookup"><span data-stu-id="0bd90-109">Example</span></span>

<span data-ttu-id="0bd90-110">此示例在 Azure 中创建新的搜索服务，并列出其资源组中的资源。</span><span class="sxs-lookup"><span data-stu-id="0bd90-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="0bd90-111">示例</span><span class="sxs-lookup"><span data-stu-id="0bd90-111">Samples</span></span>

<span data-ttu-id="0bd90-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="0bd90-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
