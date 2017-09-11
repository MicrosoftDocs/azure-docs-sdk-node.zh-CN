---
title: "用于 Node.js 的 Azure PowerBI Embedded 模块"
description: "用于 Node.js 的 Azure PowerBI Embedded 模块参考"
keywords: Azure,SDK,API,PowerBI Embedded, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 74e69421d372ff4ccaebf2b811152dd83b9b4e7b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="cc8e1-104">用于 Node.js 的 Azure PowerBI Embedded 模块</span><span class="sxs-lookup"><span data-stu-id="cc8e1-104">Azure PowerBI Embedded modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="cc8e1-105">概述</span><span class="sxs-lookup"><span data-stu-id="cc8e1-105">Overview</span></span>

<span data-ttu-id="cc8e1-106">使用 Power BI Embedded Azure 服务，可将 Power BI 报表直接集成到 Node 应用程序，以创建或编辑图表与报表。</span><span class="sxs-lookup"><span data-stu-id="cc8e1-106">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="cc8e1-107">详细了解 [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)。</span><span class="sxs-lookup"><span data-stu-id="cc8e1-107">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="cc8e1-108">管理包</span><span class="sxs-lookup"><span data-stu-id="cc8e1-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cc8e1-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="cc8e1-109">Install the npm module</span></span>

<span data-ttu-id="cc8e1-110">安装 Azure Power BI npm 模块</span><span class="sxs-lookup"><span data-stu-id="cc8e1-110">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="cc8e1-111">示例</span><span class="sxs-lookup"><span data-stu-id="cc8e1-111">Example</span></span>

<span data-ttu-id="cc8e1-112">此示例在现有资源组中创建工作区集合。</span><span class="sxs-lookup"><span data-stu-id="cc8e1-112">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="cc8e1-113">示例</span><span class="sxs-lookup"><span data-stu-id="cc8e1-113">Samples</span></span>

<span data-ttu-id="cc8e1-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="cc8e1-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
