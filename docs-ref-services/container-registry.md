---
title: 用于 Node.js 的 Azure 容器注册表模块
description: 用于 Node.js 的 Azure 容器注册表模块参考
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "49728374"
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="0245b-103">用于 Node.js 的 Azure 容器注册表模块</span><span class="sxs-lookup"><span data-stu-id="0245b-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="0245b-104">Azure 容器注册表是基于开源 Docker 注册表 2.0 的托管 Docker 注册表服务。</span><span class="sxs-lookup"><span data-stu-id="0245b-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="0245b-105">可以创建和维护 Azure 容器注册表来存储与管理专用的 Docker 容器映像。</span><span class="sxs-lookup"><span data-stu-id="0245b-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="0245b-106">可将 Azure 中的容器注册表与现有的容器开发和部署管道配合使用，现成地吸收 Docker 社区的专业知识。</span><span class="sxs-lookup"><span data-stu-id="0245b-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="0245b-107">管理包</span><span class="sxs-lookup"><span data-stu-id="0245b-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0245b-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0245b-108">Install the npm module</span></span>

<span data-ttu-id="0245b-109">安装 Azure 容器注册表 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0245b-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="0245b-110">示例</span><span class="sxs-lookup"><span data-stu-id="0245b-110">Example</span></span>

<span data-ttu-id="0245b-111">此示例获取可用容器的列表。</span><span class="sxs-lookup"><span data-stu-id="0245b-111">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="0245b-112">示例</span><span class="sxs-lookup"><span data-stu-id="0245b-112">Samples</span></span>

<span data-ttu-id="0245b-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="0245b-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
