---
title: 用于 JavaScript 的认知服务语音 SDK
description: 用于 JavaScript 的认知服务语音 SDK 参考
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.subservice: speech-service
ms.openlocfilehash: b1375b6beb478cab2475539c03b6bac9f0ea99e0
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052578"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="580ee-103">用于 JavaScript 的认知服务语音 SDK</span><span class="sxs-lookup"><span data-stu-id="580ee-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="580ee-104">概述</span><span class="sxs-lookup"><span data-stu-id="580ee-104">Overview</span></span>

<span data-ttu-id="580ee-105">为了简化支持语音的应用程序的开发，Microsoft 提供了可以与[语音服务](https://aka.ms/csspeech)配合使用的语音 SDK。</span><span class="sxs-lookup"><span data-stu-id="580ee-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="580ee-106">语音 SDK 提供一致的本机语音转文本和语音翻译 API。</span><span class="sxs-lookup"><span data-stu-id="580ee-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="580ee-107">安装 npm 模块</span><span class="sxs-lookup"><span data-stu-id="580ee-107">Install the npm module</span></span>

<span data-ttu-id="580ee-108">安装认知服务语音 SDK npm 模块</span><span class="sxs-lookup"><span data-stu-id="580ee-108">Install the Cognitive Services Speech SDK npm module</span></span>

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a><span data-ttu-id="580ee-109">示例</span><span class="sxs-lookup"><span data-stu-id="580ee-109">Example</span></span> 

<span data-ttu-id="580ee-110">以下代码片段演示如何从文件中进行简单的语音识别：</span><span class="sxs-lookup"><span data-stu-id="580ee-110">The following code snippets illustrates how to do simple speech recognition from a file:</span></span>

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

<span data-ttu-id="580ee-111">查看[分步快速入门](/azure/cognitive-services/speech-service/quickstart-js-node)。</span><span class="sxs-lookup"><span data-stu-id="580ee-111">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>

## <a name="samples"></a><span data-ttu-id="580ee-112">示例</span><span class="sxs-lookup"><span data-stu-id="580ee-112">Samples</span></span>

* <span data-ttu-id="580ee-113">[适用于 Node.js 的分步快速入门](/azure/cognitive-services/speech-service/quickstart-js-node)。</span><span class="sxs-lookup"><span data-stu-id="580ee-113">[Step-by-step quickstart for Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>
* <span data-ttu-id="580ee-114">[适用于浏览器的分步快速入门](/azure/cognitive-services/speech-service/quickstart-js-browser)。</span><span class="sxs-lookup"><span data-stu-id="580ee-114">[Step-by-step quickstart for the browser](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>
* <span data-ttu-id="580ee-115">在[语音 SDK 示例存储库](https://aka.ms/csspeech/samples)中可找到更多示例。</span><span class="sxs-lookup"><span data-stu-id="580ee-115">More samples can be found in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
