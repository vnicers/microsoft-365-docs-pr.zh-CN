---
title: 针对 GDPR 的 Office 365 信息保护概述
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
- M365-security-compliance
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
description: 概览针对 GDPR 的 Office 365 信息保护。了解如何发现、分类、保护和监视个人数据。
ms.openlocfilehash: 72ce55b5ceb2ec3ff95cada481ec4aee0bbe8eef
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48197403"
---
# <a name="overview-of-office-365-information-protection-for-gdpr"></a>针对 GDPR 的 Office 365 信息保护概述

此解决方案演示了如何保护存储在 Office 365 服务中的敏感数据。其中包括针对发现、分类、保护和监视个人数据的指导性建议。该解决方案以一般数据保护条例 (GDPR) 为例，但用户可以采用同一流程实现对许多其他条例的符合性。

GDPR 对个人数据的收集、存储、处理和共享进行了规范化。个人数据在 GDPR 中的定义非常宽泛，即指属于欧盟 (EU) 居民的已确定身份的或可识别的自然人的任何相关数据。

第 4 条 – 定义

> “个人数据”表示已确定身份的或可识别的自然人（“数据主体”）的任何相关信息；可识别的自然人是指可被直接或间接识别出的自然人，尤其是通过参考姓名、证件号码、位置数据、网络标识等标识，或通过参考特定于该自然人的身体、生理、基因、精神、经济、文化或社会标识的一个或多个因素进行识别；

该解决方案旨在帮助组织发现和保护 Office 365 中可能受 GDPR 制约的个人数据。它并不用作 GDPR 符合性证明。组织负责确保其自己的 GDPR 符合性，并且经建议咨询其法律和合规团队，或向专门致力于符合性的第三方寻求指导和建议。

[GDPR 评估](https://www.microsoft.com/cyberassessment/en/gdpr/uso365?ls=Email&mkt_tok=eyJpIjoiTTJFeE5USXlOR1EwTWpJMiIsInQiOiJQTmdCYWR5NTlOd3JLWHZlb2NzNldKclQ4ZVBzVmhGeUhoUlFcL1pvSDIyXC9Ka05iTUR1aGpxT0YxQ0FUeGNDOUlkbWZLM1U4SUZWZmEyaGF6XC9ueUxkTHJzZnB3VDRMZlhPdkR4MzRLWkF5ckRNdWwxUkgzXC9yRU8yNkttSHhTb3VpZjNyVlJrNm9TTVZRYU5HR240a0FRPT0ifQ%3D%3D)是可免费使用的快速在线自评工具，它可帮助组织检查其为符合 GDPR 要求而达到的整体就绪程度。

## <a name="assess-and-manage-your-compliance-risk"></a>评估和管理符合性风险

实现 GDPR 符合性的第一步是评估 GDPR 是否适用于组织，如果适用，适用程度如何。此分析包括了解组织所处理的数据及此数据所在的位置。

### <a name="step-1--use-compliance-manager-to-view-the-regulation-requirements-and-track-your-progress"></a>步骤 1 — 使用合规性管理器查看法规要求并跟踪进度

合规性管理器帮助跟踪、实现和管理审核控制，可帮助组织实现各种标准的符合性，其中包括 GDPR。

![使用合规性管理器查看要求并跟踪进度](../media/Overview-image1.png)

有关详细信息，请参阅[合规性管理器](compliance-manager.md)。

### <a name="step-2--use-content-search-and-sensitive-information-types-to-find-personal-data"></a>步骤 2 — 使用内容搜索和敏感信息类型查找个人数据 

发现环境中受 GDPR 制约的个人数据。结合使用内容搜索和敏感信息类型执行以下操作：

- 在个人数据所在的位置进行查找和报告。

- 优化敏感数据类型及其他查询，查找环境中的所有个人数据。

![使用内容搜索和敏感信息类型查找个人数据](../media/Overview-image2.png)

敏感信息类型定义了自动进程识别特定信息类型（例如卫生服务号码和信用卡号码）的方式。本文附带了一组敏感信息类型，可以从这些类型入手。即将推出适用于欧盟国家/地区的个人数据的更多敏感信息类型。

有关详细信息，请参阅[搜索和查找个人数据](search-for-and-find-personal-data.md)。 

## <a name="classify-protect-and-monitor-personal-data-in-office-365-and-other-saas-apps"></a>分类、保护和监视 Office 365 及其他 SaaS 应用中的个人数据

用于 Office 365 信息保护的一些功能也可用于保护其他 SaaS 应用程序中的敏感数据。

![分类、保护和监视个人数据](../media/Overview-image3.png)

本节的剩余部分（步骤 3-5）对此图进行了说明。

### <a name="step-3--decide-if-you-want-to-use-labels-in-addition-to-sensitive-information-types"></a>步骤 3 — 决定是否使用除敏感信息类型之外的其他标签

敏感信息类型是一种分类形式。请参阅[为个人数据构建分类架构](architect-a-classification-schema-for-personal-data.md)，以决定是否还要使用标签。若要应用标签，请参阅[向 Office 365 中的个人数据应用标签](apply-labels-to-personal-data-in-office-365.md)。

在此图中，敏感信息类型和标签应用到了 Office 365。即将可以结合使用这些内容和 Cloud App Security 来查找其他 SaaS 应用（例如 Box 和 Salesforce）中的敏感数据。

### <a name="step-4--protect-personal-data-in-office-365"></a>步骤 4 — 保护 Office 365 中的个人数据 

个人数据保护始于 Office 365 数据丢失防护。有若干个其他功能被推荐用于保护个人数据的访问，其中包括适用于电子邮件的 Office 365 邮件加密功能。

这些保护功能可针对特定数据集：

- 网站和库级别的权限

- 网站级别的外部共享策略

- 网站级别的设备访问策略

对 Office 365 和其他云服务访问的保护包括：

- 企业移动性 + 安全性 (EMS) 中的标识和设备访问保护

- 特权访问管理

- Windows 10 安全功能

有关应用保护的详细信息，请参阅[向 Office 365 中的个人数据应用保护](apply-protection-to-personal-data-in-office-365.md)。

### <a name="step-5--monitor-for-leaks-of-personal-data"></a>步骤 5 — 监视个人数据泄露

Office 365 数据丢失防护报告提供了监视敏感数据的最详细的信息。可以使用审核日志设置自动警报并调查违规行为。Cloud App Security 将查找和监视敏感数据的功能扩展到了其他 SaaS 提供程序。有关这些工具的详细信息，请参阅[监视个人数据违规行为](/security/office-365-security/monitor-for-leaks-of-personal-data.md)。
