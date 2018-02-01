---
title: "用于 Node.js 的 Azure Data Lake Analytics 模块"
description: "用于 Node.js 的 Azure Data Lake Analytics 模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 28dae604ae9977eb33470757e207ac12a592c676
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="4cf67-103">用于 Node.js 的 Azure Data Lake Analytics 模块</span><span class="sxs-lookup"><span data-stu-id="4cf67-103">Azure Data Lake Analytics modules for Node.js</span></span>

<span data-ttu-id="4cf67-104">Azure Data Lake Analytics 是一项按需分析作业服务，用于简化大数据分析。</span><span class="sxs-lookup"><span data-stu-id="4cf67-104">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="4cf67-105">可以专注于编写、运行和管理作业，而不是运行分布式基础结构。</span><span class="sxs-lookup"><span data-stu-id="4cf67-105">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="4cf67-106">无需部署、配置和调整硬件，只需编写查询即可转换数据并提取有价值的见解。</span><span class="sxs-lookup"><span data-stu-id="4cf67-106">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="4cf67-107">通过将表盘设置为所需值，该分析服务就可以立即处理任何规模的作业。</span><span class="sxs-lookup"><span data-stu-id="4cf67-107">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="4cf67-108">只需为运行作业付费，让服务变得更为经济高效。</span><span class="sxs-lookup"><span data-stu-id="4cf67-108">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="4cf67-109">该分析服务支持 Azure Active Directory，让用户可管理访问和角色，并与用户的本地识别系统集成。</span><span class="sxs-lookup"><span data-stu-id="4cf67-109">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="4cf67-110">它还包括了 U-SQL 语言，有效结合了 SQL 的优点和用户代码的表达力。</span><span class="sxs-lookup"><span data-stu-id="4cf67-110">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="4cf67-111">U-SQL 的可缩放分布式运行时可让用户高效地分析存储中的数据，以及跨 Azure 中的 SQL Server、Azure SQL 数据库和 Azure SQL 数据仓库的数据。</span><span class="sxs-lookup"><span data-stu-id="4cf67-111">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="4cf67-112">管理包</span><span class="sxs-lookup"><span data-stu-id="4cf67-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4cf67-113">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="4cf67-113">Install the npm module</span></span>

<span data-ttu-id="4cf67-114">使用 npm 安装用于 Node.js 的 Azure Data Lake Analytics 模块</span><span class="sxs-lookup"><span data-stu-id="4cf67-114">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="4cf67-115">示例</span><span class="sxs-lookup"><span data-stu-id="4cf67-115">Example</span></span>

<span data-ttu-id="4cf67-116">此示例列出给定订阅的所有分析帐户。</span><span class="sxs-lookup"><span data-stu-id="4cf67-116">This example lists all of the analytics accounts for a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4cf67-117">示例</span><span class="sxs-lookup"><span data-stu-id="4cf67-117">Samples</span></span>

<span data-ttu-id="4cf67-118">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="4cf67-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
