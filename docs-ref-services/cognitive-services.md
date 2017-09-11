---
title: "用于 Node.js 的 Azure 认知服务模块"
description: "用于 Node.js 的 Azure 认知服务模块参考"
keywords: "Azure,SDK,API,认知服务, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>用于 Node.js 的 Azure 认知服务模块

## <a name="overview"></a>概述

Azure 认知服务是一组面向开发人员的 API、SDK 和服务，可提高应用程序的智能性、吸引力和可发现性。 Microsoft 认知服务是在 Microsoft 不断发展的机器学习 API 产品组合基础上的拓展，可让开发人员轻松地在其应用程序中添加智能功能 – 例如情绪和动作检测；面部、语音与视觉识别；语音与语言理解。 我们的愿景是让逐渐能够观看、聆听、讲述、理解甚至思考的系统为更多的个人计算体验和生产力提供辅助。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 认知服务 npm 模块

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>示例

此示例列出所有认知服务帐户。

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
