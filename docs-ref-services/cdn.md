---
title: 用于 Node.js 的 Azure CDN 模块
description: 用于 Node.js 的 Azure CDN 模块参考
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: b330eeedc178f20064b4a6b1c3f4f7d266590f11
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="0cffe-103">用于 Node.js 的 Azure CDN 模块</span><span class="sxs-lookup"><span data-stu-id="0cffe-103">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0cffe-104">概述</span><span class="sxs-lookup"><span data-stu-id="0cffe-104">Overview</span></span>

<span data-ttu-id="0cffe-105">Azure 内容分发网络 (CDN) 为开发人员提供一个全局解决方案用于传递 Azure 或其他任何位置中托管的高带宽内容。</span><span class="sxs-lookup"><span data-stu-id="0cffe-105">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="0cffe-106">使用 CDN，可以缓存从 Azure Blob 存储、Web 应用程序、虚拟机、应用程序文件夹或其他 HTTP/HTTPS 位置加载的公开对象。</span><span class="sxs-lookup"><span data-stu-id="0cffe-106">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="0cffe-107">可以将 CDN 缓存定位在战略性的位置上，以便提供最大的带宽向用户传送内容。</span><span class="sxs-lookup"><span data-stu-id="0cffe-107">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="0cffe-108">CDN 通常用于传送静态内容，例如图像、样式表、文档、文件、客户端脚本和 HTML 页面。</span><span class="sxs-lookup"><span data-stu-id="0cffe-108">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="0cffe-109">管理包</span><span class="sxs-lookup"><span data-stu-id="0cffe-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0cffe-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0cffe-110">Install the npm module</span></span>

<span data-ttu-id="0cffe-111">安装 Azure CDN npm 模块</span><span class="sxs-lookup"><span data-stu-id="0cffe-111">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="0cffe-112">示例</span><span class="sxs-lookup"><span data-stu-id="0cffe-112">Example</span></span>

<span data-ttu-id="0cffe-113">此示例列出所有 CDN 配置文件。</span><span class="sxs-lookup"><span data-stu-id="0cffe-113">This example lists all of the CDN profiles.</span></span>

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

## <a name="samples"></a><span data-ttu-id="0cffe-114">示例</span><span class="sxs-lookup"><span data-stu-id="0cffe-114">Samples</span></span>

<span data-ttu-id="0cffe-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="0cffe-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
