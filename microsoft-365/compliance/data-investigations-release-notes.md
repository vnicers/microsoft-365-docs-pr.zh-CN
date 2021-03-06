---
title: Microsoft 365 中的 "数据调查" (预览) 的发行说明
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
description: 在本文中，您将找到发行说明，其中包含 Microsoft 365 中的数据调查 (预览版) 工具的更改和新功能。
ms.openlocfilehash: 2a46236d000c62c4ab73f8a47e9c9f661fb17a61
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285408"
---
# <a name="release-notes-for-data-investigations-preview-in-microsoft-365"></a>Microsoft 365 中的 "数据调查" (预览) 的发行说明

您可以使用新的数据调查 (Microsoft 365 中的预览) 工具来会审、调查和修正与数据相关的事件，例如数据外泄事件或内部调查。 数据调查的公共预览为您提供了对即将推出的功能和更新的早期访问权限。 若要尽早访问最新功能，请在 "安全" & 合规性中心 (预览) 中新建调查。 若要了解如何操作，请参阅 [在 Microsoft 365 中管理数据外泄事件](manage-data-spillage-incidents.md)。

## <a name="whats-new"></a>最近更新 

- **调查** -您可以通过创建调查来对搜索和事件进行分组。 通过添加或删除成员来管理可访问调查的人员。  您还可以选择并标记您喜爱的调查。 使用新仪表板跟踪和监控调查中和跨调查的活动。 完成调查后，可以关闭或删除它。

- **感兴趣的人** –当您将用户添加到调查中的人时，您可以查看他们的邮箱、OneDrive for business 帐户和 Microsoft 团队网站。 您可以使用它们来限定调查内容搜索的范围。 若要进一步调查感兴趣的人员，您还可以查看与 Microsoft 365 和其他 Microsoft 服务中的活动相关的审核记录。

- **搜索** –使用各种搜索条件创建组织范围的搜索。 如果您知道要搜索的用户或网站，可以通过将这些用户添加为感兴趣的人员或在 "搜索创建向导" 中指定网站位置来执行此操作。 

- **证据** –创建新的证据集并添加要查看的搜索结果。 您可以查看各个文档、批注以留下调查说明，以及导出结果以移到不同的环境。 

- **审阅** –使用本机、文本和近本机视图查看添加到事件中的文档。 您还可以将分析应用于文档以按重复项、电子邮件线索和主题对项目进行分组，这有助于协助您复查事件。 

- **密文、标记和批注** –在审阅文档时设置密文、应用标记和批注。
  
- **高级索引** –如果有任何部分已编制索引的项目，它们将按需编制索引，以便所有数据都可供搜索。

- **错误修正** –修正或下载处理错误。 这包括对大型文件类型的补救性支持、受密码保护的文件以及与索引错误相关的其他问题。 

- **作业** –跟踪长时间运行的进程的状态。

- **硬删除邮箱项目** -在紧急情况下，您可能需要永久删除错放的项目。 为此，您可以在 Security & 合规性中心 PowerShell 中运行 **new-compliancesearchaction-PurgeType HardDelete** 命令，以永久删除邮箱中的项目。 有关详细信息，请参阅 [New-ComplianceSearchAction](https://docs.microsoft.com/powershell/module/exchange/new-compliancesearchaction)。
