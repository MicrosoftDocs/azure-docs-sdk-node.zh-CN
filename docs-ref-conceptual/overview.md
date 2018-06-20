---
title: 用于 Node.js 的 Azure 模块
description: 用于 Node.js 的 Azure 管理和服务模块概述
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 165e1580e408b71b6147e51c41e22bc8fe7277a1
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220529"
---
# <a name="azure-modules-for-nodejs"></a><span data-ttu-id="c1d12-103">用于 Node.js 的 Azure 模块</span><span class="sxs-lookup"><span data-stu-id="c1d12-103">Azure modules for Node.js</span></span>

<span data-ttu-id="c1d12-104">使用用于 Node.js 的 Azure 模块，通过 Node.js 应用程序管理 Azure 资源和连接到服务。</span><span class="sxs-lookup"><span data-stu-id="c1d12-104">Manage Azure resources and connect to services from your Node.js applications with the Azure modules for Node.js.</span></span> <span data-ttu-id="c1d12-105">代码以 [npm 模块](node-sdk-azure-install.md)的形式提供，方便在项目中使用。</span><span class="sxs-lookup"><span data-stu-id="c1d12-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="c1d12-106">管理 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="c1d12-106">Manage Azure resources</span></span>

<span data-ttu-id="c1d12-107">使用管理模块可在应用中创建和查询资源，或构建自己的 Azure 自动化工具。</span><span class="sxs-lookup"><span data-stu-id="c1d12-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="c1d12-108">例如，若要使用现有的网络接口创建 Linux VM，可编写以下代码：</span><span class="sxs-lookup"><span data-stu-id="c1d12-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
                    primary: true
                }
            ]
        },
        storageProfile: {
            imageReference: {
                publisher: 'Canonical',
                offer: 'UbuntuServer',
                sku: '16.04-LTS',
                version: 'latest'
            },
        }
    };
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="c1d12-109">查看[安装说明](node-sdk-azure-install.md)了解模块的完整列表，并查看[入门文章](node-sdk-azure-get-started.md)来设置身份验证并针对自己的 Azure 订阅运行示例代码来创建和更新资源。</span><span class="sxs-lookup"><span data-stu-id="c1d12-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="c1d12-110">连接到 Azure 服务</span><span class="sxs-lookup"><span data-stu-id="c1d12-110">Connect to Azure services</span></span>

<span data-ttu-id="c1d12-111">除了使用 Azure 模块在 Azure 中创建和管理资源以外，还可以通过包在应用中连接和使用 Azure 云服务。</span><span class="sxs-lookup"><span data-stu-id="c1d12-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="c1d12-112">例如，可以更新表 SQL 数据库或者将文件上传到 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="c1d12-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="c1d12-113">从[完整列表](node-sdk-azure-install.md)中选择特定服务所需的包，并访问 [Node.js 开发人员中心](https://azure.microsoft.com/develop/nodejs/)获取教程和示例代码，了解如何在应用中使用这些模块。</span><span class="sxs-lookup"><span data-stu-id="c1d12-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [Node.js developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="c1d12-114">例如，若要输出 Azure 存储容器中每个 Blob 的内容：</span><span class="sxs-lookup"><span data-stu-id="c1d12-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="c1d12-115">代码示例和参考</span><span class="sxs-lookup"><span data-stu-id="c1d12-115">Sample code and reference</span></span>

<span data-ttu-id="c1d12-116">以下示例涵盖可以通过 Azure 管理模块完成的常见任务，并提供可在自己应用中使用的现成代码：</span><span class="sxs-lookup"><span data-stu-id="c1d12-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="c1d12-117">虚拟机</span><span class="sxs-lookup"><span data-stu-id="c1d12-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="c1d12-118">Web 应用</span><span class="sxs-lookup"><span data-stu-id="c1d12-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="c1d12-119">SQL 数据库</span><span class="sxs-lookup"><span data-stu-id="c1d12-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="c1d12-120">我们针对服务和管理模块中的所有模块提供了[参考](https://docs.microsoft.com/javascript/api)文档。</span><span class="sxs-lookup"><span data-stu-id="c1d12-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="c1d12-121">[发行说明](https://github.com/Azure/azure-sdk-for-node/releases)中介绍了新增功能、重大更改，并提供了有关如何从以前的版本迁移的说明。</span><span class="sxs-lookup"><span data-stu-id="c1d12-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>