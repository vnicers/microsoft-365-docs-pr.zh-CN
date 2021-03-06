---
title: 威胁资源管理器和实时检测
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 82ac9922-939c-41be-9c8a-7c75b0a4e27d
ms.collection:
- M365-security-compliance
- m365-initiative-defender-office365
description: 了解如何在安全合规中心中使用 Explorer 和实时检测， &amp; 以有效且高效地对威胁进行调查和响应。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 20b13e177a69d981a4c6793d4810256e33158a35
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "48414258"
---
# <a name="threat-explorer-and-real-time-detections"></a>威胁资源管理器和实时检测

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


如果您的组织具有 [office 365 高级威胁防护](office-365-atp.md) (OFFICE 365 ATP) ，并且您拥有 [必要的权限](#required-licenses-and-permissions)，则您可以使用 **资源管理器** 或 **实时检测** (以前的 *实时报告* — [请参阅最近更新](#new-features-in-threat-explorer-and-real-time-detections)！ ) 。 在安全 & 合规性中心中，转到 " **威胁管理**"，然后选择 " **浏览器**" _或_" **实时检测**"。

|在 ATP 计划2中，您将看到：|在 ATP 计划1中，您将看到：|
|---|---|
|![威胁资源管理器](../../media/threatmgmt-explorer.png)|![实时检测](../../media/threatmgmt-realtimedetections.png)|
|

通过资源管理器 (或) 的实时检测功能，您有一个功能强大的报告，使安全操作团队能够有效且高效地调查威胁并对其做出响应。 该报告类似于以下图像：

![转到 "威胁管理 \> 资源管理器"](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

使用此报告，可以执行以下操作：

- [查看 Microsoft 365 安全功能检测到的恶意软件](#see-malware-detected-in-email-by-technology)
- [查看有关仿冒 Url 的数据，然后单击 "判定"](#view-data-about-phishing-urls-and-click-verdict)
- [从资源管理器中的视图启动自动调查和响应过程](#start-automated-investigation-and-response) (ATP 计划2仅) 
- ... [调查恶意电子邮件，](#more-ways-to-use-explorer-or-real-time-detections)等等！

## <a name="experience-improvements-to-threat-explorer-and-real-time-detections"></a>体验资源管理器和 Real-Time 检测的改进

在改进搜寻过程的过程中，我们已对威胁资源管理器和 Real-Time 检测进行了一些更新。 这些是 "体验" 改进，重点是让求职体验更一致。 下面概述了这些更改：

- [时区改进](#timezone-improvements)
- [刷新过程中的更新](#update-in-the-refresh-process)
- [要添加到筛选器的图表深入分析](#chart-drilldown-to-add-to-filters)
- [在产品信息更新中](#in-product-information-updates)

### <a name="timezone-improvements"></a>时区改进

我们将显示门户中的电子邮件记录的时区以及导出的数据的时区。 在电子邮件网格、详细信息浮出控件、电子邮件日程表和类似的电子邮件等体验中，时区将可见，从而使用户可以清楚地了解结果集的时区。

![在资源管理器中查看时区](../../media/TimezoneImprovements.png)

### <a name="update-in-the-refresh-process"></a>刷新过程中的更新

我们已经听说过与自动刷新 (混淆的反馈，例如日期，一旦您更改日期，页面将刷新) 并手动刷新 (其他筛选器) 。 同样，删除筛选器会导致自动刷新，这会导致在修改查询时更改不同的筛选器会导致不一致的搜索体验的情况。 若要解决此情况，我们将迁移到手动筛选机制。
从经验的角度来看，用户可以应用和删除筛选器集 (的不同范围的筛选器，并在日期) ，然后按 "刷新" 按钮，在完成定义查询的情况下筛选结果。 "刷新" 按钮也已更新，可在屏幕上清楚地调用它。 我们还提供了有关此更改的更新工具提示和产品内文档。

![单击 "刷新" 以筛选结果](../../media/ManualRefresh.png)

### <a name="chart-drilldown-to-add-to-filters"></a>要添加到筛选器的图表深入分析

现在，您可以单击 "图表图例" 值，将该值作为筛选器添加。 请注意，您仍必须单击 "刷新" 按钮，才能将结果作为上述更改的一部分进行筛选。

![通过要筛选的图表深入分析](../../media/ChartDrilldown.png)

### <a name="in-product-information-updates"></a>在产品信息更新中

您还应查看产品中的其他详细信息。 例如，网格中的搜索结果总数) ，以及有关标签、错误消息和工具提示的改进，以提供有关筛选器、搜索体验和结果集的详细信息，请参阅下图所示的 (。

![查看产品信息](../../media/ProductInfo.png)

## <a name="extended-capabilities-in-threat-explorer"></a>威胁资源管理器中的扩展功能

### <a name="top-targeted-users"></a>主要目标用户

今天，我们在恶意软件的主要部分中公开主要目标用户的列表， (主要恶意软件系列中的电子邮件) 。 我们将在网络钓鱼和所有电子邮件视图中扩展此视图，在该视图中，您将能够查看前五个目标用户以及每个用户对相应 (视图的尝试次数。例如，对于 "网络钓鱼" 视图，您将能够查看) 的网络钓鱼尝试次数。
您还可以将目标用户列表导出为3000，并将每个电子邮件视图的脱机分析尝试次数导出到最大值为。 此外，选择 "否"。  (例如，下面的13次) 将在威胁 Explorer 中打开筛选视图，以便您可以在电子邮件和威胁中查看该用户的更多详细信息。

![主要目标用户](../../media/Top_Targeted_Users.png)


### <a name="exchange-transport-rules"></a>Exchange 传输规则
作为数据扩充的一部分，您还应该能够查看应用于邮件的所有不同传输规则。 此信息将显示在电子邮件网格视图中 (查看此内容，请在网格中选择 "列选项"，并在 "网格中的列选项" 中添加 Exchange 传输规则) 以及电子邮件中的 "详细信息" 浮出控件。
你将能够同时查看 GUID 以及应用于邮件的传输规则的名称。 此外，您还可以使用传输规则的名称搜索邮件。 这是一个 "包含" 搜索，这意味着您也可以使用部分搜索进行搜索。

#### <a name="important-note"></a>重要说明：
ETR 搜索和名称可用性取决于已分配给你的特定角色。 您需要具有以下角色/权限之一才能查看 ETR 名称和搜索。  如果没有为您分配以下任何角色，您将无法看到传输规则的名称，并使用 ETR 名称搜索邮件的名称。 不过，你将能够在电子邮件详细信息中看到 ETR 标签和 GUID 信息。 有关在电子邮件网格、电子邮件 flyouts、筛选器和导出中查看记录的其他体验不受影响。

- 仅限 EXO-数据丢失防护：全部
- 仅 EXO-O365SupportViewConfig： All
- AAD 或 EXO-安全管理员： All
- AAD 或 EXO-安全读者： All
- 仅限 EXO-传输规则： All
- 仅限 EXO-View-Only 配置： All

在电子邮件网格、详细信息浮出控件和导出的 CSV 中，Etr 显示如下所示的名称/GUID。

![Exchange 传输规则](../../media/ETR_Details.png)

### <a name="inbound-connectors"></a>入站连接器

连接器是一组说明，可用于自定义电子邮件流动到 Microsoft 365 或 Office 365 组织的方式，并能够应用任何安全限制或控件。 在威胁资源管理器中，您现在可以查看与电子邮件相关的连接器，也可以使用连接器名称搜索电子邮件。
对连接器的搜索是 ' 包含 ' 性质的，这意味着分部关键字搜索也应正常工作。
在主网格视图中，"详细信息" 浮出控件和导出的 CSV，连接器以如下所示的名称/GUID 格式显示：

![连接器详细信息](../../media/Connector_Details.png)

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>威胁资源管理器中的新功能和实时检测

威胁资源管理器和实时检测添加了三个新功能：

- [预览电子邮件标头并下载电子邮件正文](#preview-email-header-and-download-email-body)
- [电子邮件日程表](#email-timeline)
- [导出 URL 单击 "数据"](#export-url-click-data)

下面概述了这些新功能。

### <a name="preview-email-header-and-download-email-body"></a>预览电子邮件标头并下载电子邮件正文

在威胁资源管理器中，预览电子邮件标头和下载电子邮件正文的功能是可用的新功能。 管理员将能够分析下载的邮件头/电子邮件是否有威胁。 由于下载电子邮件可能会降低信息的暴露风险，因此此过程由基于角色的访问控制 (RBAC) 控制。 必须向另一个角色 (组中添加一个新的角色、 *预览*，如安全操作或安全管理员) ，以授予在所有电子邮件视图中下载邮件和预览邮件头的能力。

但是，资源管理器 (和实时检测) 也会添加新的新字段，旨在为您提供有关电子邮件土地的更完整的信息。 此更改的目标部分是使搜索更易于进行安全操作人员，但最终结果是了解问题电子邮件的位置。

这是如何完成的？ 传递状态现已分为两列：

- **传递操作** -此电子邮件的状态是什么？
- **送达位置** -此电子邮件的路由结果

传递操作是由于现有策略或检测而导致对电子邮件执行的操作。 以下是电子邮件可能执行的操作：

|附带|Junked|Blocked|代替|
|---|---|---|---|
|电子邮件已传递到用户的收件箱或文件夹，用户可以直接访问它。|电子邮件发送到用户的 "垃圾邮件" 文件夹或 "已删除" 文件夹，并且用户有权访问这些文件夹中的电子邮件。|隔离的、失败的或已丢弃的任何电子邮件。 用户完全无法访问它！|所有恶意附件都被替换为 .txt 文件的电子邮件，以表明附件是恶意的。|

|附带|Junked|Blocked|代替|
|---|---|---|---|
|电子邮件已传递到用户的收件箱或其他文件夹，用户可以直接访问它。|电子邮件发送到用户的 "垃圾邮件" 文件夹或 "已删除" 文件夹，并且用户有权访问这些文件夹中的电子邮件。|隔离的、失败的或已删除的任何电子邮件、以及用户无法访问的任何电子邮件。|任何电子邮件，其中恶意附件被替换为 .txt 文件，以表明这些附件是恶意的。|
|

用户可以看到的内容及其不能执行的操作：

|最终用户可以访问|最终用户无法访问|
|---|---|
|附带|Blocked|
|Junked|代替|

"送达位置" 显示运行送达后的策略和检测结果。 它已链接到传递操作。 添加此字段是为了深入了解在发现问题邮件时所采取的操作。 以下是送达位置的可能值：

- **收件箱或文件夹**：电子邮件位于收件箱中或文件夹 (根据您的电子邮件规则) 。
- **本地或 external**：邮箱在云上不存在，但在本地。
- **垃圾邮件文件夹**：电子邮件位于用户的 "垃圾邮件" 文件夹中。
- "**已删除**邮件" 文件夹：用户的 "已删除邮件" 文件夹中的电子邮件。
- **隔离**：隔离中的电子邮件，并且不在用户的邮箱中。
- **失败**：电子邮件无法访问邮箱。
- 已**删除**：电子邮件在邮件流中的某处丢失。

### <a name="email-timeline"></a>电子邮件日程表

**电子邮件日程表**是另一个新的浏览器功能，旨在提高管理员的求职体验。 它会在随机时减少，因为检查不同位置以尝试了解事件的时间较少。 当电子邮件上的多个事件发生时，或在同一时间结束时，这些事件将显示在 "日程表" 视图中。 事实上，在传递给邮件的某些事件将在 "特殊操作" 列中捕获。 将该邮件的时间线中的信息与邮件投递后执行的特殊操作组合在一起，管理员可以了解其策略的工作方式，即最后路由邮件的位置，在某些情况下，最终评估是什么。

有关调查恶意电子邮件的详细讨论，请参阅 [调查和修正 Office 365 中提供的恶意电子邮件](investigate-malicious-email-that-was-delivered.md)。

### <a name="export-url-click-data"></a>导出 URL 单击 "数据"

此外，您现在可以将 URL 单击的报告导出到 Microsoft Excel 中，以查看其网络消息 ID 和单击结论，从而使了解您的 URL 单击流量更容易的任务。 下面介绍了它的工作原理。 从 "Office 365 快速启动" 上的 "威胁管理" 开始，依次单击 "通过此链"：

**浏览器** \>**查看网络钓鱼** \>**单击** \>**顶部 url 或 URL 顶部单击** \>**单击任意记录以打开 "URL 飞出**"

当您单击列表中的某个 URL 时，将会在弹出面板上看到一个新的 "导出" 按钮。 使用此按钮可以将数据移动到 Excel 电子表格，以便更轻松地进行报告。

您可以在实时检测报告中获取相同的位置，如下所示：

**浏览器** \>**实时检测** \>**查看网络钓鱼** \>**Url** \>**顶部的 url 或顶部的单击** \>**单击任意记录以打开 "URL 飞出** \> "**导航到 "单击" 选项卡。**

> [!TIP]
> 当您通过网络邮件 ID 搜索浏览器或关联的第三方工具时，网络邮件 ID 会将单击映射回特定邮件。 在网络邮件 ID 中搜索将为管理员提供与单击结果关联的特定电子邮件。 在有导出功能的情况下，网络邮件 ID 的关联标识将使分析速度更快、更强大。

![在资源管理器中单击选项卡](../../media/tp_ExportClickResultAndNetworkID.png)

## <a name="see-malware-detected-in-email-by-technology"></a>查看电子邮件中的技术检测到恶意软件

假设您想要查看 Microsoft 365 技术在电子邮件中检测到的恶意软件。 若要执行此操作，请使用资源管理器 (的 [电子邮件 > 恶意软件](threat-explorer-views.md#email--malware) 视图或实时检测) 。

1. 在 "安全性 & 合规性中心 ([https://protection.office.com](https://protection.office.com) ") 中，选择 "**威胁管理**  >  **资源管理器** (" 或 "**实时检测**") 。  (本示例使用 Explorer。 ) 

2. 在 "**视图**" 菜单中，选择 "**电子邮件**  >  **恶意软件**"。

   ![浏览器的视图菜单](../../media/ExplorerViewEmailMalwareMenu.png)

3. 单击 "**发件人**"，然后选择 "**基本**  >  **检测技术**"。

   您的检测技术现在可用作报告的筛选器。

   ![恶意软件检测技术](../../media/ExplorerEmailMalwareDetectionTech.png)

4. 选择一个选项，然后单击 " **刷新** " 按钮以应用该筛选器。

   ![选定的检测技术](../../media/ExplorerEmailMalwareDetectionTechATP.png)

报告将刷新，以显示使用您选择的技术选项在电子邮件中检测到恶意软件的结果。 在这里，你可以进行进一步分析。

## <a name="view-data-about-phishing-urls-and-click-verdict"></a>查看有关仿冒 Url 的数据，然后单击 "判定"

假定您要查看通过电子邮件中的 Url 进行的网络钓鱼尝试，包括允许、阻止和重写的 Url 的列表。 若要标识所单击的 Url，则需要配置 [安全链接](atp-safe-links.md) 。 确保已为单击时的保护设置了 [安全链接策略](set-up-atp-safe-links-policies.md) ，然后单击 "安全链接" 中的 "verdicts" 进行日志记录。

若要查看邮件中的网络钓鱼 Url 并单击网络钓鱼邮件中的 Url，请使用资源管理器 (的 [电子邮件 > 网络钓鱼](threat-explorer-views.md#email--phish) 视图或实时检测) 。

1. 在 "安全性 & 合规性中心 ([https://protection.office.com](https://protection.office.com) ") 中，选择 "**威胁管理**  >  **资源管理器** (" 或 "**实时检测**") 。  (本示例使用 Explorer。 ) 

2. 在 "**视图**" 菜单中，选择 "**电子邮件**  >  **网络钓鱼**"。

   ![浏览器的视图菜单](../../media/ExplorerViewEmailPhishMenu.png)

3. 单击 "**发件人**"，然后选择 " **url**  >  **" 单击 "判定"**。

4. 选择一个或多个选项（如 "已 **阻止** " 和 " **阻止被覆盖**"），然后单击与应用该筛选器的选项位于同一行中的 " **刷新** " 按钮。  (不刷新浏览器窗口。 ) 

   ![Url 并单击 "verdicts"](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)

    报告将刷新，以在报告下的 "URL" 选项卡上显示两个不同的 URL 表：

   - **上面的 url** 是您已筛选出的邮件中包含的 url，并且每个 URL 的电子邮件传递操作都会计数。 在网络钓鱼电子邮件视图中，此列表通常包含合法的 Url。 攻击者在其邮件中加入了好和坏的 Url，以尝试传递它们，但它们会使用户更有趣地单击恶意链接。 Url 表按总电子邮件计数进行排序 (但请注意，此列处于隐藏状态，以简化视图) 。

   - 单击**鼠标顶部**的安全链接包装的 url 已被单击，按总单击次数排序 (此列也不会显示以简化视图) 。 "总计计数依据" 列指示安全链接单击每个单击的 URL 的 "已判定计数"。 在网络钓鱼电子邮件视图中，这些 Url 更常见或恶意 Url，但可能包括不是威胁但位于网络钓鱼邮件中的 Url。 URL 单击未打开的链接将不会显示在此处。

   这两个 URL 表通过传递操作和位置显示网络钓鱼电子邮件中的前几个 url，并且它们显示的 URL 单击已被阻止 (或访问被阻止) 的情况，以便您可以了解用户收到的潜在坏链接和用户的交互情况。 在这里，你可以进行进一步分析。 例如，在图表下方，您可以看到在组织的环境中被阻止的电子邮件中的最高 Url。

   ![阻止的资源管理器 Url](../../media/ExplorerPhishClickVerdictURLs.png)

   选择一个 URL 以查看更详细的信息。

   > [!NOTE]
   > 在 "URL 浮出控件" 对话框中，将删除对电子邮件的筛选，以显示您的环境中 URL 公开的完整视图。 这样，您就可以在资源管理器中筛选出您关注的电子邮件，找出潜在威胁的特定 Url，然后通过 "URL 详细信息") 对话框 (了解您的环境中的 URL 公开情况，而无需向资源管理器视图本身添加 URL 筛选器。

### <a name="interpretation-of-different-click-verdicts"></a>不同的单击 verdicts 的解释

在电子邮件或 URL flyouts 中，点击率和在筛选体验中，你将看到不同的 click 值作为你的求职体验的一部分。 下面是单击 Verdicts 及其解释的可能值：

- **无**：我们无法捕获 URL 的结论。 用户可能已通过 URL 单击。
- **允许**：允许用户导航到 URL。
- 已**阻止**：阻止用户导航到 URL。
- **挂起的判定**：用户显示沙箱挂起页面。
- **被阻止的被覆盖**：阻止用户导航到 URL;但是，用户 overrode 阻止导航到 URL。
- **挂起的判定被绕过**：向用户显示沙箱页面;但是，用户 overrode 页面以导航到 URL。
- **错误**：用户显示错误页。 这也意味着捕获判定的错误。
- **失败**：捕获判定时出现未知异常。 用户可能已通过 URL 单击。

## <a name="review-email-messages-reported-by-users"></a>查看用户报告的电子邮件

假设您想要查看您的组织中的用户使用 [Outlook 和 web 上的 outlook 的报告邮件外接程序](enable-the-report-message-add-in.md)报告为垃圾邮件、非垃圾邮件或网络钓鱼的电子邮件。 为此，请使用浏览器 (的 [电子邮件 > 提交](threat-explorer-views.md#email--submissions) 视图或实时检测) 。

1. 在 "安全性 & 合规性中心 ([https://protection.office.com](https://protection.office.com) ") 中，选择 "**威胁管理**  >  **资源管理器** (" 或 "**实时检测**") 。  (本示例使用 Explorer。 ) 

2. 在 "**视图**" 菜单中，选择 "**电子邮件**  >  **提交**"。

   ![浏览器的视图菜单](../../media/explorer-view-menu-email-user-reported.png)

3. 单击 "**发件人**"，然后选择 "**基本**  >  **报告类型**"。

4. 选择一个选项，如 " **网络钓鱼**"，然后单击 " **刷新** " 按钮。

   ![用户报告的网络钓鱼](../../media/EmailUserReportedReportType.png)

报告将刷新，以显示组织中的人员已报告为网络钓鱼尝试的电子邮件的相关数据。 您可以使用此信息进行进一步分析，如有必要，调整您的 [ATP 反网络钓鱼策略](configure-atp-anti-phishing-policies.md)。

## <a name="start-automated-investigation-and-response"></a>启动自动调查和响应

> [!NOTE]
> **Office 365 ATP 计划 2**和**Office 365 E5**中提供了自动调查和响应功能。

 (NEW！ ) [自动调查和响应](automated-investigation-response-office.md) 可在调查和缓解 cyberattacks 的过程中节省您的安全操作团队时间和精力。 除了配置可触发安全行动手册的警报外，还可以从资源管理器中的视图启动自动调查和响应过程。

有关此操作的详细信息，请参阅 [示例：安全管理员从资源管理器触发调查](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)。

## <a name="more-ways-to-use-explorer-or-real-time-detections"></a>使用资源管理器 (或实时检测) 的更多方法

除了本文中介绍的方案，您还可以使用浏览器 (或实时检测) 更多的报告选项。

- [查找和调查投递的恶意电子邮件](investigate-malicious-email-that-was-delivered.md)
- [威胁防护状态报告](view-email-security-reports.md#threat-protection-status-report)
- [获取有关威胁资源管理器中的视图的概述 (和实时检测) ](threat-explorer-views.md)
- [Microsoft 威胁防护中的自动调查和响应](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

## <a name="required-licenses-and-permissions"></a>所需的许可证和权限

您必须具有 [Office 365 ATP](office-365-atp.md) 才能获取资源管理器或实时检测。

- 资源管理器包含在 Office 365 ATP 计划2中。
- 实时检测报告包含在 Office 365 ATP 计划1中。
- 计划为应受 Office 365 ATP 保护的所有用户分配许可证。  (资源管理器或实时检测显示许可用户的检测数据。 ) 

若要查看和使用资源管理器或实时检测，您必须具有适当的权限，例如，授予安全管理员或安全阅读者的权限。

- 对于安全 &amp; 合规中心，您必须具有以下分配的角色之一：

  - 组织管理
  - 安全管理员 (可以在 Azure Active Directory 管理中心 (中分配此项 [https://aad.portal.azure.com](https://aad.portal.azure.com)) # A3
  - 安全读取者

- 对于 Exchange Online，必须在 Exchange 管理中心 () 或 PowerShell cmdlet 中分配以下角色之一 [https://outlook.office365.com/ecp](https://outlook.office365.com/ecp) (请参阅 [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell)) ：

  - 组织管理
  - 仅限查看组织管理
  - “仅供查看收件人”角色
  - 合规性管理

若要了解有关角色和权限的详细信息，请参阅以下资源：

- [安全 &amp; 合规性中心中的权限](permissions-in-the-security-and-compliance-center.md)
- [Exchange Online 中的功能权限](https://docs.microsoft.com/exchange/permissions-exo/feature-permissions)

## <a name="some-differences-between-threat-explorer-and-real-time-detections"></a>威胁资源管理器和实时检测的区别

- Office 365 ATP 计划1中提供了 **实时检测** 报告，而 **威胁浏览器** 在 office 365 atp 计划2中可用。
- **实时检测**报告允许你实时查看检测。 **威胁资源管理器** 也会执行此功能，但也允许您查看给定攻击的其他详细信息。
- " **所有电子邮件** " 视图在 **威胁资源管理器** 中可用 (并且不在 **实时检测** 报告) 中。
- **威胁资源管理器**中包含更多筛选功能和可用操作。

有关更多详细信息，请参阅 [Office 365 ATP 服务说明：功能在高级威胁防护中的功能可用性 (ATP) 计划](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)。
