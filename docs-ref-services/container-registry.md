---
title: "用于 Node.js 的 Azure 容器注册表模块"
description: "用于 Node.js 的 Azure 容器注册表模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: dda0e9bbfaa8a3e060f3b8f820d5bab315662629
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="d00ed-103">用于 Node.js 的 Azure 容器注册表模块</span><span class="sxs-lookup"><span data-stu-id="d00ed-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="d00ed-104">Azure 容器注册表是基于开源 Docker 注册表 2.0 的托管 Docker 注册表服务。</span><span class="sxs-lookup"><span data-stu-id="d00ed-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="d00ed-105">可以创建和维护 Azure 容器注册表来存储与管理专用的 Docker 容器映像。</span><span class="sxs-lookup"><span data-stu-id="d00ed-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="d00ed-106">可将 Azure 中的容器注册表与现有的容器开发和部署管道配合使用，现成地吸收 Docker 社区的专业知识。</span><span class="sxs-lookup"><span data-stu-id="d00ed-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="d00ed-107">管理包</span><span class="sxs-lookup"><span data-stu-id="d00ed-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d00ed-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="d00ed-108">Install the npm module</span></span>

<span data-ttu-id="d00ed-109">安装 Azure 容器注册表 npm 模块</span><span class="sxs-lookup"><span data-stu-id="d00ed-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="d00ed-110">示例</span><span class="sxs-lookup"><span data-stu-id="d00ed-110">Example</span></span>

<span data-ttu-id="d00ed-111">此示例获取可用容器的列表。</span><span class="sxs-lookup"><span data-stu-id="d00ed-111">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="d00ed-112">示例</span><span class="sxs-lookup"><span data-stu-id="d00ed-112">Samples</span></span>

<span data-ttu-id="d00ed-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="d00ed-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
