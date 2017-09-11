---
title: "用于 Node.js 的 Azure CDN 模块"
description: "用于 Node.js 的 Azure CDN 模块参考"
keywords: Azure,SDK,API,CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a>用于 Node.js 的 Azure CDN 模块

## <a name="overview"></a>概述

Azure 内容交付网络 (CDN) 为开发人员提供一个全局解决方案用于传递 Azure 或其他任何位置中托管的高带宽内容。 使用 CDN，可以缓存从 Azure Blob 存储、Web 应用程序、虚拟机、应用程序文件夹或其他 HTTP/HTTPS 位置加载的公开对象。 可以将 CDN 缓存定位在战略性的位置上，以便提供最大的带宽向用户传送内容。 CDN 通常用于传送静态内容，例如图像、样式表、文档、文件、客户端脚本和 HTML 页面。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure CDN npm 模块

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>示例

此示例列出所有 CDN 配置文件。

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
