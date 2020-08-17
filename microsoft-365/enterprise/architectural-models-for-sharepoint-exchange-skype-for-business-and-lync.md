---
title: SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: 摘要：获取介绍 SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型、部署和平台选项的 IT 海报。
ms.openlocfilehash: 67f1018c70dfc86306b0d1e7ceb6061a166b3db8
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687991"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a><span data-ttu-id="a83a4-103">SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型</span><span class="sxs-lookup"><span data-stu-id="a83a4-103">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>

<span data-ttu-id="a83a4-104">这些 IT 海报介绍了 SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型和部署选项，并提供了在 Microsoft Azure 中部署 SharePoint 的设计信息。</span><span class="sxs-lookup"><span data-stu-id="a83a4-104">These IT posters describe the architectural models and deployment options for SharePoint, Exchange, Skype for Business, and Lync, and they provide design information for deploying SharePoint in Microsoft Azure.</span></span>
  
<span data-ttu-id="a83a4-105">借助 Microsoft 365，你可以将用户熟悉的协作和通信服务作为基于云的服务来提供。</span><span class="sxs-lookup"><span data-stu-id="a83a4-105">With Microsoft 365, you can provide the collaboration and communication services your users are familiar with as a cloud-based service.</span></span> <span data-ttu-id="a83a4-106">有一些例外情况，无论是在本地部署还是使用 Microsoft 365，用户体验均保持不变。</span><span class="sxs-lookup"><span data-stu-id="a83a4-106">With a few exceptions, the user experience remains the same whether you are maintaining an on-premises deployment or using Microsoft 365.</span></span> <span data-ttu-id="a83a4-107">此统一的用户体现使得决定在何处放置每个工作负荷以及在何处提出问题变得简单直接，例如：</span><span class="sxs-lookup"><span data-stu-id="a83a4-107">This unified user experience makes it less straightforward to decide where to place each workload and raises questions such as:</span></span>
  
- <span data-ttu-id="a83a4-108">如何确定选择哪个平台选项用于各个工作负载？</span><span class="sxs-lookup"><span data-stu-id="a83a4-108">How do you determine which platform option to choose for your individual workloads?</span></span>
    
- <span data-ttu-id="a83a4-109">将任何服务保留在内部部署是否有意义？</span><span class="sxs-lookup"><span data-stu-id="a83a4-109">Does it make sense to keep any service on-premises?</span></span>
    
- <span data-ttu-id="a83a4-110">混合部署合适的方案是什么样的？</span><span class="sxs-lookup"><span data-stu-id="a83a4-110">What is a scenario where a hybrid deployment is appropriate?</span></span>
    
- <span data-ttu-id="a83a4-111">Microsoft Azure 如何适应图片？</span><span class="sxs-lookup"><span data-stu-id="a83a4-111">How does Microsoft Azure fit in the picture?</span></span>
    
- <span data-ttu-id="a83a4-112">Azure 中的 Office 服务器工作负载所支持的配置是什么？</span><span class="sxs-lookup"><span data-stu-id="a83a4-112">What are the supported configurations for Office Server workloads in Azure?</span></span>
    
> [!TIP]
> <span data-ttu-id="a83a4-p102">此页上的大多数海报都有多种语言，包括中文、英语、法语、德语、意大利语、日语、朝鲜语、葡萄牙语、俄语和西班牙语。若要下载其中一种语言的海报，请单击相应海报的**更多语言**链接。</span><span class="sxs-lookup"><span data-stu-id="a83a4-p102">Most of the posters on this page are available in multiple languages, including Chinese, English, French, German, Italian, Japanese, Korean, Portuguese, Russian, and Spanish. To download a poster in one of these languages, click the **More languages** link for that poster.</span></span>
  
<span data-ttu-id="a83a4-p103">请将你的想法告诉我们！向我们 ([cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com)) 发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a83a4-p103">Let us know what you think! Send us email at [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com).</span></span> 
  
<span data-ttu-id="a83a4-117">此页面链接到下列海报：</span><span class="sxs-lookup"><span data-stu-id="a83a4-117">This page links you to the following posters:</span></span>
  
- <span data-ttu-id="a83a4-118">**体系结构模型海报** 可以使用这些资源确定 SharePoint 2016 和 Skype for Business 2015 的理想平台和配置。</span><span class="sxs-lookup"><span data-stu-id="a83a4-118">**Architectural models posters** You can use these resources to determine your ideal platform and configuration for SharePoint 2016 and Skype for Business 2015.</span></span>
    
  - [<span data-ttu-id="a83a4-119">Microsoft 2016 SharePoint 体系结构模型</span><span class="sxs-lookup"><span data-stu-id="a83a4-119">Microsoft SharePoint 2016 Architectural Models</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [<span data-ttu-id="a83a4-120">SharePoint Server 2016 数据库</span><span class="sxs-lookup"><span data-stu-id="a83a4-120">SharePoint Server 2016 Databases</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [<span data-ttu-id="a83a4-121">Microsoft Skype for Business 2015 体系结构模型</span><span class="sxs-lookup"><span data-stu-id="a83a4-121">Microsoft Skype for Business 2015 Architectural Models</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- <span data-ttu-id="a83a4-122">**平台选项海报** 可使用这些资源确定 SharePoint 2013、Exchange 2013 和Lync 2013 的理想平台和配置。</span><span class="sxs-lookup"><span data-stu-id="a83a4-122">**Platform options posters** You can use these resources to determine your ideal platform and configuration for SharePoint 2013, Exchange 2013, and Lync 2013.</span></span>
    
  - [<span data-ttu-id="a83a4-123">SharePoint 2013 平台选项</span><span class="sxs-lookup"><span data-stu-id="a83a4-123">SharePoint 2013 Platform Options</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [<span data-ttu-id="a83a4-124">Exchange 2013 平台选项</span><span class="sxs-lookup"><span data-stu-id="a83a4-124">Exchange 2013 Platform Options</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [<span data-ttu-id="a83a4-125">Lync 2013 平台选项</span><span class="sxs-lookup"><span data-stu-id="a83a4-125">Lync 2013 Platform Options</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- <span data-ttu-id="a83a4-126">**Azure 解决方案海报中的 SharePoint Server 2013** 可以使用 IT 海报确定 Azure 基础结构服务中 SharePoint Server 2013 工作负载的设计和配置。</span><span class="sxs-lookup"><span data-stu-id="a83a4-126">**SharePoint Server 2013 in Azure solutions posters** You can use these IT posters to determine the design and configuration for SharePoint Server 2013 workloads in Azure infrastructure services.</span></span>
    
  - [<span data-ttu-id="a83a4-127">Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="a83a4-127">Internet sites in Microsoft Azure using SharePoint Server 2013</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [<span data-ttu-id="a83a4-128">设计示例：Microsoft Azure 中的 SharePoint 2013 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="a83a4-128">Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [<span data-ttu-id="a83a4-129">SharePoint 灾难恢复到 Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a83a4-129">SharePoint Disaster Recovery to Microsoft Azure</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a><span data-ttu-id="a83a4-130">体系结构模型海报</span><span class="sxs-lookup"><span data-stu-id="a83a4-130">Architectural models posters</span></span>

<span data-ttu-id="a83a4-p104">这些 SharePoint 2016 和 Skype for Business 2015 的新 IT 海报，提供了一种以轻松打印形式比较各种部署方法的方式。每张海报都提供了所有配置或平台的可用选项列表，并针对每个选项提供了以下信息：</span><span class="sxs-lookup"><span data-stu-id="a83a4-p104">These new IT posters for SharePoint 2016 and Skype for Business 2015 provide a way to compare the various deployment methods in an easy-to-print format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:</span></span>
  
- <span data-ttu-id="a83a4-133">**概述** 平台的简短摘要，包括概念图。</span><span class="sxs-lookup"><span data-stu-id="a83a4-133">**Overview** A brief summary of the platform, including a conceptual diagram.</span></span>
    
- <span data-ttu-id="a83a4-134">**最适用于** 非常适用于特定平台的常见方案。</span><span class="sxs-lookup"><span data-stu-id="a83a4-134">**Best for** Common scenarios that are ideally suited for the particular platform.</span></span>
    
- <span data-ttu-id="a83a4-135">**许可要求** 部署所需的许可证。</span><span class="sxs-lookup"><span data-stu-id="a83a4-135">**License requirements** The licenses you need for deployment.</span></span>
    
- <span data-ttu-id="a83a4-136">**体系结构任务** 架构师需要做出的决定。</span><span class="sxs-lookup"><span data-stu-id="a83a4-136">**Architecture tasks** The decisions you need to make as an architect.</span></span>
    
- <span data-ttu-id="a83a4-137">**IT 专业人员任务或职责** IT 员工需履行的日常职责。</span><span class="sxs-lookup"><span data-stu-id="a83a4-137">**IT Pro tasks or responsibilities** The daily responsibilities that your IT staff needs to plan for.</span></span>
    
<span data-ttu-id="a83a4-138"><a name="SP2016_ArchModel"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-138"><a name="SP2016_ArchModel"> </a></span></span>
### <a name="microsoft-sharepoint-2016-architectural-models"></a><span data-ttu-id="a83a4-139">Microsoft SharePoint 2016 体系结构模型</span><span class="sxs-lookup"><span data-stu-id="a83a4-139">Microsoft SharePoint 2016 Architectural Models</span></span>

|<span data-ttu-id="a83a4-140">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-140">**Item**</span></span>|<span data-ttu-id="a83a4-141">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-141">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-142">[![SharePoint 2016 体系结构模型海报缩略图](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650)</span><span class="sxs-lookup"><span data-stu-id="a83a4-142">[![Thumbnail for the SharePoint 2016 Architectural Models poster](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650)</span></span> <br/> <span data-ttu-id="a83a4-143">[PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=52650)</span><span class="sxs-lookup"><span data-stu-id="a83a4-143">[PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=52650)</span></span> <br/> | <span data-ttu-id="a83a4-144">此 IT 海报介绍了业务决策者和解决方案架构师需要了解的 SharePoint Online、Microsoft Azure 和 SharePoint 本地配置。</span><span class="sxs-lookup"><span data-stu-id="a83a4-144">This IT poster describes the SharePoint Online, Microsoft Azure, and SharePoint on-premises configurations that business decision makers and solutions architects need to know about.</span></span> <br/><br/> <span data-ttu-id="a83a4-145">- **SharePoint Online (SaaS)** – 通过服务型软件 (SaaS) 订阅模型使用 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="a83a4-145">- **SharePoint Online (SaaS)** - Consume SharePoint through a Software as a Service (SaaS) subscription model.</span></span> <br/> <span data-ttu-id="a83a4-146">- **SharePoint 混合** – 按你自己的步调将 SharePoint 网站和应用移到云。</span><span class="sxs-lookup"><span data-stu-id="a83a4-146">- **SharePoint Hybrid** - Move your SharePoint sites and apps to the cloud at your own pace.</span></span> <br/> <span data-ttu-id="a83a4-p105">- **Azure 中的 SharePoint (IaaS)** – 将你的本地环境扩展到 Microsoft Azure 中并在其中部署 SharePoint 2016 服务器。（建议用于高可用性/灾难恢复和开发/测试环境。）</span><span class="sxs-lookup"><span data-stu-id="a83a4-p105">- **SharePoint in Azure (IaaS)** - You extend your on-premises environment into Microsoft Azure and deploy SharePoint 2016 Servers there. (This is recommended for High Availability/Disaster Recovery and dev/test environments.) </span></span><br/> <span data-ttu-id="a83a4-149">- **SharePoint 本地部署** – 规划、部署、维护和自定义你维护的数据中心中的 SharePoint 环境。</span><span class="sxs-lookup"><span data-stu-id="a83a4-149">- **SharePoint On-premises** - You plan, deploy, maintain and customize your SharePoint environment in a datacenter that you maintain.</span></span> <br/> |
   
<span data-ttu-id="a83a4-150"><a name="SP2016_Databases"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-150"><a name="SP2016_Databases"> </a></span></span>
### <a name="sharepoint-server-2016-databases"></a><span data-ttu-id="a83a4-151">SharePoint Server 2016 数据库</span><span class="sxs-lookup"><span data-stu-id="a83a4-151">SharePoint Server 2016 Databases</span></span>

|<span data-ttu-id="a83a4-152">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-152">**Item**</span></span>|<span data-ttu-id="a83a4-153">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-153">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-154">[![SharePoint Server 2016 数据库海报的缩略图](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041)</span><span class="sxs-lookup"><span data-stu-id="a83a4-154">[![Thumbnail for the SharePoint Server 2016 Databases poster](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041)</span></span> <br/> <span data-ttu-id="a83a4-155">[PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=55041)</span><span class="sxs-lookup"><span data-stu-id="a83a4-155">[PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=55041)</span></span> <br/> | <span data-ttu-id="a83a4-p106">此 IT 海报是 SharePoint Server 2016 数据库的快速参考指南。每个数据库都包含以下详细信息：</span><span class="sxs-lookup"><span data-stu-id="a83a4-p106">This IT poster is a quick reference guide for SharePoint Server 2016 databases. Each database has the following details: </span></span><br/><br/> <span data-ttu-id="a83a4-158">- 大小</span><span class="sxs-lookup"><span data-stu-id="a83a4-158">- Size</span></span> <br/> <span data-ttu-id="a83a4-159">- 扩展指南</span><span class="sxs-lookup"><span data-stu-id="a83a4-159">- Scaling guidance</span></span> <br/> <span data-ttu-id="a83a4-160">- I/O 模式</span><span class="sxs-lookup"><span data-stu-id="a83a4-160">- I/O patterns</span></span> <br/> <span data-ttu-id="a83a4-161">- 要求：</span><span class="sxs-lookup"><span data-stu-id="a83a4-161">- Requirements</span></span> <br/><br/>  <span data-ttu-id="a83a4-p107">第一页包含 SharePoint 系统数据库和具有多个数据库的服务应用程序。第二页显示了具有单个数据库的所有服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="a83a4-p107">The first page has the SharePoint system databases and the service applications that have multiple databases. The second page shows all of the service applications that have single databases. </span></span><br/><br/>  <span data-ttu-id="a83a4-164">有关 SharePoint Server 2016 数据库的详细信息，请参阅 [SharePoint Server 2016 中的数据库类型和说明](https://docs.microsoft.com/SharePoint/technical-reference/database-types-and-descriptions)</span><span class="sxs-lookup"><span data-stu-id="a83a4-164">For more information about the SharePoint Server 2016 databases, see [Database types and descriptions in SharePoint Server 2016](https://docs.microsoft.com/SharePoint/technical-reference/database-types-and-descriptions)</span></span> <br/> |
   
<span data-ttu-id="a83a4-165"><a name="SfB2015_ArchModel"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-165"><a name="SfB2015_ArchModel"> </a></span></span>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a><span data-ttu-id="a83a4-166">Microsoft Skype for Business 2015 体系结构模型</span><span class="sxs-lookup"><span data-stu-id="a83a4-166">Microsoft Skype for Business 2015 Architectural Models</span></span>

|<span data-ttu-id="a83a4-167">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-167">**Item**</span></span>|<span data-ttu-id="a83a4-168">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-168">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-169">[![Skype for Business 体系结构模型海报缩略图](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022)</span><span class="sxs-lookup"><span data-stu-id="a83a4-169">[![Thumbnail for the Skype for Business Architectural Models poster](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022)</span></span> <br/> <span data-ttu-id="a83a4-170">[PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=55022)</span><span class="sxs-lookup"><span data-stu-id="a83a4-170">[PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=55022)</span></span> <br/> |<span data-ttu-id="a83a4-171">本海报介绍了业务决策制定者和解决方案架构师需要了解的 Skype for Business Online、本地、混合、云 PBX 及与 Exchange 和 SharePoint 配置的集成。</span><span class="sxs-lookup"><span data-stu-id="a83a4-171">This poster describes the Skype for Business Online, on-premises, hybrid, cloud PBX, and integration with Exchange and SharePoint configurations that business decision makers and solutions architects need to know about.</span></span> <br/><br/> <span data-ttu-id="a83a4-172">它旨在使 IT 专业受众了解使用 Skype for Business Online 和 Skype for Business 本地可以利用的不同的基本体系结构模型。</span><span class="sxs-lookup"><span data-stu-id="a83a4-172">It is intended for the IT Pro audience to raise awareness of the different fundamental architectural models through which Skype for Business Online and Skype for Business on premises can be consumed.</span></span> <br/><br/><span data-ttu-id="a83a4-p108">从最适合组织需求和未来计划的配置开始。根据需要考虑并使用其他配置。例如，你可能要考虑与 Exchange 和 SharePoint 集成，或者考虑与利用 Microsoft 云 PBX 产品/服务的解决方案集成。</span><span class="sxs-lookup"><span data-stu-id="a83a4-p108">Start with whichever configuration best suits your organization's needs and future plans. Consider and use others as needed. For example, you might want to consider integration with Exchange and SharePoint or a solution that takes advantage of Microsoft's Cloud PBX offering.</span></span>  <br/> |
   
## <a name="platform-options-posters"></a><span data-ttu-id="a83a4-176">平台选项海报</span><span class="sxs-lookup"><span data-stu-id="a83a4-176">Platform options posters</span></span>

<span data-ttu-id="a83a4-p109">这些 SharePoint 2013、Exchange 2013 和 Lync 2013 的 IT 海报以大型海报形式提供了一种总体比较各种部署方法的方式。每张海报都提供了所有配置或平台的可用选项列表，并针对每个选项提供了以下信息：</span><span class="sxs-lookup"><span data-stu-id="a83a4-p109">These IT posters for SharePoint 2013, Exchange 2013, and Lync 2013 provide a way to compare the various deployment methods at a single glance in a large poster format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:</span></span>
  
- <span data-ttu-id="a83a4-179">**概述** 平台的简短摘要，包括概念图。</span><span class="sxs-lookup"><span data-stu-id="a83a4-179">**Overview** A brief summary of the platform, including a conceptual diagram.</span></span>
    
- <span data-ttu-id="a83a4-180">**最适用于** 非常适用于特定平台的常见方案。</span><span class="sxs-lookup"><span data-stu-id="a83a4-180">**Best for** Common scenarios that are ideally suited for the particular platform.</span></span>
    
- <span data-ttu-id="a83a4-181">**许可要求** 部署所需的许可证。</span><span class="sxs-lookup"><span data-stu-id="a83a4-181">**License requirements** The licenses you need for deployment.</span></span>
    
- <span data-ttu-id="a83a4-182">**体系结构任务** 架构师需要做出的决定。</span><span class="sxs-lookup"><span data-stu-id="a83a4-182">**Architecture tasks** The decisions you need to make as an architect.</span></span>
    
- <span data-ttu-id="a83a4-183">**IT 专业人员任务或职责** IT 员工需履行的日常职责。</span><span class="sxs-lookup"><span data-stu-id="a83a4-183">**IT Pro tasks or responsibilities** The daily responsibilities that your IT staff needs to plan for.</span></span>
    
<span data-ttu-id="a83a4-184"><a name="SP2013_Options"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-184"><a name="SP2013_Options"> </a></span></span>
## <a name="sharepoint-2013-platform-options"></a><span data-ttu-id="a83a4-185">SharePoint 2013 平台选项</span><span class="sxs-lookup"><span data-stu-id="a83a4-185">SharePoint 2013 Platform Options</span></span>

****

|<span data-ttu-id="a83a4-186">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-186">**Item**</span></span>|<span data-ttu-id="a83a4-187">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-187">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-188">[![SharePoint 2013 平台选项的缩略图](../media/SP-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332)</span><span class="sxs-lookup"><span data-stu-id="a83a4-188">[![Thumbnail image of SharePoint 2013 Platform Options](../media/SP-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332)</span></span> <br/> <span data-ttu-id="a83a4-189">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=40332)</span><span class="sxs-lookup"><span data-stu-id="a83a4-189">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=40332)</span></span> <br/> |<span data-ttu-id="a83a4-190">对于业务决策者 (BDM) 和架构师，此模型显示 SharePoint 2013、Microsoft 365 中的 SharePoint、与 Microsoft 365 的本地混合、Azure 和仅本地部署的平台选项。</span><span class="sxs-lookup"><span data-stu-id="a83a4-190">For business decision makers (BDMs) and architects, this model shows the platform options for SharePoint 2013, SharePoint in Microsoft 365, on-premises hybrid with Microsoft 365, Azure, and on-premises only deployments.</span></span> <span data-ttu-id="a83a4-191">它包括每个体系结构的概述、建议、许可证要求以及每个平台的架构师和 IT 专业人员任务列表。</span><span class="sxs-lookup"><span data-stu-id="a83a4-191">It includes an overview of each architecture, recommendations, license requirements, and lists of architect and IT Pro tasks for each platform.</span></span> <span data-ttu-id="a83a4-192">突出显示了 Azure 上的几种 SharePoint 解决方案。</span><span class="sxs-lookup"><span data-stu-id="a83a4-192">Several SharePoint solutions on Azure are highlighted.</span></span> <br/> |
   
<span data-ttu-id="a83a4-193"><a name="Exch2013_options"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-193"><a name="Exch2013_options"> </a></span></span>
## <a name="exchange-2013-platform-options"></a><span data-ttu-id="a83a4-194">Exchange 2013 平台选项</span><span class="sxs-lookup"><span data-stu-id="a83a4-194">Exchange 2013 Platform Options</span></span>

****

|<span data-ttu-id="a83a4-195">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-195">**Item**</span></span>|<span data-ttu-id="a83a4-196">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-196">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-197">[![Exchange 平台选项的缩略图](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676)</span><span class="sxs-lookup"><span data-stu-id="a83a4-197">[![Thumbnail image of Exchange Platform Options](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676)</span></span> <br/> <span data-ttu-id="a83a4-198">[PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=42676)</span><span class="sxs-lookup"><span data-stu-id="a83a4-198">[PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=42676)</span></span> <br/> |<span data-ttu-id="a83a4-199">对于 BDM 和架构师，此模型介绍了可用的 Exchange 2013 平台选项。</span><span class="sxs-lookup"><span data-stu-id="a83a4-199">For BDMs and architects, this model describes the available platform options for Exchange 2013.</span></span> <span data-ttu-id="a83a4-200">客户可以从使用 Microsoft 365 的 Exchange Online、混合 Exchange、Exchange Server 本地和托管 Exchange 中进行选择。</span><span class="sxs-lookup"><span data-stu-id="a83a4-200">Customers can choose from Exchange Online with Microsoft 365, Hybrid Exchange, Exchange Server on-premises and Hosted Exchange.</span></span> <span data-ttu-id="a83a4-201">此海报包括每个体系结构选项的详细信息，包括每个选项最理想的方案、许可证要求和 IT 专业人员职责。</span><span class="sxs-lookup"><span data-stu-id="a83a4-201">The poster includes details of each architectural option, including the most ideal scenarios for each, the license requirements and IT Pro responsibilities.</span></span> <br/> |
   
<span data-ttu-id="a83a4-202"><a name="Lync2013_Options"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-202"><a name="Lync2013_Options"> </a></span></span>
## <a name="lync-2013-platform-options"></a><span data-ttu-id="a83a4-203">Lync 2013 平台选项</span><span class="sxs-lookup"><span data-stu-id="a83a4-203">Lync 2013 Platform Options</span></span>

****

|<span data-ttu-id="a83a4-204">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-204">**Item**</span></span>|<span data-ttu-id="a83a4-205">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-205">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-206">[![Lync 平台选项的缩略图](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677)</span><span class="sxs-lookup"><span data-stu-id="a83a4-206">[![Thumbnail image of Lync Platform Options](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677)</span></span> <br/> <span data-ttu-id="a83a4-207">[PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=41677)</span><span class="sxs-lookup"><span data-stu-id="a83a4-207">[PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=41677)</span></span> <br/> |<span data-ttu-id="a83a4-208">对于 BDM 和架构师，此模型介绍了可用的 Lync 2013 平台选项。</span><span class="sxs-lookup"><span data-stu-id="a83a4-208">For BDMs and architects, this model describes the available platform options for Lync 2013.</span></span> <span data-ttu-id="a83a4-209">客户可以从使用 Microsoft 365 的 Lync Online、混合 Lync、Lync Server 内部部署和托管 Lync 中进行选择。</span><span class="sxs-lookup"><span data-stu-id="a83a4-209">Customers can choose from Lync Online with Microsoft 365, Hybrid Lync, Lync Server on-premises and Hosted Lync.</span></span> <span data-ttu-id="a83a4-210">IT 海报包括每个体系结构选项的详细信息，包括每个选项最理想的方案、许可证要求和 IT 专业人员职责。</span><span class="sxs-lookup"><span data-stu-id="a83a4-210">The IT poster includes details of each architectural option, including the most ideal scenarios for each, the license requirements and IT Pro responsibilities.</span></span>  <br/> |
   
<span data-ttu-id="a83a4-211"><a name="Lync2013_Options"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-211"><a name="Lync2013_Options"> </a></span></span>
## <a name="sharepoint-in-azure-solutions-posters"></a><span data-ttu-id="a83a4-212">Azure 解决方案中的 SharePoint 海报</span><span class="sxs-lookup"><span data-stu-id="a83a4-212">SharePoint in Azure solutions posters</span></span>

<span data-ttu-id="a83a4-213">这些 IT 海报以大型海报形式说明了使用 SharePoint Server 2013 的基于 Azure 的解决方案。</span><span class="sxs-lookup"><span data-stu-id="a83a4-213">These IT posters show Azure-based solutions using SharePoint Server 2013 in a large poster format.</span></span>
  
<span data-ttu-id="a83a4-214"><a name="Azure_sharepoint2013"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-214"><a name="Azure_sharepoint2013"> </a></span></span>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="a83a4-215">Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="a83a4-215">Internet sites in Microsoft Azure using SharePoint Server 2013</span></span>

****

|<span data-ttu-id="a83a4-216">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-216">**Item**</span></span>|<span data-ttu-id="a83a4-217">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-217">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-218">[![使用 SharePoint 的 Azure 中的 Internet 网站图像](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992)</span><span class="sxs-lookup"><span data-stu-id="a83a4-218">[![Image of Internet sites in Azure using SharePoint](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992)</span></span> <br/> <span data-ttu-id="a83a4-219">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=41992)</span><span class="sxs-lookup"><span data-stu-id="a83a4-219">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=41992)</span></span> <br/> |<span data-ttu-id="a83a4-220">此海报概述了在 Azure 中构建面向 Internet 的网站时所涉及的关键设计活动和推荐体系结构。</span><span class="sxs-lookup"><span data-stu-id="a83a4-220">This poster outlines key design activities and recommended architecture choices for Internet-facing sites in Azure.</span></span>  <br/><br/> <span data-ttu-id="a83a4-221">有关详细信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="a83a4-221">For more information, see the following articles:</span></span>  <br/><br/> <span data-ttu-id="a83a4-222">- [Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)</span><span class="sxs-lookup"><span data-stu-id="a83a4-222">- [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)</span></span> <br/> <span data-ttu-id="a83a4-223">- [用于 SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md)</span><span class="sxs-lookup"><span data-stu-id="a83a4-223">- [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)</span></span> <br/> |
   
<span data-ttu-id="a83a4-224"><a name="DesignSampleInternetSites"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-224"><a name="DesignSampleInternetSites"> </a></span></span>
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="a83a4-225">设计示例：Microsoft Azure 中的 SharePoint 2013 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="a83a4-225">Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

****

|<span data-ttu-id="a83a4-226">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-226">**Item**</span></span>|<span data-ttu-id="a83a4-227">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-227">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-228">[![设计示例图像：Microsoft Azure for SharePoint 2013 中的 Internet 站点](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991)</span><span class="sxs-lookup"><span data-stu-id="a83a4-228">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991)</span></span> <br/> <span data-ttu-id="a83a4-229">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=41991)</span><span class="sxs-lookup"><span data-stu-id="a83a4-229">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=41991)</span></span> <br/> |<span data-ttu-id="a83a4-230">从此设计示例入手，在 Azure 中使用 SharePoint Server 2013 构建你自己的面向 Internet 的网站。</span><span class="sxs-lookup"><span data-stu-id="a83a4-230">Use this design sample as a starting point for your own architecture Internet-facing site in Azure using SharePoint Server 2013.</span></span> <br/><br/> <span data-ttu-id="a83a4-231">有关详细信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="a83a4-231">For more information, see the following articles:</span></span>  <br/><br/> <span data-ttu-id="a83a4-232">- [Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)</span><span class="sxs-lookup"><span data-stu-id="a83a4-232">- [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)</span></span> <br/> <span data-ttu-id="a83a4-233">- [用于 SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md)</span><span class="sxs-lookup"><span data-stu-id="a83a4-233">- [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)</span></span> <br/> |
   
<span data-ttu-id="a83a4-234"><a name="sharepoint_recovery_Azure"> </a></span><span class="sxs-lookup"><span data-stu-id="a83a4-234"><a name="sharepoint_recovery_Azure"> </a></span></span>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="a83a4-235">SharePoint 灾难恢复到 Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a83a4-235">SharePoint Disaster Recovery to Microsoft Azure</span></span>

****

|<span data-ttu-id="a83a4-236">**项**</span><span class="sxs-lookup"><span data-stu-id="a83a4-236">**Item**</span></span>|<span data-ttu-id="a83a4-237">**说明**</span><span class="sxs-lookup"><span data-stu-id="a83a4-237">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a83a4-238">[![到 Azure 的 SharePoint 灾难恢复过程](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993)</span><span class="sxs-lookup"><span data-stu-id="a83a4-238">[![SharePoint disaster-recovery process to Azure](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993)</span></span> <br/> <span data-ttu-id="a83a4-239">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=41993)</span><span class="sxs-lookup"><span data-stu-id="a83a4-239">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=41993)</span></span> <br/> |<span data-ttu-id="a83a4-240">此 IT 海报显示 Azure 中的灾难恢复环境的体系结构原则。</span><span class="sxs-lookup"><span data-stu-id="a83a4-240">This IT poster shows architecture principles for a disaster recovery environment in Azure.</span></span> <br/><br/> <span data-ttu-id="a83a4-241">有关详细信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="a83a4-241">For more information, see the following articles:</span></span>  <br/><br/> <span data-ttu-id="a83a4-242">- [Microsoft Azure 中的 SharePoint Server 2013 灾难恢复](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)</span><span class="sxs-lookup"><span data-stu-id="a83a4-242">- [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)</span></span> <br/> <span data-ttu-id="a83a4-243">- [用于 SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md)</span><span class="sxs-lookup"><span data-stu-id="a83a4-243">- [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)</span></span> <br/> |
   
## <a name="see-also"></a><span data-ttu-id="a83a4-244">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a83a4-244">See Also</span></span>

[<span data-ttu-id="a83a4-245">Microsoft 365 解决方案和体系结构中心</span><span class="sxs-lookup"><span data-stu-id="a83a4-245">Microsoft 365 solution and architecture center</span></span>](../solutions/solution-architecture-center.md)
  
[<span data-ttu-id="a83a4-246">适用于企业架构师的 Microsoft 云插图</span><span class="sxs-lookup"><span data-stu-id="a83a4-246">Microsoft cloud for enterprise architects illustrations</span></span>](../solutions/cloud-architecture-models.md)
  
[<span data-ttu-id="a83a4-247">Microsoft 365 测试实验室指南</span><span class="sxs-lookup"><span data-stu-id="a83a4-247">Microsoft 365 Test Lab Guides</span></span>](m365-enterprise-test-lab-guides.md)
  
[<span data-ttu-id="a83a4-248">混合解决方案</span><span class="sxs-lookup"><span data-stu-id="a83a4-248">Hybrid solutions</span></span>](hybrid-solutions.md)
