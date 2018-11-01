---
title: 用于 Node.js 的 Azure Data Lake Store 模块
description: 用于 Node.js 的 Azure Data Lake Store 模块参考
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50354255"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="8f817-103">用于 Node.js 的 Azure Data Lake Store 模块</span><span class="sxs-lookup"><span data-stu-id="8f817-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="8f817-104">Azure Data Lake Store 是一个企业范围的超大规模存储库，适用于大数据分析工作负载。</span><span class="sxs-lookup"><span data-stu-id="8f817-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="8f817-105">使用 Azure Data Lake 可以在单个位置捕获任何大小、类型和引入速度的数据进行操作和探索分析。</span><span class="sxs-lookup"><span data-stu-id="8f817-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="8f817-106">管理包</span><span class="sxs-lookup"><span data-stu-id="8f817-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8f817-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="8f817-107">Install the npm module</span></span>

<span data-ttu-id="8f817-108">使用 npm 安装用于 Node.js 的 Azure Data Lake Store 模块</span><span class="sxs-lookup"><span data-stu-id="8f817-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="8f817-109">示例</span><span class="sxs-lookup"><span data-stu-id="8f817-109">Example</span></span>

<span data-ttu-id="8f817-110">此示例列出给定 Azure 订阅中的所有 Data Lake Store 帐户。</span><span class="sxs-lookup"><span data-stu-id="8f817-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="8f817-111">示例</span><span class="sxs-lookup"><span data-stu-id="8f817-111">Samples</span></span>

<span data-ttu-id="8f817-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="8f817-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
