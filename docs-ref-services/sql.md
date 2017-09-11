---
title: "用于 Node.js 的 Azure SQL 模块"
description: "用于 Node.js 的 Azure SQL 模块参考"
keywords: Azure, Node, SDK, API, nodejs, javascript, sql
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 65ee90b4e6ca248b9d19a3685163211ca547cad4
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-sql-modules-for-nodejs"></a>用于 Node.js 的 Azure SQL 模块

## <a name="overview"></a>概述

通过 Node.js 处理 [Azure SQL 数据库](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)中存储的数据。
管理库提供一个接口用于方便管理 Microsoft Azure SQL 数据库。

## <a name="client-package"></a>客户端程序包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 SQL Server 客户端 npm 模块

```bash
npm install tedious
```

### <a name="example"></a>示例

此示例连接到 SQL Server 数据库并执行简单查询。

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a>管理包

### <a name="install-npm-modules"></a>安装 npm 模块

安装 Azure SQL Server 管理 npm 模块

```
npm install azure-arm-sql
```   

### <a name="example"></a>示例

执行身份验证，创建客户端，并列出所有服务器。

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>示例

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
