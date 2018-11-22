---
title: 用于 Node.js 的 Azure Cosmos DB 模块
description: 用于 Node.js 的 Azure Cosmos DB 模块参考
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 2e2813bb3b213de4066b2a3bc971586667a83f68
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2018
ms.locfileid: "52102065"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="a2b35-103">用于 Node.js 的 Azure Cosmos DB 模块</span><span class="sxs-lookup"><span data-stu-id="a2b35-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="a2b35-104">Azure Cosmos DB 由 Microsoft 提供，是全球分布式多模型数据库。</span><span class="sxs-lookup"><span data-stu-id="a2b35-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="a2b35-105">使用 Azure Cosmos DB 可跨任意数量的 Azure 地理区域弹性且独立地缩放吞吐量和存储。</span><span class="sxs-lookup"><span data-stu-id="a2b35-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="a2b35-106">它通过综合服务级别协议 (SLA) 提供吞吐量、延迟、可用性和一致性保证，这是其他数据库服务无法提供的。</span><span class="sxs-lookup"><span data-stu-id="a2b35-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="a2b35-107">Azure Cosmos DB 包含一个与架构无关、已经过写入优化、资源受到管理的数据库引擎，该引擎本身支持多个数据模型：键值、文档、图和列式数据模型。</span><span class="sxs-lookup"><span data-stu-id="a2b35-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="a2b35-108">它还以可扩展的方式支持许多用于访问数据的 API，包括 MongoDB、SQL、Gremlin/Graph、Azure 表和 Cassandra（预览版）。</span><span class="sxs-lookup"><span data-stu-id="a2b35-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="a2b35-109">管理包</span><span class="sxs-lookup"><span data-stu-id="a2b35-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a2b35-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="a2b35-110">Install the npm module</span></span> 

<span data-ttu-id="a2b35-111">安装 Azure Cosmos DB npm 模块。</span><span class="sxs-lookup"><span data-stu-id="a2b35-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="a2b35-112">示例</span><span class="sxs-lookup"><span data-stu-id="a2b35-112">Example</span></span>

<span data-ttu-id="a2b35-113">此示例列出所有 Azure Cosmos DB 帐户。</span><span class="sxs-lookup"><span data-stu-id="a2b35-113">This example lists all Azure Cosmos DB accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a><span data-ttu-id="a2b35-114">示例</span><span class="sxs-lookup"><span data-stu-id="a2b35-114">Samples</span></span>

* [<span data-ttu-id="a2b35-115">使用 Azure Cosmos DB 开发 Node.js 应用</span><span class="sxs-lookup"><span data-stu-id="a2b35-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="a2b35-116">使用 Azure Cosmos DB 开发 Node.js 应用 - Gremlin</span><span class="sxs-lookup"><span data-stu-id="a2b35-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="a2b35-117">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="a2b35-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
