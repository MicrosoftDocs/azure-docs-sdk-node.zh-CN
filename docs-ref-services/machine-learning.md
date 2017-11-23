---
title: "用于 Node.js 的 Azure 机器学习模块"
description: "用于 Node.js 的 Azure 机器学习模块参考"
keywords: "Azure,SDK,API,机器学习, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 465b569d0eef53208211be2c2ff36d28bb28d107
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="5151f-104">用于 Node.js 的 Azure 机器学习模块</span><span class="sxs-lookup"><span data-stu-id="5151f-104">Azure Machine Learning modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5151f-105">概述</span><span class="sxs-lookup"><span data-stu-id="5151f-105">Overview</span></span>

<span data-ttu-id="5151f-106">机器学习是一项数据科研技术，可帮助计算机从现有的数据中学习，预测将来的行为、结果和趋势。</span><span class="sxs-lookup"><span data-stu-id="5151f-106">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="5151f-107">机器学习的这种预测可让应用和设备变得更聪明。</span><span class="sxs-lookup"><span data-stu-id="5151f-107">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="5151f-108">在网上购物时，机器学习可根据购买的产品帮助推荐其他产品。</span><span class="sxs-lookup"><span data-stu-id="5151f-108">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="5151f-109">刷信用卡时，机器学习可将这笔交易与交易数据库进行比较，帮助检测诈骗。</span><span class="sxs-lookup"><span data-stu-id="5151f-109">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="5151f-110">当吸尘器机器人打扫房间时，机器学习可帮助它确定作业是否已完成。</span><span class="sxs-lookup"><span data-stu-id="5151f-110">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="5151f-111">管理包</span><span class="sxs-lookup"><span data-stu-id="5151f-111">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="5151f-112">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="5151f-112">Install the npm module</span></span>

<span data-ttu-id="5151f-113">安装 Azure 机器学习 npm 模块</span><span class="sxs-lookup"><span data-stu-id="5151f-113">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="5151f-114">示例</span><span class="sxs-lookup"><span data-stu-id="5151f-114">Example</span></span>

<span data-ttu-id="5151f-115">此示例列出所有机器学习提交计划。</span><span class="sxs-lookup"><span data-stu-id="5151f-115">This example lists all machine learning committment plans.</span></span>

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

## <a name="samples"></a><span data-ttu-id="5151f-116">示例</span><span class="sxs-lookup"><span data-stu-id="5151f-116">Samples</span></span>

<span data-ttu-id="5151f-117">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="5151f-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
