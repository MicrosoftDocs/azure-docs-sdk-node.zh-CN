---
title: 用于 Node.js 的 Azure 容器服务模块
description: 用于 Node.js 的 Azure 容器服务模块参考
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689821"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a><span data-ttu-id="c6c1f-103">用于 Node.js 的 Microsoft Azure SDK - ContainerServiceClient</span><span class="sxs-lookup"><span data-stu-id="c6c1f-103">Microsoft Azure SDK for Node.js - ContainerServiceClient</span></span>
<span data-ttu-id="c6c1f-104">此项目提供用于访问 Azure 的 Node.js 包。</span><span class="sxs-lookup"><span data-stu-id="c6c1f-104">This project provides a Node.js package for accessing Azure.</span></span> <span data-ttu-id="c6c1f-105">现在支持：</span><span class="sxs-lookup"><span data-stu-id="c6c1f-105">Right now it supports:</span></span>
- <span data-ttu-id="c6c1f-106">**Node.js 6.x.x 或更高版本**</span><span class="sxs-lookup"><span data-stu-id="c6c1f-106">**Node.js version 6.x.x or higher**</span></span>

## <a name="features"></a><span data-ttu-id="c6c1f-107">功能</span><span class="sxs-lookup"><span data-stu-id="c6c1f-107">Features</span></span>


## <a name="how-to-install"></a><span data-ttu-id="c6c1f-108">安装方法</span><span class="sxs-lookup"><span data-stu-id="c6c1f-108">How to Install</span></span>

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a><span data-ttu-id="c6c1f-109">如何使用</span><span class="sxs-lookup"><span data-stu-id="c6c1f-109">How to use</span></span>

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a><span data-ttu-id="c6c1f-110">身份验证、客户端创建以及将 containerServices 列为示例。</span><span class="sxs-lookup"><span data-stu-id="c6c1f-110">Authentication, client creation and list containerServices as an example.</span></span>

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a><span data-ttu-id="c6c1f-111">相关项目</span><span class="sxs-lookup"><span data-stu-id="c6c1f-111">Related projects</span></span>

- [<span data-ttu-id="c6c1f-112">Microsoft Azure SDK for Node.js</span><span class="sxs-lookup"><span data-stu-id="c6c1f-112">Microsoft Azure SDK for Node.js</span></span>](https://github.com/Azure/azure-sdk-for-node)