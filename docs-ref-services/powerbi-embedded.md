---
title: "用于 Node.js 的 Azure PowerBI Embedded 模块"
description: "用于 Node.js 的 Azure PowerBI Embedded 模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 5dbe134acb38787916f48277b2114e199601e128
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="ebc3a-103">用于 Node.js 的 Azure PowerBI Embedded 模块</span><span class="sxs-lookup"><span data-stu-id="ebc3a-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="ebc3a-104">使用 Power BI Embedded Azure 服务，可将 Power BI 报表直接集成到 Node 应用程序，以创建或编辑图表与报表。</span><span class="sxs-lookup"><span data-stu-id="ebc3a-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="ebc3a-105">详细了解 [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)。</span><span class="sxs-lookup"><span data-stu-id="ebc3a-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="ebc3a-106">管理包</span><span class="sxs-lookup"><span data-stu-id="ebc3a-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ebc3a-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="ebc3a-107">Install the npm module</span></span>

<span data-ttu-id="ebc3a-108">安装 Azure Power BI npm 模块</span><span class="sxs-lookup"><span data-stu-id="ebc3a-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="ebc3a-109">示例</span><span class="sxs-lookup"><span data-stu-id="ebc3a-109">Example</span></span>

<span data-ttu-id="ebc3a-110">此示例在现有资源组中创建工作区集合。</span><span class="sxs-lookup"><span data-stu-id="ebc3a-110">This example creates a workspace collection in an existing resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ebc3a-111">示例</span><span class="sxs-lookup"><span data-stu-id="ebc3a-111">Samples</span></span>

<span data-ttu-id="ebc3a-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ebc3a-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
