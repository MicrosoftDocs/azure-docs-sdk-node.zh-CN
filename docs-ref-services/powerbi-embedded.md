---
title: 用于 Node.js 的 Azure PowerBI Embedded 模块
description: 用于 Node.js 的 Azure PowerBI Embedded 模块参考
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 4d0a1ebf75591a9a3575172f325309ddbac7885c
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260885"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="b1086-103">用于 Node.js 的 Azure PowerBI Embedded 模块</span><span class="sxs-lookup"><span data-stu-id="b1086-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="b1086-104">使用 Power BI Embedded Azure 服务，可将 Power BI 报表直接集成到 Node 应用程序，以创建或编辑图表与报表。</span><span class="sxs-lookup"><span data-stu-id="b1086-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="b1086-105">详细了解 [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)。</span><span class="sxs-lookup"><span data-stu-id="b1086-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="b1086-106">管理包</span><span class="sxs-lookup"><span data-stu-id="b1086-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b1086-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="b1086-107">Install the npm module</span></span>

<span data-ttu-id="b1086-108">安装 Azure Power BI npm 模块</span><span class="sxs-lookup"><span data-stu-id="b1086-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="b1086-109">示例</span><span class="sxs-lookup"><span data-stu-id="b1086-109">Example</span></span>

<span data-ttu-id="b1086-110">此示例在现有资源组中创建工作区集合。</span><span class="sxs-lookup"><span data-stu-id="b1086-110">This example creates a workspace collection in an existing resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b1086-111">示例</span><span class="sxs-lookup"><span data-stu-id="b1086-111">Samples</span></span>

<span data-ttu-id="b1086-112">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b1086-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
