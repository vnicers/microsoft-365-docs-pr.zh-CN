---
title: 从核心电子数据展示事例导出和下载内容
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: 本文介绍如何从核心电子数据展示事例导出和下载内容。
ms.openlocfilehash: e0d4315c48a0d0878b8052265ff8663cd1987169
ms.sourcegitcommit: bd51f626f0c7788c2a3cf89deee25264659aebd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2020
ms.locfileid: "43551367"
---
# <a name="export-content-from-a-core-ediscovery-case"></a>从核心电子数据展示事例导出内容

成功运行搜索后，您可以导出搜索结果。 当您导出搜索结果时，邮箱项目会下载到 PST 文件或单个邮件中。 当您从 SharePoint 和 OneDrive for business 网站导出内容时，会导出本机 Office 文档和其他文档的副本。 包含有关每个导出的每个项目的信息的结果 .csv 文件和包含有关每个搜索结果的信息的清单文件（以 XML 格式）也将被导出。
  
您可以导出[与事例关联的单个搜索](#export-the-results-of-a-single-search)的结果，也可以导出[与事例相关联的多个搜索](#export-the-results-of-multiple-searches)的结果。
  
## <a name="export-the-results-of-a-single-search"></a>导出单个搜索的结果

1. 转到[https://compliance.microsoft.com](https://compliance.microsoft.com)并使用已为其分配了相应电子数据展示权限的用户帐户的凭据登录。

2. 在 Microsoft 365 合规性中心的左侧导航窗格中，单击 "**全部显示**"，然后单击 "**电子数据展示 > 核心**"。

3. 在 "**核心电子数据展示**" 页上，选择要从中导出搜索结果的事例，然后单击 "**打开事例**"。

4. 在该案例的**主页**上，单击 "**搜索**" 选项卡。

5. 在案例的搜索列表中，单击要从中导出搜索结果的搜索，然后单击浮出控件上的 "**导出结果**"。

    将显示 "**导出结果**" 页。 

    !["导出结果" 页](../media/ab0bb46d-310b-4374-8644-717146df6676.png)
  
    导出与核心电子数据展示事例关联的搜索结果的工作流与导出 "**内容搜索**" 页上的搜索的搜索结果相同。 有关分步说明，请参阅[导出内容搜索结果](export-search-results.md)。

    > [!NOTE]
    > 当您导出搜索结果时，您可以选择启用重复数据删除，以便即使在搜索的邮箱中找到同一邮件的多个实例，也只导出电子邮件的一个副本。 有关重复数据删除和标识重复项目的详细信息，请参阅[电子数据展示搜索结果中的重复数据](de-duplication-in-ediscovery-search-results.md)消除。

    在您开始导出后，搜索结果将准备好下载，这意味着它们会被上载到 Microsoft 云中的 Microsoft 提供的 Azure 存储位置。
  
6. 单击 "**导出**" 选项卡以显示事例的导出作业列表。
  
    您可能需要单击 "**刷新**" 以更新导出作业的列表，以便显示您创建的导出作业。 导出作业与对应的搜索具有相同的名称，并将 **_Export**追加到搜索名称。

7. 单击您创建的导出作业以在弹出页面上显示状态信息。 此信息包括已转移到 Azure 存储位置的项目的百分比。

8. 在转移所有项目后，单击 "**下载结果**" 将搜索结果下载到您的本地计算机。 有关下载搜索结果的详细信息，请参阅[Export content search results](export-search-results.md#step-2-download-the-search-results)中的步骤2

## <a name="export-the-results-of-multiple-searches"></a>导出多个搜索的结果

作为导出与事例相关联的单个搜索结果的替代方法，可以在单个导出作业中从同一事例导出多个搜索的结果。 导出多个搜索的结果比一次性导出搜索结果更快、更轻松。
  
> [!NOTE]
> 如果其中一个搜索配置为在保留时搜索位置，则不能导出多个搜索的结果。

1. 转到[https://compliance.microsoft.com](https://compliance.microsoft.com)并使用已为其分配了相应电子数据展示权限的用户帐户的凭据登录。

2. 在 Microsoft 365 合规性中心的左侧导航窗格中，单击 "**全部显示**"，然后单击 "**电子数据展示 > 核心**"。

3. 在 "**核心电子数据展示**" 页上，选择要从中导出搜索结果的事例，然后单击 "**打开事例**"。

4. 在该案例的**主页**上，单击 "**搜索**" 选项卡。
    
5. 在案例的搜索列表中，选中要从中导出搜索结果的两个或多个搜索旁边的复选框。 

   将显示 "**批量操作**" 弹出页面。 

    ![在 "批量操作" 页面上，单击 "导出结果"](../media/f34e3707-a9c1-494f-91a4-da1165aa730a.png)
  
6. 单击 "**导出结果**"。

   将显示 "**导出结果**" 页。 

    !["导出结果" 页](../media/ab0bb46d-310b-4374-8644-717146df6676.png)
  
    在这种情况下，导出与核心电子数据展示事例相关联的多个搜索结果的工作流与导出单个搜索的搜索结果相同。 请参阅上一节中的步骤5。

### <a name="more-information-about-exporting-the-results-of-multiple-searches"></a>有关导出多个搜索结果的详细信息

- 当您导出多个搜索的结果时，将使用**OR**运算符组合来自所有搜索的搜索查询，然后启动组合搜索。 组合搜索的估计结果将显示在所选导出作业的飞出页面中。 然后，将搜索结果复制到 Microsoft 云中的 Azure 存储位置。 复制作业的状态也会显示在弹出页面上。 如前所述，在复制所有搜索结果后，可以将其下载到本地计算机。

- 要导出的所有搜索的查询中的最大关键字数为500。 这与单个搜索的限制相同。 这是因为导出作业通过使用**OR**运算符组合了所有搜索查询。 如果超过此限制，将返回错误。 在这种情况下，您必须从较少的搜索中导出结果或简化要导出的原始搜索的搜索查询。

- 导出的搜索结果按在中找到该项目的内容位置进行组织。 这意味着导出结果中的内容位置可能会有不同搜索返回的项目。 例如，如果选择在一个 PST 文件中为每个邮箱导出电子邮件，则 PST 文件可能会有来自多个搜索的结果。

- 如果您导出的多个搜索返回相同内容位置中的同一电子邮件项目或文档，将只导出该项目的一个副本。

- 在创建多个搜索后，不能编辑该导出。 例如，不能在导出作业中添加或删除搜索。 您必须创建导出作业来更改要导出的搜索结果。 在创建导出作业之后，您只可以将结果下载到计算机，重新启动导出，或删除导出作业。

- 如果重新启动导出，则对构成导出作业的搜索的查询所做的任何更改都不会影响检索到的搜索结果。 当您重新启动导出时，在创建导出作业时运行的相同组合搜索查询作业将会重新运行。

- 此外，如果您重新启动导出，则复制到 Azure 存储位置的搜索结果会覆盖以前的结果。 以前复制的结果将不能下载。

- 在高级电子数据展示（经典）中准备多个搜索搜索的结果不可用。 您只能在高级电子数据展示（经典）中准备单次搜索的结果以进行分析。
