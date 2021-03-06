---
title: 管理中心中的 Microsoft 365 报表-SharePoint 网站使用情况
ms.author: pebaum
author: pebaum
manager: pamgreen
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
- SPO160
- BSA160
ms.assetid: 4ecfb843-e5d5-464d-8bf6-7ed512a9b213
description: '获取 SharePoint 网站使用情况报表，了解用户在 SharePoint 网站中存储的文件数、要使用的文件数以及使用的总存储空间。 '
ms.openlocfilehash: 8c2428a49a42a1d259c69297feff13e5c00a9b8e
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "47948852"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>管理中心中的 Microsoft 365 报表-SharePoint 网站使用情况

作为 Microsoft 365 管理员，" **报表** " 仪表板显示组织中各个产品的活动概述。 使用该仪表板，能够更深入细致地了解特定于每个产品的活动。 例如，可以获得有关从 SharePoint 获取的值的高级视图，其中包括用户存储在 SharePoint 网站的总文件数、频繁使用的文件数以及所有这些网站中已使用的存储。 然后，可深入研究 SharePoint 网站使用情况报表，了解所有网站的趋势和其中每个网站的详细信息。 
  
> [!NOTE]
> 您必须是 Microsoft 365 或 Exchange、SharePoint、团队服务、团队通信或 Skype for Business 管理员中的全局管理员、全局读取器或报告阅读器才能查看报告。
在管理中心中，不支持对 GCC 高和 DoD 租户进行 Microsoft 365 报告。
 
## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>如何访问 SharePoint 网站使用情况报表

1. 在管理中心中，转到 " **报告** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">使用情况</a>"。

    
2. 从 " **选择报表** " 下拉下，选择 " **SharePoint** \> **网站使用情况**"。
  
## <a name="interpreting-the-sharepoint-site-usage-report"></a>解读 SharePoint 网站使用情况报表

![SharePoint Site Usage Report](../../media/4f88fb7d-9aa8-470e-9e23-e31caaf77d78.png)
  
|Item|说明|
|:-----|:-----|
|1.  <br/> |可查看" **SharePoint 网站使用情况**"报表，了解过去 7 天、30 天、90 天或 180 天的趋势。 但是，如果您在报告中选择某一天，则表 (7) 将显示从当前日期起的最长28天的数据 (而不是生成报告的日期) 。  <br/> |
|2.  <br/> |每个报告中的数据通常最长为过去24到48小时。 <br/> |
|3.  <br/> |" **网站** " 图表显示网站总数和活动网站数，包括用户已查看、修改、上传、下载、共享或同步文件或在报告期间查看页面的任何网站。  <br/> |
|4.  <br/> |" **文件**"图表显示所有网站中的总文件数和活动文件数。总文件数包括用户文件和系统文件。在指定时间内如果存储、同步、修改或共享了文件，则该文件被视为活动文件。  |
|5.  <br/> |" **存储**"图表显示报告时段内分配和使用存储的趋势。  <br/> |
|6.  <br/> |" **页面**"图表显示在所有网站中查看的页面数。  <br/> |
|7.  <br/> |您可以通过选择图例中的项目来筛选所见图表。 例如，在 " **文件** " 图表上，选择 " **文件** " 或 " **活动文件**"。 在 " **网站** " 图表上，您可以选择 " **网站总数** " 或 " **活动网站**"。 在 " **存储** " 图表上，您可以选择 " **存储已分配** " 或 "存储已 **使用"。** 更改选择不会更改网格表中的信息。  <br/> |
|8.  <br/> | 下表显示按网站的活动细目。  <br/> ![使用率报告的列选项](../../media/sharepointsite-usage.png)           <br/> " **网站 URL**"表示网站的完整 URL。  <br/> " **已删除**"是网站的删除状态。需要至少 7 天时间，网站才会标记为已删除。  <br/> " **网站所有者**"表示网站主要所有者的用户名。  <br/>**网站所有者主要名称** 是网站所有者的电子邮件地址。  <br/> " **上次活动日期(UTC)**"指上次在网站上检测到文件活动或查看了页面的日期。  <br/> " **文件**"表示网站上的文件数。  <br/> "**活动文件**" 表示网站上的活动文件数。<br/> 注意：如果在指定的时间段内删除了文件，报告中显示的活动文件数可能大于网站上的当前文件数。<br/>" **使用的存储空间 (MB)**"表示当前网站上正在使用的存储空间大小。  <br/> " **分配的存储空间 (MB)**"表示分配给该网站的最大存储空间大小。  <br/> " **页面查看次数**"表示在网站上查看页面的次数。  <br/> " **访问的页数**"表示在网站上访问的独特页面数。  <br/> " **根网站模板**"表示用于创建网站的模板。  <br/> 注意：如果要按不同的网站类型筛选数据，则导出数据并使用根 Web 模板列。 <br/>如果组织的策略阻止你查看可识别其中用户信息的报表，你可以更改所有这些报表的隐私设置。 请查看[Microsoft 365 管理中心的活动报告](activity-reports.md)中的 "**如何隐藏用户级别详细信息？** " 一节。  <br/> |
|9.  <br/> |选择 "**管理列** ![ " 管理列 ](../../media/13d2e536-de88-4db3-80c7-7a3a57298eb4.png) 以在报告中添加或删除列。    <br/> |
|10.  <br/> |您还可以通过选择 " **导出**导出" 链接，将报告数据导出到 Excel .csv 文件中 ![ ](../../media/4dc548cc-8061-48d5-9240-6793affca43a.png) 。 此操作可导出所有网站的数据，使你能够对数据进行简单的排序和筛选，以进一步分析数据。 如果网站数量不足 2000，则可在报表中的表格内进行排序和筛选。 如果网站数超过 2000，则需要导出数据才能进行排序和筛选。  <br/> 注意：将数据导出到 Excel 文件时，请注意，生成内容报告的日期会反映在 " **数据的** 依据" 列中的文件中。      <br/>   |
|||
