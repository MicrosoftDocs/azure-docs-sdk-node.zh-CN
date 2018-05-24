---
title: 用于 Node.js 的 Azure Redis 缓存模块
description: 用于 Node.js 的 Azure Redis 缓存模块参考
author: wesmc7777
ms.author: wesmc
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: afeee19cb79b54561b6cbef4a79de8b1606adb4d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="azure-redis-cache-modules-for-nodejs"></a>用于 Node.js 的 Azure Redis 缓存模块

Azure Redis 缓存基于流行的开源 Redis 项目。 使用它可以访问 Microsoft 管理的、可从 Azure 应用访问的安全专用 Redis 实例。

Redis 是一种高级键值存储，其中键可包含数据结构，例如字符串、哈希、列表、集和排序集。 Redis 支持针对这些数据类型的一组原子操作。

详细了解 [Azure Redis 缓存](https://docs.microsoft.com/azure/redis-cache/)。

## <a name="client-package"></a>客户端程序包

### <a name="install-the-npm-module"></a>安装 npm 模块

使用 npm 安装用于 Node.js 的 Redis 模块

```bash
npm install redis
```

### <a name="example"></a>示例

此示例连接到 Azure Redis 缓存实例，存储键/值对，然后根据键读取存储的值。

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

使用 npm 安装用于 Node.js 的 Azure Redis 缓存模块

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>示例

此示例在 Azure 中进行身份验证，并列出指定资源组中的所有 Redis 缓存实例。

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a>示例

* [如何在 Node.js 中使用 Azure Redis 缓存](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
