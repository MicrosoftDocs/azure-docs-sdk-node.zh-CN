---
title: "用于 Node.js 的 Azure PostgreSQL 模块"
description: "用于 Node.js 的 Azure PostgreSQL 模块参考"
keywords: "Azure, Node, SDK, API, nodejs, javascript, 数据库, PostgreSQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="b2a91-104">用于 Node.js 的 Azure PostgreSQL 模块</span><span class="sxs-lookup"><span data-stu-id="b2a91-104">Azure PostgreSQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b2a91-105">概述</span><span class="sxs-lookup"><span data-stu-id="b2a91-105">Overview</span></span>

<span data-ttu-id="b2a91-106">建议用于访问 Azure Database for PostgreSQL 的客户端库是开源的[用于 Azure Database for PostgreSQL 的 Node.js 连接库](https://www.npmjs.com/package/pg)。</span><span class="sxs-lookup"><span data-stu-id="b2a91-106">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="b2a91-107">此库是适用于 Node.js 的非阻塞性 PostgreSQL 客户端，支持纯粹的 JavaScript 和可选的本机 libpq 绑定。</span><span class="sxs-lookup"><span data-stu-id="b2a91-107">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="b2a91-108">详细了解 [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="b2a91-108">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="b2a91-109">客户端程序包</span><span class="sxs-lookup"><span data-stu-id="b2a91-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b2a91-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="b2a91-110">Install the npm module</span></span>

<span data-ttu-id="b2a91-111">使用 npm 安装 PostgreSQL 客户端模块。</span><span class="sxs-lookup"><span data-stu-id="b2a91-111">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="b2a91-112">示例</span><span class="sxs-lookup"><span data-stu-id="b2a91-112">Example</span></span>

<span data-ttu-id="b2a91-113">此示例打开客户端连接并执行简单查询。</span><span class="sxs-lookup"><span data-stu-id="b2a91-113">This example opens a client connection and executes a simple query.</span></span>

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a><span data-ttu-id="b2a91-114">示例</span><span class="sxs-lookup"><span data-stu-id="b2a91-114">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="b2a91-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b2a91-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
