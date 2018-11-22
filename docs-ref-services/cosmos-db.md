---
title: 用于 Node.js 的 Azure Cosmos DB 模块
description: 用于 Node.js 的 Azure Cosmos DB 模块参考
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 2e2813bb3b213de4066b2a3bc971586667a83f68
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2018
ms.locfileid: "52102065"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>用于 Node.js 的 Azure Cosmos DB 模块

Azure Cosmos DB 由 Microsoft 提供，是全球分布式多模型数据库。 使用 Azure Cosmos DB 可跨任意数量的 Azure 地理区域弹性且独立地缩放吞吐量和存储。 它通过综合服务级别协议 (SLA) 提供吞吐量、延迟、可用性和一致性保证，这是其他数据库服务无法提供的。

Azure Cosmos DB 包含一个与架构无关、已经过写入优化、资源受到管理的数据库引擎，该引擎本身支持多个数据模型：键值、文档、图和列式数据模型。 它还以可扩展的方式支持许多用于访问数据的 API，包括 MongoDB、SQL、Gremlin/Graph、Azure 表和 Cassandra（预览版）。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块 

安装 Azure Cosmos DB npm 模块。

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>示例

此示例列出所有 Azure Cosmos DB 帐户。

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a>示例

* [使用 Azure Cosmos DB 开发 Node.js 应用](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [使用 Azure Cosmos DB 开发 Node.js 应用 - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
