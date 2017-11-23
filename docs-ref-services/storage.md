---
title: "用于 Node.js 的 Azure 存储模块"
description: "用于 Node.js 的 Azure 存储模块参考"
keywords: "Azure, Node, SDK, API, 存储, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="3719d-104">用于 Node.js 的 Azure 存储模块</span><span class="sxs-lookup"><span data-stu-id="3719d-104">Azure Storage modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="3719d-105">概述</span><span class="sxs-lookup"><span data-stu-id="3719d-105">Overview</span></span>

<span data-ttu-id="3719d-106">使用 Azure 存储客户端模块可以：</span><span class="sxs-lookup"><span data-stu-id="3719d-106">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="3719d-107">通过 [Azure Blob 存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)读取和写入对象与文件</span><span class="sxs-lookup"><span data-stu-id="3719d-107">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="3719d-108">使用 [Azure 队列存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)在已连接到云的应用程序之间发送和接收消息</span><span class="sxs-lookup"><span data-stu-id="3719d-108">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="3719d-109">使用 [Azure 表存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)读取和写入大型结构化数据</span><span class="sxs-lookup"><span data-stu-id="3719d-109">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="3719d-110">使用管理模块通过 Node.js 应用创建、更新和管理 Azure 存储帐户，以及查询和重新生成访问密钥。</span><span class="sxs-lookup"><span data-stu-id="3719d-110">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="3719d-111">客户端包</span><span class="sxs-lookup"><span data-stu-id="3719d-111">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3719d-112">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3719d-112">Install the npm module</span></span>

<span data-ttu-id="3719d-113">安装 Azure 存储客户端 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3719d-113">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="3719d-114">示例</span><span class="sxs-lookup"><span data-stu-id="3719d-114">Example</span></span>

<span data-ttu-id="3719d-115">此示例创建一个存储容器，并将本地文件 `data.txt` 上传到其中。</span><span class="sxs-lookup"><span data-stu-id="3719d-115">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a><span data-ttu-id="3719d-116">管理包</span><span class="sxs-lookup"><span data-stu-id="3719d-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3719d-117">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3719d-117">Install the npm module</span></span> 

<span data-ttu-id="3719d-118">安装 Azure 存储管理 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3719d-118">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="3719d-119">示例</span><span class="sxs-lookup"><span data-stu-id="3719d-119">Example</span></span>

<span data-ttu-id="3719d-120">此示例列出存储帐户。</span><span class="sxs-lookup"><span data-stu-id="3719d-120">This example list the storage accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="3719d-121">示例</span><span class="sxs-lookup"><span data-stu-id="3719d-121">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="3719d-122">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="3719d-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
