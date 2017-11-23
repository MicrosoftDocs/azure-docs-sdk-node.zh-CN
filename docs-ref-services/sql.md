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
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="51649-104">用于 Node.js 的 Azure SQL 模块</span><span class="sxs-lookup"><span data-stu-id="51649-104">Azure SQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="51649-105">概述</span><span class="sxs-lookup"><span data-stu-id="51649-105">Overview</span></span>

<span data-ttu-id="51649-106">通过 Node.js 处理 [Azure SQL 数据库](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)中存储的数据。</span><span class="sxs-lookup"><span data-stu-id="51649-106">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="51649-107">管理库提供一个接口用于方便管理 Microsoft Azure SQL 数据库。</span><span class="sxs-lookup"><span data-stu-id="51649-107">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="51649-108">客户端程序包</span><span class="sxs-lookup"><span data-stu-id="51649-108">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="51649-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="51649-109">Install the npm module</span></span>

<span data-ttu-id="51649-110">安装 SQL Server 客户端 npm 模块</span><span class="sxs-lookup"><span data-stu-id="51649-110">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="51649-111">示例</span><span class="sxs-lookup"><span data-stu-id="51649-111">Example</span></span>

<span data-ttu-id="51649-112">此示例连接到 SQL Server 数据库并执行简单查询。</span><span class="sxs-lookup"><span data-stu-id="51649-112">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="51649-113">管理包</span><span class="sxs-lookup"><span data-stu-id="51649-113">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="51649-114">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="51649-114">Install npm modules</span></span>

<span data-ttu-id="51649-115">安装 Azure SQL Server 管理 npm 模块</span><span class="sxs-lookup"><span data-stu-id="51649-115">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="51649-116">示例</span><span class="sxs-lookup"><span data-stu-id="51649-116">Example</span></span>

<span data-ttu-id="51649-117">执行身份验证，创建客户端，并列出所有服务器。</span><span class="sxs-lookup"><span data-stu-id="51649-117">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="51649-118">示例</span><span class="sxs-lookup"><span data-stu-id="51649-118">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="51649-119">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="51649-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
