---
title: 自动调查和响应 (空中) 概述
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365-initiative-defender-office365
keywords: 自动事件响应、调查、修正和威胁防护
ms.date: 09/29/2020
description: 在 Microsoft Defender for Office 365 中获取自动调查和响应功能的概述
ms.custom:
- air
- seo-marvel-mar2020
ms.openlocfilehash: 850291966c2f2da51782d8e70de23ff4f06d6136
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "48413958"
---
# <a name="an-overview-of-automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Microsoft Defender for Office 365 中的自动调查和响应 (空中) 的概述

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


随着安全警报的触发，安全操作团队可查看这些警报并采取措施来保护您的组织。 有时，安全操作团队可能会受到触发的警报量的感觉的不知所措。 Microsoft Defender for Office 365 中的自动调查和响应 (空中) 功能可提供帮助。 

通过 AIR，您的安全操作团队可以更高效地运行。 空中功能包括自动调查过程，以响应目前存在的已知威胁。 适当的补救措施等待批准，使安全操作团队能够响应检测到的威胁。 

本文提供了空中的概述。 当您准备好开始使用 AIR 时，请参阅 [自动调查和响应威胁](office-365-air.md)。

## <a name="at-a-high-level"></a>高级别

随着警报的触发，安全行动手册将生效。 根据具体情况，可以开始执行 [自动调查过程](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) 。 在进行自动调查的过程中和之后，建议采取 [补救措施](air-remediation-actions.md) 。 在 Microsoft Defender for Office 365 中不会自动执行任何操作。 您的安全操作团队将进行审核，然后 [批准或拒绝每个修正操作](air-review-approve-pending-completed-actions.md)。 当调查中的所有操作都被批准或拒绝时，调查完成。 所有这些活动都会在 Microsoft 365 安全中心 () 中进行跟踪和查看 [https://security.microsoft.com](https://security.microsoft.com) 。  (若要了解详细信息，请参阅 [查看调查) 的详细信息](air-view-investigation-results.md#view-details-of-an-investigation) 。

以下各节提供了有关警报、安全行动手册和操作中的示例的更多详细信息。

## <a name="alerts"></a>警报

[警报](../../compliance/alert-policies.md#viewing-alerts) 表示用于事件响应的安全操作团队工作流的触发器。 确定要调查的正确通知集的优先级，同时确保没有威胁是 unaddressed 的挑战。 在手动对通知进行调查时，安全操作团队必须对实体（如内容、设备和用户）进行 (（如内容、设备和用户）进行寻找和关联，) 威胁的风险。 此类任务和工作流可能非常耗时，并涉及多个工具和系统。 通过让关键安全和威胁管理警报自动触发安全响应行动手册，可以通过空气、调查和响应安全事件进行自动化。 

目前，对于气流，从下列类型的警报策略生成的警报将自动调查：  

- 检测到潜在的恶意 URL 单击
- 用户报告为网络钓鱼的电子邮件`*`
- 包含在传递后删除的恶意软件的电子邮件`*`
- 包含投递后删除的网络钓鱼 Url 的电子邮件`*`
- 检测到可疑的电子邮件发送模式
- 限制用户发送电子邮件
- 管理员触发了电子邮件的手动调查`*`

> [!NOTE]
> 标有星号 () 的警报在 `*` Microsoft 365 安全中心中的相应警报策略中被分配了一个 *信息性* 严重性，电子邮件通知处于关闭状态。 可以通过 [报警策略配置](../../compliance/alert-policies.md#alert-policy-settings)启用电子邮件通知。 

若要查看警报，请在安全 & 合规性中心中，选择 "**通知**" "  >  **查看警报**"。 选择一个警报以查看其详细信息，然后在那里使用 " **查看调查** " 链接转到相应的 [调查](air-view-investigation-results.md#investigation-graph)。  

> [!NOTE]
> 默认情况下，通知视图中隐藏信息警报。 若要查看它们，请更改警报筛选以包含信息警报。

如果您的组织通过警报管理系统、服务管理系统或安全信息和事件管理 (SIEM) 系统管理安全警报，则可以通过电子邮件通知或通过 [Office 365 管理活动 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)向该系统发送通知。 通过电子邮件或 API 的调查通知通知包含访问 Microsoft 365 安全中心中的警报的链接，使分配的安全管理员能够快速导航到调查。

![链接到调查的警报](../../media/air-alerts-page-details.png) 

## <a name="security-playbooks"></a>安全行动手册

安全行动手册是后端策略，是 Microsoft Defender for Office 365 和 Microsoft 威胁防护中的自动化的核心。 空中提供的安全行动手册基于常见的实际安全方案，并根据安全操作团队的反馈进行开发。 当您的组织中触发特定警报时，将自动启动安全行动手册。 通知触发后，相关的行动手册将由自动调查和响应系统运行。 调查根据特定警报的操作手册分析预警的步骤，查看所有关联的元数据 (包括电子邮件、用户、主题、发件人等 ) 。 根据调查行动手册的发现，AIR 推荐了组织的安全团队可采取的一组操作来控制和缓解威胁。 

你将使用空中获取的安全行动手册旨在解决组织在当今的电子邮件中遇到的最常见威胁。 它们基于安全操作和事件响应团队的输入，包括帮助保护 Microsoft 和客户资产的人员。

- 用户报告的网络钓鱼邮件
- URL-单击 "判定更改"
- 检测到投递后 (恶意软件 ZAP) 
- 网络钓鱼的检测到传送后的 ZAP (网络钓鱼 ZAP) 
- 用户报告为已损坏 
- 管理员从资源管理器恶意软件、网络钓鱼或所有电子邮件视图触发的手动电子邮件调查 () 

在完成后，将发布更多行动手册和行动手册更新。 访问 [Microsoft 365 路线图](https://www.microsoft.com/microsoft-365/roadmap) 以查看计划和即将推出的其他内容。

### <a name="playbooks-include-investigation-and-recommendations"></a>行动手册包括调查和建议

在空中，每个安全行动手册包括： 

- 对电子邮件的实体进行根调查 (如文件、Url、收件人、IP 地址等) 
- 对组织收到的类似电子邮件的进一步搜寻 
- 确定并关联其他潜在威胁所需的步骤，以及 
- 建议的威胁补救措施。

每个高级步骤都包含多个执行的子步骤，以提供对威胁的深入、详细和详尽的响应。

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>示例：用户报告的网络钓鱼邮件启动调查行动手册

假定组织中的某个用户收到电子邮件，而他们认为是网络钓鱼尝试。 经过培训的用户报告此类邮件，使用 [报告邮件加载项](enable-the-report-message-add-in.md) 将其发送到 Microsoft 进行分析。 提交也会发送到您的系统，并在 " **提交** " 视图中显示 (以前称为 **用户报告** 的视图) 。 此外，用户报告的消息现在会触发基于系统的信息警报，这将自动启动调查行动手册。

在根调查阶段，会评估电子邮件的各个方面。 这些方面包括：

- 确定它可能属于哪种类型的威胁;
- 发件人数;
- 电子邮件的发送位置 (发送基础结构) ;
- 是否已传递或阻止电子邮件的其他实例;
- 我们分析家中的一种评估;
- 电子邮件是否与任何已知的市场活动相关联;
- 等等。

根调查完成后，行动手册提供了要对其关联的原始电子邮件和实体执行的建议操作的列表。
  
接下来，执行以下几个威胁调查和搜寻步骤：

- 类似的电子邮件通过电子邮件群集搜索进行标识。
- 该信号与其他平台（如 [Microsoft Defender For Endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)）共享。
- 确定是否有用户通过可疑电子邮件中的任何恶意链接单击过。
- 在 Exchange Online Protection ([EOP](exchange-online-protection-overview.md)) 和 Office 365 高级威胁防护 ([ATP](office-365-atp.md)) 中进行检查，以查看用户是否报告了任何其他类似的消息。
- 将执行检查以查看是否已泄露用户。 此检查跨 Office 365、 [Microsoft 云应用安全性](https://docs.microsoft.com/cloud-app-security)和 [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)之间的信号，关联任何相关的用户活动异常。

在搜寻阶段，会为各种搜寻步骤分配风险和威胁。 

修正是行动手册的最后阶段。 在此阶段中，将根据调查和搜寻阶段采取补救措施。 

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>示例：安全管理员触发来自威胁资源管理器的调查

除了由警报触发的自动调查之外，组织的安全操作团队还可以通过 [威胁资源管理器](threat-explorer.md)中的视图触发自动调查。  此调查还会创建一个警报，以便 Microsoft Defender 事件和外部 SIEM 工具可以查看是否触发了此调查。 

例如，假设您正在使用资源管理器中的 **恶意软件** 视图。 使用图表下方的选项卡，选择 " **电子邮件** " 选项卡。如果选择列表中的一个或多个项目，则 " **+ 动作** " 按钮将激活。 

![包含所选邮件的资源管理器](../../media/Explorer-Malware-Email-ActionsInvestigate.png)

使用 " **操作** " 菜单，可以选择 **触发调查**。

![选定邮件的 "操作" 菜单](../../media/explorer-malwareview-selectedemails-actions.jpg)

与由警报触发的行动手册类似，通过资源管理器中的视图触发的自动调查包括根调查、标识和关联威胁的步骤以及缓解这些威胁的建议操作。

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>示例：安全操作团队使用 Office 365 管理活动 API 将空中与其 SIEM 集成

Microsoft Defender for Office 365 中的空中功能包括 [报告 & 详细信息](air-view-investigation-results.md) ，安全操作团队可以使用这些信息来监视和解决威胁。 但您也可以将空中功能与其他解决方案集成。 示例包括安全信息和事件管理 (SIEM) 系统、案例管理系统或自定义报告解决方案。 这些类型的集成可以通过使用 [Office 365 管理活动 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)来实现。 

例如，最近，一个组织为其安全操作团队设置了一种方法，以查看用户报告的已由 AIR 处理的网络钓鱼警报。 其解决方案将相关警报与组织的 SIEM 服务器及其事例管理系统集成在一起。 该解决方案大大减少了误报的数量，使其安全操作团队能够将他们的时间和精力集中在真正的威胁上。 若要了解有关此自定义解决方案的详细信息，请参阅 [技术社区博客：使用 Office 365 ATP 和 O365 管理 API 提高 SOC 的有效性](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185)。

## <a name="next-steps"></a>后续步骤

- [开始使用空中](office-365-air.md)

- [访问 Microsoft 365 路线图以查看已计划和即将发布的内容](https://www.microsoft.com/microsoft-365/roadmap?filters=)

- [了解 Microsoft 365 Defender 中的其他自动化调查和响应功能](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir?view=o365-worldwide&preserve-view=true)
