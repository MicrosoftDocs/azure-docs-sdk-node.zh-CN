---
title: 用于 Node.js 的 Azure Data Lake Store 模块
description: 用于 Node.js 的 Azure Data Lake Store 模块参考
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51453381"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a>用于 Node.js 的 Azure Data Lake Store 模块

Azure Data Lake Store 是一个企业范围的超大规模存储库，适用于大数据分析工作负载。 使用 Azure Data Lake 可以在单个位置捕获任何大小、类型和引入速度的数据进行操作和探索分析。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

使用 npm 安装用于 Node.js 的 Azure Data Lake Store 模块

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a>示例

此示例列出给定 Azure 订阅中的所有 Data Lake Store 帐户。

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
