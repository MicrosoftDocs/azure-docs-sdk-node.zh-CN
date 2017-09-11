---
title: "在 Node.js 中使用 Azure 消息传送和 IoT 的示例代码"
description: "演示在 Node.js 中使用 Azure 消息传送和 IoT 的示例代码"
author: tomarcher
manager: douge
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: tarcher
ms.openlocfilehash: 5d7fc46edde0df844f8e4933bef672e619bd06fc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2017
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="b3307-103">在 Node.js 中使用 Azure 消息传送和 IoT 的示例代码</span><span class="sxs-lookup"><span data-stu-id="b3307-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="b3307-104">以下示例代码演示在 Node.js 中使用 Azure 消息传送和 IoT</span><span class="sxs-lookup"><span data-stu-id="b3307-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="b3307-105">如需其他任务的代码，可以浏览 [Azure Node.js 示例](https://azure.microsoft.com/resources/samples/?term=nodejs)的完整列表。</span><span class="sxs-lookup"><span data-stu-id="b3307-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="b3307-106">**Azure IoT 中心**</span><span class="sxs-lookup"><span data-stu-id="b3307-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="b3307-107">Azure IoT 中心 ping</span><span class="sxs-lookup"><span data-stu-id="b3307-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="b3307-108">帮助验证设备与 Azure IoT 中心之间的连接的简单 ping 解决方案。</span><span class="sxs-lookup"><span data-stu-id="b3307-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| [<span data-ttu-id="b3307-109">通过推特发送 Azure IoT 服务根据运行 Node.js 的 Intel Edison 发出的数据检测到的振动异常</span><span class="sxs-lookup"><span data-stu-id="b3307-109">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) | <span data-ttu-id="b3307-110">一个使用 Azure IoT 中心的 IoT 项目，演示运行 Node 的设备如何发送遥测数据供 Azure IoT 服务分析。</span><span class="sxs-lookup"><span data-stu-id="b3307-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="b3307-111">**Intel Edison IoT**</span><span class="sxs-lookup"><span data-stu-id="b3307-111">**Intel Edison IoT**</span></span> ||
| [<span data-ttu-id="b3307-112">Intel Edison Azure IoT 初学者工具包入门</span><span class="sxs-lookup"><span data-stu-id="b3307-112">Get started with Intel Edison Azure IoT Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) | <span data-ttu-id="b3307-113">使用 Azure IoT 初学者工具包 (Intel Edison) 演示 Azure IoT。</span><span class="sxs-lookup"><span data-stu-id="b3307-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="b3307-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="b3307-114">**MQTT**</span></span> ||
| [<span data-ttu-id="b3307-115">示例 MQTT 和 HTTP 网关模块</span><span class="sxs-lookup"><span data-stu-id="b3307-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="b3307-116">提供两个网关模块，公开用于上传遥测数据的 IoT 中心式 MQTT 和 HTTPS 终结点。在本例中，MQTT 模块也是 C2D 消息传送模块。</span><span class="sxs-lookup"><span data-stu-id="b3307-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="b3307-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="b3307-117">**Raspberry Pi**</span></span> ||
| [<span data-ttu-id="b3307-118">Microsoft Azure IoT Raspberry Pi 初学者工具包入门</span><span class="sxs-lookup"><span data-stu-id="b3307-118">Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) | <span data-ttu-id="b3307-119">演示如何使用 Azure IoT Raspberry Pi 初学者工具包。</span><span class="sxs-lookup"><span data-stu-id="b3307-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| [<span data-ttu-id="b3307-120">将 Microsoft Azure IoT Raspberry Pi 3 初学者工具包连接到远程监视解决方案</span><span class="sxs-lookup"><span data-stu-id="b3307-120">Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) | <span data-ttu-id="b3307-121">了解如何将 Raspberry Pi 3 设备连接到 Azure IoT 套件远程监视解决方案。</span><span class="sxs-lookup"><span data-stu-id="b3307-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
