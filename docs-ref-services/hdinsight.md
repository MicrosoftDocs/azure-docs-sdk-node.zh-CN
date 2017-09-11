---
title: "用于 Node.js 的 Azure HDInsight 模块"
description: "用于 Node.js 的 Azure HDInsight 模块参考"
keywords: Azure,SDK,API,HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>用于 Node.js 的 Azure HDInsight 模块

## <a name="overview"></a>概述

Azure HDInsight 是 Hortonworks Data Platform (HDP) 提供的 Hadoop 组件的云分发版。 Apache Hadoop 是原始的开源框架，适用于对计算机群集上的大数据集进行分布式处理和分析。

HDInsight 使 Hadoop 技术更易于使用，其特点是：
- 减少设置和配置。 请参阅“在 HDInsight 中预配 Hadoop 群集”。
- 提高可用性和可靠性。 请参阅“HDInsight 可用性和可靠性”。
- 通过集成 Active Directory 增强安全和监管功能。 请参阅“加入域的群集”。
- 在不中断作业的情况下进行动态缩放
- 提供组件更新和最新版本。 请参阅“HDInsight 上的 Hadoop 组件和版本”。
- 与其他 Azure 服务（包括 Web 应用和 SQL 数据库）集成

Hadoop 技术堆栈包括相关的软件和实用程序（Apache Hive、HBase、Spark、Kafka 等）。 

## <a name="management-package"></a>管理包

### <a name="install-the-npm-modules"></a>安装 npm 模块

使用 npm 安装用于 Node.js 的 Azure HDInsight 模块

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>示例 

此示例创建 HD Insight 客户端，然后列出所有可用群集。 

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

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
