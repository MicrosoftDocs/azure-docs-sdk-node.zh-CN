---
title: "用于 Node.js 的 Azure 应用服务模块"
description: "用于 Node.js 的 Azure 应用服务模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: b722344f056a52785aef6d853a797231dcafc699
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a>用于 Node.js 的 Azure 应用服务模块

## <a name="overview"></a>概述

Azure 应用服务是 Microsoft Azure 的平台即服务 (PaaS) 产品。 为任何平台或设备创建 Web 应用和移动应用。 将应用与 SaaS 解决方案集成、与本地应用程序进行连接，以及实现业务流程的自动化。 Azure 在完全托管的虚拟机 (VM) 上运行应用程序，由用户选择共享的 VM 资源或专用 VM。

应用服务所包括的 Web 功能和移动功能是以前作为 Azure 网站和 Azure 移动服务单独交付的。 它还包括各种新功能，可以实现业务流程的自动化，并可托管云 API。 应用服务是一项集成服务，允许用户将各种组件（网站、移动应用后端、RESTful API 和业务流程）组合到单个解决方案中。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-package"></a>安装 npm 包

安装用于 Node.js 的 Azure 应用服务模块

```bash
npm install azure-arm-website
```

### <a name="example"></a>示例

此示例使用 Node.js 在 Azure 上创建一个网站。

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

## <a name="samples"></a>示例

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
