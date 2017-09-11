---
title: "用于 Node.js 的 Azure Data Lake Analytics 模块"
description: "用于 Node.js 的 Azure Data Lake Analytics 模块参考"
keywords: Azure,SDK,API,Data Lake Analytics, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 46f414ac6909de5bd956666baf51be1ca9d25ac7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>用于 Node.js 的 Azure Data Lake Analytics 模块

## <a name="overview"></a>概述
Azure Data Lake Analytics 是一项按需分析作业服务，用于简化大数据分析。 可以专注于编写、运行和管理作业，而不是运行分布式基础结构。 无需部署、配置和调整硬件，只需编写查询即可转换数据并提取有价值的见解。 通过将表盘设置为所需值，该分析服务就可以立即处理任何规模的作业。 只需为运行作业付费，让服务变得更为经济高效。 该分析服务支持 Azure Active Directory，让用户可管理访问和角色，并与用户的本地识别系统集成。 它还包括了 U-SQL 语言，有效结合了 SQL 的优点和用户代码的表达力。 U-SQL 的可缩放分布式运行时可让用户高效地分析存储中的数据，以及跨 Azure 中的 SQL Server、Azure SQL 数据库和 Azure SQL 数据仓库的数据。

### <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

使用 npm 安装用于 Node.js 的 Azure Data Lake Analytics 模块

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>示例

此示例列出给定订阅的所有分析帐户。

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
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
