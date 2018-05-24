---
title: 用于 Node.js 的 Azure 开发测试实验室模块
description: 用于 Node.js 的 Azure 开发测试实验室模块参考
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 5bd010d26ca11f9909191f25128b9bdb89811fd5
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="45752-103">用于 Node.js 的 Azure 开发测试实验室模块</span><span class="sxs-lookup"><span data-stu-id="45752-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="45752-104">Azure 开发测试实验室是一项可帮助开发人员和测试人员在 Azure 中快速创建环境，同时尽量减少浪费并控制成本的服务。</span><span class="sxs-lookup"><span data-stu-id="45752-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="45752-105">可使用可重用模板和项目通过快速预配 Windows 和 Linux 环境来测试应用程序的最新版本。</span><span class="sxs-lookup"><span data-stu-id="45752-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="45752-106">轻松地将部署管道与开发测试实验室集成，以预配按需环境。</span><span class="sxs-lookup"><span data-stu-id="45752-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="45752-107">通过预配多个测试代理，增加负载测试，并为培训和演示创建预先预配的环境。</span><span class="sxs-lookup"><span data-stu-id="45752-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="45752-108">管理包</span><span class="sxs-lookup"><span data-stu-id="45752-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="45752-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="45752-109">Install the npm module</span></span>

<span data-ttu-id="45752-110">安装 Azure 开发测试实验室 npm 模块</span><span class="sxs-lookup"><span data-stu-id="45752-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="45752-111">示例</span><span class="sxs-lookup"><span data-stu-id="45752-111">Example</span></span>

<span data-ttu-id="45752-112">此示例获取并列显实验室的详细信息。</span><span class="sxs-lookup"><span data-stu-id="45752-112">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a><span data-ttu-id="45752-113">示例</span><span class="sxs-lookup"><span data-stu-id="45752-113">Samples</span></span>

<span data-ttu-id="45752-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="45752-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
