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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50339915"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a>用于 Node.js 的 Azure 事件网格库

将简单的基于 HTTP 的事件处理与 Azure 事件网格配合使用，开发事件驱动型应用程序，以便侦听并响应来自 Azure 服务和自定义源的事件。

[详细了解](/azure/event-grid/overview) Azure 事件网格，通过 [Azure Blob 存储事件教程](/azure/storage/blobs/storage-blob-event-quickstart)来入门。 

## <a name="publish-sdk"></a>发布 SDK

创建事件，进行身份验证，然后使用 Azure 事件网格发布 SDK 将内容发布到主题。

### <a name="installation"></a>安装

使用 npm 将模块添加到项目：

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a>示例代码

以下代码段将模拟事件发布到事件网格主题。 可以通过 Azure 门户或 Azure CLI 检索终结点和主题访问键：

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

此示例演示如何处理 Azure 存储中的事件：

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
> [了解客户端 API](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a>管理 SDK

使用管理 SDK 创建、更新或删除事件网格实例、主题和订阅。

### <a name="installation"></a>安装

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a>示例代码

以下代码创建事件网格主题 `topic1` 并返回与新建主题相关联的访问键。

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
> [了解管理 API](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a>了解详细信息

- [使用事件网格 SDK 接收事件](/azure/event-grid/receive-events)
