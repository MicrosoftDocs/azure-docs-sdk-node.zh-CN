---
title: 用于 Node.js 的 Azure 授权模块
description: 用于 Node.js 的 Azure 授权模块参考
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2018
ms.locfileid: "52048372"
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="b3feb-103">用于 Node.js 的 Azure 授权模块</span><span class="sxs-lookup"><span data-stu-id="b3feb-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b3feb-104">概述</span><span class="sxs-lookup"><span data-stu-id="b3feb-104">Overview</span></span>

<span data-ttu-id="b3feb-105">Azure 应用服务身份验证/授权功能方便应用程序登录用户，避免在应用后端更改代码。</span><span class="sxs-lookup"><span data-stu-id="b3feb-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="b3feb-106">授权可以方便地保护应用程序和处理每个用户的数据。</span><span class="sxs-lookup"><span data-stu-id="b3feb-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="b3feb-107">管理包</span><span class="sxs-lookup"><span data-stu-id="b3feb-107">Management package</span></span>

<span data-ttu-id="b3feb-108">使用 npm 安装用于 Node.js 的 Azure 授权模块</span><span class="sxs-lookup"><span data-stu-id="b3feb-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b3feb-109">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="b3feb-109">Install the npm module</span></span>

<span data-ttu-id="b3feb-110">安装 Azure 授权 npm 模块</span><span class="sxs-lookup"><span data-stu-id="b3feb-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="b3feb-111">示例</span><span class="sxs-lookup"><span data-stu-id="b3feb-111">Example</span></span>

<span data-ttu-id="b3feb-112">此示例列出所请求的资源组的所有角色分配。</span><span class="sxs-lookup"><span data-stu-id="b3feb-112">This example lists all role assignments for the requested resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a><span data-ttu-id="b3feb-113">示例</span><span class="sxs-lookup"><span data-stu-id="b3feb-113">Samples</span></span>

<span data-ttu-id="b3feb-114">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b3feb-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
