---
title: "用于 Node.js 的 Azure 服务映射模块"
description: "用于 Node.js 的 Azure 服务映射模块参考"
keywords: "Azure,SDK,API,服务映射, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="3d32f-104">用于 Node.js 的 Azure 服务映射模块</span><span class="sxs-lookup"><span data-stu-id="3d32f-104">Azure Service Map modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="3d32f-105">概述</span><span class="sxs-lookup"><span data-stu-id="3d32f-105">Overview</span></span>

<span data-ttu-id="3d32f-106">服务映射自动发现 Windows 和 Linux 系统上的应用程序组件并映射服务之间的通信。</span><span class="sxs-lookup"><span data-stu-id="3d32f-106">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="3d32f-107">服务映射显示 TCP 连接的任何体系结构中服务器、进程和端口之间的连接，只需安装代理，无需任何其他配置。</span><span class="sxs-lookup"><span data-stu-id="3d32f-107">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="3d32f-108">详细了解 [Azure 服务映射](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)。</span><span class="sxs-lookup"><span data-stu-id="3d32f-108">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="3d32f-109">管理包</span><span class="sxs-lookup"><span data-stu-id="3d32f-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3d32f-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3d32f-110">Install the npm module</span></span>

<span data-ttu-id="3d32f-111">安装 Azure 服务映射 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3d32f-111">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="3d32f-112">示例</span><span class="sxs-lookup"><span data-stu-id="3d32f-112">Example</span></span>

<span data-ttu-id="3d32f-113">此示例列出指定的资源组和工作区的所有服务映射。</span><span class="sxs-lookup"><span data-stu-id="3d32f-113">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="3d32f-114">示例</span><span class="sxs-lookup"><span data-stu-id="3d32f-114">Samples</span></span>

<span data-ttu-id="3d32f-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="3d32f-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
