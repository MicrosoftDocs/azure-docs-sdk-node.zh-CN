---
title: 用于 Node.js 的 Azure 事件网格库
description: 用于 Node.js 的 Azure 事件网格库参考
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: ''
ms.technology: ''
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: bddf4efc1eda186aee92d30af24125823c7a8f7b
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "48979641"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="c8618-103">用于 Node.js 的 Azure 事件网格库</span><span class="sxs-lookup"><span data-stu-id="c8618-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="c8618-104">将简单的基于 HTTP 的事件处理与 Azure 事件网格配合使用，开发事件驱动型应用程序，以便侦听并响应来自 Azure 服务和自定义源的事件。</span><span class="sxs-lookup"><span data-stu-id="c8618-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="c8618-105">[详细了解](/azure/event-grid/overview) Azure 事件网格，通过 [Azure Blob 存储事件教程](/azure/storage/blobs/storage-blob-event-quickstart)来入门。</span><span class="sxs-lookup"><span data-stu-id="c8618-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="c8618-106">发布 SDK</span><span class="sxs-lookup"><span data-stu-id="c8618-106">Publish SDK</span></span>

<span data-ttu-id="c8618-107">创建事件，进行身份验证，然后使用 Azure 事件网格发布 SDK 将内容发布到主题。</span><span class="sxs-lookup"><span data-stu-id="c8618-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="c8618-108">安装</span><span class="sxs-lookup"><span data-stu-id="c8618-108">Installation</span></span>

<span data-ttu-id="c8618-109">使用 npm 将模块添加到项目：</span><span class="sxs-lookup"><span data-stu-id="c8618-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="c8618-110">示例代码</span><span class="sxs-lookup"><span data-stu-id="c8618-110">Example code</span></span>

<span data-ttu-id="c8618-111">以下代码段将模拟事件发布到事件网格主题。</span><span class="sxs-lookup"><span data-stu-id="c8618-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="c8618-112">可以通过 Azure 门户或 Azure CLI 检索终结点和主题访问键：</span><span class="sxs-lookup"><span data-stu-id="c8618-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

<span data-ttu-id="c8618-113">此示例演示如何处理 Azure 存储中的事件：</span><span class="sxs-lookup"><span data-stu-id="c8618-113">This sample shows how to handle an event from Azure Storage:</span></span>

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8618-114">了解客户端 API</span><span class="sxs-lookup"><span data-stu-id="c8618-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="c8618-115">管理 SDK</span><span class="sxs-lookup"><span data-stu-id="c8618-115">Management SDK</span></span>

<span data-ttu-id="c8618-116">使用管理 SDK 创建、更新或删除事件网格实例、主题和订阅。</span><span class="sxs-lookup"><span data-stu-id="c8618-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="c8618-117">安装</span><span class="sxs-lookup"><span data-stu-id="c8618-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="c8618-118">示例代码</span><span class="sxs-lookup"><span data-stu-id="c8618-118">Example code</span></span>

<span data-ttu-id="c8618-119">以下代码创建事件网格主题 `topic1` 并返回与新建主题相关联的访问键。</span><span class="sxs-lookup"><span data-stu-id="c8618-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8618-120">了解管理 API</span><span class="sxs-lookup"><span data-stu-id="c8618-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="c8618-121">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="c8618-121">Learn more</span></span>

- [<span data-ttu-id="c8618-122">使用事件网格 SDK 接收事件</span><span class="sxs-lookup"><span data-stu-id="c8618-122">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)
