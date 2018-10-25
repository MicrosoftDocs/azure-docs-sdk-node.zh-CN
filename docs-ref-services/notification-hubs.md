---
title: 用于 Node.js 的 Azure 通知中心模块
description: 用于 Node.js 的 Azure 通知中心模块参考
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 18eae632b41b71bc64b052852b677507da2678e9
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "49720682"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="35b60-103">用于 Node.js 的 Azure 通知中心模块</span><span class="sxs-lookup"><span data-stu-id="35b60-103">Azure Notification Hubs modules for Node.js</span></span>

<span data-ttu-id="35b60-104">Azure 通知中心提供易用的多平台扩展式推送引擎。</span><span class="sxs-lookup"><span data-stu-id="35b60-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="35b60-105">使用单个跨平台 API 调用，即可轻松地从任意云或本地后端向任意移动平台发送有针对性的个性化推送通知。</span><span class="sxs-lookup"><span data-stu-id="35b60-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="35b60-106">通知中心非常适合用于企业和消费者方案。</span><span class="sxs-lookup"><span data-stu-id="35b60-106">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="35b60-107">下面是通知中心的几个客户用例：</span><span class="sxs-lookup"><span data-stu-id="35b60-107">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="35b60-108">以较低的延迟向数百万用户发送突发新闻通知。</span><span class="sxs-lookup"><span data-stu-id="35b60-108">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="35b60-109">向感兴趣的用户群发送基于位置的优惠券。</span><span class="sxs-lookup"><span data-stu-id="35b60-109">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="35b60-110">向媒体/体育/财经/游戏应用程序的用户或组发送活动相关的通知。</span><span class="sxs-lookup"><span data-stu-id="35b60-110">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="35b60-111">将促销内容推送到应用，以吸引客户并向其推销。</span><span class="sxs-lookup"><span data-stu-id="35b60-111">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="35b60-112">向用户通知企业事件，例如，有新消息和新的工作项。</span><span class="sxs-lookup"><span data-stu-id="35b60-112">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="35b60-113">发送多重身份验证的代码。</span><span class="sxs-lookup"><span data-stu-id="35b60-113">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="35b60-114">管理包</span><span class="sxs-lookup"><span data-stu-id="35b60-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="35b60-115">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="35b60-115">Install the npm module</span></span>

<span data-ttu-id="35b60-116">安装 Azure 通知中心模块</span><span class="sxs-lookup"><span data-stu-id="35b60-116">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="35b60-117">示例</span><span class="sxs-lookup"><span data-stu-id="35b60-117">Example</span></span>

<span data-ttu-id="35b60-118">此示例列出所有通知中心。</span><span class="sxs-lookup"><span data-stu-id="35b60-118">This example lists all notification hubs.</span></span>

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a><span data-ttu-id="35b60-119">示例</span><span class="sxs-lookup"><span data-stu-id="35b60-119">Samples</span></span>

* [<span data-ttu-id="35b60-120">Node.js 后端的应用服务移动应用完整快速入门</span><span class="sxs-lookup"><span data-stu-id="35b60-120">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [<span data-ttu-id="35b60-121">通过推特发送 Azure IoT 服务根据运行 Node.js 的 Intel Edison 发出的数据检测到的振动异常</span><span class="sxs-lookup"><span data-stu-id="35b60-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="35b60-122">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="35b60-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
