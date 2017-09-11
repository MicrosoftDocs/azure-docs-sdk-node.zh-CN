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
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="18b42-104">用于 Node.js 的 Azure MySQL 模块</span><span class="sxs-lookup"><span data-stu-id="18b42-104">Azure MySQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="18b42-105">概述</span><span class="sxs-lookup"><span data-stu-id="18b42-105">Overview</span></span>

<span data-ttu-id="18b42-106">建议用于访问 Azure Database for MySQL 的客户端库是开源的[用于 Azure Database for MySQL 的 Node.js 连接库](https://github.com/sidorares/node-mysql2)。</span><span class="sxs-lookup"><span data-stu-id="18b42-106">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="18b42-107">详细了解 [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="18b42-107">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="18b42-108">客户端包</span><span class="sxs-lookup"><span data-stu-id="18b42-108">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="18b42-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="18b42-109">Install the npm module</span></span>

<span data-ttu-id="18b42-110">使用 npm 安装 MySQL 客户端模块。</span><span class="sxs-lookup"><span data-stu-id="18b42-110">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="18b42-111">示例</span><span class="sxs-lookup"><span data-stu-id="18b42-111">Example</span></span>

<span data-ttu-id="18b42-112">此示例连接到 MySQL 数据库，并执行一个简单的查询来检索所有客户。</span><span class="sxs-lookup"><span data-stu-id="18b42-112">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="18b42-113">示例</span><span class="sxs-lookup"><span data-stu-id="18b42-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="18b42-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="18b42-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
