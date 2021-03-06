---
title: 搜索内容
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.assetid: df2d1e0f-b476-42c9-aade-4a260b24f193
description: 使用安全 & 合规中心中的内容搜索电子数据展示工具在 Exchange 邮箱、SharePoint 网站中的文档和 OneDrive 位置以及 Skype for Business 中的即时消息对话中快速查找电子邮件。
ms.openlocfilehash: c02bcf627cec46b52ba9ff449a0d39b185ce4a0a
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285978"
---
# <a name="search-for-content-using-the-content-search-tool"></a>使用内容搜索工具搜索内容

使用安全 & 合规中心中的内容搜索工具在 Exchange 邮箱、SharePoint 网站中的文档和 OneDrive 位置以及 Skype for Business 中的即时消息对话中快速查找电子邮件。 您可以使用内容搜索工具在协作工具（如 Microsoft 团队和 Microsoft 365 组）中搜索电子邮件、文档和即时消息对话。
  
## <a name="search-for-content"></a>搜索内容

第一步是开始使用内容搜索工具来选择要搜索的内容位置，并配置关键字查询以搜索特定项。 或者，您可以只保留查询为空，并返回目标位置中的所有项。
  
- [创建和运行](content-search.md) 内容搜索 
    
- [构建搜索查询和使用条件](keyword-queries-and-search-conditions.md) 以缩小搜索范围 
    
- [配置搜索权限筛选](permissions-filtering-for-content-search.md) ，使电子数据展示管理器只能在组织中搜索邮箱或网站的子集 
    
- [运行 ID 列表搜索](csv-file-for-an-id-list-content-search.md) 以搜索特定的电子邮件 
    
- 在 Microsoft 365 中搜索本地用户的[基于云的邮箱](search-cloud-based-mailboxes-for-on-premises-users.md)

- 查看搜索结果的[关键字统计信息](view-keyword-statistics-for-content-search.md)，然后根据需要优化查询 
    
- 搜索贵组织已导入到 Microsoft 365 的[第三方数据](use-content-search-to-search-third-party-data-that-was-imported.md) 
    
- [批量编辑](bulk-edit-content-searches.md) 多个搜索的查询和内容位置 
    
- [重试内容搜索](retry-failed-content-search.md) 以解决内容位置错误

- [保留密件抄送收件人](https://docs.microsoft.com/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) ，以便可以搜索它们 


## <a name="perform-actions-on-content-you-find"></a>对你找到的内容执行操作

在运行搜索并根据需要对其进行优化后，下一步是对搜索返回的结果执行某些操作。 您可以导出结果并将其下载到本地计算机，或在组织中进行电子邮件攻击的情况下，可以从用户邮箱中删除搜索结果。
  
- [导出内容搜索的结果](export-search-results.md) 并将其下载到本地计算机 
    
- [搜索和删除电子](search-for-and-delete-messages-in-your-organization.md) 邮件，例如内容为病毒、危险附件或网络钓鱼邮件的邮件 
    
- [导出](export-a-content-search-report.md) 有关内容搜索结果的报告，而不导出实际结果 
    
- 在导出搜索结果时[提高下载速度](increase-download-speeds-when-exporting-ediscovery-results.md) 
    
## <a name="learn-more-about-content-search"></a>了解有关内容搜索的详细信息

内容搜索易于使用，但也是一个功能强大的工具。 幕后，有很多事情正在进行。 你对它的了解越多，并了解其行为及其限制，就越能成功地将其用于组织的搜索和调查需求。 了解以下信息：
  
- [Exchange 和 SharePoint 中部分索引的项目](partially-indexed-items-in-content-search.md) 以及如何在导出和下载搜索结果时包括或排除这些项目 
    
- [调查部分索引项目](investigating-partially-indexed-items-in-ediscovery.md) 并确定组织对它们的暴露 
    
- [内容搜索工具的限制](limits-for-content-search.md)，例如，可以一次运行的最大搜索数以及可在单个搜索中包含的最大内容位置数 
    
- 导出和下载搜索结果时，[估计和实际搜索结果](differences-between-estimated-and-actual-ediscovery-search-results.md)以及它们之间可能存在差异的原因 
    
- [搜索结果中的重复数据消除](de-duplication-in-ediscovery-search-results.md) ，可在导出搜索结果的电子邮件时启用 
    
## <a name="use-scripts-for-advanced-scenarios"></a>将脚本用于高级方案

有时，您必须执行更高级、复杂和重复的内容搜索任务。 在这些情况下，在安全 & 合规性中心中使用 PowerShell 命令更简单、更快捷。 为了简化此过程，我们已创建了许多安全 & 合规性中心 PowerShell 脚本，以帮助您完成复杂的内容搜索相关任务。
  
- 在确信项目的响应能力位于该文件夹中时，[搜索特定邮箱和网站文件夹](use-content-search-for-targeted-collections.md) (被称为*目标集合*)  
    
- [在邮箱和 OneDrive 位置搜索](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md) 用户列表 
    
- [创建、报告和删除多个搜索](create-report-on-and-delete-multiple-content-searches.md) 以快速高效地识别和挑选搜索数据 
    
- [克隆内容搜索](clone-a-content-search.md) 并快速比较不同关键字搜索查询在相同的内容位置运行的结果;或者在创建新搜索时无需重新输入大量内容位置，使用该脚本来节省时间 
    

