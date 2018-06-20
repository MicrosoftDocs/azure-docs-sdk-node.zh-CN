---
title: 用于 Node.js 的 Azure 模块入门
description: 使用适用于 Node.js 的 Azure 模块开始进行身份验证和资源管理
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 072574c70b658806cd998dc0af8a81be3ea56bb4
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220579"
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="410eb-103">用于 Node.js 的 Azure 模块入门</span><span class="sxs-lookup"><span data-stu-id="410eb-103">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="410eb-104">本指南逐步讲解如何安装 Azure Node.js 模块，使用服务主体在 Azure 中进行身份验证，以及运行可在 Azure 订阅中创建资源并连接到 Azure 云服务的示例代码。</span><span class="sxs-lookup"><span data-stu-id="410eb-104">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="410eb-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="410eb-105">Prerequisites</span></span>

- <span data-ttu-id="410eb-106">一个 Azure 帐户。</span><span class="sxs-lookup"><span data-stu-id="410eb-106">An Azure account.</span></span> <span data-ttu-id="410eb-107">如果没有帐户，可[获取一个免费试用帐户](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="410eb-107">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="410eb-108">Node.js</span><span class="sxs-lookup"><span data-stu-id="410eb-108">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="410eb-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) 或 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)。</span><span class="sxs-lookup"><span data-stu-id="410eb-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="410eb-110">准备环境</span><span class="sxs-lookup"><span data-stu-id="410eb-110">Prepare your environment</span></span>

<span data-ttu-id="410eb-111">在空目录中创建新项目并安装以下 npm 模块：</span><span class="sxs-lookup"><span data-stu-id="410eb-111">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="410eb-112">设置身份验证</span><span class="sxs-lookup"><span data-stu-id="410eb-112">Set up authentication</span></span>

<span data-ttu-id="410eb-113">Node.js 应用程序需要 Azure 订阅中的读取和创建权限才能运行本指南中的示例代码。</span><span class="sxs-lookup"><span data-stu-id="410eb-113">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="410eb-114">创建一个服务主体，并将应用程序配置为使用该服务主体的凭据运行。</span><span class="sxs-lookup"><span data-stu-id="410eb-114">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="410eb-115">服务主体是与标识关联的非交互式帐户，该帐户仅拥有运行应用所需的特权。</span><span class="sxs-lookup"><span data-stu-id="410eb-115">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="410eb-116">[使用 Azure CLI 2.0 创建服务主体](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli)并捕获输出。</span><span class="sxs-lookup"><span data-stu-id="410eb-116">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="410eb-117">需要在密码参数而非 `MY_SECURE_PASSWORD` 中提供[安全密码](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy)。</span><span class="sxs-lookup"><span data-stu-id="410eb-117">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

<span data-ttu-id="410eb-118">导出 *appId*、*password* 和 *tenant* 的值作为环境变量：</span><span class="sxs-lookup"><span data-stu-id="410eb-118">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="410eb-119">使用 [az account show](https://docs.microsoft.com/cli/azure/account#show) 获取订阅的 ID</span><span class="sxs-lookup"><span data-stu-id="410eb-119">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

<span data-ttu-id="410eb-120">导出订阅 ID 作为环境变量</span><span class="sxs-lookup"><span data-stu-id="410eb-120">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="410eb-121">创建 Linux 虚拟机</span><span class="sxs-lookup"><span data-stu-id="410eb-121">Create a Linux virtual machine</span></span>

<span data-ttu-id="410eb-122">使用以下代码在当前目录中创建新文件 *createVM.js*。</span><span class="sxs-lookup"><span data-stu-id="410eb-122">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="410eb-123">使用合理的密码更新 `adminPass` 的值。</span><span class="sxs-lookup"><span data-stu-id="410eb-123">Update the value of `adminPass` with a good password.</span></span>

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
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

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

<span data-ttu-id="410eb-124">通过命令行运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="410eb-124">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="410eb-125">完成该代码后，请获取新虚拟机的 IP，并使用代码中 `adminPass` 的值通过 SSH 登录。</span><span class="sxs-lookup"><span data-stu-id="410eb-125">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="410eb-126">将 Blob 写入 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="410eb-126">Write a blob to Azure Storage</span></span>

<span data-ttu-id="410eb-127">使用以下代码在当前目录中创建新文件 *uploadFile.js*。</span><span class="sxs-lookup"><span data-stu-id="410eb-127">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

<span data-ttu-id="410eb-128">运行以下命令，并将输出中的 URL 复制并粘贴到 Web 浏览器，以查看 Azure 存储中的文件：</span><span class="sxs-lookup"><span data-stu-id="410eb-128">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="410eb-129">清理资源</span><span class="sxs-lookup"><span data-stu-id="410eb-129">Clean up resources</span></span>

<span data-ttu-id="410eb-130">删除资源组，以删除本指南中创建的资源。</span><span class="sxs-lookup"><span data-stu-id="410eb-130">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="410eb-131">后续步骤</span><span class="sxs-lookup"><span data-stu-id="410eb-131">Next steps</span></span>

<span data-ttu-id="410eb-132">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="410eb-132">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="410eb-133">引用</span><span class="sxs-lookup"><span data-stu-id="410eb-133">Reference</span></span> 

<span data-ttu-id="410eb-134">我们为所有包提供了[参考](/javascript/api/overview/azure/)文档。</span><span class="sxs-lookup"><span data-stu-id="410eb-134">A [reference](/javascript/api/overview/azure/) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="410eb-135">获取帮助和提供反馈</span><span class="sxs-lookup"><span data-stu-id="410eb-135">Get help and give feedback</span></span>

<span data-ttu-id="410eb-136">在 [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js) 社区中提问。</span><span class="sxs-lookup"><span data-stu-id="410eb-136">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="410eb-137">在[项目 GitHub](https://github.com/Azure/azure-sdk-for-node) 中针对用于 Node.js 的 Azure 模块报告 bug 和反映问题。</span><span class="sxs-lookup"><span data-stu-id="410eb-137">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

