---
title: "用于 Node.js 的 Azure Redis 缓存模块"
description: "用于 Node.js 的 Azure Redis 缓存模块参考"
keywords: "Azure,SDK,API,Redis 缓存, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 8a10e522e39461697b740750b63fc82a6cc320ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="179e4-104">用于 Node.js 的 Azure Redis 缓存模块</span><span class="sxs-lookup"><span data-stu-id="179e4-104">Azure Redis Cache modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="179e4-105">概述</span><span class="sxs-lookup"><span data-stu-id="179e4-105">Overview</span></span>

<span data-ttu-id="179e4-106">Azure Redis 缓存基于流行的开源 Redis 项目。</span><span class="sxs-lookup"><span data-stu-id="179e4-106">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="179e4-107">使用它可以访问 Microsoft 管理的、可从 Azure 应用访问的安全专用 Redis 实例。</span><span class="sxs-lookup"><span data-stu-id="179e4-107">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="179e4-108">Redis 是一种高级键值存储，其中键可包含数据结构，例如字符串、哈希、列表、集和排序集。</span><span class="sxs-lookup"><span data-stu-id="179e4-108">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="179e4-109">Redis 支持针对这些数据类型的一组原子操作。</span><span class="sxs-lookup"><span data-stu-id="179e4-109">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="179e4-110">详细了解 [Azure Redis 缓存](https://docs.microsoft.com/azure/redis-cache/)。</span><span class="sxs-lookup"><span data-stu-id="179e4-110">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="179e4-111">客户端程序包</span><span class="sxs-lookup"><span data-stu-id="179e4-111">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="179e4-112">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="179e4-112">Install the npm module</span></span>

<span data-ttu-id="179e4-113">使用 npm 安装用于 Node.js 的 Redis 模块</span><span class="sxs-lookup"><span data-stu-id="179e4-113">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="179e4-114">示例</span><span class="sxs-lookup"><span data-stu-id="179e4-114">Example</span></span>

<span data-ttu-id="179e4-115">此示例连接到 Azure Redis 缓存实例，存储键/值对，然后根据键读取存储的值。</span><span class="sxs-lookup"><span data-stu-id="179e4-115">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="179e4-116">管理包</span><span class="sxs-lookup"><span data-stu-id="179e4-116">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="179e4-117">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="179e4-117">Install the npm module</span></span>

<span data-ttu-id="179e4-118">使用 npm 安装用于 Node.js 的 Azure Redis 缓存模块</span><span class="sxs-lookup"><span data-stu-id="179e4-118">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="179e4-119">示例</span><span class="sxs-lookup"><span data-stu-id="179e4-119">Example</span></span>

<span data-ttu-id="179e4-120">此示例在 Azure 中进行身份验证，并列出指定资源组中的所有 Redis 缓存实例。</span><span class="sxs-lookup"><span data-stu-id="179e4-120">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

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


## <a name="samples"></a><span data-ttu-id="179e4-121">示例</span><span class="sxs-lookup"><span data-stu-id="179e4-121">Samples</span></span>

* [<span data-ttu-id="179e4-122">如何在 Node.js 中使用 Azure Redis 缓存</span><span class="sxs-lookup"><span data-stu-id="179e4-122">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="179e4-123">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="179e4-123">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
