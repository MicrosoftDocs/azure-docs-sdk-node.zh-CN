---
title: "用于 Node.js 的 Azure 容器注册表模块"
description: "用于 Node.js 的 Azure 容器注册表模块参考"
keywords: "Azure,SDK,API,容器注册表, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="00f59-104">用于 Node.js 的 Azure 容器注册表模块</span><span class="sxs-lookup"><span data-stu-id="00f59-104">Azure Container Registry modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="00f59-105">概述</span><span class="sxs-lookup"><span data-stu-id="00f59-105">Overview</span></span>

<span data-ttu-id="00f59-106">Azure 容器注册表是基于开源 Docker 注册表 2.0 的托管 Docker 注册表服务。</span><span class="sxs-lookup"><span data-stu-id="00f59-106">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="00f59-107">可以创建和维护 Azure 容器注册表来存储与管理专用的 Docker 容器映像。</span><span class="sxs-lookup"><span data-stu-id="00f59-107">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="00f59-108">可将 Azure 中的容器注册表与现有的容器开发和部署管道配合使用，现成地吸收 Docker 社区的专业知识。</span><span class="sxs-lookup"><span data-stu-id="00f59-108">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="00f59-109">管理包</span><span class="sxs-lookup"><span data-stu-id="00f59-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="00f59-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="00f59-110">Install the npm module</span></span>

<span data-ttu-id="00f59-111">安装 Azure 容器注册表 npm 模块</span><span class="sxs-lookup"><span data-stu-id="00f59-111">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="00f59-112">示例</span><span class="sxs-lookup"><span data-stu-id="00f59-112">Example</span></span>

<span data-ttu-id="00f59-113">此示例获取可用容器的列表。</span><span class="sxs-lookup"><span data-stu-id="00f59-113">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="00f59-114">示例</span><span class="sxs-lookup"><span data-stu-id="00f59-114">Samples</span></span>

<span data-ttu-id="00f59-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="00f59-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
