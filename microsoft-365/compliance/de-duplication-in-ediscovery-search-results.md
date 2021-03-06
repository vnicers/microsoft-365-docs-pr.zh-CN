---
title: 电子数据展示搜索结果中的重复数据删除
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/21/2016
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 5af334b6-a15d-4f73-97f8-1423457d9f6b
ms.custom:
- seo-marvel-apr2020
description: 了解如何消除重复的电子数据展示搜索结果，以便只导出电子邮件的一个副本。
ms.openlocfilehash: 44b56faf54b32e8126885a3344448a4794c35783
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2020
ms.locfileid: "47357522"
---
# <a name="de-duplication-in-ediscovery-search-results"></a>电子数据展示搜索结果中的重复数据删除

本文介绍了如何消除重复数据展示搜索结果，并说明了重复数据消除算法的限制。
  
使用电子数据展示工具导出电子数据展示搜索的结果时，您可以选择对导出的结果进行重复数据消除。 应用场景 启用重复数据删除时 (默认情况下，不会启用重复数据删除) ，即使在搜索的邮箱中找到同一邮件的多个实例，也只导出电子邮件的一个副本。 重复数据消除可帮助您通过减少在导出搜索结果时必须查看和分析的项目数来节省时间。 但重要的是要了解重复数据消除的工作方式，并了解在导出过程中可能会导致唯一项目标记为重复的算法的限制。
  
## <a name="how-duplicate-messages-are-identified"></a>如何标识重复邮件

电子数据展示工具使用以下电子邮件属性的组合来确定邮件是否重复：
  
- **InternetMessageId** -此属性指定电子邮件的 Internet 邮件标识符，它是指特定邮件的特定版本的全局唯一标识符。 此 ID 由发件人的电子邮件客户端程序或用于发送邮件的主机电子邮件系统生成。 如果某人向多个收件人发送邮件，则该邮件的每个实例的 Internet 邮件 ID 都是相同的。 对原始邮件的后续修订将接收到不同的邮件标识符。 

- **ConversationTopic** -此属性指定邮件的会话线程的主题。 **ConversationTopic**属性的值是描述对话的总体主题的字符串。 保留项包括初始邮件和在答复初始邮件时发送的所有邮件。 同一对话中的邮件具有与 **ConversationTopic** 属性相同的值。 此属性的值通常是生成对话的初始邮件中的主题行。 

- **BodyTagInfo** -这是一个内部 Exchange 存储属性。 此属性的值是通过检查邮件正文中的各种属性计算得出的。 此属性用于标识邮件正文中的差异。 

在电子数据展示导出过程中，将对匹配搜索条件的每封邮件比较这三个属性。 如果两个 (或更多) 邮件的这些属性相同，则会确定这些邮件是重复的，因此，如果启用重复数据消除功能，则将只导出邮件的一个副本。 导出的邮件称为 "源项目"。 有关重复邮件的信息包含在 **Results.csv** 和导出的搜索结果附带的 **Manifest.xml** 报告中。 在 **Results.csv** 文件中，通过在 " **复制到项** " 列中包含一个值来标识重复的邮件。 此列中的值与导出的邮件的 " **项目标识** " 列中的值相匹配。 
  
下图显示了如何在 **Results.csv** 中显示重复的邮件，以及如何在搜索结果中导出 **Manifest.xml** 报告。 这些报告不包括前面所述的电子邮件属性，这些属性在重复数据消除算法中使用。 相反，报告包括分配给 Exchange 存储中的项目的 **项目标识** 属性。 
  
 ### <a name="resultscsv-report-viewed-in-excel"></a>在 Excel) 中查看 Results.csv 报表 (
  
![查看有关 Results.csv 报表中的重复项的信息](../media/e3d64004-3b91-4cba-b6f3-934b46cbdcdb.png)
  
 ### <a name="manifestxml-report-viewed-in-excel"></a>在 Excel) 中查看 Manifest.xml 报表 (
  
![查看有关 Manifest.xml 报表中的重复项的信息](../media/69aa4786-9883-46ff-bcae-b35e0daf4a6d.png)
  
此外，还会在导出报告中包含重复邮件中的其他属性。 这包括重复邮件所在的邮箱、邮件是否已发送到通讯组，以及邮件是否为 "抄送" 或 "密件抄送" 给其他用户。
  
## <a name="limitations-of-the-de-duplication-algorithm"></a>对重复数据消除算法的限制

重复数据消除算法有一些已知的限制，可能会导致出现唯一项目标记为重复项。 请务必了解这些限制，以便您可以决定是否使用可选的重复数据删除功能。
  
有一种情况是，重复数据删除功能可能错误地将邮件标识为重复邮件，而不是将其导出 (但仍将其引用为 "导出报告) " 中的重复项。 这些是用户编辑但不发送的邮件。 例如，假设用户在 Outlook 中选择一封邮件，复制该邮件的内容，然后将其粘贴到新邮件中。 然后，用户通过删除或添加附件，或更改 "主题" 行或正文本身来更改其中一个副本。 如果这两个邮件与电子数据展示搜索的查询相匹配，则在导出搜索结果时启用重复数据删除时，将只导出其中的一个邮件。 因此，即使原始邮件或复制的邮件已更改，这两个修订的邮件都不会发送，因此 **InternetMessageId**、 **ConversationTopic** 和 **BodyTagInfo** 属性的值未更新。 但如前所述，这两条消息将在 "导出报告" 中列出。 
  
启用 "写入时复制" 页面保护功能时（如果邮箱处于诉讼保留或就地保留状态），也可以将唯一邮件标记为重复。 "写入时复制" 功能会将原始邮件复制 (并将其保存到用户的 "可恢复项目" 文件夹的 "版本" 文件夹中，然后保存 "修订到原始项目") 。 在这种情况下，"可恢复的项目" 文件夹中的修订副本和原始邮件 () 可能会被视为重复邮件，因此只能导出其中的一个。
  
> [!IMPORTANT]
> 如果重复数据消除算法的限制可能会影响您的搜索结果的质量，则在导出项目时不应启用重复数据删除。 如果此部分中所述的情况不可能是搜索结果中的因素，并且您想要减少最有可能重复的项目数，则应考虑启用重复数据删除。 
  
## <a name="more-information"></a>更多信息

- 本文中的信息适用于使用以下电子数据展示工具之一导出搜索结果：

  - Office 365 中的合规性中心内的内容搜索

  - Exchange Online 中的就地电子数据展示

  - SharePoint Online 中的电子数据展示中心

- 有关导出搜索结果的详细信息，请参阅：

  - [导出内容搜索](export-search-results.md)

  - [导出内容搜索报告](export-a-content-search-report.md)

  - [将就地电子数据展示搜索结果导出到 PST 文件](https://go.microsoft.com/fwlink/p/?linkid=832671)

  - [在电子数据展示中心导出内容和创建报表](https://docs.microsoft.com/SharePoint/governance/export-content-and-create-reports-in-the-ediscovery-center)
