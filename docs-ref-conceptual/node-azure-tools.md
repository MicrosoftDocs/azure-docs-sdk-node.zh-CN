---
title: Azure 中面向 Node.js 开发人员的工具 | Microsoft Docs
description: 在 Azure 上安装用于 Node.js 开发的单个工具
services: multiple
author: rloutlaw
manager: routlaw
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 11/07/2017
ms.author: routlaw
ms.openlocfilehash: 172cc3e1bff763cbf768dce5aa85065da0dd4927
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220729"
---
# <a name="azure-tools-for-nodejs-developers"></a><span data-ttu-id="b588a-103">面向 Node.js 开发人员的 Azure 工具</span><span class="sxs-lookup"><span data-stu-id="b588a-103">Azure tools for Node.js developers</span></span>
<span data-ttu-id="b588a-104">建议使用以下工具在 Node.js 中进行 Azure 方面的开发。</span><span class="sxs-lookup"><span data-stu-id="b588a-104">The following tools are recommended for developing with Azure on Node.js.</span></span>

## <a name="azure-cli"></a><span data-ttu-id="b588a-105">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="b588a-105">Azure CLI</span></span>
<span data-ttu-id="b588a-106">Azure CLI 经过优化，可从命令行管理 Azure 资源。</span><span class="sxs-lookup"><span data-stu-id="b588a-106">Azure CLI is optimized for managing Azure resources from the command line.</span></span>

![CLI](media/node-azure-tools/cli.png)
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="b588a-108">安装 Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="b588a-108">Install the Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)

## <a name="visual-studio-code"></a><span data-ttu-id="b588a-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b588a-109">Visual Studio Code</span></span>
<span data-ttu-id="b588a-110">在任何 OS 上编辑和调试 Node.js 应用。</span><span class="sxs-lookup"><span data-stu-id="b588a-110">Edit and debug Node.js apps on any OS.</span></span>

![Visual Studio Code](media/node-azure-tools/vs-code.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b588a-112">下载 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b588a-112">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="azure-extensions"></a><span data-ttu-id="b588a-113">Azure 扩展</span><span class="sxs-lookup"><span data-stu-id="b588a-113">Azure Extensions</span></span>
<span data-ttu-id="b588a-114">在 Visual Studio Code 中使用以下免费扩展来直接与 Azure 服务对接。</span><span class="sxs-lookup"><span data-stu-id="b588a-114">Use the following free extensions to interface with Azure services directly in Visual Studio Code.</span></span>

| <span data-ttu-id="b588a-115">工具</span><span class="sxs-lookup"><span data-stu-id="b588a-115">Tool</span></span> | <span data-ttu-id="b588a-116">说明</span><span class="sxs-lookup"><span data-stu-id="b588a-116">Description</span></span>  |
|:---------:|---------|
| [<span data-ttu-id="b588a-117">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="b588a-117">Azure Functions</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions) <br> <span data-ttu-id="b588a-118">[![Azure Functions 工具](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span><span class="sxs-lookup"><span data-stu-id="b588a-118">[![Azure Functions Tools](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span></span> | <span data-ttu-id="b588a-119">创建、管理、查看、调试和部署函数</span><span class="sxs-lookup"><span data-stu-id="b588a-119">Create, manage, view, debug, and deploy functions</span></span>|
| [<span data-ttu-id="b588a-120">Azure 应用服务</span><span class="sxs-lookup"><span data-stu-id="b588a-120">Azure App Service</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice) <br> <span data-ttu-id="b588a-121">[![应用服务工具](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span><span class="sxs-lookup"><span data-stu-id="b588a-121">[![App Service Tools](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span></span> | <span data-ttu-id="b588a-122">浏览站点和 Azure 门户、创建新站点（仅限 Node.js 中的 Linux）并部署到槽位</span><span class="sxs-lookup"><span data-stu-id="b588a-122">Browse sites and the Azure portal, create new sites (Linux on Node.js only) and deploy to slots</span></span> |
| [<span data-ttu-id="b588a-123">Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="b588a-123">Cosmos DB </span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)  <br> <span data-ttu-id="b588a-124">[![Cosmos DB 工具](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span><span class="sxs-lookup"><span data-stu-id="b588a-124">[![Cosmos DB Tools](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span></span>| <span data-ttu-id="b588a-125">在 Azure 中创建、浏览和更新全球分布式多模型数据库</span><span class="sxs-lookup"><span data-stu-id="b588a-125">Create, browse, and update globally distributed, multi-model databases in Azure</span></span> |
| [<span data-ttu-id="b588a-126">Docker</span><span class="sxs-lookup"><span data-stu-id="b588a-126">Docker</span></span>](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)   <br> <span data-ttu-id="b588a-127">[![Cosmos DB 工具](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span><span class="sxs-lookup"><span data-stu-id="b588a-127">[![Cosmos DB Tools](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span></span>| <span data-ttu-id="b588a-128">管理 Docker 容器和映像、Docker 中心及 Azure 容器注册表</span><span class="sxs-lookup"><span data-stu-id="b588a-128">Manage Docker containers and images, Docker Hub, and Azure container registry</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="b588a-129">在 Visual Studio Code Marketplace 中获取更多的 Azure 扩展</span><span class="sxs-lookup"><span data-stu-id="b588a-129">Get more Azure extensions in the Visual Studio Code marketplace</span></span>](https://marketplace.visualstudio.com/search?term=azure&target=VSCode&category=All%20categories&sortBy=Relevance)