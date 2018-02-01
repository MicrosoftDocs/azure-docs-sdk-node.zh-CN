---
title: "用于 Node.js 的 Azure 开发测试实验室模块"
description: "用于 Node.js 的 Azure 开发测试实验室模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 7754280741c09d47e138518d33628c667944c651
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>用于 Node.js 的 Azure 开发测试实验室模块

Azure 开发测试实验室是一项可帮助开发人员和测试人员在 Azure 中快速创建环境，同时尽量减少浪费并控制成本的服务。 可使用可重用模板和项目通过快速预配 Windows 和 Linux 环境来测试应用程序的最新版本。 轻松地将部署管道与开发测试实验室集成，以预配按需环境。 通过预配多个测试代理，增加负载测试，并为培训和演示创建预先预配的环境。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 开发测试实验室 npm 模块

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>示例

此示例获取并列显实验室的详细信息。

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

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
