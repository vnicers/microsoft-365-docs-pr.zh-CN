---
title: "\"管理中心\" 中的 Microsoft 365 报表-表单活动"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
audience: Admin
ms.topic: article
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
description: 了解如何使用 microsoft 365 管理中心中的 Microsoft 365 报告仪表板获取 Microsoft Forms 活动报告。
ms.openlocfilehash: 78b09edfbfeb83c056af16787085b7c4cfe93fc6
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "47949200"
---
# <a name="microsoft-365-reports-in-the-admin-center---forms-activity"></a>"管理中心" 中的 Microsoft 365 报表-表单活动

Microsoft 365 " **报告** " 仪表板显示组织中各产品的活动概述。 它让你能够深入研究各产品级报表，以便更细致地了解每个产品内的活动。 请查看[报表概述主题](activity-reports.md)。
  
例如，您可以通过查看用户与表单的交互信息来了解使用 Microsoft 表单的每个用户的活动。 它还可帮助您了解所创建的窗体的数量和用户响应的窗体数量，以了解协作级别。
  
> [!NOTE]
> 您必须是 Microsoft 365 或 Exchange、SharePoint、团队服务、团队通信或 Skype for Business 管理员中的全局管理员、全局读取器或报告阅读器才能查看报告。 

## <a name="how-to-get-to-the-forms-activity-report"></a>如何访问表单活动报告

1. 在管理中心，转到“**报表**”\> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">使用情况</a>页面。

    
2. 从 " **选择报表** " 下拉下，选择 " **表单** \> **活动**"。

## <a name="interpret-the-forms-activity-report"></a>解释表单活动报告

您可以通过查看 " **活动** " 和 " **用户** " 图表，获取用户的表单活动的视图。 

![表单活动报告](../../media/adminformsactivity.png)

|Item|说明|
|:-----|:-----|
|1.  <br/> |可以查看 " **表单活动** " 报表，了解过去7天、30天、90天或180天的趋势。 但是，如果您在报告中选择某一天，则表 (7) 将显示从当前日期起的最长28天的数据 (而不是生成报告的日期) 。  <br/> |
|2.  <br/> |每个报告中的数据通常最长为过去24到48小时。  <br/> |
|3.  <br/> |[！注意] [！注意] [！注意] **用户** 视图可帮助您了解活动表单用户数的趋势。 如果用户已在表单 (创建、编辑、查看等 ) 或在特定时间段内对表单进行了响应，则将该用户视为活动用户。  <br/> |
|4.  <br/> |" **活动** " 视图可帮助您了解活动用户数的趋势。 如果用户在特定期间执行了文件活动（如保存、同步、修改或共享）或访问了页面，则视该用户为活跃用户。<br/> 注意：一个活动可针对单个表单多次发生，但只计为一个活动窗体。 例如，您可以创建一个窗体，并在指定的时间段内继续多次编辑同一窗体，但它只计为一个单个窗体。 但是，如果用户提交同一窗体的多个响应，则每个响应仍为单个响应，因此将计数多次。 <br/> |
|5.<br/>|在 " **用户** " 图表上，Y 轴表示唯一用户数。 X 轴是唯一用户处于活动状态的日期。 图例为：<br/><br/>**设计器** 意味着用户已创建或编辑窗体。<br/>**响应** 程序意味着用户已向表单 (s) 提交了响应。<br/> **总用户** 是指公司中已成为设计者或响应者的任何人。<br/><br/> 在 " **活动** " 图表中，Y 轴表示唯一窗体或响应的计数。 X 轴是表单或响应活动发生的日期。 图例为：<br/><br/>**创建的表单** 是用户创建的独特表单的计数。<br/> **已登录响应** 组织中的用户已收到已登录响应的计数。<br/> **匿名响应** 是组织中的用户已收到的匿名响应数。<br/><br/>|
|6.<br/>|您可以通过选择图例中的项目来筛选您在图表上看到的系列。 例如，在 "用户" 图表上，选择 "设计器"、"响应者" 或 "总用户"，仅查看与每个用户相关的信息。 更改此选择不会更改下方的网格表中的信息。|
|7.<br/>|该表显示了每个用户级别的活动细目。图例为：<br/><br/>**Username** 是在 Microsoft Forms 上执行活动的用户的电子邮件地址。<br/>**上次活动日期 (UTC) ** 是用户在所选日期范围内执行表单活动的最晚日期。 要查看指定日期发生的活动，请直接在图表中选择该日期。<br/><br/>此操作将筛选表，以便仅为在特定日期执行活动的用户显示文件活动数据。<br/><br/>**创建的表单数** 是用户创建的表单数。<br/> "**表单响应数**" 是用户已提交响应的表单数。|
|8.<br/>|选择 " **管理列** " 图标可在报表中添加或删除列。|
|9.<br/>|您还可以通过选择 " **导出** " 链接将报告数据导出到 Excel .csv 文件中。 这将导出所有用户的数据，并使您能够执行简单的聚合、排序和筛选以进行进一步分析。 如果用户少于100，则可以在报表本身的表中对表进行排序和筛选。 如果用户数超过100，则需要导出数据，才能对其进行筛选和排序。|