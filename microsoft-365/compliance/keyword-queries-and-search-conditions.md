---
title: 内容搜索的关键字查询和搜索条件
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
f1_keywords:
- ms.o365.cc.SearchQueryLearnMore
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: c4639c2e-7223-4302-8e0d-b6e10f1c3be3
ms.custom:
- seo-marvel-apr2020
description: 了解可以在 Office 365 安全 & 合规中心中搜索的电子邮件和文件属性。
ms.openlocfilehash: fb3d0b9d941658f2613344d00984dbe7846565a6
ms.sourcegitcommit: 66f1f430b3dcae5f46cb362a32d6fb7da4cff5c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2020
ms.locfileid: "46662296"
---
# <a name="keyword-queries-and-search-conditions-for-content-search"></a>内容搜索的关键字查询和搜索条件

本主题介绍了在 Exchange Online 中的电子邮件项目和存储在 SharePoint 和 OneDrive for business 网站上的电子邮件项目中，可以使用安全 & 合规中心中的内容搜索功能搜索的电子邮件和文档属性。 您还可以在 Security & 合规性中心 PowerShell 中使用** \* -new-compliancesearch** cmdlet 搜索这些属性。 本主题还介绍了以下内容：   
  
- 使用布尔搜索运算符、搜索条件和其他搜索查询技术来优化搜索结果。
    
- 在 SharePoint 和 OneDrive for Business 中搜索敏感数据类型和自定义敏感数据类型。
    
- 搜索与组织外部用户共享的网站内容
    
有关如何创建内容搜索的分步说明，请参阅 [Office 365 中的内容搜索](content-search.md)。

  
> [!NOTE]
> Security & 合规性中心中的内容搜索和安全 & 合规中心 PowerShell 中的相应** \* new-compliancesearch** Cmdlet 使用关键字查询语言 (KQL) 。 有关更多详细信息，请参阅 [关键字查询语言语法参考](https://go.microsoft.com/fwlink/?LinkId=269603)。 
  
## <a name="searchable-email-properties"></a>可搜索的电子邮件属性

下表列出了可使用安全性 & 合规性中心中的内容搜索功能或通过使用 **new-compliancesearch** 或 **new-compliancesearch** cmdlet 搜索的电子邮件属性。 该表包括属性的一个示例：每个属性的  _值_ 语法和示例返回的搜索结果的说明。 您可以  `property:value` 在 "关键字" 框中为内容搜索键入这些对。 

> [!NOTE]
> 搜索电子邮件属性时，不能搜索指定属性为空或为空的项目。 例如，使用 " *属性：值* 对的值对" **主题： ""** 搜索具有空主题行的电子邮件将返回零个结果。 这也适用于搜索网站和联系人属性。
  
|**属性**|**属性描述**|**示例**|**示例返回的搜索结果**|
|:-----|:-----|:-----|:-----|
|AttachmentNames|电子邮件附件的文件名。|`attachmentnames:annualreport.ppt`  <br/> `attachmentnames:annual*` <br/> attachmentnames:.pptx|含有名称为 annualreport.ppt 的附件的邮件。 在第二个示例中，使用通配符返回附件名中带有单词"annual"的邮件。 第三个示例返回具有 .pptx 文件扩展名的所有附件。|
|Bcc|电子邮件的 "密件抄送" 字段。<sup>1</sup>|`bcc:pilarp@contoso.com`  <br/> `bcc:pilarp`  <br/> `bcc:"Pilar Pinilla"`|所有示例都返回"密件抄送"字段中包含"Pilar Pinilla"的邮件。|
|Category| 搜索类别。 用户可以通过使用 Outlook 或 web 上的 Outlook (以前称为 Outlook Web App) 来定义类别。 可能的值是：  <br/><br/>  蓝色  <br/>  绿色  <br/>  橙色  <br/>  紫色  <br/>  红色  <br/>  黄色|`category:"Red Category"`|在源邮箱中已指定红色类别的邮件。|
|抄送|电子邮件的 "抄送" 字段。<sup>1</sup>|`cc:pilarp@contoso.com`  <br/> `cc:"Pilar Pinilla"`|在这两个示例中，在 "抄送" 字段中指定了包含 Pilar Pinilla 的邮件。|
|Folderid|特定邮箱文件夹的文件夹 ID (GUID) 。 如果使用此属性，请务必搜索指定文件夹所在的邮箱。 将仅搜索指定的文件夹。 不会搜索文件夹中的所有子文件夹。 若要搜索子文件夹，您需要使用要搜索的子文件夹的 Folderid 属性。  <br/> 有关搜索 Folderid 属性和使用脚本获取特定邮箱的文件夹 Id 的详细信息，请参阅 [使用目标集合的内容搜索](use-content-search-for-targeted-collections.md)。|`folderid:4D6DD7F943C29041A65787E30F02AD1F00000000013A0000`  <br/> `folderid:2370FB455F82FC44BE31397F47B632A70000000001160000 AND participants:garthf@contoso.com`|第一个示例返回指定邮箱文件夹中的所有项目。 第二个示例返回指定邮箱文件夹中由 garthf@contoso.com 发送或接收的所有项目。|
|发件人|电子邮件的发件人。<sup>1</sup>|`from:pilarp@contoso.com`  <br/> `from:contoso.com`|由指定用户或指定域发送的邮件。|
|HasAttachment|指示邮件是否包含附件。 使用值 **true** 或 **false**。|`from:pilar@contoso.com AND hasattachment:true`|由指定用户发送的包含附件的邮件。|
|Importance|The importance of an email message, which a sender can specify when sending a message. By default, messages are sent with normal importance, unless the sender sets the importance as **high** or **low**.  |`importance:high`  <br/> `importance:medium`  <br/> `importance:low`|将重要性标记为高、中等或低的邮件。|
|IsRead|指示是否已读取邮件。 使用值 **true** 或 **false**。|`isread:true`  <br/> `isread:false`|第一个示例返回 IsRead 属性设置为 **True**的邮件。 第二个示例返回 IsRead 属性设置为 **False**的邮件。|
|ItemClass|使用此属性可搜索组织导入到 Office 365 中的特定第三方数据类型。 对此属性使用以下语法：  `itemclass:ipm.externaldata.<third-party data type>*`|`itemclass:ipm.externaldata.Facebook* AND subject:contoso`  <br/> `itemclass:ipm.externaldata.Twitter* AND from:"Ann Beebe" AND "Northwind Traders"`|第一个示例返回在 Subject 属性中包含 "contoso" 一词的 Facebook 项目。 第二个示例返回由王小姐 Beebe 发布且包含关键字短语 "罗斯文商贸" 的 Twitter 项目。  <br/> 有关 ItemClass 属性的第三方数据类型要使用的值的完整列表，请参阅 [使用内容搜索来搜索导入到 Office 365 的第三方数据](use-content-search-to-search-third-party-data-that-was-imported.md)。|
|Kind| 要搜索的电子邮件的类型。 可能的值：  <br/>  联系人  <br/>  文档  <br/>  电子邮件  <br/>  externaldata  <br/>  传真  <br/>  即时消息  <br/>  日志  <br/>  会议  <br/>  microsoftteams (返回 Microsoft 团队中的聊天、会议和呼叫中的项目)   <br/>  注释  <br/>  公告  <br/>  RSS 源  <br/>  任务  <br/>  语音邮件|`kind:email`  <br/> `kind:email OR kind:im OR kind:voicemail`  <br/> `kind:externaldata`|第一个示例返回满足搜索条件的电子邮件。 第二个示例返回电子邮件、即时消息对话 (，其中包括 Microsoft 团队中的 Skype for Business 对话和聊天) 以及符合搜索条件的语音邮件。 第三个示例返回从 Microsoft 365 中的邮箱导入的项目，这些项目是符合搜索条件的第三方数据源（如 Twitter、Facebook 和 Cisco Jabber）中的邮箱。 有关详细信息，请参阅 [在 Office 365 中存档第三方数据](https://www.microsoft.com/?ref=go)。|
|Participants|电子邮件中的所有人员字段。 这些字段分别为 "发件人"、"收件人" 和 "密件抄送"。<sup>1</sup>|`participants:garthf@contoso.com`  <br/> `participants:contoso.com`|发送自/到 garthf@contoso.com 的邮件。第二个示例返回 contoso.com 域中的用户发送的所有邮件或发送至 contoso.com 域中的用户的所有邮件。|
|Received|收件人接收电子邮件的日期。|`received:04/15/2016`  <br/> `received>=01/01/2016 AND received<=03/31/2016`|2016年4月15日收到的邮件。 第二个示例返回在2016年1月1日到2016年3月31日之间收到的所有邮件。|
|收件人|电子邮件中的所有收件人字段。 这些字段分别为 "收件人"、"抄送" 和 "密件抄送"。<sup>1</sup>|`recipients:garthf@contoso.com`  <br/> `recipients:contoso.com`|发送到 garthf@contoso.com 的邮件。第二个示例返回发送至 contoso.com 域中任何收件人的邮件。|
|Sent|发件人发送电子邮件的日期。|`sent:07/01/2016`  <br/> `sent>=06/01/2016 AND sent<=07/01/2016`|在指定日期或指定日期范围内发送的邮件。|
|Size|邮件的大小（以字节为单位）。|`size>26214400`  <br/> `size:1..1048567`|大于25的邮件？？10mb. 第二个示例返回大小介于 1 到 1,048,567 (1 MB) 字节之间的邮件。|
|Subject|电子邮件主题行中的文本。  <br/> **注意：** 在查询中使用 Subject 属性时，搜索将返回主题行中包含您要搜索的文本的所有邮件。 换言之，查询不会仅返回那些具有完全匹配的邮件。 例如，如果您搜索，则  `subject:"Quarterly Financials"` 结果将包含主题为 "季度财务 2018" 的邮件。|`subject:"Quarterly Financials"`  <br/> `subject:northwind`|在主题行文本中的任意位置包含短语 "季度财务" 的邮件。 第二个示例返回主题行中包含单词"northwind"的所有邮件。|
|收件人|电子邮件的"收件人"字段。<sup>1</sup>|`to:annb@contoso.com`  <br/> `to:annb ` <br/> `to:"Ann Beebe"`|所有示例返回在"收件人:"行中指定为 Ann Beebe 的邮件。|
|||||
   
> [!NOTE]
> <sup>1</sup> 对于收件人属性的值，可以使用电子邮件地址 (也称为 *用户主体名称* 或 UPN) 、显示名称或别名来指定用户。 例如，你可以使用 annb@contoso.com、annb 或"Ann Beebe"指定用户 Ann Beebe。<br/><br/>在搜索 (From、To、Cc、Bcc、参与者和收件人) 的任何收件人属性时，Microsoft 365 将尝试通过在 Azure Active Directory 中进行查找来扩展每个用户的标识。  如果在 Azure Active Directory 中找到用户，则查询将展开，以包含用户的电子邮件地址 (或 UPN) 、别名、显示名称和 LegacyExchangeDN。<br/><br/>例如， `participants:ronnie@contoso.com` 扩展到的查询 `participants:ronnie@contoso.com OR participants:ronnie OR participants:"Ronald Nelson" OR participants:"<LegacyExchangeDN>"` 。<br/><br/>若要防止收件人展开，可以在搜索查询中向电子邮件地址的末尾添加通配符 (星号) 的字符。例如， `participants:ronnie@contoso.com*` 。

## <a name="searchable-site-properties"></a>可搜索网站属性

下表列出了一些 SharePoint 和 OneDrive for business 属性，可以使用安全 & 合规性中心中的内容搜索功能或使用 **new-compliancesearch** 或 **new-compliancesearch** cmdlet 搜索这些属性。 该表包括属性的一个示例：每个属性的  _值_ 语法和示例返回的搜索结果的说明。 
  
有关可搜索的 SharePoint 属性的完整列表，请参阅 [sharepoint 中的已爬网和托管属性概述](https://go.microsoft.com/fwlink/p/?LinkId=331599)。 可以在可**查询**的列中搜索 **"是" 标记为 "是"** 的属性。 
  
|**属性**|**属性描述**|**示例**|**示例返回的搜索结果**|
|:-----|:-----|:-----|:-----|
|作者|作者字段位于 Office 文档中，复制文档后仍然存在其中。 例如，如果用户创建一个文档，并将其发送给其他人，然后再将其上载到 SharePoint，则该文档仍将保留原作者。 请务必对此属性使用用户的显示名称。|`author:"Garth Fort"`|所有文档的作者均为 Garth Fort。|
|ContentType|项目的 SharePoint 内容类型，如项目、文档或视频。|`contenttype:document`|将返回所有文档。|
|已创建|创建项目的日期。|`created>=06/01/2016`|在2016年6月1日或之后创建的所有项目。|
|CreatedBy|创建或上载项目的人员。 请务必对此属性使用用户的显示名称。|`createdby:"Garth Fort"`|所有项目均由 Garth Fort 创建或上载。|
|DetectedLanguage|项目的语言。|`detectedlanguage:english`|所有项目均为英语。|
|DocumentLink|SharePoint 或 OneDrive for business 网站上特定文件夹的路径 (URL) 。 如果使用此属性，请务必搜索指定文件夹所在的网站。  <br/> 若要返回在为 documentlink 属性指定的文件夹的子文件夹中的项目，您必须将/添加 \* 到指定文件夹的 URL; 例如，  `documentlink: "https://contoso.sharepoint.com/Shared Documents/*"`  <br/> <br/>有关搜索 documentlink 属性和使用脚本获取特定网站上的文件夹的 documentlink Url 的详细信息，请参阅 [使用目标集合的内容搜索](use-content-search-for-targeted-collections.md)。|`documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Private"`  <br/> `documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Shared with Everyone/*" AND filename:confidential`|第一个示例返回指定的 OneDrive for Business 文件夹中的所有项目。 第二个示例返回指定站点文件夹中的文档 (以及文件名中包含单词 "保密" 的所有子文件夹) 。|
|文件扩展名|文件的扩展名;例如，.docx、one、.pptx 或 .xlsx。|`fileextension:xlsx`|Excel 2007 及更高版本 (的所有 Excel 文件) |
|FileName|文件的名称。|`filename:"marketing plan"`  <br/> `filename:estimate`|第一个示例返回标题中具有完全匹配短语“marketing plan”的文件。第二个示例返回文件名中具有单词“estimate”的文件。|
|LastModifiedTime|项目的上次更改日期。|`lastmodifiedtime>=05/01/2016`  <br/> `lastmodifiedtime>=05/10/2016 AND lastmodifiedtime<=06/1/2016`|第一个示例返回在2016年5月1日或之后更改的项。 第二个示例返回在5月1日、2016和6月1日之间更改的项目2016。|
|ModifiedBy|上次更改项目的人员。 请务必对此属性使用用户的显示名称。|`modifiedby:"Garth Fort"`|由 Garth Fort 最后更改的所有项目。|
|路径|SharePoint 或 OneDrive for business 网站中特定网站 (URL) 的路径。  <br/> 若要返回在为 path 属性指定的网站中的文件夹中的项目，您必须将/添加 \* 到指定网站的 URL; 例如，  `path: "https://contoso.sharepoint.com/Shared Documents/*"`  <br/> <br/> **注意：** 使用该  `Path` 属性搜索 OneDrive 位置不会在搜索结果中返回媒体文件，如 .png、tiff 或 .wav 文件。 在搜索查询中使用不同的 site 属性搜索 OneDrive 文件夹中的媒体文件。 <br/>|`path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/"`  <br/> `path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/*" AND filename:confidential`|第一个示例返回指定的 OneDrive for business 网站中的所有项目。 第二个示例返回指定网站中的文档 (和包含文件名中的 "机密" 一词的 "网站) 中的文件夹。|
|SharedWithUsersOWSUser|与指定用户共享并显示在用户的 OneDrive for business 网站中的 " **与我共享** " 页上的文档。 这些文档已与组织中的其他人员明确与指定的用户共享。 当您导出与使用 SharedWithUsersOWSUser 属性的搜索查询匹配的文档时，文档将从与指定用户共享文档的人员的原始内容位置导出。 有关详细信息，请参阅 [搜索组织中共享的网站内容](#searching-for-site-content-shared-within-your-organization)。|`sharedwithusersowsuser:garthf`  <br/> `sharedwithusersowsuser:"garthf@contoso.com"`|这两个示例都将返回所有已与 Garth Fort 显式共享且显示在 Garth Fort 的 OneDrive for business 帐户中的 " **与我共享** " 页上的内部文档。|
|Site|组织中站点或站点组的 URL。|`site:"https://contoso-my.sharepoint.com"`  <br/> `site:"https://contoso.sharepoint.com/sites/teams"`|第一个示例返回组织中所有用户的 OneDrive for Business 网站中的项目。 第二个示例返回所有团队网站中的项目。|
|Size|邮件的大小（以字节为单位）。|`size>=1`  <br/> `size:1..10000`|第一个示例返回大于 1 字节的项目。第二个示例返回大小介于 1 到 10,000 字节之间的项目。|
|标题|文档的标题。 Title 属性是在 Microsoft Office 文档中指定的元数据。 它不同于文档的文件名。|`title:"communication plan"`|Office 文档的 Title 元数据属性中包含短语“communication plan”的任何文档。|
|||||
   
## <a name="searchable-contact-properties"></a>可搜索联系人属性

下表列出了已编制索引且您可以搜索使用内容搜索的联系人属性。 这些属性是用户可为联系人配置的属性，这些属性也称为 "个人联系人") 位于用户邮箱的 "个人通讯簿" 中 (。 若要搜索联系人，可以选择要搜索的邮箱，然后在关键字查询中使用一个或多个联系人属性。
  
> [!TIP]
> 若要搜索包含空格或特殊字符的值，请使用双引号 ( "" ) 以包含短语;例如，  `businessaddress:"123 Main Street"` 。 
  
|**属性**|**属性描述**|
|:-----|:-----|
|BusinessAddress|" **商务地址** " 属性中的地址。 该属性也称为 "联系人属性" 页上的 " **工作** 地址"。|
|BusinessPhone|任何 **业务电话** 号码属性中的电话号码。|
|CompanyName|**Company**属性中的名称。|
|Department|**部门**属性中的名称。|
|DisplayName|联系人的显示名称。 这是联系人的 " **全名** " 属性中的名称。|
|EmailAddress|联系人的任何电子邮件地址属性的地址。 用户可以添加联系人的多个电子邮件地址。 使用此属性将返回与联系人的任何电子邮件地址相匹配的联系人。|
|FileAs|**File as**属性。 此属性用于指定联系人在用户的联系人列表中的列出方式。 例如，可以将联系人列为  *firstname、lastname*  或  *lastname、名字*。|
|GivenName|" **First name** " 属性中的名称。|
|HomeAddress|任何 " **住宅** 地址" 属性中的地址。|
|HomePhone|任何 " **住宅** 电话号码" 属性中的电话号码。|
|IMAddress|IM 地址属性，通常是用于即时消息的电子邮件地址。|
|MiddleName|**中间**名属性中的名称。|
|MobilePhone|" **移动** 电话号码" 属性中的电话号码。|
|Nickname|**昵称**属性中的名称。|
|OfficeLocation|**Office**或**office location**属性中的值。|
|OtherAddress|**其他**地址属性的值。|
|Surname|" **Last** name" 属性中的名称。|
|标题|" **职务" 属性中** 的标题。|
|||||

## <a name="searchable-sensitive-data-types"></a>可搜索敏感数据类型

您可以使用 "安全和合规中心" 中的内容搜索功能来搜索存储在 SharePoint 和 OneDrive for business 网站上的文档中的敏感数据（如信用卡号或社会保险号）。 可以通过  `SensitiveType` 在关键字查询中使用属性和敏感信息类型的名称来执行此操作。 例如，查询  `SensitiveType:"Credit Card Number"` 返回包含信用卡号的文档。 查询  `SensitiveType:"U.S. Social Security Number (SSN)"` 返回包含美国社会安全号码的文档。 若要查看可以搜索的敏感数据类型的列表，请转到**Classifications** \> Security & 合规性中心中的 "分类**敏感信息类型**"。 或者，您可以使用 Security & 合规性中心 PowerShell 中的 **DlpSensitiveInformationType** cmdlet 来显示敏感信息类型的列表。 
  
您还可以使用  `SensitiveType` 属性来搜索您 (的自定义敏感信息类型的名称，或为您的组织创建的其他管理员) 。 您可以使用 Security & 合规性中心中的 "**敏感信息类型**" 页上的 "**发布者**" 列 (或 PowerShell) 中的**Publisher**属性来区分内置和自定义的敏感信息类型。 有关详细信息，请参阅 [创建自定义敏感信息类型](create-a-custom-sensitive-information-type.md)。
  
有关使用属性创建查询的详细信息  `SensitiveType` ，请参阅 [窗体 a 查询来查找存储在网站上的敏感数据](form-a-query-to-find-sensitive-data-stored-on-sites.md)。

> [!NOTE]
> 您不能使用敏感数据类型和 `SensitiveType` search 属性在 Exchange Online 邮箱中搜索敏感数据。 但是，可以使用数据丢失防护 (DLP) 策略来保护传输中的敏感 emaill 数据。 有关详细信息，请参阅 [数据丢失防护策略概述](data-loss-prevention-policies.md) 和 [搜索和查找个人数据](search-for-and-find-personal-data.md)。
  
## <a name="search-operators"></a>搜索运算符

布尔搜索运算符（如 **AND**、 **OR**和 **NOT**）可帮助您通过在搜索查询中包含或排除特定单词来定义更精确的搜索。 其他技术，如使用属性运算符 (如 \> = 或.。) 、引号、圆括号和通配符，可帮助您优化搜索查询。 下表列出了可用于缩小或拓宽搜索结果范围的运算符。 
  
|**运算符**|**用法**|**说明**|
|:-----|:-----|:-----|
|AND|keyword1 AND keyword2|返回包含所有指定关键字或表达式的项  `property:value` 。 例如，  `from:"Ann Beebe" AND subject:northwind` 将返回王小姐 Beebe 发送的所有邮件，其中包含 "主题" 行中的 "罗斯文" 一词。 <sup>2</sup>|
|+|keyword1 + keyword2 + keyword3|Returns items that contain  *either*  `keyword2` or  `keyword3` *and*  that also contain  `keyword1`. Therefore, this example is equivalent to the query  `(keyword2 OR keyword3) AND keyword1`.  <br/> 该查询  `keyword1 + keyword2` (符号) 后面有一个空格 **+** **，而** 不是使用 AND 运算符。 This query would be equivalent to  `"keyword1 + keyword2"` and return items with the exact phase  `"keyword1 + keyword2"`.|
|OR|keyword1 OR keyword2|返回包含一个或多个指定关键字或表达式的项  `property:value` 。 <sup>2</sup>|
|NOT|keyword1 NOT keyword2  <br/> NOT from:"Ann Beebe"  <br/> 不是种类： im|排除由关键字或表达式指定的项目  `property:value` 。 在第二个示例中，排除王小姐 Beebe 发送的邮件。 第三个示例排除了所有即时消息对话，例如保存到对话历史记录邮箱文件夹中的 Skype for Business 对话。 <sup>2</sup>|
|-|keyword1 -keyword2|与 **NOT** 运算符作用相同。 因此，此查询将返回包含  `keyword1` 和将排除包含的项的项  `keyword2` 。|
|NEAR|keyword1 NEAR(n) keyword2|返回包含邻近字词的项目，其中 n 表示间隔的字词数量。 例如， `best NEAR(5) worst` 返回任何一个 "最差" 为 "最佳" 的五个字中的项。 如果您没有指定数目，则默认距离是 8 个字词。 <sup>2</sup>|
|:|property:value|冒号 (：语法中的 )  `property:value` 指定要搜索的属性的值包含指定的值。 例如，  `recipients:garthf@contoso.com` 返回发送至 garthf@contoso.com 的所有邮件。|
|=|属性 = 值|与 **：** 运算符相同。|
|\<|property\<value|表示正在搜索的属性小于指定的值。<sup>1</sup>|
|\>|property\>value|表示正在搜索的属性大于指定的值。<sup>1</sup>|
|\<=|property\<=value|表示正在搜索的属性小于等于指定的值。<sup>1</sup>|
|\>=|property\>=value|表示正在搜索的属性大于等于指定的值。<sup>1</sup>|
|..|属性： value1。value2|表示正在搜索的属性大于等于 value1，小于等于 value2。<sup>1</sup>|
|"  "|"fair value"  <br/> subject:"Quarterly Financials"|使用双引号 ( "" ) 可在关键字和搜索查询中搜索确切的短语或术语  `property:value` 。|
|\*|cat\*  <br/> subject:set\*|前缀通配符（其中星号放在单词的末尾）用于在关键字或  `property:value` 查询中搜索零个或多个匹配字符。 例如，  `title:set*` 返回包含 word set、setup 和 set (的文档，以及在文档标题中以 "set" ) 开头的其他单词。  <br/><br/> **注意：** 只能使用前缀通配符搜索;例如， **cat \* **或**set \* **。 后缀搜索 (** \* cat** ) 、中缀搜索 (**c \* t**) 和子字符串搜索 (不支持** \* cat \* **) 。|
|(  )| (fair OR free) AND (from:contoso.com)  <br/> (IPO OR initial) AND (stock OR shares)  <br/> (quarterly financials)|括号将布尔短语、 `property:value` 项目和关键字结合到一起。例如，  `(quarterly financials)` 返回包含单词"quarterly"和"financials"的项目。  |
|||||
   
> [!NOTE]
> <sup>1</sup> 为含有日期或数值的属性使用此运算符。<br/> <sup>2</sup> 布尔搜索运算符必须为大写形式；例如， **AND** 。 如果使用小写运算符（例如 **和**），它将被视为搜索查询中的关键字。 
  
## <a name="search-conditions"></a>搜索条件

您可以向搜索查询中添加条件以缩小搜索范围，并返回一组更细化的结果。 每个条件向开始搜索时创建和运行的 KQL 搜索查询添加一个子句。
  
[通用属性的条件 ](#conditions-for-common-properties)

[邮件属性的条件](#conditions-for-mail-properties)

[文档属性的条件](#conditions-for-document-properties)

[与条件一起使用的运算符](#operators-used-with-conditions)

[使用条件的准则](#guidelines-for-using-conditions)

[示例](#examples-of-using-conditions-in-search-queries)
  
### <a name="conditions-for-common-properties"></a>通用属性的条件

在同一搜索中同时搜索邮箱和网站时，使用通用属性创建一个条件。 下表列出了添加条件时要使用的可用属性。
  
|**条件**|**说明**|
|:-----|:-----|
|日期|对于电子邮件而言，是指收件人收到邮件的日期，或发件人发送邮件的日期。 对于文档，是上次修改文档的日期。|
|发件人/作者|对于电子邮件而言，是指发送邮件的人。 对于文档而言，是指从 Office 文档的作者字段中引用的人员。 你可以键入多个名称，用逗号分隔。 通过 **OR** 运算符在逻辑上连接两个或多个值。|
|大小 (以字节为单位) |对于电子邮件和文档而言，是项目的大小（以字节为单位）。|
|主题/职务|对电子邮件而言，是指邮件的主题行中的文本。 对于文档而言，是指文档的标题。 如上文所述，Title 属性是在 Microsoft Office 文档中指定的元数据。 您可以键入多个主题/标题的名称，以逗号分隔。 通过 **OR** 运算符在逻辑上连接两个或多个值。|
|合规性标签|对于电子邮件和文档，自动标记策略或已由用户手动分配的保留标签自动分配给邮件和文档的保留标签。 保留标签用于对电子邮件和文档进行分类，以根据标签定义的设置对电子邮件和文档进行分类和强制实施保留规则。 您可以键入部分保留标签名称，然后使用通配符或键入完整的标签名称。 有关保留标签的详细信息，请参阅 [了解保留策略和保留标签](retention.md)。|
|||
  
### <a name="conditions-for-mail-properties"></a>邮件属性的条件

搜索邮箱或公用文件夹时使用邮件属性创建条件。 下表列出了可以用于条件的电子邮件属性。 这些属性是之前所述的电子邮件属性的子集。 为方便起见，将重复这些说明。
  
|**条件**|**说明**|
|:-----|:-----|
|邮件类型| 要搜索的邮件类型。 此属性与“Kind”电子邮件属性相同。 可能的值：  <br/><br/>  联系人  <br/>  文档  <br/>  电子邮件  <br/>  externaldata  <br/>  传真  <br/>  即时消息  <br/>  日志  <br/>  会议  <br/>  microsoftteams  <br/>  注释  <br/>  公告  <br/>  RSS 源  <br/>  任务  <br/>  语音邮件|
|Participants|电子邮件中的所有人员字段。 这些字段分别为 "收件人"、"收件人" 和 "密件抄送"。|
|类型|电子邮件项目的邮件类属性。 这是 ItemClass 电子邮件属性的相同属性。 它也是一个多值条件。 因此，若要选择多个邮件类，请按住 **CTRL** 键，然后在下拉列表中单击要添加到条件的两个或多个邮件类。 在列表中选择的每个邮件类别将在相应的搜索查询中通过 **OR** 运算符逻辑连接。  <br/> 有关邮件类别的列表 (以及它们对应的邮件类 ID) 由 Exchange 使用，并且您可以在 **邮件类** 列表中选择，请参阅 [项目类型和邮件类](https://go.microsoft.com/fwlink/?linkid=848143)。|
|Received|收件人接收电子邮件的日期。 此属性与“Received”电子邮件属性相同。|
|收件人|电子邮件中的所有收件人字段。 这些字段分别为 "收件人"、"抄送" 和 "密件抄送"。|
|发件人|电子邮件的发件人。|
|Sent|发件人发送电子邮件的日期。 此属性与“Sent”电子邮件属性相同。|
|Subject|电子邮件主题行中的文本。|
|到|"收件人" 字段中的电子邮件的收件人。|
|||
  
### <a name="conditions-for-document-properties"></a>文档属性的条件

在 SharePoint 和 OneDrive for business 网站上搜索文档时使用文档属性创建条件。 下表列出了可以用于条件的文档属性。 这些属性是之前所述的网站属性的子集。 为方便起见，将重复这些说明。
  
|**条件**|**说明**|
|:-----|:-----|
|作者|作者字段位于 Office 文档中，复制文档后仍然存在其中。 例如，如果用户创建一个文档，并将其发送给其他人，然后再将其上载到 SharePoint，则该文档仍将保留原作者。|
|标题|文档的标题。 Title 属性是 Office 文档中指定的元数据。 它与文档的文件名不同。|
|已创建|创建文档的日期。|
|上次修改时间|上次修改文档的日期。|
|文件类型|文件的扩展名;例如，.docx、one、.pptx 或 .xlsx。 此属性与 FileExtension 网站属性相同。|
|||
  
### <a name="operators-used-with-conditions"></a>与条件一起使用的运算符

当您添加一个条件时，您可以选择与该条件的属性类型相关的运算符。下表描述了与条件一起使用的运算符，并列出了在搜索查询中使用的等效项。
  
|**Operator**|**查询等效项**|**说明**|
|:-----|:-----|:-----|
|段后|`property>date`|使用日期条件。返回在指定日期后发送、接收或修改的项。 |
|Before|`property<date`|使用日期条件。返回在指定日期前发送、接收或修改的项。|
|行间|`date..date`|使用日期和大小条件。 当使用日期条件时，返回在指定的日期范围内发送、接收或修改的项。 当使用大小条件时，返回大小在指定范围内的项。|
|包含任意|`(property:value) OR (property:value)`|与指定字符串值的属性条件一起使用。 返回包含一个或多个指定字符串值任何部分的项目。|
|不包含任何|`-property:value`  <br/> `NOT property:value`|与指定字符串值的属性条件一起使用。 返回不包含指定字符串值任何部分的项目。|
|不等于任何|`-property=value`  <br/> `NOT property=value`|与指定字符串值的属性条件一起使用。返回不包含特定字符串的项目。|
|等于|`size=value`|返回与指定大小相等的项。<sup>1</sup>|
|等于任何|`(property=value) OR (property=value)`|与指定字符串值的属性条件一起使用。返回完全匹配一个或多个指定字符串值的项目。|
|多于|`size>value`|返回指定属性大于指定值的项。<sup>1</sup>|
|大于或等于|`size>=value`|返回指定属性大于或等于指定值的项。<sup>1</sup>|
|小于|`size<value`|返回大于或等于特定值的项。<sup>1</sup>|
|小于或等于|`size<=value`|返回大于或等于特定值的项。<sup>1</sup>|
|不等于|`size<>value`|返回不等于指定大小的项。<sup>1</sup>|
|||
   
> [!NOTE]
> <sup>1</sup> 此运算符仅适用于使用 Size 属性的条件。 
  
### <a name="guidelines-for-using-conditions"></a>使用条件的准则

在使用搜索条件时，请牢记以下几点。
  
- 可通过使用 **AND** 运算符在逻辑上将条件连接至关键字查询（在关键字框中指定）。 这意味着，项目必须满足关键字查询和要在结果中包括的条件。 这就是条件如何帮助缩小结果范围的原理。 
    
- 如果向搜索查询中添加两个或更多个唯一条件 (条件指定不同的属性) ，则这些条件通过 **AND** 运算符逻辑连接。 这意味着仅返回满足所有条件（除了任何关键字查询以外）的项目。 
    
- 如果您对相同属性添加多个条件，则使用 **OR** 运算符在逻辑上对这些条件进行连接。 这意味着将返回满足关键字查询以及任何一个条件的项。 因此，相同条件的组通过 **OR** 运算符彼此相连，然后唯一性条件集通过 **AND** 运算符彼此相连。 
    
- 如果将多个值 (以逗号或分号分隔) 添加到单个条件中，则这些值由 **or** 运算符连接。 这意味着如果这些项包含条件中指定的任何属性值，则返回这些项。 
    
- 使用 "关键字" 框和条件创建的搜索查询将显示在 " **搜索** " 页上所选搜索的详细信息窗格中。 在查询中，表示法右侧的一切都  `(c:c)` 表示添加到查询中的条件。 
    
- 条件只将属性添加到搜索查询中，而不会添加运算符。 这就是在详细信息窗格中显示的查询不显示表示法右侧的运算符的原因  `(c:c)` 。 执行查询时，KQL 会添加逻辑运算符（根据前面所述的规则）。 
    
- 您可以使用拖放控件 resequence 条件的顺序。 在控件上单击以查看条件并将其向上或向下移动。
    
- 同前面所述一样，某些条件属性允许您输入多个值。 各个值在逻辑上使用 **OR** 运算符相连。 这会导致出现使用相同逻辑表示有相同条件的多个实例，而每个实例都有一个值。 下图显示了一个包含多个值的单个条件的示例，以及一个使用单个值为同一属性)  (多个条件的示例。 这两个示例都将产生相同的查询：  `(filetype:docx) OR (filetype:pptx) OR (filetype:xlsx)`
    
    ![邮件必须匹配该规则的所有条件。如果需要匹配一个条件或另一个条件，请对每个条件使用不同的规则。例如，如果您要为带有附件的邮件和内容匹配某个模式的邮件添加相同的免责声明，请为每个条件创建一个规则。您可以轻松地复制规则。](../media/9880aa29-d117-4531-be20-6d53f1d21341.gif)
  
    ![同一属性的多个搜索条件](../media/1e63d37d-6d8d-4c9b-a509-a7e1c3a05193.gif)
  
> [!TIP]
> 如果条件接受多个值，则建议您使用一个条件，并指定多个值（用逗号或分号分隔）。这有助于确保所应用的查询逻辑就是您想要的。 
  
### <a name="examples-of-using-conditions-in-search-queries"></a>示例

以下示例显示了包含条件的搜索查询的基于 GUI 的版本、搜索查询语法，这些语法显示在所选搜索 (的细节窗格中， **new-compliancesearch** cmdlet) 以及相应的 KQL 查询的逻辑也会返回该语法。 
  
#### <a name="example-1"></a>示例 1

本示例返回 SharePoint 和 OneDrive for business 网站上包含信用卡号的文档，并且在2016年1月1日之前进行了最后修改。
  
 **GUI**
  
![第一个搜索条件示例](../media/099515ba-d4ee-474e-af25-3aa48816b87b.gif)
  
 **搜索查询语法**
  
 `SensitiveType:"Credit Card Number"(c:c)(lastmodifiedtime<2016-01-01)`
  
 **搜索查询逻辑**
  
 `SensitiveType:"Credit Card Number" AND (lastmodifiedtime<2016-01-01)`
  
#### <a name="example-2"></a>示例 2

本示例返回包含关键字“report”且在 2105 年 4 月 1 日之前发送或创建的电子邮件项目或文档，且电子邮件的主题字段或文档的标题属性中包含词语“northwind”。查询不包括符合其他搜索条件的网页。 
  
 **GUI**
  
![第二个搜索条件示例](../media/fe07d495-df81-42da-8106-3cdb409c6e7f.gif)
  
 **搜索查询语法**
  
 `report(c:c)(date<2016-04-01)(subjecttitle:"northwind")(-filetype:aspx)`
  
 **搜索查询逻辑**
  
 `report AND (date<2016-04-01) AND (subjecttitle:"northwind") NOT (filetype:aspx)`
  
#### <a name="example-3"></a>示例 3

本示例返回在12/1/2016 和11/30/2016 之间发送的、包含以 "phone" 或 "smartphone" 开头的单词的电子邮件或日历会议。
  
 **GUI**
  
![搜索条件示例三](../media/973d45fc-0923-43d6-9d0a-25e4a625f057.gif)
  
 **搜索查询语法**
  
 `phone* OR smartphone*(c:c)(sent=2016-12-01..2016-11-30)(kind="email")(kind="meetings")`
  
 **搜索查询逻辑**
  
 `phone* OR smartphone* AND (sent=2016-12-01..2016-11-30) AND ((kind="email") OR (kind="meetings"))`
  
## <a name="special-characters"></a>特殊字符

某些特殊字符不包含在搜索索引中，因此不可搜索。 这还包括在搜索查询中表示搜索运算符的特殊字符。 下面的列表列出了由实际搜索查询中的空格替换或导致搜索错误的特殊字符。

`+ - = : ! @ # % ^ & ; _ / ? ( ) [ ] { }`

## <a name="searching-for-site-content-shared-with-external-users"></a>搜索与外部用户共享的网站内容

您还可以使用安全 & 合规中心中的内容搜索功能搜索存储在 SharePoint 和 OneDrive for business 网站上的文档，这些文档已与组织外部的人员共享。 这可以帮助你识别与组织外部人员共享的敏感信息或专有信息。 可以通过  `ViewableByExternalUsers` 在关键字查询中使用属性来执行此操作。 此属性返回使用以下共享方法之一与外部用户共享的文档或网站： 
  
- 要求用户以经过身份验证的用户身份登录组织的共享邀请。
    
- 匿名来宾链接，它允许具有此链接的任何人访问资源，而无需进行身份验证。
    
下面是一些示例：
  
- 查询将  `ViewableByExternalUsers:true AND SensitiveType:"Credit Card Number"` 返回与组织外部的人员共享的所有项目，并包含信用卡号。 
    
- 该查询将  `ViewableByExternalUsers:true AND ContentType:document AND site:"https://contoso.sharepoint.com/Sites/Teams"` 返回组织中与外部用户共享的所有工作组网站上的文档列表。 
    
> [!TIP]
> 搜索查询（如  `ViewableByExternalUsers:true AND ContentType:document` 可能会在搜索结果中返回大量 .aspx 文件）。 若要消除这些 (或其他类型的文件) ，可以使用  `FileExtension` 属性排除特定的文件类型; 例如  `ViewableByExternalUsers:true AND ContentType:document NOT FileExtension:aspx` 。 
  
哪些内容视为与组织的外部人员共享的内容？ 您组织的 SharePoint 和 OneDrive for business 网站中通过发送共享邀请或在公共位置共享的文档。 例如，下列用户活动会产生外部用户可以查看的内容：
  
- 用户与组织外部的人员共享文件或文件夹。
    
- 用户创建共享文件并将链接发送给组织外部的人员。 此链接允许外部用户查看（或编辑）该文件。
    
- 用户向组织外部的人员发送共享邀请或来宾链接以查看（或编辑）共享文件。
    
### <a name="issues-using-the-viewablebyexternalusers-property"></a>使用 ViewableByExternalUsers 属性的问题

虽然该  `ViewableByExternalUsers` 属性表示文档或网站与外部用户共享的状态，但对此属性的功能和不反映的情况有一些注意事项。 在以下方案中，  `ViewableByExternalUsers` 不会更新属性的值，并且使用此属性的内容搜索查询的结果可能不准确。 
  
- 对共享策略的更改，例如关闭网站或组织的外部共享。 该属性仍会将以前的共享文档显示为外部可访问，即使外部访问可能已被吊销也是如此。
    
- 对组成员身份的更改，例如向 Microsoft 365 组或 Microsoft 365 安全组添加或删除外部用户。 对于组有权访问的项目，该属性不会自动更新。
    
- 向外部用户发送共享邀请，其中收件人尚未接受邀请，因此尚未访问内容。
    
在这些情况下，该  `ViewableByExternalUsers` 属性将不会反映当前的共享状态，直到网站或文档库是重新爬网和编制索引。 

## <a name="searching-for-site-content-shared-within-your-organization"></a>搜索组织中共享的网站内容

如前所述，您可以使用  `SharedWithUsersOWSUser` 属性，以便搜索组织中的人员之间共享的文档。 当某个人与组织内的另一个用户共享文件 (或) 文件夹时，共享文件的链接将显示在与之共享文件的人员的 OneDrive for Business 帐户中的 " **与我共享** " 页上。 例如，若要搜索已与 Sara Davis 共享的文档，可以使用查询  `SharedWithUsersOWSUser:"sarad@contoso.com"` 。 如果您导出此搜索的结果，则会下载原始文档，这些文档位于使用 Sara) 共享文档的人员的内容位置中 (。
  
使用属性时，必须与特定用户显式共享文档以在搜索结果中返回  `SharedWithUsersOWSUser` 。 例如，当某人在其 OneDrive 帐户中共享文档时，可以选择将其与组织内部或外部 (的任何人共享) ，仅与组织内的人员共享，或与特定人员共享它。 以下是 OneDrive 中的 " **共享** " 窗口的屏幕截图，其中显示了三个共享选项。 
  
![使用 SharedWithUsersOWSUser 属性的搜索查询将仅返回与特定人员共享的文件](../media/469a4b61-68bd-4ab0-b612-ab6302973886.png)
  
使用该属性的搜索查询将仅返回通过使用第三个选项共享的文档， (与 **特定人员**) 共享  `SharedWithUsersOWSUser` 。 

## <a name="searching-for-skype-for-business-conversations"></a>正在搜索 Skype for Business 对话

您可以使用以下关键字查询专门搜索 Skype for Business 对话中的内容：

```powershell
kind:im
```

以前的搜索查询还会从 Microsoft 团队中返回聊天。 若要防止出现这种情况，您可以通过使用以下关键字查询缩小搜索结果，以仅包括 Skype for Business 对话：

```powershell
kind:im AND subject:conversation
```

以前的关键字查询在 Microsoft 团队中排除了聊天，因为 Skype for Business 对话以电子邮件的形式保存，主题行以单词 "对话" 开头。

若要搜索在特定日期范围内发生的 Skype for Business 对话，请使用以下关键字查询：

```powershell
kind:im AND subject:conversation AND (received=startdate..enddate)
```

## <a name="search-tips-and-tricks"></a>搜索提示和技巧

- 关键字搜索不区分大小写。 例如， **cat** 和 **CAT** 将返回相同的结果。 

- 布尔运算符 **AND**、 **OR**、 **NOT**和 **NEAR** 必须为大写。 

- 两个关键字或两个  `property:value` 表达式之间的空格与使用 **AND** 相同。 例如，  `from:"Sara Davis" subject:reorganization` 返回在 "主题" 行中包含 "重组" 一词的 "Sara Davis" 发送的所有邮件。 

- 使用与格式相匹配的语法 `property:value` 。 值不区分大小写，并且它们不可以在运算符后留有空格。 如果有空格，则您的预期值将是全文本搜索。 例如 `to: pilarp` ，搜索 "pilarp" 作为关键字，而不是发送到 pilarp 的邮件。 

- 在搜索收件人属性（如 To、From、Cc 或 Recipients）时，您可以使用 SMTP 地址、别名或显示名来表示收件人。例如，您可以使用 pilarp@contoso.com、pilarp 或"Pilar Pinilla"。

- 只能使用前缀通配符搜索;例如， **cat \* **或**set \* **。 后缀搜索 (** \* cat**) 、中缀搜索 (**c \* t**) 和子字符串搜索 (不支持** \* cat \* **) 。

- 在搜索属性时，如果搜索值包含多个单词，则使用双引号 ( "" ) 。 例如， `subject:budget Q1` 返回包含 "主题" 行中的 **预算** 的邮件，并在邮件或任何邮件属性中的任何位置包含 **Q1** 。 使用 `subject:"budget Q1"` 返回 "主题" 行中任意位置包含 **预算 Q1** 的所有邮件。

- 若要将使用某个属性值标记的内容从搜索结果中排除，请在属性名称前放置减号 (-)。 例如， `-from:"Sara Davis"` 排除由 Sara Davis 发送的所有邮件。

- 您可以基于邮件类型导出项目。 例如，若要在 Microsoft 团队中导出 Skype 对话和聊天，请使用语法 `kind:im` 。 若要仅返回电子邮件，请使用 `kind:email` 。 若要在 Microsoft 团队中返回聊天、会议和呼叫，请使用 `kind:microsoftteams` 。
