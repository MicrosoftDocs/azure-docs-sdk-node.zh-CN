---
title: 用于 Node.js 的 Azure 中继模块
description: 用于 Node.js 的 Azure 中继模块参考
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: e0bb24ac422d71bd8c957e94cceffd57bf121e48
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51465991"
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="3cf40-103">用于 Node.js 的 Azure 中继模块</span><span class="sxs-lookup"><span data-stu-id="3cf40-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="3cf40-104">Azure 中继服务通过允许安全地向公有云公开位于企业网络内的服务来创建混合应用程序，无需打开防火墙连接，也无需对企业网络基础结构进行彻底更改。</span><span class="sxs-lookup"><span data-stu-id="3cf40-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="3cf40-105">中继支持各种不同的传输协议和 Web 服务标准。</span><span class="sxs-lookup"><span data-stu-id="3cf40-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="3cf40-106">[详细了解 Azure 中继](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)。</span><span class="sxs-lookup"><span data-stu-id="3cf40-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="3cf40-107">管理包</span><span class="sxs-lookup"><span data-stu-id="3cf40-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3cf40-108">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3cf40-108">Install the npm module</span></span>

<span data-ttu-id="3cf40-109">安装 Azure 中继 npm 模块</span><span class="sxs-lookup"><span data-stu-id="3cf40-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="3cf40-110">示例</span><span class="sxs-lookup"><span data-stu-id="3cf40-110">Example</span></span>

<span data-ttu-id="3cf40-111">此示例列出中继客户端的命名空间。</span><span class="sxs-lookup"><span data-stu-id="3cf40-111">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="3cf40-112">示例</span><span class="sxs-lookup"><span data-stu-id="3cf40-112">Samples</span></span>

<span data-ttu-id="3cf40-113">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="3cf40-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
