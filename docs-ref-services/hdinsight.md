---
title: 用于 Node.js 的 Azure HDInsight 模块
description: 用于 Node.js 的 Azure HDInsight 模块参考
author: mumian
ms.author: jgao
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 311933f619ceab5d679c8b0a767d3b52960c5ce1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="4ccfc-103">用于 Node.js 的 Azure HDInsight 模块</span><span class="sxs-lookup"><span data-stu-id="4ccfc-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="4ccfc-104">Azure HDInsight 是 Hortonworks Data Platform (HDP) 提供的 Hadoop 组件的云分发版。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="4ccfc-105">Apache Hadoop 是原始的开源框架，适用于对计算机群集上的大数据集进行分布式处理和分析。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="4ccfc-106">HDInsight 使 Hadoop 技术更易于使用，其特点是：</span><span class="sxs-lookup"><span data-stu-id="4ccfc-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="4ccfc-107">减少设置和配置。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-107">Less setup and configuration.</span></span> <span data-ttu-id="4ccfc-108">请参阅“在 HDInsight 中预配 Hadoop 群集”。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="4ccfc-109">提高可用性和可靠性。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-109">High availability and reliability.</span></span> <span data-ttu-id="4ccfc-110">请参阅“HDInsight 可用性和可靠性”。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="4ccfc-111">通过集成 Active Directory 增强安全和监管功能。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="4ccfc-112">请参阅“加入域的群集”。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="4ccfc-113">在不中断作业的情况下进行动态缩放</span><span class="sxs-lookup"><span data-stu-id="4ccfc-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="4ccfc-114">提供组件更新和最新版本。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-114">Component updates and current versions.</span></span> <span data-ttu-id="4ccfc-115">请参阅“HDInsight 上的 Hadoop 组件和版本”。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="4ccfc-116">与其他 Azure 服务（包括 Web 应用和 SQL 数据库）集成</span><span class="sxs-lookup"><span data-stu-id="4ccfc-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="4ccfc-117">Hadoop 技术堆栈包括相关的软件和实用程序（Apache Hive、HBase、Spark、Kafka 等）。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="4ccfc-118">管理包</span><span class="sxs-lookup"><span data-stu-id="4ccfc-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="4ccfc-119">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="4ccfc-119">Install the npm modules</span></span>

<span data-ttu-id="4ccfc-120">使用 npm 安装用于 Node.js 的 Azure HDInsight 模块</span><span class="sxs-lookup"><span data-stu-id="4ccfc-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="4ccfc-121">示例</span><span class="sxs-lookup"><span data-stu-id="4ccfc-121">Example</span></span> 

<span data-ttu-id="4ccfc-122">此示例创建 HD Insight 客户端，然后列出所有可用群集。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a><span data-ttu-id="4ccfc-123">示例</span><span class="sxs-lookup"><span data-stu-id="4ccfc-123">Samples</span></span>

<span data-ttu-id="4ccfc-124">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
