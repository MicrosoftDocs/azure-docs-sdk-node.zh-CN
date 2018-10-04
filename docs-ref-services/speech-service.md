---
title: 用于 JavaScript 的认知服务语音 SDK
description: 用于 JavaScript 的认知服务语音 SDK 参考
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48458645"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>用于 JavaScript 的认知服务语音 SDK

## <a name="overview"></a>概述

为了简化支持语音的应用程序的开发，Microsoft 提供了可以与[语音服务](https://aka.ms/csspeech)配合使用的语音 SDK。
语音 SDK 提供一致的本机语音转文本和语音翻译 API。

> [!NOTE]
> 认知服务语音 SDK 目前仅适用于浏览器。
> 很快会推出 NPM 包。

### <a name="install-the-speech-sdk"></a>安装语音 SDK

下载 [.zip 包](https://aka.ms/csspeech/jsbrowserpackage)形式的语音 SDK，然后将其解压缩。
这样会将多个文件解压缩，包括名为 `microsoft.cognitiveservices.speech.sdk.bundle.js` 的文件。
在网页中以脚本资源形式加载此文件，然后即可使用语音 SDK：

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>示例 

以下代码片段演示如何在浏览器中进行简单的语音识别：

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

查看[分步快速入门](/azure/cognitive-services/speech-service/quickstart-js-browser)。

## <a name="samples"></a>示例

浏览[语音 SDK 示例存储库](https://aka.ms/csspeech/samples)中的更多示例。
