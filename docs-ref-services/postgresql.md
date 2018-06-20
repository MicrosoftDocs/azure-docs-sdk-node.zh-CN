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
ms.locfileid: "34262051"
---
# <a name="azure-postgresql-modules-for-nodejs"></a>用于 Node.js 的 Azure PostgreSQL 模块

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
