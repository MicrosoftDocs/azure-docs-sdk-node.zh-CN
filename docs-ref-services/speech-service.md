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
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "49724412"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="d1fbb-103">用于 JavaScript 的认知服务语音 SDK</span><span class="sxs-lookup"><span data-stu-id="d1fbb-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="d1fbb-104">概述</span><span class="sxs-lookup"><span data-stu-id="d1fbb-104">Overview</span></span>

<span data-ttu-id="d1fbb-105">为了简化支持语音的应用程序的开发，Microsoft 提供了可以与[语音服务](https://aka.ms/csspeech)配合使用的语音 SDK。</span><span class="sxs-lookup"><span data-stu-id="d1fbb-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="d1fbb-106">语音 SDK 提供一致的本机语音转文本和语音翻译 API。</span><span class="sxs-lookup"><span data-stu-id="d1fbb-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="d1fbb-107">认知服务语音 SDK 目前仅适用于浏览器。</span><span class="sxs-lookup"><span data-stu-id="d1fbb-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="d1fbb-108">很快会推出 NPM 包。</span><span class="sxs-lookup"><span data-stu-id="d1fbb-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="d1fbb-109">安装语音 SDK</span><span class="sxs-lookup"><span data-stu-id="d1fbb-109">Install the Speech SDK</span></span>

<span data-ttu-id="d1fbb-110">下载 [.zip 包](https://aka.ms/csspeech/jsbrowserpackage)形式的语音 SDK，然后将其解压缩。</span><span class="sxs-lookup"><span data-stu-id="d1fbb-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="d1fbb-111">这样会将多个文件解压缩，包括名为 `microsoft.cognitiveservices.speech.sdk.bundle.js` 的文件。</span><span class="sxs-lookup"><span data-stu-id="d1fbb-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="d1fbb-112">在网页中以脚本资源形式加载此文件，然后即可使用语音 SDK：</span><span class="sxs-lookup"><span data-stu-id="d1fbb-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="d1fbb-113">示例</span><span class="sxs-lookup"><span data-stu-id="d1fbb-113">Example</span></span> 

<span data-ttu-id="d1fbb-114">以下代码片段演示如何在浏览器中进行简单的语音识别：</span><span class="sxs-lookup"><span data-stu-id="d1fbb-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

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

<span data-ttu-id="d1fbb-115">查看[分步快速入门](/azure/cognitive-services/speech-service/quickstart-js-browser)。</span><span class="sxs-lookup"><span data-stu-id="d1fbb-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="d1fbb-116">示例</span><span class="sxs-lookup"><span data-stu-id="d1fbb-116">Samples</span></span>

<span data-ttu-id="d1fbb-117">浏览[语音 SDK 示例存储库](https://aka.ms/csspeech/samples)中的更多示例。</span><span class="sxs-lookup"><span data-stu-id="d1fbb-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
