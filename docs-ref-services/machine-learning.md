---
title: 用于 Node.js 的 Azure 机器学习模块
description: 用于 Node.js 的 Azure 机器学习模块参考
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7e39084c65a40e47ed61cc01daf994aff447690e
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50270551"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="ec4b7-103">用于 Node.js 的 Azure 机器学习模块</span><span class="sxs-lookup"><span data-stu-id="ec4b7-103">Azure Machine Learning modules for Node.js</span></span>

<span data-ttu-id="ec4b7-104">机器学习是一项数据科研技术，可帮助计算机从现有的数据中学习，预测将来的行为、结果和趋势。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-104">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="ec4b7-105">机器学习的这种预测可让应用和设备变得更聪明。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-105">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="ec4b7-106">在网上购物时，机器学习可根据购买的产品帮助推荐其他产品。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-106">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="ec4b7-107">刷信用卡时，机器学习可将这笔交易与交易数据库进行比较，帮助检测诈骗。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-107">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="ec4b7-108">当吸尘器机器人打扫房间时，机器学习可帮助它确定作业是否已完成。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-108">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="ec4b7-109">管理包</span><span class="sxs-lookup"><span data-stu-id="ec4b7-109">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="ec4b7-110">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="ec4b7-110">Install the npm module</span></span>

<span data-ttu-id="ec4b7-111">安装 Azure 机器学习 npm 模块</span><span class="sxs-lookup"><span data-stu-id="ec4b7-111">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="ec4b7-112">示例</span><span class="sxs-lookup"><span data-stu-id="ec4b7-112">Example</span></span>

<span data-ttu-id="ec4b7-113">此示例列出所有机器学习提交计划。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-113">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="ec4b7-114">示例</span><span class="sxs-lookup"><span data-stu-id="ec4b7-114">Samples</span></span>

<span data-ttu-id="ec4b7-115">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
