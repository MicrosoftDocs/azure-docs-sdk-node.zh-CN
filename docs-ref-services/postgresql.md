---
title: 用于 Node.js 的 Azure PostgreSQL 模块
description: 用于 Node.js 的 Azure PostgreSQL 模块参考
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: 706f636a89e5e89c1dbf760e01c684bcc9588f1f
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="cbc8c-103">用于 Node.js 的 Azure PostgreSQL 模块</span><span class="sxs-lookup"><span data-stu-id="cbc8c-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="cbc8c-104">建议用于访问 Azure Database for PostgreSQL 的客户端库是开源的[用于 Azure Database for PostgreSQL 的 Node.js 连接库](https://www.npmjs.com/package/pg)。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="cbc8c-105">此库是适用于 Node.js 的非阻塞性 PostgreSQL 客户端，支持纯粹的 JavaScript 和可选的本机 libpq 绑定。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="cbc8c-106">详细了解 [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="cbc8c-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="cbc8c-107">客户端程序包</span><span class="sxs-lookup"><span data-stu-id="cbc8c-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cbc8c-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="cbc8c-108">Install the npm module</span></span>

<span data-ttu-id="cbc8c-109">使用 npm 安装 PostgreSQL 客户端模块。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="cbc8c-110">示例</span><span class="sxs-lookup"><span data-stu-id="cbc8c-110">Example</span></span>

<span data-ttu-id="cbc8c-111">此示例打开客户端连接并执行简单查询。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="cbc8c-112">示例</span><span class="sxs-lookup"><span data-stu-id="cbc8c-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="cbc8c-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
