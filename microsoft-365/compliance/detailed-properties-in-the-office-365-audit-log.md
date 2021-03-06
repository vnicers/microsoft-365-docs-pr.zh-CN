---
title: 审核日志中的详细属性
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- BCS160
- MET150
ms.assetid: ce004100-9e7f-443e-942b-9b04098fcfc3
description: 本文提供了导出 Office 365 审核日志记录的结果时包括的其他属性的说明。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0eed03602d1103806ef5560a792cc931e5266692
ms.sourcegitcommit: 929ca8f4d5fc006c3827f7a8b7d2b43e54c1b42a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46674600"
---
# <a name="detailed-properties-in-the-audit-log"></a>审核日志中的详细属性

从 Security & 合规中心导出审核日志搜索结果时，您可以选择下载符合搜索条件的所有结果。 为此，请选择 "**导出结果** \> "。在 "**审核日志搜索**" 页上**下载所有结果**。 有关详细信息，请参阅 [搜索审核日志](search-the-audit-log-in-security-and-compliance.md)。
  
 当您导出审核日志搜索的所有结果时，会将统一审核日志中的原始数据复制到一个逗号分隔值 (CSV) 文件下载到本地计算机。 此文件包含来自名为 **AuditData**的列中的每个审核记录的其他信息。 此列包含来自审核日志记录的多个属性的多值属性。 此多值属性中的每个 **属性：值** 对都用逗号分隔开。 
  
下表描述了 (的属性，具体取决于在多属性 **AuditData** 列中) 事件发生的服务。 **具有此属性列的 Office 365 服务**指示包含该属性的用户或管理员) 的活动服务和类型 (。 有关这些属性的详细信息或有关此主题中未列出的属性的详细信息，请参阅 [管理活动 API 架构](https://go.microsoft.com/fwlink/p/?LinkId=717993)。
  
> [!TIP]
> 您可以使用 Excel 中 Power Query 的 JSON 转换功能将 **AuditData** 列拆分为多个列，以便每个属性都有自己的列。 这让你能够对一个或多个属性进行排序和筛选。 若要了解如何执行此操作，请参阅 [导出、配置和查看审核日志记录](export-view-audit-log-records.md)。 
  
|**属性**|**说明**|**包含此属性的 Microsoft 365 服务**|
|:-----|:-----|:-----|
|Actor|执行操作的用户或服务帐户。|Azure Active Directory|
|AddOnName|在团队中添加、删除或更新的加载项的名称。 Microsoft 团队中的加载项类型为 bot、连接器或选项卡。|Microsoft Teams|
|AddOnType|在团队中添加、删除或更新的加载项的类型。 以下值指示加载项的类型。  <br/> **1** -表示机器人。<br/> **2** -指示连接器。<br/> **3** -指示一个选项卡。|Microsoft Teams|
|AzureActiveDirectoryEventType|Azure Active Directory 事件的类型。 以下值指示事件的类型。  <br/> **0** -指示帐户登录事件。<br/> **1** -指示 Azure 应用程序安全事件。|Azure Active Directory|
|ChannelGuid|Microsoft 团队频道的 ID。 通道所在的团队由 **TeamName** 和 **TeamGuid** 属性标识。|Microsoft Teams|
|ChannelName|Microsoft 团队频道的名称。 通道所在的团队由 **TeamName** 和 **TeamGuid** 属性标识。|Microsoft Teams|
|Client|用于登录事件的客户端设备、设备 OS 和设备浏览器 (例如，Nokia Lumia 920;Windows Phone 8;IE Mobile 11) 。|Azure Active Directory|
|ClientInfoString|有关用于执行此操作的电子邮件客户端的信息，例如浏览器版本、Outlook 版本和移动设备信息|Exchange (邮箱活动) |
|ClientIP|记录活动时使用的设备的 IP 地址。 IP 地址显示为 IPv4 或 IPv6 地址格式。<br/><br/> 对于某些服务，此属性中显示的值可能是代表用户调用服务的受信任应用程序（例如，Web 应用上的 Office）的 IP 地址，而不是执行活动的人员使用的设备的 IP 地址。 <br/><br/>此外，对于管理活动 (或由系统帐户) 对于与 Azure Active Directory 相关的事件执行的活动，不记录 IP 地址，ClientIP 属性的值为 `null` 。 |Azure Active Directory、Exchange、SharePoint|
|CreationTime|用户执行活动时的协调世界时 (UTC) 日期和时间。|全部|
|DestinationFileExtension|复制或移动的文件的文件扩展名。 仅对 FileCopied 和 FileMoved 用户活动显示此属性。|SharePoint|
|DestinationFileName|复制或移动文件的名称。 仅对 FileCopied 和 FileMoved 操作显示此属性。|SharePoint|
|DestinationRelativeUrl|在其中复制或移动文件的目标文件夹的 URL。 **SiteURL**、 **DestinationRelativeURL**和**destinationfilename 所**属性的值的组合与**ObjectID**属性的值相同，后者是复制的文件的完整路径名称）。 仅对 FileCopied 和 FileMoved 用户活动显示此属性。|SharePoint|
|EventSource|识别在 SharePoint 中发生的事件。 可能的值为 **SharePoint** 和 **ObjectModel**。|SharePoint|
|ExternalAccess|对于 Exchange 管理员活动，指定是由组织中的用户、Microsoft 数据中心人员或数据中心服务帐户还是由委派的管理员运行 cmdlet。 值 **False** 表示 cmdlet 由组织中的某人运行。 值 **True** 表示 cmdlet 由数据中心人员、数据中心服务帐户或委托的管理员运行。  <br/> 对于 "Exchange 邮箱活动"，指定是否由组织外部的用户访问邮箱。|Exchange|
|ExtendedProperties|Azure Active Directory 事件的扩展属性。|Azure Active Directory|
|ID|报告条目的 ID。 ID 唯一标识报告条目。|全部|
|InternalLogonType|仅供内部使用。|Exchange (邮箱活动) |
|ItemType|访问或修改的对象类型。 可能的值包括 **文件**、 **文件夹**、 **Web**、 **网站**、 **租户**和 **DocumentLibrary**。|SharePoint|
|LoginStatus|标识可能已发生的登录失败。|Azure Active Directory|
|LogonType|邮箱访问的类型。 以下值指示访问邮箱的用户的类型。  <br/><br/> **0** -指示邮箱所有者。<br/> **1** -指示管理员。<br/> **2** -指示一个代理。 <br/>**3** -指示 Microsoft 数据中心中的传输服务。<br/> **4** -表示 Microsoft 数据中心中的服务帐户。 <br/>**6** -表示委派管理员。|Exchange (邮箱活动) |
|MailboxGuid|访问邮箱的 Exchange GUID。|Exchange (邮箱活动) |
|MailboxOwnerUPN|拥有已访问邮箱的人员的电子邮件地址。|Exchange (邮箱活动) |
|Members|列出已在团队中添加或删除的用户。 以下值表示分配给用户的角色类型。  <br/><br/> **1** -指示所有者角色。<br/> **2** - 表示“成员”角色。<br/> **3** - 表示“来宾”角色。 <br/><br/>成员属性还包括组织的名称和成员的电子邮件地址。|Microsoft Teams|
|ModifiedProperties (Name、NewValue、OldValue) |属性包含在管理员事件中，例如将用户添加为网站或网站集管理组的成员。 该属性包括已修改的属性的名称 (例如，网站管理员组) 已修改属性的新值 (如添加为网站管理员的用户，以及已修改对象的以前的值。|所有 (管理活动) |
|ObjectId|对于 Exchange 管理员审核日志，通过 cmdlet 修改的对象的名称。  <br/> 对于 SharePoint 活动，是由用户访问的文件或文件夹的完整 URL 路径名称。  <br/> 对于 Azure AD 活动，为已修改的用户帐户的名称。|全部|
|Operation|用户或管理员活动的名称。 此属性的值对应于在 " **活动** " 下拉列表中选择的值。 如果选择了 " **显示所有活动的结果** "，则报告将包含所有服务的所有用户和管理员活动的条目。 有关记录在审核日志中的操作/活动的说明，请参阅在[Office 365 中搜索审核日志](search-the-audit-log-in-security-and-compliance.md)中的 "已**审核的活动**" 选项卡。  <br/> 对于 Exchange 管理员活动，此属性标识已运行的 cmdlet 名称。|全部|
|OrganizationId|您的组织的 GUID。|全部|
|路径|访问的邮件所在的邮箱文件夹的名称。 此属性还标识在其中创建或复制/移动邮件的文件夹。|Exchange (邮箱活动) |
|参数|对于 Exchange 管理员活动，与在 Operation 属性中标识的 cmdlet 一起使用的所有参数的名称和值。|Exchange (管理活动) |
|RecordType|记录指示的操作类型。 以下值指示记录类型。  <br/><br/> **1** -指示 Exchange 管理员审核日志中的记录。 <br/>**2** -指示对 singled 邮箱项目执行的操作的 Exchange 邮箱审核日志中的记录。 <br/>**3** -还指示 Exchange 邮箱审核日志中的记录。 此记录类型指示对源邮箱中的多个项目执行了该操作 (例如，将多个项目移动到 "已删除邮件" 文件夹或永久删除多个项目) 。 <br/>**4** -指示 SharePoint 中的网站管理员操作，例如管理员或用户分配对网站的权限。 <br/>**6** -指示 SharePoint 中与文件或文件夹相关的操作，例如用户查看或修改文件。 <br/>**8** -指示在 Azure Active Directory 中执行的管理员操作。 <br/>**9** -指示 Azure Active Directory 中的 OrgId 登录事件。 此记录类型已被弃用。 <br/>**10** -指示由 Microsoft 人员在数据中心执行的安全 cmdlet 事件。 <br/>**11** -指示 SharePoint 中的数据丢失保护 (DLP) 事件。<br/> **13** -当使用统一的 DLP 策略进行配置时，指示 Exchange 中的 DLP 事件。 基于 Exchange 邮件流规则的 DLP 事件 (也称为传输规则) 不受支持。<br>**14** -指示 SharePoint 中的共享事件。<br/> **15** -指示 Azure Active Directory 中的安全令牌服务 (STS) 登录事件。 <br/>**18** -表示安全 & 合规中心事件。 <br/>**19** -指示在非常短的时间内发生的重复性活动的聚合 Exchange 邮箱操作。 <br/>**20** -指示 Power BI 事件。 <br/>**21**-指示 Dynamics 365 事件。<br/>**22** -指示 Yammer 事件。 <br/>**23** -指示 Skype for business 事件。 <br/>**24** -指示电子数据展示事件。 此记录类型指示在安全与合规中心中运行内容搜索和管理电子数据展示事例所执行的活动。 有关详细信息，请参阅 [在审核日志中搜索电子数据展示活动](search-for-ediscovery-activities-in-the-audit-log.md)。<br/>**25、26或 27** -表示 Microsoft 团队活动。 <br/>**28** -指示来自 Exchange Online Protection 和 Office 365 高级威胁防护的网络钓鱼和恶意软件事件。<br/>**29** -指示来自 Exchange Online Protection 和 Office 365 高级威胁防护的提交事件。<br/>**30** -指示以前称为 microsoft Flow) 事件的 Microsoft Power 自动 (。<br/> **31** -指示高级电子数据展示事件。<br/> **32** -指示 Microsoft Stream 事件。<br/> **33** -指示与 SharePoint 中的 DLP 分类相关的事件。<br/>**35** -指示 Microsoft 项目事件。 <br/> **36** -指示 SharePoint 列表事件。<br/>**37** -指示与 SharePoint 注释相关的事件。 <br/>**38** -指示与安全与合规中心中的保留策略和保留标记相关的事件。  <br/>**40** -指示安全性和合规性警报信号中产生的事件。<br/> **41** -指示 Office 365 高级威胁防护中的安全链接时间段和阻止覆盖事件。<br/>**42** -指示与 Security & 合规中心中的见解和报告相关的事件。<br/>**44** -指示 Workplace Analytics 事件。 <br/>**45** -指示电源应用事件。 <br/> **47** -指示 SharePoint、OneDrive 和 Microsoft 团队中的文件的来自 Office 365 高级威胁防护的网络钓鱼和恶意软件事件。<br/> **49** -指示适用于医疗保健的 Microsoft 团队中的 [患者应用程序](https://docs.microsoft.com/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-audit) 事件。 <br/>**50** -指示与 MailItemsAccessed 邮箱审核操作相关的事件。 <br/>**51** 表示与反垃圾邮件和邮件卫生相关的事件。 <br/>**52** -指示与数据见解 REST API 相关的事件。<br/>**53** -指示与信息屏障策略的应用程序相关的事件。 有关详细信息，请参阅 [定义信息障碍策略](information-barriers-policies.md)。 <br/>**54** -指示 SharePoint 列表项事件。<br/>**55** -指示 SharePoint 内容类型事件。<br/> **56** -指示 SharePoint 列表字段事件。 <br/>**62** -指示与电子邮件攻击市场活动相关的事件。 有关详细信息，请参阅 [Office 365 ATP 中的市场活动视图](https://docs.microsoft.com/microsoft-365/security/office-365-security/campaigns)。<br/>**64** -指示自动调查和响应事件。 有关信息，请参阅 [Office 365 中的自动化调查和响应 (AIR) ](../security/office-365-security/automated-investigation-response-office.md)<br/>**65** -指示隔离审核记录事件。<br/>**66** -指示 Microsoft Forms 事件。<br/>**68** -指示 Exchange 中的通信合规性事件。 有关详细信息，请参阅 [Microsoft 365 中的通信合规性](communication-compliance.md)。<br/>**69** -指示与客户密钥加密相关的事件。 有关详细信息，请参阅 [Office 365 中的使用客户密钥的服务加密](customer-key-overview.md)。 
|ResultStatus|指示操作属性中 (指定 **的操作是否** 成功) 。  <br/> 对于 Exchange 管理员活动，值为 **True** (成功) 或 **False** (失败) 。|全部  <br/>|
|SecurityComplianceCenterEventType|指示活动是安全 & 合规中心事件。 所有安全 & 合规性中心活动的值都为此属性的值为 **0** 。|安全与合规中心|
|SharingType|分配给用户的共享权限类型，该用户是与资源共享的。 此用户在 **UserSharedWith** 属性中进行标识。|SharePoint|
|Site|用户访问的文件或文件夹所在网站的 GUID。|SharePoint|
|SiteUrl|用户访问的文件或文件夹所在网站的 URL。|SharePoint|
|SourceFileExtension|用户访问的文件的文件扩展名。 如果访问对象是一个文件夹，则此属性为空。|SharePoint|
|SourceFileName|用户访问的文件或文件夹名称。|SharePoint|
|SourceRelativeUrl|包含用户访问文件的文件夹的 URL。 **SiteURL**、 **SourceRelativeURL**和**SourceFileName**属性的值的组合与**ObjectID**属性的值相同，后者是用户访问的文件的完整路径名称）。|SharePoint|
|主题|访问的邮件的主题行。|Exchange (邮箱活动) |
|TabType| 在团队中添加、删除或更新的选项卡的类型。 此属性的可能值为：  <br/><br/> **Excel pin** -excel 选项卡。  <br/> **扩展** -所有第一方和第三方应用;如类计划、VSTS 和窗体。  <br/> **备注** -OneNote 选项卡。  <br/> **Pdfpin** -PDF 选项卡。  <br/> **Powerbi** -一个 Powerbi 选项卡。  <br/> **Powerpointpin** -一个 PowerPoint 选项卡。  <br/> **Sharepointfiles** -A SharePoint 选项卡。  <br/> **网页** -"固定的网站" 选项卡。  <br/> **Wiki-选项卡** -wiki 选项卡。  <br/> **Wordpin** -一个 Word 选项卡。|Microsoft Teams|
|Target|操作 (在 **Operation** 属性中标识的用户已在执行) 。 例如，如果将来宾用户添加到 SharePoint 或 Microsoft 团队，则该用户将在此属性中列出。|Azure Active Directory|
|TeamGuid|Microsoft 团队中的团队的 ID。|Microsoft Teams|
|TeamName|Microsoft 团队中的团队的名称。|Microsoft Teams|
|UserAgent|有关用户浏览器的信息。 此信息由浏览器提供。|SharePoint|
|UserDomain|有关执行操作的用户 (主角) 的用户租户组织的标识信息。|Azure Active Directory|
|UserID|执行操作的用户 (在 **操作** 属性) 中指定，从而导致记录记录。 审核日志中还包含由系统帐户 (（如 SHAREPOINT\system 或 NT AUTHORITY\SYSTEM) ）执行的活动的审核记录。 UserId 属性的另一个常见值为 app@sharepoint。 这表明执行活动的“用户”是在 SharePoint 中拥有必要权限的应用程序，代表用户、管理员或服务执行组织范围内操作（例如，搜索 SharePoint 网站或 OneDrive 帐户）。 有关详细信息，请参阅[审核记录中的 app\@sharepoint 用户](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records)。 |全部|
|UserKey|在 **UserID** 属性中标识的用户的替代 ID。 例如，使用用户在 SharePoint 中执行的事件的 passport 唯一 ID (PUID) 填充此属性。 此属性还可能指定与其他服务和系统帐户执行的事件中发生的事件的 **UserID** 属性相同的值。|全部|
|UserSharedWith|与之共享资源的用户。 如果 **Operation** 属性的值为 **SharingSet**，则包含此属性。 此用户也在报告中的 " **共享与** " 列中列出。|SharePoint|
|UserType|执行操作的用户类型。 以下值指示用户类型。 <br/> <br/> **0** -常规用户。 <br/>**2** -Microsoft 365 组织中的管理员。<sup>1</sup> <br/>**3** -Microsoft 数据中心管理员或数据中心系统帐户。 <br/>**4** -系统帐户。 <br/>**5** -应用程序。 <br/>**6** -服务主体。<br/>**7** -自定义策略。<br/>**8** -系统策略。|全部|
|版本|指示由已记录的 **Operation** 属性) 标识的活动 (的版本号。|全部|
|Workload|发生活动的 Microsoft 365 服务。|全部|
||||

> [!NOTE]
><sup>1</sup> 对于与 Azure Active Directory 相关的事件，审核记录中不使用管理员的值。 审核由管理员执行的活动的记录将指示常规用户 (例如， **UserType： 0**) 执行了该活动。 **UserID**属性将标识执行活动的人员 (常规用户或管理员) 。<br/>

当您查看特定事件的详细信息时，还会显示上述属性（如果您单击 " **详细信息** "）。
  
![单击“详细信息”，查看审核日志事件记录的详细属性](../media/6df582ae-d339-4735-b1a6-80914fb77a08.png)
