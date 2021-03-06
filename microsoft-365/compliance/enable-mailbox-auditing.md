---
title: 管理邮箱审核
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: aaca8987-5b62-458b-9882-c28476a66918
ms.custom: seo-marvel-apr2020
description: 默认情况下，邮箱审核日志记录在 Microsoft 365 (中已启用，默认情况下也称为默认邮箱审核或邮箱审核) 。 这意味着邮箱所有者、代理人和管理员执行的某些操作将自动记录在邮箱审核日志中，在此日志中可以搜索在邮箱上执行的活动。
ms.openlocfilehash: 7c0a4417496bcf18362dbcfe53b751c549ef98b9
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2020
ms.locfileid: "47545838"
---
# <a name="manage-mailbox-auditing"></a>管理邮箱审核

从2019年1月起，Microsoft 将默认为所有组织启用邮箱审核日志记录。 这意味着邮箱所有者、代理人和管理员执行的某些操作将会自动记录，当您在邮箱审核日志中搜索时，相应的邮箱审核记录将可用。 默认情况下，邮箱审核启用前，您必须为组织中的每个用户邮箱手动启用它。

以下是邮箱审核在默认情况下的一些优点：

- 当您创建新邮箱时，将自动启用审核。 您无需为新用户手动启用它。

- 您无需管理已审核的邮箱操作。 默认情况下，会为每个登录类型审核一组预定义的邮箱操作 (Admin、Delegate 和 Owner) 。

- 当 Microsoft 发布新的邮箱操作时 (尤其有助于保护组织和帮助您进行法庭) 调查的操作。该操作将自动添加到默认情况下被审核的邮箱操作的列表中。 这意味着您无需监视对邮箱添加的新操作。

- 您的组织中有一致的邮箱审核策略 (，因为您正在审核对所有邮箱) 的相同操作。

> [!NOTE]
>* 有关默认情况下的邮箱审核发布的重要事项是：不需要执行任何操作来管理邮箱审核。 但是，若要了解详细信息，自定义邮箱审核的默认设置，或将其全部关闭，本主题可为你有所帮助。
>- 默认情况下，在安全 & 合规中心或通过 Office 365 管理活动 API 中的审核日志搜索中仅提供用于 E5 用户的邮箱审核事件。 有关详细信息，请参阅本主题中的 [详细信息](#more-information) 部分。

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>默认情况下验证邮箱审核启用

若要验证您的组织的默认邮箱审核是否已启用，请在 [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)中运行以下命令：

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

值 **为 False** 表示对组织启用默认情况下邮箱审核。 默认情况下，此设置将覆盖特定邮箱上的邮箱审核设置。 例如，如果邮箱审核对邮箱禁用 (则邮箱) 上的 *AuditEnabled* 属性为 **False** 时，仍会为邮箱审核默认邮箱操作，因为默认情况下邮箱审核对组织启用。

若要将特定邮箱的邮箱审核功能保持为禁用状态，请为邮箱所有者和已委派邮箱访问权限的其他用户配置邮箱审核旁路。 有关详细信息，请参阅本主题中的 [绕过邮箱审核日志记录](#bypass-mailbox-audit-logging) 一节。

> [!NOTE]
> 如果为组织启用了默认情况下的邮箱审核，则受影响的邮箱的 *AuditEnabled* 属性不会从 **False** 更改为 **True**。 换言之，默认情况下邮箱审核将忽略邮箱上的 *AuditEnabled* 属性。

## <a name="supported-mailbox-types"></a>支持的邮箱类型

下表显示了默认情况下邮箱审核当前支持的邮箱类型：

|**邮箱类型**|**支持**|**不支持**|
|:---------|:---------:|:---------:|
|用户邮箱|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
|共享邮箱|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
|Microsoft 365 组邮箱|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
|资源邮箱||![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|公用文件夹邮箱||![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|

## <a name="logon-types-and-mailbox-actions"></a>登录类型和邮箱操作

登录类型对对邮箱执行了审核操作的用户进行分类。 以下列表介绍了邮箱审核日志记录中使用的登录类型：

- **Owner**：邮箱所有者 (与邮箱) 相关联的帐户。

- **委派**：

  - 向另一个邮箱分配了 SendAs、SendOnBehalf 或 FullAccess 权限的用户。

  - 为用户的邮箱分配了 FullAccess 权限的管理员。

- **管理员**：

  - 使用以下其中一种 Microsoft 电子数据展示工具搜索邮箱：

    - 合规性中心中的内容搜索。

    - 合规中心中的电子数据展示或高级电子数据展示。

    - Exchange Online 中的就地电子数据展示。

  - 可以使用 Microsoft Exchange Server MAPI 编辑器访问邮箱。

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>用户邮箱和共享邮箱的邮箱操作

下表介绍了可用于用户邮箱和共享邮箱的邮箱审核日志记录中的邮箱操作。

- 复选标记 ( ![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)) 指示可以为登录类型记录邮箱操作 (并不是所有的登录类型都可用于) 所有的操作。

- <sup>\*</sup>在复选标记指示邮箱操作在默认情况下被记录为登录类型的星号 ( ) 。

- 请记住，对邮箱具有完全访问权限的管理员被视为代理。

|**邮箱操作**|**说明**|**管理员**|**委派用户**|**所有者**|
|:---------|:---------|:---------:|:---------:|:---------:|
|**AddFolderPermissions**|**注意**：虽然此值被接受为邮箱操作，但它已包含在 **UpdateFolderPermissions** 操作中，并且不会单独审核。 换言之，请勿使用此值。||||
|**ApplyRecord**|项目标记为记录。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**复制**|已将某个邮件复制到另一个文件夹。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|||
|**创建**|在邮箱中的 "日历"、"联系人"、"便笺" 或 "任务" 文件夹中创建了一个项目 (例如，新的会议请求将) 中创建。 不会审核邮件的创建、发送或接收。 也不会审核邮箱文件夹的创建。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**默认**||![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**FolderBind**|已访问某个邮箱文件夹。 当管理员或委派打开邮箱时，也会记录此操作。 <br/><br/> **注意**：代理执行的文件夹绑定操作的审核记录已合并。 在24小时内为单个文件夹访问生成一个审核记录。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
|**HardDelete**|已将某个邮件从"已恢复邮件"文件夹中清除。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**MailItemsAccessed**|邮件数据由邮件协议和客户端访问。 此值仅适用于 E5 或 E5 合规性附加订阅用户。 有关详细信息，请参阅 [对调查的关键事件的访问权限](advanced-audit.md#access-to-crucial-events-for-investigations)。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**MailboxLogin**|用户已登录到其邮箱。 |||![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**MessageBind**|在预览窗格中查看或由管理员打开邮件。 **注意**：虽然此值被接受为邮箱操作，但不再记录这些操作。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|||
|**ModifyFolderPermissions**|**注意**：虽然此值被接受为邮箱操作，但它已包含在 **UpdateFolderPermissions** 操作中，并且不会单独审核。 换言之，请勿使用此值。||||
|**移动**|已将某个邮件移至另一个文件夹。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**MoveToDeletedItems**|已删除邮件，并已将其移动到“已删除邮件”文件夹。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**RecordDelete**| (移到 "可恢复的项目" 文件夹) ，并将标记为记录的项目软删除。 标记为记录的项目无法永久删除 (从 "可恢复的项目" 文件夹) 清除。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**RemoveFolderPermissions**|**注意**：虽然此值被接受为邮箱操作，但它已包含在 **UpdateFolderPermissions** 操作中，并且不会单独审核。 换言之，请勿使用此值。||||
|**SendAs**|已使用“发送方式”权限发送邮件。 这表示另一个用户发送了邮件，而该邮件就好像来自于邮箱所有者。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>||
|**SendOnBehalf**|已使用“代表发送”权限发送邮件。 这表示另一个用户代表邮箱所有者发送了邮件。 邮件将向收件人说明发送此邮件时使用的身份及实际发送者。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>||
|**SoftDelete**|已永久删除或已从“已删除邮件”文件夹中删除邮件。 软删除的项目将移动到 "可恢复的项目" 文件夹中。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**更新**|已更改邮件或其属性。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|向邮箱分配了日历委派。 日历代理为同一组织内的其他人授予管理邮箱所有者日历的权限。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>||![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**UpdateComplianceTag**|将不同的保留标签应用于邮件项目 (项目只能为其分配一个保留标签) 。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**UpdateFolderPermissions**|文件夹权限已更改。 文件夹权限用于控制组织中的哪些用户可以访问邮箱中的文件夹以及位于这些文件夹中的邮件。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**UpdateInboxRules**|添加、删除或更改了收件箱规则。 "收件箱" 规则用于根据指定的条件处理用户收件箱中的邮件，并在满足规则条件时采取操作，例如将邮件移动到指定文件夹或删除邮件。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|

> [!IMPORTANT]
> 如果在组织中启用了默认情况下邮箱审核启用 *前* 对任何登录类型进行的邮箱操作的自定义审核，则这些自定义设置将保留在邮箱中，并且不会被默认邮箱操作覆盖，如本节中所述。 若要将审核邮箱操作还原为其默认值 (可随时) 执行的操作，请参阅本主题后面的 [还原默认邮箱操作](#restore-the-default-mailbox-actions) 部分。

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>适用于 Microsoft 365 组邮箱的邮箱操作

邮箱审核默认情况下会将邮箱审核日志记录提供给 Microsoft 365 组邮箱，但不能自定义要记录的内容 (您无法添加或删除为任何登录类型) 记录的邮箱操作。

下表介绍了默认情况下为每个登录类型在 Microsoft 365 组邮箱上记录的邮箱操作。

请记住，对 Microsoft 365 组邮箱具有完全访问权限的管理员被视为代理。

|**邮箱操作**|**说明**|**管理员**|**委派用户**|**所有者**|
|:---------|:---------|:---------:|:---------:|:---------:|
|**创建**|创建日历项目。 不会审核邮件的创建、发送或接收。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>||
|**HardDelete**|已将某个邮件从"已恢复邮件"文件夹中清除。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**MoveToDeletedItems**|已删除邮件，并已将其移动到“已删除邮件”文件夹。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**SendAs**|已使用“发送方式”权限发送邮件。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>||
|**SendOnBehalf**|已使用“代表发送”权限发送邮件。 |![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>||
|**SoftDelete**|已永久删除或已从“已删除邮件”文件夹中删除邮件。 软删除的项目将移动到 "可恢复的项目" 文件夹中。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|
|**更新**|已更改邮件或其属性。|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|![复选标记](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)<sup>\*</sup>|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>验证是否为每个登录类型记录了默认邮箱操作

默认情况之下的邮箱审核将新的 *DefaultAuditSet* 属性添加到所有邮箱。 此属性的值指示是否在邮箱上审核 (由 Microsoft) 管理的默认邮箱操作。

若要在用户邮箱或共享邮箱上显示值，请将 \<MailboxIdentity\> 名称、别名、电子邮件地址或用户主体名称替换为邮箱的名称、别名、电子邮件地址或用户主体名称 (用户名) 并在 Exchange Online PowerShell 中运行以下命令：

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

若要在 Microsoft 365 组邮箱中显示值，请将 \<MailboxIdentity\> 其替换为共享邮箱的名称、别名或电子邮件地址，并在 Exchange Online PowerShell 中运行以下命令：

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

该值 `Admin, Delegate, Owner` 指示：

- 审核所有三种登录类型的默认邮箱操作。 这是你在 Microsoft 365 组邮箱中看到的唯一值。

- *管理员尚未*更改用户邮箱或共享邮箱上任何登录类型的已审核邮箱操作。 注释默认情况下，这是在组织中最初启用邮箱审核之后的默认状态。

如果管理员已更改了通过在**设置邮箱**) cmdlet 上使用*AuditAdmin*、 *AuditDelegate*或*AuditOwner*参数对登录类型审核的邮箱操作 (，则该属性值将有所不同。

例如， `Owner` 用户邮箱或共享邮箱上的 *DefaultAuditSet* 属性的值表示：

- 审核邮箱所有者的默认邮箱操作。

- 已 `Delegate` `Admin` 从默认操作更改了和登录类型的已审核邮箱操作。

*DefaultAuditSet*属性的空值表示已在用户邮箱或共享邮箱上更改了所有三种登录类型的邮箱操作。

有关详细信息，请参阅本主题中的 " [更改或还原在默认情况下记录的邮箱操作](#change-or-restore-mailbox-actions-logged-by-default) " 部分

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>显示正在登录邮箱的邮箱操作

若要查看当前登录用户邮箱或共享邮箱的邮箱操作，请将 \<MailboxIdentity\> 名称、别名、电子邮件地址或用户主体名称替换为邮箱的名称、别名、电子邮件地址或用户主体名称 (用户名) ，并在 Exchange Online PowerShell 中运行以下一个或多个命令。

> [!NOTE]
> 虽然您可以将此 `-GroupMailbox` 开关添加到 Microsoft 365 组邮箱的以下 **Get 邮箱** 命令中，但不相信返回的值。 本主题前面的 " [microsoft 365 组邮箱的邮箱操作](#mailbox-actions-for-microsoft-365-group-mailboxes) " 一节中介绍了为 Microsoft 365 组邮箱审核的默认和静态邮箱操作。

#### <a name="owner-actions"></a>所有者操作

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditOwner
```

#### <a name="delegate-actions"></a>委派操作

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditDelegate
```

#### <a name="admin-actions"></a>管理操作

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditAdmin
```

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>更改或还原默认情况下记录的邮箱操作

如前所述，默认情况下启用邮箱审核的主要好处之一是：无需管理已审核的邮箱操作。 Microsoft 为你执行此操作，我们将在默认情况下自动添加要审核的新邮箱操作。

但是，您的组织可能需要审核用户邮箱和共享邮箱的一组不同的邮箱操作。 本部分中的过程介绍如何更改针对每种登录类型进行审核的邮箱操作，以及如何还原为 Microsoft 托管的默认操作。

> [!IMPORTANT]
> 如果使用以下过程自定义登录用户邮箱或共享邮箱的邮箱操作，则任何由 Microsoft 发布的新默认邮箱操作都不会在这些邮箱上自动进行审核。 您需要将任何新邮箱操作手动添加到自定义的操作列表中。

### <a name="change-the-mailbox-actions-to-audit"></a>更改要审核的邮箱操作

您可以使用 AuditAdmin **cmdlet 上的** *AuditAdmin*、 *AuditDelegate*或*AuditOwner*参数更改为用户邮箱和共享 (邮箱审核的邮箱操作。不能) 自定义对 Microsoft 365 组邮箱的审核操作。

您可以使用两种不同的方法来指定邮箱操作：

- 使用以下语法*替换* (覆盖) 现有邮箱操作： `action1,action2,...actionN` 。

- 使用以下语法在不影响其他现有值的情况下*添加或删除*邮箱操作： `@{Add="action1","action2",..."actionN"}` 或 `@{Remove="action1","action2",..."actionN"}` 。

此示例通过使用 SoftDelete 和 HardDelete 覆盖默认操作来更改名为 "Gabriela Laureano" 的邮箱的管理员邮箱操作。

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

本示例将 Mailboxlogin 该值 owner 操作添加到邮箱 laura@contoso.onmicrosoft.com。

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

本示例删除工作组讨论邮箱的 MoveToDeletedItems 委派操作。

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

无论使用哪种方法，自定义对用户邮箱或共享邮箱的审核邮箱操作都有以下结果：

- 对于您自定义的登录类型，已审核的邮箱操作不再由 Microsoft 进行管理。

- 您自定义的登录类型不再像[前面所述](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type)的那样显示在邮箱的*DefaultAuditSet*属性值中。

### <a name="restore-the-default-mailbox-actions"></a>还原默认邮箱操作

如果自定义了在用户邮箱或共享邮箱上审核的邮箱操作，则可以使用以下语法还原一种或多种登录类型的默认邮箱操作：

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

可以指定用逗号分隔的多个 *DefaultAuditSet* 值

**注意**：以下过程不适用于 Microsoft 365 组邮箱 (它们仅限于 [此处](#mailbox-actions-for-microsoft-365-group-mailboxes) 所述的默认操作) 。

本示例将还原邮箱 mark@contoso.onmicrosoft.com 上所有登录类型的默认审核邮箱操作。

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

本示例将还原邮箱 chris@contoso.onmicrosoft.com 上的管理员登录类型的默认审核邮箱操作，但保留代理和所有者登录类型的自定义已审核邮箱操作。

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

为登录类型还原默认的已审核邮箱操作的结果如下：

- 邮箱操作的当前列表将替换为登录类型的默认邮箱操作。

- 由 Microsoft 发布的任何新邮箱操作都会自动添加到登录类型的已审核操作列表中。

- 邮箱的 *DefaultAuditSet* 属性值将更新，以包含已还原的登录类型。

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>为你的组织默认关闭邮箱审核

您可以通过在 Exchange Online PowerShell 中运行以下命令，在默认情况下为整个组织关闭邮箱审核：

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

默认情况下，禁用邮箱审核具有以下结果：

- 对您的组织禁用邮箱审核。

- 从您禁用邮箱审核时，默认情况下不会审核任何邮箱操作，即使在邮箱上启用了审核 (邮箱上的 *AuditEnabled* 属性为 **True**) 。

- 邮箱审核没有为新邮箱启用，并将新邮箱或现有邮箱的 *AuditEnabled* 属性设置为 **True** 将被忽略。

- 将忽略使用 **get-mailboxauditbypassassociation** cmdlet) 配置的任何邮箱审核绕过关联设置 (。

- 现有邮箱审核记录将一直保留，直到记录的审核日志期限过期为止。

### <a name="turn-on-mailbox-auditing-on-by-default"></a>默认情况下启用邮箱审核

若要为您的组织重新启用邮箱审核，请在 Exchange Online PowerShell 中运行以下命令：

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>绕过邮箱审核日志记录

目前，在组织中启用默认邮箱审核时，不能禁用特定邮箱的邮箱审核。 例如，将 *AuditEnabled* 邮箱属性设置为 **False** 将被忽略。

但是，您仍可以使用 Exchange Online PowerShell 中的 **get-mailboxauditbypassassociation** cmdlet 来阻止记录指定用户的 *任何* 邮箱操作，而不考虑这些操作在何处发生。 例如：

- 不记录绕过用户执行的邮箱所有者操作。

- 委派由其他用户邮箱执行的绕过用户执行的操作 (包括不记录) 的共享邮箱。

- 不会记录绕过用户执行的管理操作。

若要绕过特定用户的邮箱审核日志记录，请将 \<MailboxIdentity\> 名称、电子邮件地址、别名或用户主体名称替换为用户 (用户名) 并运行以下命令：

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

若要验证是否对指定用户跳过审核，请运行以下命令：

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

如果值 **为 True** ，则表示对用户绕过邮箱审核日志记录。

## <a name="more-information"></a>更多信息

- 虽然默认情况下已对所有组织启用邮箱审核日志记录功能，但只有拥有 E5 许可证的用户才会在 [安全 & 合规性中心中](search-the-audit-log-in-security-and-compliance.md) 或通过 [Office 365 管理活动 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)在审核日志搜索中返回邮箱审核日志事件（ **默认情况下**）。

  若要检索没有 E5 许可证的用户的邮箱审核日志条目，可以执行以下操作：

  - 手动启用单个邮箱的邮箱审核 (运行命令 `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true`) 。 执行此操作后，您可以在安全 & 合规性中心中或通过 Office 365 管理活动 API 使用审核日志搜索。
  
    > [!NOTE]
    > 如果邮箱审核在邮箱上似乎已启用，但您的搜索未返回任何结果，请将 _AuditEnabled_ 参数的值更改为 `$false` ，然后再更改回 `$true` 。
  
  - 在 Exchange Online PowerShell 中使用以下 cmdlet：

    - [搜索-search-mailboxauditlog](https://docs.microsoft.com/powershell/module/exchange/search-mailboxauditlog) 以搜索特定用户的邮箱审核日志。

    - [New-mailboxauditlogsearch](https://docs.microsoft.com/powershell/module/exchange/new-mailboxauditlogsearch) 搜索特定用户的邮箱审核日志，并将结果通过电子邮件发送给指定的收件人。

  - 使用 exchange 管理中心 (EAC) 在 Exchange Online 中执行以下操作：

    - [导出邮箱审核日志](https://docs.microsoft.com/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)

    - [运行非所有者邮箱访问报告](https://docs.microsoft.com/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- 默认情况下，邮箱审核日志记录会在被删除前的90天后保留。 您可以使用 Exchange Online PowerShell 中的 "**设置邮箱**" cmdlet 上的*AuditLogAgeLimit*参数更改审核日志记录的期限。 但是，增加此值不会允许您在审核日志中搜索超过90天的事件。

  如果增加期限，则需要使用 Exchange Online PowerShell 中的 [search-mailboxauditlog](https://docs.microsoft.com/powershell/module/exchange/search-mailboxauditlog) cmdlet 在用户的邮箱审核日志中搜索早于90天的记录。

- 如果您已在邮箱审核之前对邮箱的 *AuditLogAgeLimit* 属性进行了更改，则该邮箱的现有审核日志期限不会发生更改。 也就是说，默认情况下邮箱审核不会影响邮箱审核记录的当前期限。

- 若要更改 Microsoft 365 组邮箱上的 *AuditLogAgeLimit* 值，需要将该开关包含 `-GroupMailbox` 在 " **设置邮箱** " 命令中。

- 邮箱审核日志记录存储在每个用户邮箱的 "可恢复的项目" 文件夹中 (名为 " *审核* ") 子文件夹中。 请记住以下有关邮箱审核记录和 "可恢复的项目" 文件夹的事项：

  - 邮箱审核记录根据 "可恢复的项目" 文件夹的存储配额进行计数，默认情况下该文件夹为 30GB (警告配额为 20 GB) 。 在以下情况时，存储配额会自动增加到 100 GB (并) 90 GB 警告配额：

    - 邮箱上放置了保留项。

    - 将邮箱分配给合规中心中的保留策略。

  - 邮箱审核记录也会对 ["可恢复的项目" 文件夹的文件夹限制进行](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits)计数。 可以在 "审核" 子文件夹中存储 (审核记录中最多有3000000个项目) 。

    > [!NOTE]
    > 邮箱默认情况下的审核不太可能会影响存储配额或 "可恢复的项目" 文件夹的文件夹限制。

    - 您可以在 Exchange Online PowerShell 中运行以下命令，以在 "可恢复的项目" 文件夹的 "审核" 子文件夹中显示项目的大小和数量：

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - 您不能直接访问 "可恢复的项目" 文件夹中的审核日志记录;相反，您可以使用 **search-mailboxauditlog** cmdlet 或搜索审核日志来查找和查看邮箱审核记录。

- 如果将邮箱置于保留或分配到合规中心中的保留策略，则在默认情况下，审核日志记录仍保留在由邮箱的 *AuditLogAgeLimit* 属性定义的持续时间 (90 天) 。 若要延长保留邮箱的审核日志记录，您需要增加邮箱的 *AuditLogAgeLimit* 值。

- 在多地理位置环境中，不支持跨地理位置邮箱审核。 例如，如果为某用户分配了访问其他地理位置的共享邮箱的权限，此用户执行的邮箱操作不会记录在共享邮箱的邮箱审核日志中。
