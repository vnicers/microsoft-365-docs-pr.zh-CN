---
title: 将就地保留置于 Exchange Online 中的软删除邮箱上
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid: ''
ms.assetid: 421f72bd-dd43-4be1-82f5-0ae9ac43bd00
ms.custom:
- seo-marvel-apr2020
description: 了解如何为软删除邮箱创建就地保留，以将其变为非活动邮箱并保留其内容。
ms.openlocfilehash: 4dcd6539519675094da9a05c7701b9f8511ce9a1
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818861"
---
# <a name="put-an-in-place-hold-on-a-soft-deleted-mailbox-in-exchange-online"></a>将就地保留置于 Exchange Online 中的软删除邮箱上

了解如何为软删除邮箱创建就地保留，以将其变为非活动邮箱并保留其内容。然后可以使用 Microsoft 电子数据展示工具来搜索非活动邮箱。

> [!IMPORTANT]
> 随着我们继续投资保留邮箱内容的不同方式，我们宣布在 Exchange 管理中心（EAC）中停用就地保留。 从2020年6月1日开始，你将无法在 Exchange Online 中创建新的就地保留。 但您仍可以在 EAC 中管理就地保留或通过在 Exchange Online PowerShell 中使用**new-mailboxsearch** cmdlet 来管理。 但是，从2020年10月1日开始，你将无法管理就地保留。 您只能将其从 EAC 中删除或使用**new-mailboxsearch** cmdlet。 有关停用就地保留的详细信息，请参阅[旧版电子数据展示工具的退休](legacy-ediscovery-retirement.md)。
  
You might have a situation where a person has left your organization, and their corresponding user account and mailbox were deleted. Afterwards, you realize there's information in the mailbox that needs to be preserved. What can you do? If the deleted mailbox retention period hasn't expired, you can put an In-Place Hold on the deleted mailbox (called a  soft-deleted mailbox ) and make it an inactive mailbox. An  *inactive mailbox*  is used to preserve a former employee's email after he or she leaves your organization. The contents of an inactive mailbox are preserved for the duration of the In-Place Hold that was is placed on the soft-deleted mailbox when it was made inactive. 在邮箱变为非活动状态后，可以使用 Exchange Online 中的就地电子数据展示、安全性 & 合规性中心中的内容搜索或 SharePoint Online 中的电子数据展示中心来搜索邮箱。 
  
> [!NOTE]
> 在 Exchange Online 中，软删除邮箱是指已删除但可以在特定保留期内恢复的邮箱。Exchange Online 中的软删除邮箱保留期为 30 天。这意味着该邮箱可以在删除后 30 天内进行恢复（或变为非活动邮箱）。30 天后，软删除邮箱将标记为永久删除并且无法恢复或变为非活动邮箱。 
  
## <a name="requirements-for-in-place-holds"></a>就地保留的要求

- 您必须在 Windows PowerShell 中使用**new-mailboxsearch** cmdlet 在软删除的邮箱上放置就地保留。 不能使用 SharePoint Online 中的 Exchange 管理中心 (EAC) 或电子数据展示中心。 

- 若要了解如何使用 Windows PowerShell 连接到 Exchange Online，请参阅[连接到 Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554)。

- 运行以下命令获取组织中软删除邮箱的标识信息。 

  ```powershell
  Get-Mailbox -SoftDeletedMailbox | FL Name,WhenSoftDeleted,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

- 有关非活动邮箱的详细信息，请参阅[Office 365 中的非活动邮箱概述](inactive-mailboxes-in-office-365.md)。

## <a name="put-an-in-place-hold-on-a-soft-deleted-mailbox-to-make-it-an-inactive-mailbox"></a>将就地保留置于软删除邮箱以使其变为非活动邮箱

使用**new-mailboxsearch** cmdlet 可将软删除的邮箱设置为非活动邮箱。 有关详细信息，请参阅 [New-MailboxSearch](https://technet.microsoft.com/library/74303b47-bb49-407c-a43b-590356eae35c.aspx)。
  
1. 创建包含软删除邮箱的属性的变量。

   ```powershell
   $SoftDeletedMailbox = Get-Mailbox -SoftDeletedMailbox -Identity <identity of soft-deleted mailbox>
   ```

    > [!IMPORTANT]
    > 在上一个命令中，使用**DistinguishedName**或**ExchangeGuid**属性的值来标识软删除的邮箱。 这些属性对于组织中的每个邮箱都是唯一的，但活动邮箱和软删除邮箱可能具有相同的主 SMTP 地址。 
  
2. 创建就地保留并将其置于软删除邮箱上。在此示例中，未指定保留持续时间。这意味着项目将被无限期保留或一直保留到将该保留从非活动邮箱中删除为止。

   ```powershell
   New-MailboxSearch -Name "InactiveMailboxHold" -SourceMailboxes $SoftDeletedMailbox.DistinguishedName -InPlaceHoldEnabled $true
    ```

   还可以在创建就地保留时指定保留持续时间。此示例保留非活动邮箱中的项目近 7 年。

   ```powershell
   New-MailboxSearch -Name "InactiveMailboxHold" -SourceMailboxes $SoftDeletedMailbox.DistinguishedName -InPlaceHoldEnabled $true -ItemHoldPeriod 2777
   ```

3. 一段时间后，运行下列命令之一，验证软删除邮箱是否为非活动邮箱。

   ```powershell
   Get-Mailbox -InactiveMailboxOnly
   ```

    或
    
   ```powershell
   Get-Mailbox -InactiveMailboxOnly -Identity $SoftDeletedMailbox.DistinguishedName  | FL IsInactiveMailbox
   ```

## <a name="more-information"></a>详细信息

在将软删除邮箱变为非活动邮箱后，有多种方法可以管理该邮箱。有关详细信息，请参阅：
  
- [更改非活动邮箱的保留期](change-the-hold-duration-for-an-inactive-mailbox.md)

- [恢复非活动邮箱](recover-an-inactive-mailbox.md)

- [还原非活动邮箱](restore-an-inactive-mailbox.md)

- [删除非活动邮箱](delete-an-inactive-mailbox.md)（通过删除保留）
