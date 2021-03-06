---
title: 了解用于 Teams 的保留
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: 了解适用于 Microsoft Teams 的保留策略。
ms.openlocfilehash: 40e68116c24622fd21bd35531ef7821d8c4b7c62
ms.sourcegitcommit: 33afa334328cc4e3f2474abd611c1411adabd39f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2020
ms.locfileid: "48370366"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>了解用于 Microsoft Teams 的保留

>*[Microsoft 365 安全性与合规性许可指南](https://aka.ms/ComplianceSD)。*

本文中的信息是对[了解保留](retention.md)的补充，因为它包含特定于 Microsoft Teams 的信息。

## <a name="how-retention-works-with-microsoft-teams"></a>用于 Microsoft Teams 的保留的工作原理

可使用保留策略保留 Teams 中的聊天和频道消息。 Teams 聊天存储在参与聊天的每个用户的邮箱中的隐藏文件夹内，Teams 频道消息存储在团队组邮箱中类似的隐藏文件夹中。

务必了解，Teams 使用由 Azure 支持的聊天服务，该服务也会存储此数据，并且默认永久存储。 因此，建议创建保留策略来使用 Teams 位置保留和删除此 Teams 数据。 此保留策略可以从 Exchange 邮箱和由 Azure 提供技术支持的基础聊天服务中永久删除数据。 有关详细信息，请参阅 [Microsoft Teams 中的安全性和合规性](https://go.microsoft.com/fwlink/?linkid=871258)，特别是[信息保护体系结构](https://docs.microsoft.com/MicrosoftTeams/security-compliance-overview#information-protection-architecture)部分。

Teams 聊天和频道消息不受针对用户或组邮箱配置的保留策略影响。 即使 Teams 聊天和频道消息存储在 Exchange 中，此 Teams 数据仍将仅包含在针对 **Teams 频道消息**和 ** Teams 聊天**位置配置的保留策略中。

> [!NOTE]
> 如果用户包含在保留 Teams 数据的活动保留策略中，并且删除了包含在此策略中的用户邮箱，为了保留 Teams 数据，邮箱会转换为[非活动邮箱](inactive-mailboxes-in-office-365.md)。 如果不需要为用户保留此 Teams 数据，请在删除用户的邮箱之前，将用户帐户从保留策略中排除。

为聊天和频道消息配置保留策略后，Exchange 服务中的计时器作业会定期评估存储这些 Teams 消息的隐藏文件夹中的项目。 计时器作业最多需要 7 天才能运行。 这些项目的保留期限到期后，它们将被移至 SubstrateHolds 文件夹，此文件夹是每个用户或组邮箱中的另一个隐藏文件夹，用于在永久删除“软删除”项目之前存储这些项目。

为聊天和频道消息配置保留策略后，内容路径取决于保留策略是“保留后删除”、“仅保留”还是“仅删除”。

如果保留策略为“保留后删除”：

![Teams 聊天和频道消息的保留流关系图](../media/teamsretentionlifecycle.png)

对于图中的两条路径：

1. **如果用户在保留期内编辑或删除了聊天或频道消息**，则该原始消息将在 21 天内复制（如果已编辑）或移动（如果已删除）到 SubstrateHolds 文件夹中。 消息将存储在此处，直到保留期到期，然后在 24 小时之内将其永久删除。

2. **如果未删除聊天或频道消息**，并且对于编辑后的当前消息，则保留期到期后，消息将被移至 SubstrateHolds 文件夹。 此操作自到期之日起最多需要 7 天。 消息位于 SubstrateHolds 文件夹中时，它将在 24 小时内被永久删除。 

> [!NOTE]
> 可通过电子数据展示工具搜索 SubstrateHolds 文件夹中的消息。 从此 SubstrateHolds 文件夹中删除消息之前，仍可以由电子数据展示工具搜索。

如果保留策略为“仅保留”或“仅删除”，内容路径在“保留后删除”策略的基础上有所变化。

### <a name="content-paths-for-retain-only-retention-policy"></a>“仅保留”保留策略的内容路径

1. **如果编辑或删除了聊天消息或频道消息**：21 天内在 SubstrateHolds 文件夹中创建原始消息的副本，并将其保留在那里，直到保留期到期。 然后，此消息会在 24 小时内从 SubstrateHolds 文件夹中永久删除。

2. **如果项目在保持期内未遭修改或删除**以及保留期内编辑后的当前消息：保留期前后无变化；消息仍保留在原始位置。

### <a name="content-paths-for-delete-only-retention-policy"></a>“仅删除”保留策略的内容路径

1. **如果消息在保持期内未遭删除**：在保持期结束时，消息将移至 SubstrateHolds 文件夹。 此操作自到期之日起最多需要 7 天。 然后，此消息会在 24 小时内从 SubstrateHolds 文件夹中永久删除。

2. **如果用户在保留期内删除项目**，该项目将在 21 天内移至 SubstrateHolds 文件夹，然后在 24 小时内被永久删除。


## <a name="skype-for-business-and-teams-interop-chats"></a>Skype for Business 和 Teams 互操作聊天

当 Skype for Business 聊天进入 Teams 时，它将成为 Teams 聊天线程中的消息，并接收到相应的邮箱中。 Teams 保留策略将从 Teams 线程应用于这些消息。 

但是，如果已为 Skype for Business 开启对话历史记录，并且从 Skype for Business 客户端将其保存到邮箱中，则 Teams 保留策略不会处理该聊天数据。 对于此内容，请使用为 Skype for Business 配置的保留策略。

## <a name="meetings-and-external-users"></a>会议和外部用户

频道会议邮件的存储方式与频道消息相同，因此对于此数据，在配置保留策略时，请选择 **Teams 频道消息**位置。

临时会议邮件的存储方式与群组聊天消息相同，因此对于此数据，在配置保留策略时，请选择 **Teams 聊天**位置。

当外部用户加入你的组织主持的会议时：

- 如果外部用户使用租户中的来宾帐户加入，此用户将有一个影子邮箱，可遵循组织的 Teams 保留策略。 会议中的任何邮件都存储在用户的邮箱和影子邮箱中。 

- 如果外部用户使用来自其他 Microsoft 365 组织的帐户加入，则你的保留策略无法删除此用户的邮件，因为它们存储在该用户在其他租户中的邮箱中。 但是对于同一会议，你的保留策略可以为你的用户删除邮件。

## <a name="when-a-user-leaves-the-organization"></a>如果某用户离开组织 

如果用户离开你的组织，并且其 Microsoft 365 帐户被删除，则其要保留的聊天消息将存储在非活动邮箱中。 聊天消息仍受用户在其邮箱变为非活动状态之前所应用的任何保留策略的约束，并且内容支持电子数据展示搜索。 有关详细信息，请参阅 [Exchange Online 中的非活动邮箱](inactive-mailboxes-in-office-365.md)。 

如果用户在 Teams 中存储了任何文件，请参阅 SharePoint 和 OneDrive 的[等效部分](retention-policies-sharepoint.md#when-a-user-leaves-the-organization)。

## <a name="limitations"></a>限制

我们正在不断努力优化 Teams 中的保留功能。 在此期间，在对 Teams 频道消息和聊天使用保留时，需要注意以下几个限制：

- **配置 Teams 频道消息的保留策略时，不包括专用频道中的 Teams 消息**。 保留策略目前不支持专用频道。 

- **Teams 聊天和频道消息不会保留赞和其他反应**。 保留策略不支持其他人以表情符形式所做的反应。

- **Outlook 错误显示的问题**。 如果为 Skype 或 Teams 位置创建保留策略，则当用户在 Outlook 桌面客户端中查看邮箱文件夹的属性时，这些策略中的某个策略将显示为默认文件夹策略。 这是 Outlook 中的错误显示问题，也是一个[已知问题](https://support.microsoft.com/help/4491013/outlook-client-displays-teams-or-skype-for-business-retention-policies)。 应作为默认文件夹策略显示的是应用于该文件夹的邮箱保留策略。 Skype 或 Teams 保留策略不适用于用户的邮箱。

- **配置问题**： 
    - 为“**Teams 频道消息**”位置选择“**选择团队**”时，你可能会看到不属于团队的 Microsoft 365 组。 不要选择这些组。
    
    - 为“**Teams 聊天**”位置选择“**选择用户**”时，你可能会看到来宾和非邮箱用户。 保留策略并非专为这些用户设计的，因此请不要选择他们。

## <a name="configuration-guidance"></a>配置指南

如果你刚开始在 Microsoft 365 中配置保留，请参阅[开始使用保留策略和保留标签](get-started-with-retention.md)。

如果已准备好配置 Teams 的保留策略，请参阅[创建和配置保留策略](create-retention-policies.md)。
