---
title: 配置垃圾邮件保护
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 管理员可以了解 Exchange Online Protection (EOP) 中的出站垃圾邮件控件，以及在需要发送大量邮件时应怎么办。
ms.openlocfilehash: 1097b768b955f2fa99c552ceda7564bef33a1aa7
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48202383"
---
# <a name="outbound-spam-protection-in-eop"></a>EOP 中的出站垃圾邮件保护

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


在使用 Exchange Online 或独立 Exchange online Protection 中的邮箱的 Microsoft 365 组织中 (EOP) 不含 Exchange Online 邮箱的组织中，我们会认真管理出站垃圾邮件。 如果一个客户有意或无意地从其组织中发送垃圾邮件，则可能会降低整个服务的声誉，并可能影响其他客户的电子邮件传递。

本主题介绍旨在帮助阻止出站垃圾邮件的控件和通知，以及在需要发送大量邮件的情况下可以执行的操作。

## <a name="what-admins-can-do-to-control-outbound-spam"></a>管理员可控制出站垃圾邮件的操作

- **使用内置通知**：当用户超过了 [服务](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) 或 [出站垃圾邮件策略](configure-the-outbound-spam-policy.md) 的发送限制且被限制为发送电子邮件时，名为 " **用户限制发送电子邮件** " 的默认通知策略将电子邮件通知发送给 **TenantAdmins** (**全局管理员**) 组的成员。 若要配置其他人接收这些通知的人，请参阅 [验证受限制用户的通知设置](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users)。 此外，检测到的默认通知策略已 **超过电子邮件发送限制** ，并且 **检测到可疑电子** 邮件发送模式将电子邮件通知发送给 **TenantAdmins** (**全局管理员**) 组的成员。 若要详细了解警报策略，请参阅[安全与合规中心内的警报策略](../../compliance/alert-policies.md)。

- **查看来自第三方电子邮件提供商的垃圾邮件投诉**：许多电子邮件服务（如 Outlook.com、YAHOO 和 AOL）在其服务中的任何用户将来自 Microsoft 365 的电子邮件标记为垃圾邮件时，将该邮件打包并发回我们进行审阅。 若要了解有关 Outlook.com 的发件人支持的详细信息，请转到 <https://sendersupport.olc.protection.outlook.com/pm/services.aspx> 。

## <a name="how-eop-controls-outbound-spam"></a>EOP 如何控制出站垃圾邮件

- **出站电子邮件流量的划分**：扫描通过该服务发送的每个出站邮件是否有垃圾邮件。 如果将邮件确定为垃圾邮件，则会从名为 " _高风险传递池_" 的次要、不太知名的 IP 地址池进行传递。 有关详细信息，请参阅[出站邮件的高风险传递池](high-risk-delivery-pool-for-outbound-messages.md)。

- **监视源 IP 地址信誉**： Microsoft 365 查询各种第三方 ip 阻止列表。 如果在这些列表中显示了用于出站电子邮件的任何 IP 地址，则会生成警报。 这使我们能够在垃圾邮件导致名誉下降时快速做出反应。 生成警报时，我们将介绍如何将 IP 地址从阻止列表中删除 (delisted) 的内部文档。

- **禁用发送过多垃圾邮件的帐户** <sup>\*</sup> ：即使我们将出站垃圾邮件与高风险传递池进行了隔离，我们也无法允许帐户 (经常发送垃圾邮件的帐户) 。 我们监视发送垃圾邮件的帐户，当它们超过 undisclosed 限制时，将阻止该帐户发送电子邮件。 单个用户和整个租户具有不同的阈值。

- **禁用发送过多电子邮件的帐户太快** <sup>\*</sup> ：除了查找标记为垃圾邮件的邮件的限制之外，还会阻止在邮箱访问总出站邮件限制时阻止帐户，而不考虑出站邮件上的垃圾邮件筛选。 已损坏的帐户可能会发送垃圾邮件筛选器错过的零天 (之前无法识别) 垃圾邮件。 由于很难确定合法的大宗邮件市场活动与垃圾邮件市场活动，因此这些限制有助于最大限度地减少任何潜在的损坏。

<sup>\*</sup> 我们不会公布确切的限制，因此垃圾邮件制造者无法将系统游戏，因此我们可以根据需要增加或减少限制。 这些限制值足够高，以防止一般的业务用户超过它们，并且足够低，以帮助包含垃圾邮件发送者导致的损坏。

## <a name="recommendations-for-customers-who-want-to-send-mass-mailings-through-eop"></a>有关想要通过 EOP 发送大宗邮件的客户的建议

在想要发送大量电子邮件的客户之间，很难对其进行权衡，而是通过较差的收件人获取实践来保护服务免受受损帐户和批量电子邮件发件人的侵袭。 第三方 IP 阻止列表上的 Microsoft 365 电子邮件源登录的成本大于阻止发送过多电子邮件的用户。

如 [Exchange Online 服务说明](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits)中所述，使用 EOP 发送批量电子邮件不是服务的受支持的使用，并且仅在 "最大努力" 的基础上允许。 对于想要发送批量电子邮件的客户，我们建议采用以下解决方案：

- **通过内部部署电子邮件服务器发送批量电子邮件**：这意味着客户将需要维护其自己的电子邮件基础结构以实现大宗邮件。

- **使用第三方批量电子邮件提供程序**：您可以使用多个第三方批量电子邮件解决方案提供程序来发送大宗邮件。 这些公司在与客户合作以确保良好的电子邮件发送实践方面有 vested 的兴趣。

邮件、移动、恶意软件防滥用工作组 (MAAWG) 发布其成员名单的位置 <https://www.maawg.org/about/roster> 。 在列表中有多个批量电子邮件提供商，并且已知是负责 internet 公民。
