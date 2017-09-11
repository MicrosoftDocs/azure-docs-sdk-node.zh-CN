---
title: "用于 Node.js 的 Azure MySQL 模块"
description: "用于 Node.js 的 Azure MySQL 模块参考"
keywords: "Azure, Node, SDK, API, nodejs, javascript, 数据库, MySQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a>用于 Node.js 的 Azure MySQL 模块

## <a name="overview"></a>概述

建议用于访问 Azure Database for MySQL 的客户端库是开源的[用于 Azure Database for MySQL 的 Node.js 连接库](https://github.com/sidorares/node-mysql2)。 

详细了解 [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)

## <a name="client-package"></a>客户端包

### <a name="install-the-npm-module"></a>安装 npm 模块

使用 npm 安装 MySQL 客户端模块。

```bash
npm install mysql2
```   

### <a name="example"></a>示例

此示例连接到 MySQL 数据库，并执行一个简单的查询来检索所有客户。

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a>示例

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
