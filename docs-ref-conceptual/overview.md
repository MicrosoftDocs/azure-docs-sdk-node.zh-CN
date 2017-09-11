---
title: "用于 Node.js 的 Azure 模块"
description: "用于 Node.js 的 Azure 管理和服务模块概述"
keywords: "Azure, Node.js, SDK, API, 管理, 客户端, 服务"
author: TomArcher
ms.author: tarcher
manager: douge
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 56dc4f4f36d4e0e9a2d40b38ff8f0b1f9690818c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-modules-for-nodejs"></a>用于 Node.js 的 Azure 模块

使用用于 Node.js 的 Azure 模块，通过 Node.js 应用程序管理 Azure 资源和连接到服务。 代码以 [npm 模块](node-sdk-azure-install.md)的形式提供，方便在项目中使用。 

## <a name="manage-azure-resources"></a>管理 Azure 资源

使用管理模块可在应用中创建和查询资源，或构建自己的 Azure 自动化工具。 

例如，若要使用现有的网络接口创建 Linux VM，可编写以下代码：

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

查看[安装说明](node-sdk-azure-install.md)了解模块的完整列表，并查看[入门文章](node-sdk-azure-get-started.md)来设置身份验证并针对自己的 Azure 订阅运行示例代码来创建和更新资源。 

## <a name="connect-to-azure-services"></a>连接到 Azure 服务

除了使用 Azure 模块在 Azure 中创建和管理资源以外，还可以通过包在应用中连接和使用 Azure 云服务。 例如，可以更新表 SQL 数据库或者将文件上传到 Azure 存储。 从[完整列表](node-sdk-azure-install.md)中选择特定服务所需的包，并访问 [Node.js 开发人员中心](https://azure.microsoft.com/develop/nodejs/)获取教程和示例代码，了解如何在应用中使用这些模块。

例如，若要输出 Azure 存储容器中每个 Blob 的内容：

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a>代码示例和参考

以下示例涵盖可以通过 Azure 管理模块完成的常见任务，并提供可在自己应用中使用的现成代码：

- [虚拟机](node-samples-services-compute.md)
- [Web 应用](node-samples-services-web-and-mobile.md)
- [SQL 数据库](node-samples-services-database.md)
   
我们针对服务和管理模块中的所有模块提供了[参考](https://docs.microsoft.com/nodejs/api)文档。 [发行说明](https://github.com/Azure/azure-sdk-for-node/releases)中介绍了新增功能、重大更改，并提供了有关如何从以前的版本迁移的说明。