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
# <a name="azure-postgresql-modules-for-nodejs"></a>用于 Node.js 的 Azure PostgreSQL 模块

## <a name="overview"></a>概述

建议用于访问 Azure Database for PostgreSQL 的客户端库是开源的[用于 Azure Database for PostgreSQL 的 Node.js 连接库](https://www.npmjs.com/package/pg)。 此库是适用于 Node.js 的非阻塞性 PostgreSQL 客户端，支持纯粹的 JavaScript 和可选的本机 libpq 绑定。

详细了解 [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)

## <a name="client-package"></a>客户端程序包

### <a name="install-the-npm-module"></a>安装 npm 模块

使用 npm 安装 PostgreSQL 客户端模块。

```bash
npm install pg
```   

### <a name="example"></a>示例

此示例打开客户端连接并执行简单查询。

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

## <a name="samples"></a>示例

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
