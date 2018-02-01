---
title: "用于 Node.js 的 Azure 认知服务模块"
description: "用于 Node.js 的 Azure 认知服务模块参考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="10018-103">用于 Node.js 的 Azure 认知服务模块</span><span class="sxs-lookup"><span data-stu-id="10018-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="10018-104">Azure 认知服务是一组面向开发人员的 API、SDK 和服务，可提高应用程序的智能性、吸引力和可发现性。</span><span class="sxs-lookup"><span data-stu-id="10018-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="10018-105">Microsoft 认知服务是在 Microsoft 不断发展的机器学习 API 产品组合基础上的拓展，可让开发人员轻松地在其应用程序中添加智能功能 – 例如情绪和动作检测；面部、语音与视觉识别；语音与语言理解。</span><span class="sxs-lookup"><span data-stu-id="10018-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="10018-106">我们的愿景是让逐渐能够观看、聆听、讲述、理解甚至思考的系统为更多的个人计算体验和生产力提供辅助。</span><span class="sxs-lookup"><span data-stu-id="10018-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="10018-107">管理包</span><span class="sxs-lookup"><span data-stu-id="10018-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="10018-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="10018-108">Install the npm module</span></span>

<span data-ttu-id="10018-109">安装 Azure 认知服务 npm 模块</span><span class="sxs-lookup"><span data-stu-id="10018-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="10018-110">示例</span><span class="sxs-lookup"><span data-stu-id="10018-110">Example</span></span>

<span data-ttu-id="10018-111">此示例列出所有认知服务帐户。</span><span class="sxs-lookup"><span data-stu-id="10018-111">This example lists all cognitive service accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="10018-112">示例</span><span class="sxs-lookup"><span data-stu-id="10018-112">Samples</span></span>

<span data-ttu-id="10018-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="10018-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
