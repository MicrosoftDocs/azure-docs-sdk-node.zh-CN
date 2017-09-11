---
title: "用于 Node.js 的 Azure 中继模块"
description: "用于 Node.js 的 Azure 中继模块参考"
keywords: "Azure,SDK,API,中继, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 7e958433e0d3cc6b464bb5980d4f161323a18ab2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="0d291-104">用于 Node.js 的 Azure 中继模块</span><span class="sxs-lookup"><span data-stu-id="0d291-104">Azure Relay modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0d291-105">概述</span><span class="sxs-lookup"><span data-stu-id="0d291-105">Overview</span></span>

<span data-ttu-id="0d291-106">Azure 中继服务通过允许安全地向公有云公开位于企业网络内的服务来创建混合应用程序，无需打开防火墙连接，也无需对企业网络基础结构进行彻底更改。</span><span class="sxs-lookup"><span data-stu-id="0d291-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="0d291-107">中继支持各种不同的传输协议和 Web 服务标准。</span><span class="sxs-lookup"><span data-stu-id="0d291-107">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="0d291-108">[详细了解 Azure 中继](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)。</span><span class="sxs-lookup"><span data-stu-id="0d291-108">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="0d291-109">管理包</span><span class="sxs-lookup"><span data-stu-id="0d291-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0d291-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0d291-110">Install the npm module</span></span>

<span data-ttu-id="0d291-111">安装 Azure 中继 npm 模块</span><span class="sxs-lookup"><span data-stu-id="0d291-111">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="0d291-112">示例</span><span class="sxs-lookup"><span data-stu-id="0d291-112">Example</span></span>

<span data-ttu-id="0d291-113">此示例列出中继客户端的命名空间。</span><span class="sxs-lookup"><span data-stu-id="0d291-113">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="0d291-114">示例</span><span class="sxs-lookup"><span data-stu-id="0d291-114">Samples</span></span>

<span data-ttu-id="0d291-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="0d291-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
