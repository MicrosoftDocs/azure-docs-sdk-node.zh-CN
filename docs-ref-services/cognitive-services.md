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
ms.openlocfilehash: fd0870f4b38928c23145a50d4c71456b4c94c3e9
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="52399-103">JavaScript Azure 认知服务模块</span><span class="sxs-lookup"><span data-stu-id="52399-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="52399-104">视觉模块</span><span class="sxs-lookup"><span data-stu-id="52399-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="52399-105">计算机视觉</span><span class="sxs-lookup"><span data-stu-id="52399-105">Computer Vision</span></span> 

<span data-ttu-id="52399-106">返回图像中找到的视觉内容的相关信息：</span><span class="sxs-lookup"><span data-stu-id="52399-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="52399-107">使用标记、描述和特定于域的模型来识别内容，并使用置信度对其进行标记。</span><span class="sxs-lookup"><span data-stu-id="52399-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="52399-108">应用“成人/不雅”设置，以便自动限制成人内容。</span><span class="sxs-lookup"><span data-stu-id="52399-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="52399-109">识别图片中的图像类型和配色方案。</span><span class="sxs-lookup"><span data-stu-id="52399-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="52399-110">在浏览器中免费[试用计算机视觉](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/)。</span><span class="sxs-lookup"><span data-stu-id="52399-110">[Try Computer Vision](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="52399-111">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="52399-112">[详细了解](/azure/cognitive-services/computer-vision/home)计算机视觉 API 并开始使用[计算机视觉 API JavaScript 快速入门](/azure/cognitive-services/computer-vision/quickstarts/javascript)。</span><span class="sxs-lookup"><span data-stu-id="52399-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="52399-113">内容审查器</span><span class="sxs-lookup"><span data-stu-id="52399-113">Content Moderator</span></span>

<span data-ttu-id="52399-114">计算机辅助的文本、视频和图像审查，借助人工审阅工具得到增强</span><span class="sxs-lookup"><span data-stu-id="52399-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="52399-115">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="52399-116">[详细了解](/azure/cognitive-services/content-moderator/overview)内容审查器服务。</span><span class="sxs-lookup"><span data-stu-id="52399-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="52399-117">人脸 API</span><span class="sxs-lookup"><span data-stu-id="52399-117">Face API</span></span>

<span data-ttu-id="52399-118">检测、识别、分析、组织和标记照片中的人脸。</span><span class="sxs-lookup"><span data-stu-id="52399-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="52399-119">在浏览器中[试用人脸 API](https://azure.microsoft.com/en-us/services/cognitive-services/face/)。</span><span class="sxs-lookup"><span data-stu-id="52399-119">[Try the Face API](https://azure.microsoft.com/en-us/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="52399-120">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="52399-121">[详细了解](/azure/cognitive-services/face/overview)人脸 API 并开始使用[人脸 API JavaScript 快速入门](/azure/cognitive-services/Face/quickstarts/javascript)。</span><span class="sxs-lookup"><span data-stu-id="52399-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="52399-122">搜索模块</span><span class="sxs-lookup"><span data-stu-id="52399-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="52399-123">Web 搜索</span><span class="sxs-lookup"><span data-stu-id="52399-123">Web search</span></span>

<span data-ttu-id="52399-124">检索必应 Web 搜索 API 索引的 Web 文档，并根据结果类型、新鲜度以及其他特征来缩小结果范围。</span><span class="sxs-lookup"><span data-stu-id="52399-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="52399-125">在浏览器中[试用 Web 搜索 API](https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="52399-125">[Try the Web Search API](https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="52399-126">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="52399-127">[详细了解](/azure/cognitive-services/bing-web-search/overview)必应 Web 搜索 API 并开始使用 [Web 搜索 API Node.js 快速入门](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52399-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="52399-128">图像搜索</span><span class="sxs-lookup"><span data-stu-id="52399-128">Image search</span></span>

<span data-ttu-id="52399-129">搜索图像，在结果中获取缩略图、完整的图像 URL、图像元数据等。</span><span class="sxs-lookup"><span data-stu-id="52399-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="52399-130">在浏览器中[试用图像搜索 API](https://azure.microsoft.com/en-us/services/cognitive-services/bing-image-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="52399-130">[Try the Image Search API](https://azure.microsoft.com/en-us/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="52399-131">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="52399-132">[详细了解](/azure/cognitive-services/bing-image-search/overview)必应图像搜索 API 并开始使用[图像搜索 API Node.js 快速入门](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52399-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="52399-133">实体搜索</span><span class="sxs-lookup"><span data-stu-id="52399-133">Entity search</span></span>

<span data-ttu-id="52399-134">针对给定的搜索词或位置，搜索关联性最大的实体（地点、人员或物体）。</span><span class="sxs-lookup"><span data-stu-id="52399-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="52399-135">在浏览器中[试用实体搜索 API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="52399-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="52399-136">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="52399-137">[详细了解](/azure/cognitive-services/bing-entities-search/search-the-web)必应实体搜索 API 并开始使用[实体搜索 API Node.js 快速入门](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52399-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="52399-138">自定义搜索</span><span class="sxs-lookup"><span data-stu-id="52399-138">Custom search</span></span>

<span data-ttu-id="52399-139">构建符合特定搜索域要求的自定义 Web 搜索。</span><span class="sxs-lookup"><span data-stu-id="52399-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="52399-140">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="52399-141">[详细了解](/azure/cognitive-services/bing-custom-search/)必应自定义搜索服务并开始使用[自定义搜索 API Node.js 快速入门](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)从应用查询自定义搜索。</span><span class="sxs-lookup"><span data-stu-id="52399-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="52399-142">视频搜索</span><span class="sxs-lookup"><span data-stu-id="52399-142">Video search</span></span>

<span data-ttu-id="52399-143">在 Web 中查找视频，获取包含创建者、编码、长度和观看次数等元数据在内的结果。</span><span class="sxs-lookup"><span data-stu-id="52399-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="52399-144">在浏览器中[试用视频搜索 API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="52399-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="52399-145">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="52399-146">[详细了解](/azure/cognitive-services/bing-video-search/search-the-web)必应视频搜索服务并开始使用[视频搜索 API Node.js 快速入门](/azure/cognitive-services/bing-video-search/nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52399-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="52399-147">新闻搜索</span><span class="sxs-lookup"><span data-stu-id="52399-147">News search</span></span>

<span data-ttu-id="52399-148">在 Web 中搜索新闻文章，并对文章、相关新闻、图像和提供者信息等元数据进行处理。</span><span class="sxs-lookup"><span data-stu-id="52399-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="52399-149">在浏览器中[试用新闻搜索 API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="52399-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="52399-150">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="52399-151">[详细了解](/azure/cognitive-services/bing-news-search/search-the-web)必应新闻搜索服务并开始使用[新闻搜索 API JavaScript 快速入门](/azure/cognitive-services/bing-news-search/nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52399-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="52399-152">语言模块</span><span class="sxs-lookup"><span data-stu-id="52399-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="52399-153">文本分析</span><span class="sxs-lookup"><span data-stu-id="52399-153">Text Analytics</span></span> 

<span data-ttu-id="52399-154">文本分析 API 是一种基于云的服务，提供对原始文本的自然语言处理。</span><span class="sxs-lookup"><span data-stu-id="52399-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="52399-155">此 API 包括三项主要功能：</span><span class="sxs-lookup"><span data-stu-id="52399-155">The API includes three main functions:</span></span>

- <span data-ttu-id="52399-156">情绪分析</span><span class="sxs-lookup"><span data-stu-id="52399-156">Sentiment analysis</span></span>
- <span data-ttu-id="52399-157">关键短语提取</span><span class="sxs-lookup"><span data-stu-id="52399-157">Key phrase extraction</span></span>
- <span data-ttu-id="52399-158">语言检测</span><span class="sxs-lookup"><span data-stu-id="52399-158">Language detection</span></span>

<span data-ttu-id="52399-159">在浏览器中[试用文本分析 API](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/)。</span><span class="sxs-lookup"><span data-stu-id="52399-159">[Try the Text Analytics API](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="52399-160">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="52399-161">[详细了解](/azure/cognitive-services/text-analytics/overview)文本分析 API 并开始使用[文本分析 API Node.js 快速入门](/azure/cognitive-services/text-analytics/quickstarts/nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52399-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="52399-162">拼写检查</span><span class="sxs-lookup"><span data-stu-id="52399-162">Spell Check</span></span>

<span data-ttu-id="52399-163">使用必应拼写检查 API 进行上下文语法和拼写检查。</span><span class="sxs-lookup"><span data-stu-id="52399-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="52399-164">在浏览器中[试用拼写检查 API](https://azure.microsoft.com/en-us/services/cognitive-services/spell-check/)。</span><span class="sxs-lookup"><span data-stu-id="52399-164">[Try the Spell Check API](https://azure.microsoft.com/en-us/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="52399-165">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 获取 JavaScript 模块：</span><span class="sxs-lookup"><span data-stu-id="52399-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="52399-166">[详细了解](/azure/cognitive-services/bing-spell-check/proof-text)拼写检查 API 并开始使用[拼写检查 API Node.js 快速入门](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52399-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="52399-167">示例</span><span class="sxs-lookup"><span data-stu-id="52399-167">Samples</span></span>

<span data-ttu-id="52399-168">详细了解可在应用中使用的[示例 Node.js 代码](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="52399-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
