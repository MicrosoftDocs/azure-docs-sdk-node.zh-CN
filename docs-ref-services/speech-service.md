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
ms.component: speech-service
ms.openlocfilehash: 43a6921d4ec782287cc041ecaabab4567b0fe677
ms.sourcegitcommit: 74417c10aee8987c3e0343728efac75823c902d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185984"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>用于 JavaScript 的认知服务语音 SDK

## <a name="overview"></a>概述

为了简化支持语音的应用程序的开发，Microsoft 提供了可以与[语音服务](https://aka.ms/csspeech)配合使用的语音 SDK。
语音 SDK 提供一致的本机语音转文本和语音翻译 API。

### <a name="install-the-npm-module"></a>安装 npm 模块

安装认知服务语音 SDK npm 模块

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a>示例 

以下代码片段演示如何从文件中进行简单的语音识别：

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

查看[分步快速入门](/azure/cognitive-services/speech-service/quickstart-js-node)。

## <a name="samples"></a>示例

* [适用于 Node.js 的分步快速入门](/azure/cognitive-services/speech-service/quickstart-js-node)。
* [适用于浏览器的分步快速入门](/azure/cognitive-services/speech-service/quickstart-js-browser)。
* 在[语音 SDK 示例存储库](https://aka.ms/csspeech/samples)中可找到更多示例。
