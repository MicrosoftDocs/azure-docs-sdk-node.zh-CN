---
title: "用于 Node.js 的 Azure 搜索模块"
description: "用于 Node.js 的 Azure 搜索模块参考"
keywords: "Azure,SDK,API,搜索, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a>用于 Node.js 的 Azure 搜索模块

## <a name="overview"></a>概述

Azure 搜索是一种搜索即服务云解决方案，它将服务器和基础结构的管理委托给 Microsoft，提供随时可用的服务。可在填充数据后使用此服务将搜索添加到应用程序。

详细了解 [Azure 搜索](https://docs.microsoft.com/azure/search/search-what-is-azure-search)。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 搜索 npm 模块

```bash
npm install azure-arm-search
```

### <a name="example"></a>示例

此示例在 Azure 中创建新的搜索服务，并列出其资源组中的资源。

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
