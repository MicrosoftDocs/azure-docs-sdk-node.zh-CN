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
ms.openlocfilehash: bfd4402c215a81c9ed8753cfe9ad9dbfaa52bd6f
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51374981"
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="ea2e4-103">用于 Node.js 的 Azure 媒体服务模块</span><span class="sxs-lookup"><span data-stu-id="ea2e4-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="ea2e4-104">Azure 媒体服务是一个可扩展的基于云的平台，开发人员可以使用它来构建可缩放的媒体管理与传送应用程序。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="ea2e4-105">媒体服务基于 REST API，你可以使用这些 API 安全地上传、存储、编码和打包视频或音频内容，以供点播以及以实时流形式传送到各种客户端（例如，电视、电脑和移动设备）。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="ea2e4-106">使用 Azure 媒体服务可以：</span><span class="sxs-lookup"><span data-stu-id="ea2e4-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="ea2e4-107">完全使用媒体服务构建端到端工作流。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="ea2e4-108">使用第三方组件来构建工作流的某些组成部分。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="ea2e4-109">例如，使用第三方编码器进行编码。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="ea2e4-110">然后，使用媒体服务进行上传、保护、打包和传送。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="ea2e4-111">实时流式传输内容，或者按需交付内容。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="ea2e4-112">本主题还提供了其他相关主题的链接。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="ea2e4-113">管理包</span><span class="sxs-lookup"><span data-stu-id="ea2e4-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ea2e4-114">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="ea2e4-114">Install the npm module</span></span>

<span data-ttu-id="ea2e4-115">安装 Azure 媒体服务 npm 模块</span><span class="sxs-lookup"><span data-stu-id="ea2e4-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="ea2e4-116">示例</span><span class="sxs-lookup"><span data-stu-id="ea2e4-116">Example</span></span>

<span data-ttu-id="ea2e4-117">此示例列出资源组的所有媒体服务。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-117">This example lists all media services for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ea2e4-118">示例</span><span class="sxs-lookup"><span data-stu-id="ea2e4-118">Samples</span></span>

<span data-ttu-id="ea2e4-119">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ea2e4-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
