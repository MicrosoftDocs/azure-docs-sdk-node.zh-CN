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
# <a name="azure-storage-modules-for-nodejs"></a>用于 Node.js 的 Azure 存储模块

## <a name="overview"></a>概述

使用 Azure 存储客户端模块可以：

- 通过 [Azure Blob 存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)读取和写入对象与文件
- 使用 [Azure 队列存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)在已连接到云的应用程序之间发送和接收消息
- 使用 [Azure 表存储](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)读取和写入大型结构化数据

使用管理模块通过 Node.js 应用创建、更新和管理 Azure 存储帐户，以及查询和重新生成访问密钥。

## <a name="client-package"></a>客户端包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 存储客户端 npm 模块

```bash
npm install azure-storage
```

### <a name="example"></a>示例

此示例创建一个存储容器，并将本地文件 `data.txt` 上传到其中。

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

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块 

安装 Azure 存储管理 npm 模块

```bash
npm install azure-arm-storage
```

### <a name="example"></a>示例

此示例列出存储帐户。

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

## <a name="samples"></a>示例

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
