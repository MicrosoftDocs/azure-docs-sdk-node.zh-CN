---
title: 用于 Node.js 的 Azure 认知服务模块
description: 用于 Node.js 的 Azure 认知服务模块参考
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2018
ms.locfileid: "51071858"
---
# <a name="javascript-azure-cognitive-services-modules"></a>JavaScript Azure 认知服务模块

## <a name="vision-modules"></a>视觉模块

### <a name="computer-vision"></a>计算机视觉 

返回图像中找到的视觉内容的相关信息：

- 使用标记、描述和特定于域的模型来识别内容，并使用置信度对其进行标记。
- 应用“成人/不雅”设置，以便自动限制成人内容。
- 识别图片中的图像类型和配色方案。

在浏览器中免费[试用计算机视觉](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-computervision
```

[详细了解](/azure/cognitive-services/computer-vision/home)计算机视觉 API 并开始使用[计算机视觉 API JavaScript 快速入门](/azure/cognitive-services/computer-vision/quickstarts/javascript)。

### <a name="content-moderator"></a>内容审查器

计算机辅助的文本、视频和图像审查，借助人工审阅工具得到增强

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-contentmoderator
```

[详细了解](/azure/cognitive-services/content-moderator/overview)内容审查器服务。

### <a name="face-api"></a>人脸 API

检测、识别、分析、组织和标记照片中的人脸。 

在浏览器中[试用人脸 API](https://azure.microsoft.com/services/cognitive-services/face/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-face
```

[详细了解](/azure/cognitive-services/face/overview)人脸 API 并开始使用[人脸 API JavaScript 快速入门](/azure/cognitive-services/Face/quickstarts/javascript)。

## <a name="search-modules"></a>搜索模块

### <a name="web-search"></a>Web 搜索

检索必应 Web 搜索 API 索引的 Web 文档，并根据结果类型、新鲜度以及其他特征来缩小结果范围。 

在浏览器中[试用 Web 搜索 API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-websearch
```

[详细了解](/azure/cognitive-services/bing-web-search/overview)必应 Web 搜索 API 并开始使用 [Web 搜索 API Node.js 快速入门](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)。

### <a name="image-search"></a>图像搜索

搜索图像，在结果中获取缩略图、完整的图像 URL、图像元数据等。

在浏览器中[试用图像搜索 API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-imagesearch
```

[详细了解](/azure/cognitive-services/bing-image-search/overview)必应图像搜索 API 并开始使用[图像搜索 API Node.js 快速入门](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)。


### <a name="entity-search"></a>实体搜索

针对给定的搜索词或位置，搜索关联性最大的实体（地点、人员或物体）。

在浏览器中[试用实体搜索 API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-entitysearch
```

[详细了解](/azure/cognitive-services/bing-entities-search/search-the-web)必应实体搜索 API 并开始使用[实体搜索 API Node.js 快速入门](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)。

### <a name="custom-search"></a>自定义搜索

构建符合特定搜索域要求的自定义 Web 搜索。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-customsearch
```

[详细了解](/azure/cognitive-services/bing-custom-search/)必应自定义搜索服务并开始使用[自定义搜索 API Node.js 快速入门](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)从应用查询自定义搜索。

### <a name="video-search"></a>视频搜索

在 Web 中查找视频，获取包含创建者、编码、长度和观看次数等元数据在内的结果。

在浏览器中[试用视频搜索 API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-videosearch
```

[详细了解](/azure/cognitive-services/bing-video-search/search-the-web)必应视频搜索服务并开始使用[视频搜索 API Node.js 快速入门](/azure/cognitive-services/bing-video-search/nodejs)。


### <a name="news-search"></a>新闻搜索

在 Web 中搜索新闻文章，并对文章、相关新闻、图像和提供者信息等元数据进行处理。

在浏览器中[试用新闻搜索 API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-newssearch
```

[详细了解](/azure/cognitive-services/bing-news-search/search-the-web)必应新闻搜索服务并开始使用[新闻搜索 API JavaScript 快速入门](/azure/cognitive-services/bing-news-search/nodejs)。


## <a name="language-modules"></a>语言模块

### <a name="text-analytics"></a>文本分析 

文本分析 API 是一种基于云的服务，提供对原始文本的自然语言处理。 此 API 包括三项主要功能：

- 情绪分析
- 关键短语提取
- 语言检测

在浏览器中[试用文本分析 API](https://azure.microsoft.com/services/cognitive-services/text-analytics/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-textanalytics
```

[详细了解](/azure/cognitive-services/text-analytics/overview)文本分析 API 并开始使用[文本分析 API Node.js 快速入门](/azure/cognitive-services/text-analytics/quickstarts/nodejs)。


### <a name="spell-check"></a>拼写检查

使用必应拼写检查 API 进行上下文语法和拼写检查。

在浏览器中[试用拼写检查 API](https://azure.microsoft.com/services/cognitive-services/spell-check/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：

```
npm install azure-cognitiveservices-spellcheck
```

[详细了解](/azure/cognitive-services/bing-spell-check/proof-text)拼写检查 API 并开始使用[拼写检查 API Node.js 快速入门](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)。

## <a name="samples"></a>示例

详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
