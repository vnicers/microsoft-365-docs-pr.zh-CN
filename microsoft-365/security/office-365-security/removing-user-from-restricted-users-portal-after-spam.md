---
title: 从“受限的用户”门户中删除被阻止的用户
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.exch.eac.ActionCenter.Restricted.Users.RestrictedUsers
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 712cfcc1-31e8-4e51-8561-b64258a8f1e5
ms.collection:
- M365-security-compliance
description: 管理员可以了解如何在 Office 365 中从“受限的用户”门户中删除用户。 用户之所以被添加到“受限的用户”门户是因为发送出站垃圾邮件，这通常是由于帐户遭入侵所致。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c63d50fcf24e19c6a3265d57ea34fb8ab852c61c
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48201551"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-office-365"></a>在 Office 365 中从“受限的用户”门户中删除被阻止的用户

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


如果某用户超过[服务限制](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options)或[出站垃圾邮件策略](configure-the-outbound-spam-policy.md)中指定的出站发送限制之一，此用户就会被限制发送电子邮件，但仍可以接收电子邮件。

此用户会被添加到安全与合规中心内的“受限用户”门户。 如果此用户试图发送电子邮件，邮件就会以未送达报告（亦称为“NDR”或“退回邮件”）形式返回，并显示错误代码 [5.1.8](https://docs.microsoft.com/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) 和以下文本：

> “你的邮件无法送达，因为系统认为你不是有效的发件人。 这种情形最常见的原因是怀疑你的电子邮件地址正在发送垃圾邮件，且不再允许它发送电子邮件。  请联系电子邮件管理员获取帮助。 远程服务器返回“550 5.1.8 拒绝访问，错误出站发件人”。

管理员可以从安全与合规中心内的“受限的发件人”门户中或使用 Exchange Online PowerShell 删除用户。

## <a name="what-do-you-need-to-know-before-you-begin"></a>开始前，有必要了解什么？

- 安全与合规中心的打开网址为 <https://protection.office.com/>。 若要直接转到“受限的用户”**** 页，请访问 <https://protection.office.com/restrictedusers>。

- 若要连接到 Exchange Online PowerShell，请参阅[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)。

- 你必须首先分配有权限，然后才能执行本主题中的步骤：

  - 若要从“受限的用户”门户中删除用户，你必须是以下任一角色组的成员：

    - [安全和合规中心](permissions-in-the-security-and-compliance-center.md)中的“**组织管理**”或“**安全管理员**”。
    - [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) 中的“**组织管理**”或“**清洁管理**”。

  - 若要以只读方式访问“受限的用户”门户，你必须是以下任一角色组的成员：

    - [安全与合规中心](permissions-in-the-security-and-compliance-center.md)内的“**安全读取者**”。
    - [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) 中的“**仅查看组织管理**”。

- 发件人超过出站电子邮件限制是帐户遭入侵的标志。 请务必先按照必需步骤操作来重新获得对帐户的控制，再从“受限的用户”门户中删除用户。 有关详细信息，请参阅[在 Office 365 中响应遭入侵的电子邮件帐户](responding-to-a-compromised-email-account.md)。

## <a name="use-the-security--compliance-center-to-remove-a-user-from-the-restricted-users-list"></a>使用安全与合规中心从“受限的用户”列表中删除用户

1. 在安全与合规中心内，依次转到“威胁管理”****\>“审阅”****\>“受限的用户”****。

2. 查找并选择要取消阻止的用户。 在“操作”**** 列中，单击“取消阻止”****。

3. 一个飞出窗口将转到有关其发送受限的帐户的详细信息。 应按照建议进行操作，确保在帐户实际遭到破坏的情况下采取适当的措施。 完成后，单击 **“下一步”**。

4. 下一个屏幕包含可帮助防止以后遭到破坏的建议。 启用多重身份验证 (MFA) 和更改密码是一种很好的防御措施。 完成后，单击 **“解锁用户”**。

5. 单击 **“是”** 确认更改。

   > [!NOTE]
   > 移除限制可能需要 30 分钟或更长时间。

## <a name="verify-the-alert-settings-for-restricted-users"></a>验证用于受限的用户的警报设置

默认警报策略“被限制发送电子邮件的用户”**** 会在用户被阻止发送出站邮件时自动通知管理员。 可以验证这些设置，并添加其他要通知的用户。 若要详细了解警报策略，请参阅[安全与合规中心内的警报策略](../../compliance/alert-policies.md)。

> [!IMPORTANT]
> 必须启用审核日志搜索，这样警报才能正常运行。 有关详细信息，请参阅[启用或禁用审核日志搜索](../../compliance/turn-audit-log-search-on-or-off.md)。

1. 在安全与合规中心内，依次转到“警报”****\>“警报策略”****。

2. 查找并选择“被限制发送电子邮件的用户”**** 警报。

3. 在随即显示的浮出控件中，验证或配置下列设置：

   - **状态**：验证此警报是否已启用 ![开关打开](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png)。

   - **电子邮件收件人**：单击“编辑”****，然后在随即显示的“编辑收件人”**** 浮出控件中验证或配置下列设置：

     - **发送电子邮件通知**：验证此复选框是否已选中（“开”****）。

     - **电子邮件收件人**：默认值为“TenantAdmins”****（表示“全局管理员”**** 成员）。 若要添加其他收件人，请单击此框的空白区域。 此时，收件人列表会显示，你可以键入名称来筛选并选择收件人。 若要从此框中删除现有收件人，请单击其名称旁边的 ![“删除”图标](../../media/scc-remove-icon.png)可。

     - **每日通知限制**：默认值为“无限制”****，但你可以选择每日通知数上限。

     完成时，请单击“保存”****。

4. 返回到“被限制发送电子邮件的用户”**** 浮出控件，单击“关闭”****。

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>使用 Exchange Online PowerShell 查看和删除“受限的用户”列表中的用户

若要查看被限制发送电子邮件的用户列表，请运行以下命令：

```powershell
Get-BlockedSenderAddress
```

若要查看特定用户的详细信息，请将 \<emailaddress\> 替换为相应用户的电子邮件地址，并运行以下命令：

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

若要详细了解语法和参数，请参阅 [Get-BlockedSenderAddress](https://docs.microsoft.com/powershell/module/exchange/get-blockedsenderaddress)。

若要从“受限的用户”列表中删除用户，请将 \<emailaddress\> 替换为相应用户的电子邮件地址，并运行以下命令：

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

若要详细了解语法和参数，请参阅 [Remove-BlockedSenderAddress](https://docs.microsoft.com/powershell/module/exchange/remove-blockedsenderaddress)。
