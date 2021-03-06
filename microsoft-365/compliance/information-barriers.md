---
title: 了解信息障碍
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
localization_priority: None
description: 使用信息障碍以确保在组织内使用 Microsoft 团队进行通信合规性。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7b223de8eba68d49a8cc0c90239305eb05bb1090
ms.sourcegitcommit: 5e40c760c1af2a4cc6d85cb782b17f5c979677c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2020
ms.locfileid: "48379193"
---
# <a name="information-barriers"></a>信息屏障

Microsoft 云服务包括强大的通信和协作功能。 但假设您要限制两个组之间的通信和协作，以避免组织中发生利益冲突。 或者，您可能希望限制组织内的某些人之间的通信和协作，以保护内部信息。 Microsoft 365 支持跨组和组织进行通信和协作，因此有一种方法可以在必要时限制特定用户组之间的通信和协作？ 通过信息障碍，你可以！ 

在 Microsoft 团队、SharePoint Online 和 OneDrive for Business 中现支持信息障碍。 假定你的 [订阅](#required-licenses-and-permissions) 包括信息障碍，合规性管理员或信息屏障管理员可以定义策略以允许或阻止 Microsoft 团队中的用户组之间的通信。 信息屏障策略可用于以下情况：

- 第一天的用户 trader 组不应与市场营销团队进行通信或与之共享文件
- 从事机密公司信息的财务人员不应与组织内的特定组进行通信或共享文件
- 具有贸易秘密材料的内部团队不应与组织内特定组中的人员进行呼叫或联机聊天
- 研究团队应仅与产品开发团队进行在线通话或聊天

> [!IMPORTANT]
> 信息障碍 ***仅支持*** 双向限制。 一种方法限制（如 "营销"）可以与日贸易贸易通信，但 ***不支持将***day 商贸与营销进行通信。

对于所有这些示例方案 (更) ，可以将信息屏障策略定义为阻止或允许在 Microsoft 团队中进行通信。 此类策略可以阻止用户不应对其进行呼叫或聊天，或使用户只能与 Microsoft 团队中的特定组进行通信。 在信息屏障策略生效时，只要这些策略涵盖的用户尝试与 Microsoft 团队中的其他人通信，就会执行检查以阻止 (或允许) 通信 (如信息屏障策略) 所定义。 若要了解有关信息障碍的用户体验方面的详细信息，请参阅 [Microsoft 团队中的信息障碍](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams)。

> [!IMPORTANT]
> 目前，信息障碍不适用于电子邮件通信。 此外，信息障碍独立于 [合规性边界](set-up-compliance-boundaries.md)。<p>在定义和应用信息屏障策略之前，请确保您的组织没有有效的 [Exchange 通讯簿策略](https://docs.microsoft.com/exchange/address-books/address-book-policies/address-book-policies) 。  (信息障碍基于通讯簿策略。 )  

## <a name="what-happens-with-information-barriers"></a>信息障碍发生的情况

在信息屏障策略就绪后，不应与其他特定用户进行通信或共享文件的人员将无法找到、选择、聊天或呼叫这些用户。 通过信息障碍，检查措施可防止未经授权的通信。

最初，信息障碍仅适用于 Microsoft 团队聊天和频道。 在 Microsoft 团队中，信息障碍策略决定并阻止以下类型的未经授权的通信：

- 搜索用户
- 向团队添加成员
- 启动与某人的聊天会话
- 启动群聊天
- 邀请某人加入会议
- 共享屏幕
- 发出呼叫
- 与其他用户共享文件
- 通过共享链接访问文件 

如果涉及的人员包含在信息屏障策略中以阻止活动，则无法继续。 此外，在信息屏障策略中包括的每个人都可以阻止与 Microsoft 团队中的其他人通信。 当受信息障碍策略影响的人员是同一个团队或组聊天的一部分时，他们可能会从这些聊天会话中删除，并且可能不允许与组进行进一步通信。

若要了解有关信息障碍的用户体验方面的详细信息，请参阅 [Microsoft 团队中的信息障碍](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams)。

## <a name="required-licenses-and-permissions"></a>所需的许可证和权限

信息屏障现在正在推出，并包含在订阅中，如：

- Microsoft 365 E5/A5
- Office 365 E5/A5
- Office 365 高级合规版
- Microsoft 365 合规性 E5/A5
- Microsoft 365 内幕风险管理

有关更多详细信息，请参阅 [合规性解决方案](https://products.office.com/business/security-and-compliance/compliance-solutions)。

若要 [定义或编辑信息障碍策略](information-barriers-policies.md)，您必须分配有下列角色之一：

- Microsoft 365 全局管理员
- Office 365 全局管理员
- 合规性管理员
- 向 IB 合规性管理 (这是一个新角色！ ) 

 (若要了解有关角色和权限的详细信息，请参阅 [Office 365 安全 & 合规中心中的权限](../security/office-365-security/protect-against-threats.md)) 

您必须熟悉 PowerShell cmdlet，才能定义、验证或编辑信息屏障策略。 尽管我们在操作 [方法一文](information-barriers-policies.md)中提供了几个 PowerShell cmdlet 示例，但你需要了解组织的其他详细信息，如参数。

## <a name="next-steps"></a>后续步骤

- [了解有关 Microsoft 团队中的信息障碍的详细信息](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams)
- [请参阅可用于信息屏障策略的属性](information-barriers-attributes.md)
- [定义信息障碍策略](information-barriers-policies.md)
- [编辑 (或删除) 信息屏障策略](information-barriers-edit-segments-policies.md)
- [了解有关 SharePoint Online 中的信息障碍的详细信息](https://docs.microsoft.com/sharepoint/information-barriers)
- [了解有关 OneDrive for Business 中的信息障碍的详细信息](https://docs.microsoft.com/onedrive/information-barriers)