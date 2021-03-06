---
title: Microsoft 365 Exchange Online 数据删除
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 了解如何在 Exchange Online 中处理邮箱和邮箱中的邮箱和项目的软和硬数据删除。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 63bb5dcde334f7c53554f910b1a8d17e1d0d69cc
ms.sourcegitcommit: c029834c8a914b4e072de847fc4c3a3dde7790c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "47332516"
---
# <a name="exchange-online-data-deletion-in-microsoft-365"></a>Microsoft 365 中的 Exchange Online 数据删除

在 Exchange Online 中，有两种删除：软删除和硬删除。 这适用于邮箱和邮箱中的项目。

## <a name="soft-deleted-and-hard-deleted-mailboxes"></a>软删除和硬删除邮箱
软删除的用户邮箱是指已使用 Microsoft 365 管理中心或删除邮箱 cmdlet 删除的邮箱，并且在30天内仍处于 Azure Active Directory 回收站中。 可通过以下任一方式软删除邮箱：
-  (user 对象超出范围或在回收站容器中时软删除了用户邮箱的关联的 Azure Active Directory 用户帐户) 。
- 用户邮箱关联的 Azure Active Directory 用户帐户已硬删除，但 Exchange Online 邮箱处于诉讼保留或电子数据展示保留状态。
- 用户邮箱关联的 Azure Active Directory 用户帐户已在最近30天内清除;这是最大保留长度的 Exchange Online 将邮箱保留为软删除状态，然后才会永久清除和不可恢复。

硬删除的用户邮箱是已通过以下方式之一删除的邮箱：
- 用户邮箱已软删除30天以上，并且关联的 Azure Active Directory 用户已硬删除。 所有邮箱内容（如电子邮件、联系人和文件）都将被永久删除。
- 已从 Azure Active Directory 中硬删除与用户邮箱关联的用户帐户。 用户邮箱现已在 Exchange Online 中软删除，并在30天内保持软删除状态。 如果在30天的时间内，新的 Azure Active Directory 用户将从具有相同 **ExchangeGuid** 或 **ArchiveGuid**的原始收件人帐户中同步，并且该新帐户已获得 Exchange Online 许可，这将导致删除原始用户邮箱。 所有邮箱内容（如电子邮件、联系人和文件）都将被永久删除。
- 使用 **删除邮箱-PermanentlyDelete**删除软删除邮箱。

上述删除方案假定用户邮箱不处于任何保留状态，如诉讼保留或电子数据展示保留。 如果邮箱上有任何类型的保留，则不能删除邮箱。 对于所有邮件用户收件人类型，任何 [保留](https://support.office.com/article/manage-legal-investigations-in-office-365-2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e?ui=en-US&rs=en-US&ad=US) 设置都将被忽略，并且不会影响硬删除或软删除。

## <a name="soft-deleted-and-hard-deleted-items"></a>软删除和硬删除项目
当用户删除邮箱项目 (例如电子邮件、联系人、日历约会或任务) 时，该项目将移动到 "可恢复的项目" 文件夹中，并将其移动到名为 "删除" 的子文件夹中。 这称为软删除。 已删除的项目保留在" 删除"文件夹中的时间取决于为邮箱设置的"已删除项目保留期限"。 默认情况下，Exchange Online 邮箱会将已删除项目保留14天，但 Exchange Online 管理员可以将此设置更改为最多30天的时间。  (有关增加 Exchange Online 邮箱的已删除邮件保留期的详细步骤，请参阅 [更改为 Exchange online 邮箱保留永久删除的项目的时间](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention)。在已删除邮件的保留时间过期之前，) 用户可以恢复或清除已删除项目。 为此，它们使用 Microsoft Outlook 或 web 上的 Outlook 中的 "恢复已删除邮件" 功能。

如果用户使用 Outlook 或 web 上的 Outlook 中的 "恢复已删除邮件" 功能清除已删除的项目，这就称为硬删除。 在 Exchange Online 中，创建新邮箱时，默认情况下会启用单个项目恢复，这样管理员仍可以在已删除项目的保留期过期之前 [恢复](https://docs.microsoft.com/Exchange/recipients/user-mailboxes/recover-deleted-messages) 硬删除的邮件。 此外，如果单个项目恢复已启用，那么当用户或进程更改邮件时，原始项目的副本也会予以保留。

## <a name="page-zeroing"></a>页面清零
*清零* 是一种安全机制，它可以对删除的数据写入零或二进制模式，以便更难以恢复删除的数据。 在 Exchange Online 中，邮箱数据库将 *页面* 用作存储单元，并实现称为 *页面清零*的覆盖过程。 默认情况下会启用页面清零，且不能被客户或 Microsoft 禁用。 将页面清零操作记录在事务日志文件中，以便给定数据库的所有副本都以类似的方式进行页清零。 对活动数据库副本的页面进行清零会导致页面在数据库的被动副本上被清零。

页面清零会将二进制模式写入硬删除记录。 页面清零模式特定于可扩展存储引擎 (ESE) 操作 (Exchange Online) 中的服务器所使用的内部数据库引擎的名称，并且与后台数据库维护操作的运行时操作不同。  (后台数据库维护是持续校验和扫描每个数据库的过程。 它的主要功能是校验数据库页的校验和，但它还处理清理空间，并将未清零的记录和页面清零，因为存储发生故障。 ) 

下表列出对应于特定运行时操作的填充模式。

| ESE 运行时操作   | 填充模式 |
|--------------------------|--------------|
| 替换                  | R            |
| 记录/长数值删除 | D            |
| 释放的页空间         | H            |


下表列出对应于在 ESE 后台数据库维护期间进行的特定操作的填充模式。

| ESE 后台数据库维护操作 | 填充模式 |
|-----------------------------------------------|--------------|
| 记录删除                                 | D            |
| 长数值删除                             | L            |
| 部分使用的页的释放页空间       | Z            |
| 未使用的页的释放页空间               | U            |


### <a name="page-zeroing-process"></a>页面清零过程
页面清零的过程取决于删除方案。 下表讨论数据库删除方案以及页清零功能的执行时间。

| 数据库删除方案 | 对数据库数据清零的 ESE 过程和时间范围 |
|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 项目将根据已删除项目的保留期而过期。 | 一个异步线程对删除的数据写入二进制模式。 此操作在数毫秒的记录删除过程中发生。 如果存储进程在异步清零工作仍处于未完成状态时出现故障 (或者由于版本存储的增长) 取消了版本存储清理，则当后台数据库维护处理数据库的该部分时，将完成清零。 |
| 查看方案： Outlook/Outlook on the web folder view 视图中的项目过期 (例如，会话视图)  | 当后台数据库维护处理该部分数据库时会进行数据清零。 |
| 移动邮箱/删除邮箱方案：源邮箱已删除 (过期的已删除邮箱)  | 当后台数据库维护处理该部分数据库时会进行数据清零。 |

### <a name="mailbox-data-types-without-page-zeroing"></a>不进行页清零的邮箱数据类型
以下邮箱数据类型对页面清零没有任何规定：
- **邮箱数据库事务日志** -当事务日志作为正常操作的一部分被删除时，文件系统中存储已删除的日志文件 () 的块将不会有任何进程。 文件系统可能会迅速为新创建的日志重新利用该可用空间，但不能保证会发生这种情况。
- **内容索引目录文件** -Exchange Online 使用搜索基础 (也称为 FAST) ，用于搜索索引功能。 搜索索引目录由存储在与邮箱数据库文件相同的卷上的多个文件组成。 当从邮箱数据库中硬删除邮件时，不会立即删除搜索编录中的关联内容。 当搜索 Foundation 在一个较大的文件中进行许多小目录文件的卷影 (或主合并) 时，将会发生内容删除。 主合并完成后，会删除较小的编录文件。 没有过程可用于对存储已删除编录文件的块进行清零。

## <a name="continuous-replication"></a>连续复制
连续复制 (也称为日志传送和重播) 在 Exchange Online 中创建和维护每个邮箱数据库的副本以提供高可用性、站点恢复能力和灾难恢复的技术。 连续复制利用 Exchange Server 数据库崩溃恢复支持，以提供对邮箱数据库的一个或多个副本执行异步更新的技术。 每个邮箱服务器都会记录在活动数据库上进行的数据库更新 (例如，用户电子邮件活动) 为 1 MB 事务日志文件的连续集合中的日志记录。 这组文件称为 "日志流"。 在连续复制中，日志流还用于异步更新数据库的一个或多个副本。 这是通过将日志传输到包含活动数据库的被动副本的位置来实现的，然后将这些日志重放到被动数据库副本中。 如果对数据库的被动副本重播活动数据库中的所有日志，则这两个数据库是等效的，并且通过此过程，对主动数据库所做的任何物理更改都会复制到该数据库的所有被动副本。

任何从邮箱数据库中删除、邮箱项目或整个邮箱以及软删除或硬删除的删除都表示对活动数据库的物理更改。 页面清零还需要对活动数据库进行物理更改。 这些更改通过一个称为 "连续复制" 的过程写入日志文件，当这些日志文件重放到数据库的被动副本时，对这些被动数据库进行相同的物理更改。