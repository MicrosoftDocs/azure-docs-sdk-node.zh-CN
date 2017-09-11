---
title: "用于 Node.js 的 Azure Analysis Services 模块"
description: "用于 Node.js 的 Azure Analysis Services 模块参考"
keywords: Azure,SDK,API,Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="7a9a4-104">用于 Node.js 的 Azure Analysis Services 模块</span><span class="sxs-lookup"><span data-stu-id="7a9a4-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7a9a4-105">概述</span><span class="sxs-lookup"><span data-stu-id="7a9a4-105">Overview</span></span>
<span data-ttu-id="7a9a4-106">此包提供一个 Node.js 模块用于方便管理 Microsoft Azure Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="7a9a4-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="7a9a4-107">管理包</span><span class="sxs-lookup"><span data-stu-id="7a9a4-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7a9a4-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="7a9a4-108">Install the npm module</span></span>

<span data-ttu-id="7a9a4-109">安装 Azure Analysis Services npm 模块</span><span class="sxs-lookup"><span data-stu-id="7a9a4-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="7a9a4-110">示例</span><span class="sxs-lookup"><span data-stu-id="7a9a4-110">Example</span></span>

<span data-ttu-id="7a9a4-111">此示例列出所有可用的 Analysis Service 服务器。</span><span class="sxs-lookup"><span data-stu-id="7a9a4-111">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="7a9a4-112">示例</span><span class="sxs-lookup"><span data-stu-id="7a9a4-112">Samples</span></span>

<span data-ttu-id="7a9a4-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="7a9a4-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
