---
title: Microsoft 365 中的记录管理入门
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
description: 需要用于管理高价值内容的 Microsoft 365 记录管理解决方案以满足法律、业务或法规方面的义务，但不确定从哪里入手？ 请阅读一些实用指南来完成入门。
ms.openlocfilehash: fd3e3368b7a23cb31a8df4953268576de2419f89
ms.sourcegitcommit: b06a4f21da247edb03fdf6a01eafb7d4fb387b33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "48333848"
---
# <a name="get-started-with-records-management"></a>记录管理入门

>*[Microsoft 365 安全性与合规性许可指南](https://aka.ms/ComplianceSD)。*

准备好开始使用 Microsoft 365 中的记录管理解决方案来管理组织的高价值内容以满足法律、业务或法规方面的义务了吗？ 请遵循下面的简要指南来完成入门：

1. **了解记录管理解决方案**以及在将文档和电子邮件声明为记录时允许或阻止的操作：[了解记录管理](records-management.md)。 

2. **了解保留标签和保留机制的工作原理**（针对 SharePoint 和 Exchange），因为保留标签将用于声明记录：[了解保留策略和保留标签](retention.md)

3. 通过[导入现有计划](file-plan-manager.md#import-retention-labels-into-your-file-plan )（如果有）或[创建用于声明记录的新保留标签](declare-records.md)来**创建有关保留设置和操作的文件计划**。

4. **发布并应用保留标签**。 保留标签是可重用的构建基块，可用于多个策略中，并可纳入用户工作流中： 
    
    - [创建保留标签并在应用中应用它们](create-apply-retention-labels.md)
    - [自动向内容应用保留标签](apply-retention-labels-automatically.md)

## <a name="subscription-and-licensing-requirements-for-records-management"></a>记录管理的订阅和许可要求

许多不同的订阅都支持记录管理，并且用户的许可要求取决于你使用的功能。

若要查看许可用户以便受益于 Microsoft 365 合规性功能的选项，请参阅 [Microsoft 365 安全性与合规性许可指南](https://aka.ms/ComplianceSD)。 对于记录保留，请参阅[记录管理](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management)部分和相关 PDF 或 Excel 下载内容，以了解功能级别许可要求。

## <a name="permissions-required-for-records-management"></a>记录管理所需的权限

负责记录管理的合规性团队成员必须有权访问 [Microsoft 365 合规中心](https://compliance.microsoft.com/)。 默认情况下，租户管理员（全局管理员）有权访问此位置，并可向合规专员和其他人提供访问权限，而不为其提供租户管理员的所有权限。若要授予实现此有限管理的权限，建议将用户添加到**记录管理**管理员角色组，这将为其授予 **RecordManagement** 角色。

此角色组中包含的权限不包括[处置评审和验证](disposition.md)所需的权限，并且即使是全局管理员，默认情况下也没有此权限。 若要管理处置，可通过创建自定义角色组或使用包含此角色的默认角色组（例如**合规性管理员**）来使用**处置管理** 角色。

有关这些角色组和角色的详细信息，请参阅[安全与合规中心内的权限](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center#roles-in-the-security--compliance-center)。

有关将用户添加到角色组并分配角色的说明，请参阅[向用户授予对安全与合规中心的访问权限](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center)。

只有在创建、配置和应用用于声明记录和管理处置的保留标签时才需要这些权限。 配置这些标签的人员不需要访问该内容。

## <a name="common-scenarios-for-records-management"></a>记录管理常见方案

请使用下表将业务需求与记录管理支持的方案对应起来。

> [!NOTE]
> 由于记录管理使用保留标签将项目标记为记录，因此此表中的许多方案还会列为[保留策略和保留标签常见方案](get-started-with-retention.md#common-scenarios-for-retention-policies-and-retention-labels)。

|我想...|文档|
|----------------|---------------|
|声明记录 |[使用保留标签声明记录](declare-records.md)|
|更新记录 |[使用记录版本控制来更新存储在 SharePoint 或 OneDrive 中的记录](record-versioning.md)|
|让管理员和用户手动为文档和电子邮件应用保留和删除操作： <br />- SharePoint <br />- OneDrive <br />- Outlook 和 Outlook 网页版|[创建保留标签并在应用中应用它们](create-apply-retention-labels.md)|
|让网站管理员为 SharePoint 库、文件夹或文档集中的所有内容设置默认保留和删除操作|[创建保留标签并在应用中应用它们](create-apply-retention-labels.md)|
|让用户使用 Outlook 规则向电子邮件自动应用保留和删除操作|[创建保留标签并在应用中应用它们](create-apply-retention-labels.md)|
|让管理员向文档理解模型应用保留和删除操作，以便将这些操作自动应用于 SharePoint 库中已标识的文档|[创建保留标签并在应用中应用它们](create-apply-retention-labels.md)|
|向文档和电子邮件自动应用保留和删除操作 |[自动向内容应用保留标签](apply-retention-labels-automatically.md)|
|从事件发生时开始计算保留期，比如：  <br />- 员工离开组织 <br />- 合同到期 <br />- 产品生存期结束| [从事件发生时开始计算保留期](event-driven-retention.md)|
|管理 SharePoint 中不同文档类型的生命周期| [使用保留标签管理 SharePoint 中存储的文档的生命周期](auto-apply-retention-labels-scenario.md)|
|确保内容在内容保留期结束时被永久删除之前，有人进行评审和批准|[处置评审](disposition.md#disposition-reviews) |
|对在保留期结束时永久删除的内容有处置证明|[处置记录](disposition.md#disposition-of-records) |
|监视将保留和删除设置应用于项目的方式和位置 | [监视保留标签](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation-for-records"></a>有关记录的最终用户文档

在 Microsoft 365 应用中，用于记录管理的保留标签具有 UI 表现形式。 请务必在将保留标签部署到生产网络前，为最终用户和技术支持人员提供指导。

最有效的最终用户文档将是你针对所选保留标签名称和配置提供的定制指南和说明。 不过，可以使用以下信息作为基本说明：

- [手动应用保留标签](create-apply-retention-labels.md#manually-apply-retention-labels)
