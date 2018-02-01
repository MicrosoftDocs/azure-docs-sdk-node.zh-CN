---
title: "用于 Node.js 的 Azure 存储模块"
description: "用于 Node.js 的 Azure 存储模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="4446b-103">用于 Node.js 的 Azure 存储模块</span><span class="sxs-lookup"><span data-stu-id="4446b-103">Azure Storage modules for Node.js</span></span>

<span data-ttu-id="4446b-104">使用 Azure 存储客户端模块可以：</span><span class="sxs-lookup"><span data-stu-id="4446b-104">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="4446b-105">通过 [Azure Blob 存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)读取和写入对象与文件</span><span class="sxs-lookup"><span data-stu-id="4446b-105">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="4446b-106">使用 [Azure 队列存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)在已连接到云的应用程序之间发送和接收消息</span><span class="sxs-lookup"><span data-stu-id="4446b-106">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="4446b-107">使用 [Azure 表存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)读取和写入大型结构化数据</span><span class="sxs-lookup"><span data-stu-id="4446b-107">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="4446b-108">使用管理模块通过 Node.js 应用创建、更新和管理 Azure 存储帐户，以及查询和重新生成访问密钥。</span><span class="sxs-lookup"><span data-stu-id="4446b-108">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="4446b-109">客户端包</span><span class="sxs-lookup"><span data-stu-id="4446b-109">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4446b-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="4446b-110">Install the npm module</span></span>

<span data-ttu-id="4446b-111">安装 Azure 存储客户端 npm 模块</span><span class="sxs-lookup"><span data-stu-id="4446b-111">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="4446b-112">示例</span><span class="sxs-lookup"><span data-stu-id="4446b-112">Example</span></span>

<span data-ttu-id="4446b-113">此示例创建一个存储容器，并将本地文件 `data.txt` 上传到其中。</span><span class="sxs-lookup"><span data-stu-id="4446b-113">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="4446b-114">管理包</span><span class="sxs-lookup"><span data-stu-id="4446b-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4446b-115">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="4446b-115">Install the npm module</span></span> 

<span data-ttu-id="4446b-116">安装 Azure 存储管理 npm 模块</span><span class="sxs-lookup"><span data-stu-id="4446b-116">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="4446b-117">示例</span><span class="sxs-lookup"><span data-stu-id="4446b-117">Example</span></span>

<span data-ttu-id="4446b-118">此示例列出存储帐户。</span><span class="sxs-lookup"><span data-stu-id="4446b-118">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4446b-119">示例</span><span class="sxs-lookup"><span data-stu-id="4446b-119">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="4446b-120">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="4446b-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
