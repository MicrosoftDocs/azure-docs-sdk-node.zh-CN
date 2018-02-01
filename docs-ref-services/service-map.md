---
title: "用于 Node.js 的 Azure 服务映射模块"
description: "用于 Node.js 的 Azure 服务映射模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 3f858e52f7a97ff77959825a1be993ef52f96e57
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="9a051-103">用于 Node.js 的 Azure 服务映射模块</span><span class="sxs-lookup"><span data-stu-id="9a051-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="9a051-104">服务映射自动发现 Windows 和 Linux 系统上的应用程序组件并映射服务之间的通信。</span><span class="sxs-lookup"><span data-stu-id="9a051-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="9a051-105">服务映射显示 TCP 连接的任何体系结构中服务器、进程和端口之间的连接，只需安装代理，无需任何其他配置。</span><span class="sxs-lookup"><span data-stu-id="9a051-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="9a051-106">详细了解 [Azure 服务映射](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)。</span><span class="sxs-lookup"><span data-stu-id="9a051-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="9a051-107">管理包</span><span class="sxs-lookup"><span data-stu-id="9a051-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9a051-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="9a051-108">Install the npm module</span></span>

<span data-ttu-id="9a051-109">安装 Azure 服务映射 npm 模块</span><span class="sxs-lookup"><span data-stu-id="9a051-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="9a051-110">示例</span><span class="sxs-lookup"><span data-stu-id="9a051-110">Example</span></span>

<span data-ttu-id="9a051-111">此示例列出指定的资源组和工作区的所有服务映射。</span><span class="sxs-lookup"><span data-stu-id="9a051-111">This example lists all service maps for the specified resource group and workspace.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9a051-112">示例</span><span class="sxs-lookup"><span data-stu-id="9a051-112">Samples</span></span>

<span data-ttu-id="9a051-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="9a051-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
