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
# <a name="azure-container-registry-modules-for-nodejs"></a>用于 Node.js 的 Azure 容器注册表模块

Azure 容器注册表是基于开源 Docker 注册表 2.0 的托管 Docker 注册表服务。 可以创建和维护 Azure 容器注册表来存储与管理专用的 Docker 容器映像。 可将 Azure 中的容器注册表与现有的容器开发和部署管道配合使用，现成地吸收 Docker 社区的专业知识。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 容器注册表 npm 模块

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>示例

此示例获取可用容器的列表。

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

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
