---
title: 用于 Node.js 的 Azure PostgreSQL 模块
description: 用于 Node.js 的 Azure PostgreSQL 模块参考
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: ed9373b767684e4893ca84de1030d062178b7ea4
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48514665"
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="9a9a8-103">用于 Node.js 的 Azure PostgreSQL 模块</span><span class="sxs-lookup"><span data-stu-id="9a9a8-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="9a9a8-104">建议用于访问 Azure Database for PostgreSQL 的客户端库是开源的[用于 Azure Database for PostgreSQL 的 Node.js 连接库](https://www.npmjs.com/package/pg)。</span><span class="sxs-lookup"><span data-stu-id="9a9a8-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="9a9a8-105">此库是适用于 Node.js 的非阻塞性 PostgreSQL 客户端，支持纯粹的 JavaScript 和可选的本机 libpq 绑定。</span><span class="sxs-lookup"><span data-stu-id="9a9a8-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="9a9a8-106">详细了解 [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="9a9a8-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="9a9a8-107">客户端程序包</span><span class="sxs-lookup"><span data-stu-id="9a9a8-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9a9a8-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="9a9a8-108">Install the npm module</span></span>

<span data-ttu-id="9a9a8-109">使用 npm 安装 PostgreSQL 客户端模块。</span><span class="sxs-lookup"><span data-stu-id="9a9a8-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="9a9a8-110">示例</span><span class="sxs-lookup"><span data-stu-id="9a9a8-110">Example</span></span>

<span data-ttu-id="9a9a8-111">此示例打开客户端连接并执行简单查询。</span><span class="sxs-lookup"><span data-stu-id="9a9a8-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9a9a8-112">示例</span><span class="sxs-lookup"><span data-stu-id="9a9a8-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="9a9a8-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="9a9a8-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
