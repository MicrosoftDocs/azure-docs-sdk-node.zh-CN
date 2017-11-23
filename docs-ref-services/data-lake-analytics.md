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
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="02a52-104">用于 Node.js 的 Azure Data Lake Analytics 模块</span><span class="sxs-lookup"><span data-stu-id="02a52-104">Azure Data Lake Analytics modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="02a52-105">概述</span><span class="sxs-lookup"><span data-stu-id="02a52-105">Overview</span></span>
<span data-ttu-id="02a52-106">Azure Data Lake Analytics 是一项按需分析作业服务，用于简化大数据分析。</span><span class="sxs-lookup"><span data-stu-id="02a52-106">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="02a52-107">可以专注于编写、运行和管理作业，而不是运行分布式基础结构。</span><span class="sxs-lookup"><span data-stu-id="02a52-107">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="02a52-108">无需部署、配置和调整硬件，只需编写查询即可转换数据并提取有价值的见解。</span><span class="sxs-lookup"><span data-stu-id="02a52-108">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="02a52-109">通过将表盘设置为所需值，该分析服务就可以立即处理任何规模的作业。</span><span class="sxs-lookup"><span data-stu-id="02a52-109">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="02a52-110">只需为运行作业付费，让服务变得更为经济高效。</span><span class="sxs-lookup"><span data-stu-id="02a52-110">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="02a52-111">该分析服务支持 Azure Active Directory，让用户可管理访问和角色，并与用户的本地识别系统集成。</span><span class="sxs-lookup"><span data-stu-id="02a52-111">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="02a52-112">它还包括了 U-SQL 语言，有效结合了 SQL 的优点和用户代码的表达力。</span><span class="sxs-lookup"><span data-stu-id="02a52-112">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="02a52-113">U-SQL 的可缩放分布式运行时可让用户高效地分析存储中的数据，以及跨 Azure 中的 SQL Server、Azure SQL 数据库和 Azure SQL 数据仓库的数据。</span><span class="sxs-lookup"><span data-stu-id="02a52-113">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="02a52-114">管理包</span><span class="sxs-lookup"><span data-stu-id="02a52-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="02a52-115">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="02a52-115">Install the npm module</span></span>

<span data-ttu-id="02a52-116">使用 npm 安装用于 Node.js 的 Azure Data Lake Analytics 模块</span><span class="sxs-lookup"><span data-stu-id="02a52-116">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="02a52-117">示例</span><span class="sxs-lookup"><span data-stu-id="02a52-117">Example</span></span>

<span data-ttu-id="02a52-118">此示例列出给定订阅的所有分析帐户。</span><span class="sxs-lookup"><span data-stu-id="02a52-118">This example lists all of the analytics accounts for a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="02a52-119">示例</span><span class="sxs-lookup"><span data-stu-id="02a52-119">Samples</span></span>

<span data-ttu-id="02a52-120">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="02a52-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
