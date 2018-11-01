---
title: 用于 Node.js 的 Azure Analysis Services 模块
description: 用于 Node.js 的 Azure Analysis Services 模块参考
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 5214cd2f171074ba330bc639643dfba490540856
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50339975"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="52596-103">用于 Node.js 的 Azure Analysis Services 模块</span><span class="sxs-lookup"><span data-stu-id="52596-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="52596-104">概述</span><span class="sxs-lookup"><span data-stu-id="52596-104">Overview</span></span>
<span data-ttu-id="52596-105">此包提供一个 Node.js 模块用于方便管理 Microsoft Azure Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="52596-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="52596-106">管理包</span><span class="sxs-lookup"><span data-stu-id="52596-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="52596-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="52596-107">Install the npm module</span></span>

<span data-ttu-id="52596-108">安装 Azure Analysis Services npm 模块</span><span class="sxs-lookup"><span data-stu-id="52596-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="52596-109">示例</span><span class="sxs-lookup"><span data-stu-id="52596-109">Example</span></span>

<span data-ttu-id="52596-110">此示例列出所有可用的 Analysis Service 服务器。</span><span class="sxs-lookup"><span data-stu-id="52596-110">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="52596-111">示例</span><span class="sxs-lookup"><span data-stu-id="52596-111">Samples</span></span>

<span data-ttu-id="52596-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52596-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
