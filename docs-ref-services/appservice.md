---
title: "用于 Node.js 的 Azure 应用服务模块"
description: "用于 Node.js 的 Azure 应用服务模块参考"
keywords: "Azure, Node, SDK, API, Web 应用, 移动, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: c695ae6d523ea731b18382ba0906f78b40ce301f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="bc598-104">用于 Node.js 的 Azure 应用服务模块</span><span class="sxs-lookup"><span data-stu-id="bc598-104">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bc598-105">概述</span><span class="sxs-lookup"><span data-stu-id="bc598-105">Overview</span></span>

<span data-ttu-id="bc598-106">Azure 应用服务是 Microsoft Azure 的平台即服务 (PaaS) 产品。</span><span class="sxs-lookup"><span data-stu-id="bc598-106">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="bc598-107">为任何平台或设备创建 Web 应用和移动应用。</span><span class="sxs-lookup"><span data-stu-id="bc598-107">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="bc598-108">将应用与 SaaS 解决方案集成、与本地应用程序进行连接，以及实现业务流程的自动化。</span><span class="sxs-lookup"><span data-stu-id="bc598-108">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="bc598-109">Azure 在完全托管的虚拟机 (VM) 上运行应用程序，由用户选择共享的 VM 资源或专用 VM。</span><span class="sxs-lookup"><span data-stu-id="bc598-109">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="bc598-110">应用服务所包括的 Web 功能和移动功能是以前作为 Azure 网站和 Azure 移动服务单独交付的。</span><span class="sxs-lookup"><span data-stu-id="bc598-110">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="bc598-111">它还包括各种新功能，可以实现业务流程的自动化，并可托管云 API。</span><span class="sxs-lookup"><span data-stu-id="bc598-111">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="bc598-112">应用服务是一项集成服务，允许用户将各种组件（网站、移动应用后端、RESTful API 和业务流程）组合到单个解决方案中。</span><span class="sxs-lookup"><span data-stu-id="bc598-112">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="bc598-113">管理包</span><span class="sxs-lookup"><span data-stu-id="bc598-113">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="bc598-114">安装 npm 包</span><span class="sxs-lookup"><span data-stu-id="bc598-114">Install the npm package</span></span>

<span data-ttu-id="bc598-115">安装用于 Node.js 的 Azure 应用服务模块</span><span class="sxs-lookup"><span data-stu-id="bc598-115">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="bc598-116">示例</span><span class="sxs-lookup"><span data-stu-id="bc598-116">Example</span></span>

<span data-ttu-id="bc598-117">此示例使用 Node.js 在 Azure 上创建一个网站。</span><span class="sxs-lookup"><span data-stu-id="bc598-117">This example creates a website on Azure using Node.js.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a><span data-ttu-id="bc598-118">示例</span><span class="sxs-lookup"><span data-stu-id="bc598-118">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="bc598-119">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="bc598-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
