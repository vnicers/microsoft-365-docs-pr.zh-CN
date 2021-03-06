---
title: 手动将邮件提交给 Microsoft 进行分析
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: dad30e2f-93fe-4d21-9a36-21c87ced85c1
ms.collection:
- M365-security-compliance
description: 管理员和最终用户可以了解如何通过电子邮件 (正常的邮件标记为损坏或坏邮件，以便) Microsoft 进行分析。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6673dc7e7ac263ea9f734c002d0ffac410fadc07
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48202193"
---
# <a name="manually-submit-messages-to-microsoft-for-analysis"></a>手动将邮件提交给 Microsoft 进行分析

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


> [!NOTE]
> 如果您是具有 Exchange Online 邮箱的组织中的管理员，我们建议您在安全 & 合规性中心中使用提交门户。 有关详细信息，请参阅 [使用管理员提交将可疑的垃圾邮件、网络钓鱼、url 和文件提交给 Microsoft](admin-submission.md)。

如果组织中的用户收到垃圾邮件 (其收件箱中的垃圾邮件) 或网络钓鱼邮件，或者如果邮件被标记为垃圾邮件，则可能会令人沮丧。 我们不断调整垃圾邮件筛选器，使其更加准确。

您和您的用户可以通过提交误报 (正常的电子邮件标记为错误) 、漏报 (错误邮件（允许 Microsoft 进行分析) 和网络钓鱼邮件）来帮助此过程。

> [!NOTE]
> 由于我们收到的提交量很大，我们可能无法应答所有分析请求。

## <a name="submit-false-negatives-to-microsoft"></a>将漏报提交给 Microsoft

> [!TIP]
> Outlook Web App) 可以使用 Microsoft Outlook 的报告消息外接程序，而不是使用以下过程来报告漏报，而不是在 Outlook 和 web 上的 Outlook 中的用户 (以前称为 Outlook Web App。 有关如何安装和使用此工具的信息，请参阅 [Enable The Report Message 外接程序](enable-the-report-message-add-in.md)。

如果您收到一封邮件，该邮件将通过应标识为垃圾邮件或网络钓鱼的垃圾邮件筛选传递，则可以根据需要将邮件提交到 Microsoft 垃圾邮件分析和 Microsoft 仿冒分析团队。 分析师将检查邮件并将其添加到服务范围的筛选器中（如果它满足分类条件）。

1. 使用以下收件人之一创建一个新的空白电子邮件：

   - **垃圾邮件**： `junk@office365.microsoft.com`

   - **网络钓鱼**： `phish@office365.microsoft.com`

2. 将垃圾邮件或仿冒邮件拖放到新邮件中。 这会将垃圾邮件或仿冒邮件保存为新邮件中的附件。 请勿复制和粘贴邮件的内容或转发邮件 (我们需要原始邮件，以便我们可以检查邮件头) 。

   > [!NOTE]
   >
   > - 您可以在新邮件中附加多封邮件。 请确保所有邮件的类型都相同：网络钓鱼邮件或垃圾邮件。
   >
   > - 保留新的邮件正文空白。
   >
   > - 使用 .msg (默认 Outlook 格式) 或 .eml (默认的 Outlook Web 格式) 附加邮件的格式。

3. 完成后，请单击 " **发送**"。

> [!TIP]
> 管理员有几种不同的方法来阻止被 misidentified 为垃圾邮件的特定邮件。 有关详细信息，请参阅 [在 EOP 中创建阻止的发件人列表](create-block-sender-lists-in-office-365.md)。

## <a name="submit-false-positives-to-microsoft"></a>向 Microsoft 提交误报

> [!TIP]
> Outlook 和 Outlook 网页版中的用户可以使用 Microsoft Outlook 的报告消息外接程序，而不是使用以下过程报告误报。 有关如何安装和使用此工具的信息，请参阅 [Enable The Report Message 外接程序](enable-the-report-message-add-in.md)。

如果邮件被错误地标识为垃圾邮件，您可以将邮件提交给 Microsoft 垃圾邮件分析团队。 分析师将评估邮件，并根据分析的结果 () 可以调整服务范围的筛选器以允许邮件通过。

1. 创建一个新的空白电子邮件， `not_junk@office365.microsoft.com` 作为收件人：

2. 将 misidentified 邮件拖放到新邮件中。 这会将 misidentified 邮件另存为新邮件中的附件。 请勿复制和粘贴邮件的内容或转发邮件 (我们需要原始邮件，以便我们可以检查邮件头) 。

   > [!NOTE]
   >
   > - 您可以在新邮件中附加多封邮件。 请确保所有邮件的类型都相同：网络钓鱼邮件或垃圾邮件。
   >
   > - 保留新的邮件正文空白。
   >
   > - 使用 .msg (默认 Outlook 格式) 或 .eml (默认的 Outlook Web 格式) 附加邮件的格式。

3. 完成后，请单击 " **发送**"。

> [!TIP]
> 管理员有几种不同的方法允许特定邮件跳过垃圾邮件筛选。 有关详细信息，请参阅 [在 EOP 中创建安全发件人列表](create-safe-sender-lists-in-office-365.md)。

## <a name="create-a-mail-flow-rule-to-receive-copies-of-messages-that-are-reported-to-microsoft"></a>创建邮件流规则以接收报告给 Microsoft 的邮件副本

有关说明，请参阅 [使用邮件流规则查看用户报告给 Microsoft 的内容](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md)。
