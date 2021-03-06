---
title: 调查 Office 365 中提供的恶意电子邮件，查找并调查恶意电子邮件
keywords: TIMailData-内联、安全事件、事件、ATP PowerShell、电子邮件恶意软件、受损用户、电子邮件网络钓鱼、电子邮件恶意软件、阅读电子邮件标头、阅读邮件头、打开电子邮件头、特殊操作
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/09/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 8f54cd33-4af7-4d1b-b800-68f8818e5b2a
ms.collection:
- M365-security-compliance
description: 了解如何使用威胁调查和响应功能查找和调查恶意电子邮件。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 120cc32a2736858a0f0d99ab37f1d51c70a6071c
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48201909"
---
# <a name="investigate-malicious-email-that-was-delivered-in-office-365"></a>调查在 Office 365 中提供的恶意电子邮件

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Office 365 高级威胁防护](office-365-atp.md) 使您能够调查将组织中的人员面临风险的活动，并采取措施保护组织。 例如，如果您是组织的安全团队的一部分，则可以查找并调查已传递的可疑电子邮件。 您可以使用 [威胁资源管理器 (或) 的实时检测 ](threat-explorer.md)来执行此操作。

> [!NOTE]
> 请在 [此处](remediate-malicious-email-delivered-office-365.md)跳转到修补文章。

## <a name="before-you-begin"></a>准备工作

请确保满足以下要求：

- 您的组织具有 [Office 365 高级威胁防护](office-365-atp.md) ，并将 [许可证分配给用户](../../admin/manage/assign-licenses-to-users.md)。

- 为你的组织启用[审核日志记录](../../compliance/turn-audit-log-search-on-or-off.md)。

- 您的组织具有为反垃圾邮件、反恶意软件、反网络钓鱼等定义的策略。 请参阅防御 [Office 365 中的威胁](protect-against-threats.md)。

- 您是全局管理员，或者您具有安全管理员或在安全合规中心中分配的搜索和清除角色 &amp; 。 查看 [安全 &amp; 合规性中心中的权限](permissions-in-the-security-and-compliance-center.md)。 对于某些操作，还必须分配新的预览角色。

### <a name="preview-role-permissions"></a>预览角色权限

若要执行某些操作（如查看邮件头或下载电子邮件内容），您必须具有一个名为 *Preview* 的新角色，并将其添加到另一个相应的角色组。 下表阐明了所需的角色和权限。

****

|活动|角色组|是否需要预览角色？|
|---|---|---|
|使用威胁资源管理器 (和实时检测) 分析威胁 |全局管理员 <br> 安全管理员 <br> 安全读取者|否|
|使用威胁资源管理器 (和实时检测) 查看电子邮件的邮件头以及预览和下载隔离的电子邮件|全局管理员 <br> 安全管理员 <br>安全读取者|否|
|使用威胁浏览器查看邮件头并下载传递给邮箱的电子邮件|全局管理员 <br>安全管理员 <br> 安全读取者 <br> 预览|是|
|

> [!NOTE]
> *预览* 是一个角色，而不是角色组;必须将预览角色添加到 Office 365 的现有角色组中。 全局管理员角色分配有 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)) ，并且安全管理员和安全读者角色在安全 & 合规性中心 () 中分配 [https://protection.office.com](https://protection.office.com) 。 若要了解有关角色和权限的详细信息，请参阅 [Security & 合规性中心中的权限](permissions-in-the-security-and-compliance-center.md)。

## <a name="find-suspicious-email-that-was-delivered"></a>查找已发送的可疑电子邮件

威胁资源管理器是一种功能强大的报告，可用于多种用途，如查找和删除邮件、标识恶意电子邮件发件人的 IP 地址或启动事件以进行进一步调查。 下面的过程重点介绍如何使用资源管理器查找和删除收件人邮箱中的恶意电子邮件。

> [!NOTE]
> 资源管理器中的默认搜索当前不包含 Zapped 项目。  这适用于所有视图，例如恶意软件或网络钓鱼视图。 若要包含 Zapped 项，需要将 "传递操作" 设置为 "已删除的由 ZAP 删除"。 如果包含所有选项，您将看到所有传递操作结果，包括 Zapped 项目。

1. **导航到 "威胁资源管理器**"：转到 [https://protection.office.com](https://protection.office.com) 并使用 Office 365 的工作或学校帐户登录并登录。 这会将您带到安全 &amp; 合规中心。

2. 在左侧导航快速启动栏中，选择 " **威胁管理** \> **资源管理器**"。

    ![具有 "传递操作" 和 "送达位置" 字段的资源管理器。](../../media/ThreatExFields.PNG)

    您可能会注意到 "新建 **特殊操作** " 列。 此功能旨在告诉管理员处理电子邮件的结果。 可以在与**传递操作**和**传递位置**相同的位置访问 "**特殊操作**" 列。 在威胁资源管理器的电子邮件日程表结束时，可能会更新特殊操作，这是旨在使求职体验更适合管理员的新功能。

3. **威胁资源管理器中的视图**：在 " **视图** " 菜单中选择 " **所有电子邮件**"。

    ![威胁资源管理器视图菜单和电子邮件-恶意软件、网络钓鱼诈骗、提交和所有电子邮件选项，也是内容恶意软件。](../../media/tp-InvestigateMalEmail-viewmenu.png)

    *恶意软件*视图当前是默认的，并捕获检测到恶意软件威胁的电子邮件。 *网络钓鱼*视图的工作方式与网络钓鱼的操作方式相同。

    但是， *所有的电子邮件视图都会* 列出组织收到的每封邮件，无论是否检测到威胁。 正如您所想到的，这是大量数据，这就是为什么此视图显示一个要求应用筛选器的占位符。  (此视图仅适用于 ATP P2 客户。 ) 

    "*提交*" 视图显示由管理员或用户提交的、报告给 Microsoft 的所有邮件。

4. **威胁资源管理器中的搜索和筛选**器：筛选器显示在搜索栏中页面的顶部，以帮助管理员进行调查。 请注意，可以同时应用多个筛选器，添加筛选器中的多个逗号分隔值，以缩小搜索范围。 请注意：

    - 筛选器对大多数筛选条件执行完全匹配。
    - Subject 筛选器使用 CONTAINS 查询。
    - URL 筛选器使用或不使用协议 (ex。 https) 。
    - URL 域、URL 路径以及 URL 域和路径筛选器不需要使用协议进行筛选。
    - 每次更改筛选值时，必须单击 "刷新" 图标以获取相关结果。

5. **高级筛选器**：使用这些筛选器，可以生成复杂的查询和筛选数据集。 单击 " *高级" 筛选器* 将打开带选项的浮出控件。

   高级筛选是搜索功能的一个极好的补充。 *收件人*、*发件人*和*发件人域*中引入了 boolean **NOT** filter，以允许管理员通过排除值来进行调查。 此选项显示在 "选择参数不 *包含任何*"。 [！注意]**不**允许管理员排除警报邮箱、默认的答复邮箱的调查，并在管理员搜索特定主题 (主题 = "注意" ) （可将收件人设置为*defaultMail \@ contoso.com）的*情况下很有用。 这是精确的值搜索。

   ![收件人-"不包含任何" 高级筛选器。](../../media/tp-InvestigateMalEmail-AdvancedFilter.png)

   *按小时筛选* 可帮助贵组织的安全团队快速向下钻取。 允许的最短持续时间为30分钟。 如果可以根据时间帧缩小可疑操作 (例如，在3小时前) ，这将限制上下文并帮助查明问题。

   ![按小时筛选选项，以缩小数据安全团队的处理量，并且其最短持续时间为30分钟。](../../media/tp-InvestigateMalEmail-FilterbyHours.png)

6. **威胁资源管理器中的字段**：威胁浏览器会公开更多与安全性相关的邮件信息，例如 *传递操作*、 *传递位置*、 *特殊操作*、 *方向*性、 *覆盖*和 *URL 威胁*。 它还允许组织的安全团队以更高确定性进行调查。

    *传递操作* 是由于现有策略或检测而导致对电子邮件执行的操作。 以下是电子邮件可能执行的操作：

    - **传递** –将电子邮件传递到用户的收件箱或文件夹，用户可以直接访问它。
    - **Junked** (传递到垃圾) –将电子邮件发送到用户的垃圾邮件文件夹或已删除的文件夹，并且用户可以访问其垃圾邮件或已删除文件夹中的电子邮件。
    - 已**阻止**–隔离、失败或丢弃的任何电子邮件。  (完全无法被用户访问。 ) 
    - **已替换** –所有恶意附件替换为 .txt 文件的电子邮件，这些文件的状态为 "恶意附件"。

    **送达位置**：提供了传递位置筛选器，以便帮助管理员了解可疑的恶意邮件结束的位置以及对它执行了哪些操作。 可将生成的数据导出到电子表格。 可能的送达位置为：

    - **收件箱或文件夹** –电子邮件位于收件箱中或特定文件夹中，具体取决于您的电子邮件规则。
    - **本地或外部** –邮箱在云中不存在，但在本地。
    - **垃圾邮件文件夹** –电子邮件位于用户的垃圾邮件文件夹中。
    - "**已删除邮件" 文件夹**–电子邮件位于用户的 "已删除邮件" 文件夹中。
    - **隔离** –隔离的电子邮件，而不是用户邮箱中的电子邮件。
    - **失败** –电子邮件无法访问邮箱。
    - **丢弃** –电子邮件在邮件流中的某处丢失。

    **方向**性：此选项允许安全操作团队按邮件发件人的 "方向" 进行筛选或进行筛选。 方向性值为 *入站*、 *出站*和 *组织内* (对应于从外部传入的邮件、从您的组织中发送或在内部发送到您的组织中的邮件，分别) 。 此信息可帮助安全操作团队发现欺骗和模拟，因为方向性值之间不匹配 (ex。 *入站*) 和发件人的域 (（ *似乎* 是内部域) 将很明显！ 方向性值是相互独立的，并且可以与邮件跟踪不同。 可将结果导出到电子表格。

    **替代**：此筛选器获取邮件的 "详细信息" 选项卡上显示的信息，并使用它来公开允许和阻止邮件的组织或用户策略被 *覆盖*的位置。 此筛选器最重要的一点是，它可以帮助组织的安全团队查看由于配置而传递了多少可疑电子邮件。 这使他们有机会根据需要修改 "允许" 和 "阻止"。 可以将此筛选器的结果集导出到电子表格。

    ****

    |威胁资源管理器替代|它们的含义|
    |---|---|
    |组织策略允许|按组织策略的指示，允许在邮箱中发送邮件。|
    |已被组织策略阻止|邮件被阻止按照组织策略的指示将邮件传递到邮箱。|
    |组织策略阻止的文件扩展名|根据组织策略的指示，文件被阻止传递到邮箱。|
    |用户策略允许|用户策略允许在邮箱中发送邮件。|
    |被用户策略阻止|阻止邮件按照用户策略的指导将邮件传递到邮箱。|
    |

    **Url 威胁**： "url 威胁" 字段已包含在电子邮件的 " *详细信息* " 选项卡上，用于指示 URL 所呈现的威胁。 URL 表现的威胁可以包含*恶意软件*、*网络钓鱼*或*垃圾邮件*，而威胁部分中不会显示*任何**威胁*的 url。

7. **电子邮件日程表视图**：安全操作团队可能需要深入研究电子邮件详细信息，以便进一步调查。 通过电子邮件时间线，管理员可以查看从传递到送达后对电子邮件执行的操作。 若要查看电子邮件日程表，请单击电子邮件的主题，然后单击 "电子邮件日程表"。  (它显示在面板上的其他标题中，如摘要或详细信息。 ) 可以将这些结果导出到电子表格。

    电子邮件日程表将打开，其中显示电子邮件的所有送达和传递后事件的表格。 如果对电子邮件没有进一步的操作，您应该会看到原始传递的单个事件，其中指出了结果（如*网络钓鱼*）的结论，如 "已*阻止*"。 管理员可以导出整个电子邮件时间线，包括选项卡和电子邮件 (的所有详细信息，如 "主题"、"发件人"、"收件人"、"网络" 和 "邮件 ID") 。 电子邮件日程表在随机时减少，因为检查不同位置的时间较少，以尝试了解自电子邮件到达后发生的事件。 当电子邮件上的多个事件发生时，或在同一时间结束时，这些事件将显示在 "日程表" 视图中。

8. **预览/下载**：威胁资源管理器为安全操作团队提供调查可疑电子邮件所需的详细信息。 您的安全操作团队可以执行以下操作之一：

    - [检查传递操作和位置](#check-the-delivery-action-and-location)。

    - [查看你的电子邮件的日程表](#view-the-timeline-of-your-email)。

### <a name="check-the-delivery-action-and-location"></a>检查传递操作和位置

在 [威胁资源管理器中 (和实时检测) ](threat-explorer.md)，现在您有 " **传递操作** " 和 " **传递位置** " 列，而不是以前的 " **传递状态** " 列。 这将导致您的电子邮件位于何处的更完整的图片。 此更改的目标部分是使调查更易于进行安全操作团队，但最终结果是了解问题电子邮件的位置。

传递状态现已分为两列：

- **传递操作** -此电子邮件的状态是什么？

- **送达位置** -此电子邮件的路由结果

传递操作是由于现有策略或检测而导致对电子邮件执行的操作。 以下是电子邮件可能执行的操作：

- **传递** –将电子邮件传递到用户的收件箱或文件夹，用户可以直接访问它。

- **Junked** –将电子邮件发送到用户的 "垃圾邮件" 文件夹或 "已删除" 文件夹，并且用户可以访问其 "垃圾邮件" 或 "已删除" 文件夹中的电子邮件。

- 已**阻止**–隔离、失败或丢弃的任何电子邮件。  (完全无法被用户访问。 ) 

- **已替换** –所有恶意附件都被替换为 .txt 文件的电子邮件，这些文件的状态为 "恶意附件"。

"送达位置" 显示运行送达后的策略和检测结果。 它已链接到传递操作。 添加此字段是为了深入了解在发现问题邮件时所采取的操作。 以下是送达位置的可能值：

- **收件箱或文件夹** –电子邮件位于收件箱中或文件夹 (根据您的电子邮件规则) 。

- **本地或外部** –邮箱在云上不存在，但在本地。

- **垃圾邮件文件夹** –电子邮件位于用户的垃圾邮件文件夹中。

- "**已删除邮件" 文件夹**–电子邮件位于用户的 "已删除邮件" 文件夹中。

- **隔离** –隔离的电子邮件，而不是用户邮箱中的电子邮件。

- **失败** –电子邮件无法访问邮箱。

- **丢弃** –电子邮件在邮件流中的某个位置丢失。

### <a name="view-the-timeline-of-your-email"></a>查看你的电子邮件的日程表

**电子邮件日程表** 是威胁资源管理器中的一个字段，可使您的安全操作团队更轻松地使用查找。 当电子邮件上的多个事件同时发生或在同一时间结束时，这些事件将显示在 "日程表" 视图中。 在 " **特殊操作** " 列中捕获到电子邮件的传递后发生的一些事件。 将电子邮件的时间线中的信息与在传递后进行的任何特殊操作组合在一起，管理员可以深入了解策略和威胁处理 (例如邮件路由的位置，在某些情况下，) 最终评估。

> [!IMPORTANT]
> 请在 [此处](remediate-malicious-email-delivered-office-365.md)跳转到修正主题。

## <a name="related-topics"></a>相关主题

[修正在 Office 365 中传递的恶意电子邮件](remediate-malicious-email-delivered-office-365.md)

[Office 365 高级威胁防护](office-365-ti.md)

[防御 Office 365 中的威胁](protect-against-threats.md)

[查看 Office 365 高级威胁防护报告](view-reports-for-atp.md)
