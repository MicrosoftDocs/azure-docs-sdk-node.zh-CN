---
title: 用于 Node.js 的 Azure MySQL 模块
description: 用于 Node.js 的 Azure MySQL 模块参考
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49019081"
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="8b6c0-103">用于 Node.js 的 Azure MySQL 模块</span><span class="sxs-lookup"><span data-stu-id="8b6c0-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="8b6c0-104">建议用于访问 Azure Database for MySQL 的客户端库是开源的[用于 Azure Database for MySQL 的 Node.js 连接库](https://github.com/sidorares/node-mysql2)。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="8b6c0-105">详细了解 [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="8b6c0-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="8b6c0-106">客户端包</span><span class="sxs-lookup"><span data-stu-id="8b6c0-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8b6c0-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="8b6c0-107">Install the npm module</span></span>

<span data-ttu-id="8b6c0-108">使用 npm 安装 MySQL 客户端模块。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="8b6c0-109">示例</span><span class="sxs-lookup"><span data-stu-id="8b6c0-109">Example</span></span>

<span data-ttu-id="8b6c0-110">此示例连接到 MySQL 数据库，并执行一个简单的查询来检索所有客户。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="8b6c0-111">示例</span><span class="sxs-lookup"><span data-stu-id="8b6c0-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="8b6c0-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
