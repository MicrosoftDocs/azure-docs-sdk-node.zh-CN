---
title: 用于 Node.js 的 Azure 媒体服务模块
description: 用于 Node.js 的 Azure 媒体服务模块参考
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: e8b2b4b994c25fadda7a37d05a12778d8c9970d8
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261989"
---
# <a name="azure-media-services-modules-for-nodejs"></a>用于 Node.js 的 Azure 媒体服务模块

Azure 媒体服务是一个可扩展的基于云的平台，开发人员可以使用它来构建可缩放的媒体管理与传送应用程序。 媒体服务基于 REST API，你可以使用这些 API 安全地上传、存储、编码和打包视频或音频内容，以供点播以及以实时流形式传送到各种客户端（例如，电视、电脑和移动设备）。

使用 Azure 媒体服务可以：
- 完全使用媒体服务构建端到端工作流。 
- 使用第三方组件来构建工作流的某些组成部分。 例如，使用第三方编码器进行编码。 然后，使用媒体服务进行上传、保护、打包和传送。
- 实时流式传输内容，或者按需交付内容。 本主题还提供了其他相关主题的链接。

## <a name="management-package"></a>管理包

### <a name="install-the-npm-module"></a>安装 npm 模块

安装 Azure 媒体服务 npm 模块

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a>示例

此示例列出资源组的所有媒体服务。

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
