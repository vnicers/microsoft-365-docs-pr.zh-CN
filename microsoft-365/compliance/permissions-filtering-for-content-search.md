---
title: 配置内容搜索的权限筛选
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1adffc35-38e5-4f7d-8495-8e0e8721f377
description: 使用内容搜索权限筛选可让电子数据展示管理器仅搜索组织中的邮箱和网站的子集。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 28afbf65678e74e087365518bd07ceaae0e40e8a
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358544"
---
# <a name="configure-permissions-filtering-for-content-search"></a>配置内容搜索的权限筛选

您可以使用搜索权限筛选让电子数据展示管理器仅搜索组织中的邮箱和网站的子集。 您还可以使用权限筛选功能让该电子数据展示管理员仅搜索满足特定搜索条件的邮箱或站点内容。 例如，您可能会让电子数据展示管理员仅搜索特定位置或部门的用户的邮箱。 为此，可以创建一个筛选器，该筛选器使用受支持的收件人筛选器来限制特定用户或用户组可以搜索哪些邮箱。 您还可以创建一个筛选器，用于指定用户可以搜索的邮箱内容。 这是通过创建使用可搜索邮件属性的筛选器来完成的。 同样，您可以让电子数据展示管理器仅搜索组织中的特定 SharePoint 网站。 通过创建限制可以搜索哪些站点的筛选器执行此操作。 您还可以创建指定可以搜索哪些站点内容的筛选器。 这是通过创建使用可搜索站点属性的筛选器来完成的。

您还可以使用搜索权限筛选功能，在组织内控制用户内容 (位置的逻辑边界 () *符合性边界* ，) 特定的电子数据展示管理器可以搜索的邮箱、SharePoint 网站和 OneDrive 帐户。 有关详细信息，请参阅 [Office 365 中的为电子数据展示调查设置合规性边界](tagging-and-assessment-in-advanced-ediscovery.md)。
  
安全 & 合规中心中的内容搜索功能支持搜索权限筛选。 这四个 cmdlet 允许您配置和管理搜索权限筛选器：
  
[新 New-compliancesecurityfilter](#new-compliancesecurityfilter)

[New-compliancesecurityfilter](#get-compliancesecurityfilter)

[New-compliancesecurityfilter](#set-compliancesecurityfilter)

[New-compliancesecurityfilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>配置权限筛选的要求

- 若要运行合规性安全筛选器 cmdlet，您必须是 Security & 合规性中心中的 "组织管理" 角色组的成员。 有关详细信息，请参阅[安全与合规中心中的权限](../security/office-365-security/permissions-in-the-security-and-compliance-center.md)。
    
- 您必须将 Windows PowerShell 同时连接到安全 & 合规性中心和 Exchange Online 组织，才能使用合规性安全筛选器 cmdlet。 这是必要的，因为这些 cmdlet 需要访问邮箱属性，这就是为什么必须连接到 Exchange Online 的原因所在。 请参阅下一节中的步骤。 
    
- 请参阅[More information](#more-information)部分，了解有关搜索权限筛选器的其他信息。 
    
- 搜索权限筛选适用于非活动邮箱，这意味着您可以使用邮箱和邮箱内容筛选来限制可以搜索非活动邮箱的用户。 有关权限筛选和非活动邮箱的其他信息，请参阅 [详细信息](#more-information) 部分。 
    
-  搜索权限筛选不能用于限制谁可以在 Exchange 中搜索公用文件夹。 
    
- 对于可以在组织中创建的搜索权限筛选器的数量没有限制。 但当搜索权限筛选器超过100个时，搜索性能将受到影响。 若要尽可能减少组织中的搜索权限筛选器数量，请在可能时创建筛选器，将 Exchange、SharePoint 和 OneDrive 的规则合并到一个筛选器中。
    
## <a name="connect-to-the-security--compliance-center-and-exchange-online-in-a-single-remote-powershell-session"></a>在单个远程 PowerShell 会话中连接到安全 & 合规性中心和 Exchange Online

1. 使用文件名后缀 **. ps1**将以下文本保存到 Windows PowerShell 脚本文件中。 例如，可以将其保存到名为 **ConnectEXO-CC.ps1**的文件中。
    
    ```powershell
    $UserCredential = Get-Credential
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
    Import-PSSession $Session -DisableNameChecking
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
    Import-PSSession $Session -AllowClobber -DisableNameChecking
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. 在本地计算机上，打开 Windows PowerShell，转到上一步中创建的脚本所在的文件夹，然后运行该脚本;例如：
    
    ```powershell
    .\ConnectEXO-CC.ps1
    ```

您如何知道这是否有效？ 运行该脚本后，安全 & 合规性中心和 Exchange Online 中的 cmdlet 将导入到您的本地 Windows PowerShell 会话中。 如果未收到任何错误，说明连接成功。 快速测试是运行安全 & 合规性中心 cmdlet 和 Exchange Online cmdlet。 例如，您可以运行 **UnifiedCompliancePrerequisite** 和 **Get 邮箱**。 
  
如果收到错误，则查看以下要求：
  
- 常见问题是密码错误。重新运行上述两个步骤，并仔细查看在步骤 1 中输入的用户名和密码。
    
- 验证您的帐户是否有权访问安全 & 合规性中心。 有关详细信息，请参阅 [为用户提供对安全 & 合规中心的访问权限](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)。
    
- 为了帮助防止受到拒绝服务 (DoS) 攻击，您最多只能打开三个与安全 & 合规性中心的远程 PowerShell 连接。
    
- 必须将 Windows PowerShell 配置为运行脚本。 这只需要执行一次，而不是每次连接时都执行。 为了使 Windows PowerShell 能够运行已签名脚本，请在提升的 Windows PowerShell 窗口（通过选择"以管理员身份运行"打开的 Windows PowerShell 窗口）中运行以下命令。

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

- 需要打开本地计算机和 Office 365 之间的 TCP 端口 80 通信。 它可能已经打开了，但是要考虑你的组织是否存在严格的 Internet 访问政策。

  
## <a name="new-compliancesecurityfilter"></a>新 New-compliancesecurityfilter

**New-compliancesecurityfilter**用于创建搜索权限筛选器。 下表介绍了此 cmdlet 的参数。 创建遵从性安全筛选器需要全部参数。 
  
|**参数**|**说明**|
|:-----|:-----|
| _Action_ <br/> | _Action_参数指定筛选器应用于的搜索操作的类型。 可能的内容搜索操作包括：  <br/><br/> **导出：** 导出搜索结果时应用筛选器。  <br/> **预览：** 在预览搜索结果时应用筛选器。  <br/> **清除：** 在清除搜索结果时应用筛选器。  <br/> **搜索：** 在运行搜索时应用筛选器。  <br/> **所有：** 将筛选器应用于所有搜索操作。  <br/> |
| _FilterName_ <br/> |_FilterName_参数指定权限筛选器的名称。 在使用 **Get-ComplianceSecurityFilter**、**Set-ComplianceSecurityFilter** 和 **Remove-ComplianceSecurityFilter** cmdlet 时，此名称可用于标识筛选器。  <br/> |
| _筛选器_ <br/> | _Filters_参数指定合规性安全筛选器的搜索条件。 您可以创建三种不同类型的筛选器：  <br/><br/> **邮箱筛选：** 此类型的筛选器指定由  _users_ 参数) 可以搜索的已分配用户 (指定的邮箱。 此类筛选器的语法为 **Mailbox_** _MailboxPropertyName_，其中  _MailboxPropertyName_ 指定用于限定可以搜索的邮箱的邮箱属性。 例如，邮箱筛选器  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` 允许分配此筛选器的用户仅搜索在 CustomAttribute10 属性中具有值 "OttawaUsers" 的邮箱。  <br/>  任何受支持的可筛选收件人属性都可用于  _MailboxPropertyName_ 属性。 有关受支持的属性的列表，请参阅可 [筛选属性的-RecipientFilter 参数](https://go.microsoft.com/fwlink/p/?LinkId=784903)。  <br/><br/> **邮箱内容筛选：** 对可搜索的内容应用了此类型的筛选器。 它指定分配的用户可以搜索的邮箱内容。 此类筛选器的语法为 **MailboxContent_** _SearchablePropertyName： Value_，其中  _SearchablePropertyName_ 指定可在内容搜索中指定的关键字查询语言 (KQL) 属性。 例如，邮箱内容筛选器  `MailboxContent_recipients:contoso.com` 允许分配此筛选器的用户仅搜索发送到 contoso.com 域中的收件人的邮件。  <br/>  有关可搜索邮件属性的列表，请参阅 [用于内容搜索的关键字查询和搜索条件](keyword-queries-and-search-conditions.md)。 <br/> <br/> **重要说明：**  单个搜索筛选器不能包含邮箱筛选器和邮箱内容筛选器。 若要将它们组合到一个筛选器中，必须使用 [筛选器列表](#using-a-filters-list-to-combine-filter-types)。  但是，筛选器可以包含相同类型的更复杂的查询。 例如，  `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`  <br/><br/> **网站和网站内容筛选：** 有两个 SharePoint 和 OneDrive for Business 网站相关筛选器，可用于指定分配的用户可以搜索的网站或网站内容：  <br/><br/> - **Site_** _SearchableSiteProperty_ <br/> - **SiteContent_** _SearchableSiteProperty_ <br/><br/>  这两个筛选器是可互换的。 例如，  `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors*'"` 并  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors*'"` 返回相同的结果。 但为了帮助您确定筛选器的功能，您可以使用  `Site_` 来指定与网站相关的属性 (如网站 URL) 并  `SiteContent_` 指定与内容相关的属性 (如文档类型）。 例如，筛选器  `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors*'"` 允许分配此筛选器的用户仅搜索 https://contoso.sharepoint.com/sites/doctors 网站集中的内容。 筛选器  `"SiteContent_FileExtension -eq 'docx'"` 将允许分配此筛选器的用户仅搜索 word 文档 (word 2007 及更高版本) 。  <br/><br/>  有关可搜索网站属性的列表，请参阅 [SharePoint 中的已爬网和托管属性概述](https://go.microsoft.com/fwlink/p/?LinkId=331599)。 可使用可**查询**列中的 **"是"** 标记的属性来创建网站或网站内容筛选器。  <br/><br/> **重要说明：** 您必须创建搜索权限筛选器，以明确阻止用户搜索特定服务中的内容位置 (如阻止用户搜索任何 Exchange 邮箱或任何 SharePoint 网站) 。 换言之，创建搜索权限筛选器，允许用户搜索组织中的所有 SharePoint 网站并不会阻止该用户搜索邮箱。 例如，若要允许 SharePoint 管理员仅搜索 SharePoint 网站，您必须创建一个阻止他们搜索邮箱的筛选器。 同样，若要仅允许 Exchange 管理员搜索邮箱，您必须创建筛选器以防止他们搜索网站。           |
| _用户_ <br/> |_Users_参数指定将此筛选器应用于其内容搜索的用户。 按其别名或主要 SMTP 地址标识用户。 您可以指定用逗号分隔的多个值，也可以通过使用值 **All** 将筛选器分配给所有用户。  <br/> 您还可以使用  _Users_ 参数指定安全 & 合规中心角色组。 这可让您创建一个自定义角色组，然后为该角色组分配搜索权限筛选器。 例如，假设您具有一家跨国公司美国子公司的电子数据展示管理员自定义角色组。 您可以使用  _Users_ 参数通过使用角色组的 Name 属性指定此角色组 () 然后使用  _Filter_ 参数仅允许在美国的邮箱中进行搜索。  <br/> 不能使用此参数指定通讯组。  <br/> |
   
### <a name="using-a-filters-list-to-combine-filter-types"></a>使用筛选器列表组合筛选器类型

*筛选器列表*是包含邮箱筛选器和使用逗号分隔的网站筛选器的筛选器列表。 使用筛选器列表是组合不同类型的筛选器的唯一受支持的方法。 在下面的示例中，请注意， **邮箱** 和 **网站** 筛选器的逗号分隔：

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "Site_Path -like 'https://contoso.sharepoint.com/sites/doctors*'"
```

在运行内容搜索的过程中处理包含筛选器列表的筛选器时，将从 "筛选器" 列表中创建两个搜索权限筛选器：一个由逗号分隔的筛选器。 因此，在前面的示例中，将创建一个邮箱搜索权限筛选器和一个网站搜索权限筛选器。 

使用筛选器列表的另一种方法是创建两个单独的搜索权限筛选器。 因此，在前面的示例中，您将为邮箱属性创建一个筛选器，并为 site 属性创建一个筛选器。 在这两种情况下，结果都相同。 使用筛选器列表或创建单独的搜索权限筛选器是一个优先考虑事项。

使用筛选器列表时，请记住以下几点：

- 您必须使用筛选器列表来创建包含 **邮箱** 筛选器和 **MailboxContent** 筛选器的筛选器。 

- 如前所述，您无需使用筛选器列表在单个搜索权限筛选器中包含 **网站** 和 **SiteContent** 筛选器。 例如，可以使用 **-或**运算符将**Site**和**SiteContent**筛选器组合在一起。

   ```powershell
   -Filters "Site_ComplianceAttribute -eq 'FourthCoffee' -or Site_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee*'"
   ```

- 筛选器列表的每个组件都可以包含复杂的筛选器语法。 例如，邮箱和网站筛选器可以包含由 **-或** 运算符分隔的多个筛选器：

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "Site_ComplianceAttribute -eq 'CohoWinery' -or Site_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>创建搜索权限筛选器的示例

下面是使用 **New-ComplianceSecurityFilter** cmdlet 创建搜索权限筛选器的示例。 
  
本示例允许用户 annb@contoso.com 仅对加拿大的邮箱执行所有内容搜索操作。 此筛选器包含 ISO 3166-1 标准的加拿大三位数字国家/地区代码。

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'" -Action All
```

本示例允许用户 "donh" 和 "suzanf" 仅搜索 "CustomAttribute1 邮箱" 属性的值为 "Marketing" 的邮箱。

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'" -Action Search
```

此示例允许“美国发现管理员”角色组的成员仅对美国的邮箱执行所有内容搜索操作。此筛选器包含 ISO 3166-1 标准的美国三位数字国家/地区代码。
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryCode  -eq '840'" -Action All
```

此示例允许电子数据展示管理器角色组的成员仅搜索渥太华用户通讯组的成员的邮箱。 Exchange Online PowerShell 中的 New-distributiongroup cmdlet 用于查找渥太华 Users 组的成员。
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'" -Action Search
```

本示例可防止任何用户删除管理团队通讯组的成员邮箱中的内容。 Exchange Online PowerShell 中的 New-distributiongroup cmdlet 用于查找 Executive 团队组的成员。

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" -Action Purge
```

本示例允许 OneDrive 电子数据展示管理器自定义角色组的成员仅搜索组织中 OneDrive for business 位置中的内容。

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "Site_Path -like 'https://contoso-my.sharepoint.com/personal*'" -Action Search
```

> [!NOTE]
> 若要限制用户搜索特定网站，请使用筛选器  `Site_Path` ，如上面的示例中所示。 使用  `Site_Site` 将不起作用。 
  
此示例将用户限制为仅对 2015 日历年期间发送的电子邮件执行所有内容搜索操作。

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'" -Action All
```

与上一示例类似，此示例将用户限制为对最近更改时间为 2015 日历年某个时间的文档执行所有内容搜索操作。

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" -Action All
```

此示例阻止 "OneDrive 发现管理器" 角色组的成员对组织中的任何邮箱执行内容搜索操作。 

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"  -Action All
```

本示例防止组织中的任何人搜索由 janets 或 sarad 发送或接收的电子邮件。

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'" -Action Search
```

此示例使用筛选器列表来组合邮箱和网站筛选器。

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "Site_ComplianceAttribute -eq 'CohoWinery' -or Site_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'" -Action ALL
```

## <a name="get-compliancesecurityfilter"></a>New-compliancesecurityfilter

**New-compliancesecurityfilter**用于返回搜索权限筛选器的列表。 使用  _FilterName_ 参数可返回特定搜索筛选器的信息。 
  
## <a name="set-compliancesecurityfilter"></a>New-compliancesecurityfilter

**New-compliancesecurityfilter**用于修改现有搜索权限筛选器。 唯一必需的参数是  _FilterName_。 
  
|**参数**|**说明**|
|:-----|:-----|
| _Action_| _Action_参数指定筛选器应用于的搜索操作的类型。 可能的内容搜索操作包括： <br/><br/> **导出：** 导出搜索结果时应用筛选器。  <br/> **预览：** 在预览搜索结果时应用筛选器。  <br/> **清除：** 在清除搜索结果时应用筛选器。  <br/> **搜索：** 在运行搜索时应用筛选器。  <br/> **所有：** 将筛选器应用于所有搜索操作。  <br/> |
| _FilterName_|_FilterName_参数指定权限筛选器的名称。 |
| _筛选器_| _Filters_参数指定合规性安全筛选器的搜索条件。 您可以创建两种不同类型的筛选器： <br/><br/>**邮箱筛选：** 此类型的筛选器指定由  _users_ 参数) 可以搜索的已分配用户 (指定的邮箱。 此类筛选器的语法为 **Mailbox_** _MailboxPropertyName_，其中  _MailboxPropertyName_ 指定用于限定可以搜索的邮箱的邮箱属性。 例如，邮箱筛选器  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` 允许分配此筛选器的用户仅搜索在 CustomAttribute10 属性中具有值 "OttawaUsers" 的邮箱。  任何受支持的可筛选收件人属性都可用于  _MailboxPropertyName_ 属性。 有关受支持的属性的列表，请参阅可 [筛选属性的-RecipientFilter 参数](https://go.microsoft.com/fwlink/p/?LinkId=784903)。 <br/><br/>**邮箱内容筛选：** 对可搜索的内容应用了此类型的筛选器。 它指定分配的用户可以搜索的邮箱内容。 此类筛选器的语法为 **MailboxContent_** _SearchablePropertyName： Value_，其中  _SearchablePropertyName_ 指定可在内容搜索中指定的关键字查询语言 (KQL) 属性。 例如，邮箱内容筛选器  `MailboxContent_recipients:contoso.com` 允许分配此筛选器的用户仅搜索发送到 contoso.com 域中的收件人的邮件。  有关可搜索邮件属性的列表，请参阅 [用于内容搜索的关键字查询](keyword-queries-and-search-conditions.md)。 <br/><br/>**网站和网站内容筛选：** 有两个 SharePoint 和 OneDrive for Business 网站相关筛选器，可用于指定分配的用户可以搜索的网站或网站内容： <br/><br/>- **Site_** *SearchableSiteProperty* <br/>- **SiteContent**_*SearchableSiteProperty*<br/><br/>这两个筛选器是可互换的。 例如，  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"`  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` 返回相同的结果。 但为了帮助您确定筛选器的功能，您可以使用  `Site_` 来指定与网站相关的属性 (如网站 URL) 并  `SiteContent_` 指定与内容相关的属性 (如文档类型）。 例如，筛选器  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` 允许分配此筛选器的用户仅搜索 https://contoso.spoppe.com/sites/doctors 网站集中的内容。 筛选器  `"SiteContent_FileExtension -eq 'docx'"` 将允许分配此筛选器的用户仅搜索 word 文档 (word 2007 及更高版本) 。  <br/><br/>有关可搜索网站属性的列表，请参阅 [SharePoint 中的已爬网和托管属性概述](https://go.microsoft.com/fwlink/p/?LinkId=331599)。 可使用可**查询**列中的 **"是"** 标记的属性来创建网站或网站内容筛选器。 <br/><br/>          |
| _用户_|_Users_参数指定将此筛选器应用于其内容搜索的用户。 由于这是一个多值属性，因此指定具有此参数的用户或用户组将覆盖现有的用户列表。 有关添加和删除选定用户的语法，请参阅下面的示例。 <br/><br/>您还可以使用  _Users_ 参数指定安全 & 合规中心角色组。 这可让您创建一个自定义角色组，然后为该角色组分配搜索权限筛选器。 例如，假设您具有一家跨国公司美国子公司的电子数据展示管理员自定义角色组。 您可以使用  _Users_ 参数通过使用角色组的 Name 属性指定此角色组 () 然后使用  _Filter_ 参数仅允许在美国的邮箱中进行搜索。 <br/><br/>不能使用此参数指定通讯组。 |

## <a name="examples-of-changing-search-permissions-filters"></a>更改搜索权限筛选器的示例

这些示例演示如何使用 **new-compliancesecurityfilter** 和 **new-compliancesecurityfilter** cmdlet 在向其分配了筛选器的现有用户列表中添加或删除用户。 当您在筛选器中添加或删除用户时，使用这些用户的 SMTP 地址指定用户。 
  
此示例是将用户添加到筛选器。

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.add("pilarp@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

此示例是从筛选器中删除用户。

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.remove("annb@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

## <a name="remove-compliancesecurityfilter"></a>New-compliancesecurityfilter

**New-compliancesecurityfilter**用于删除搜索筛选器。 使用  _FilterName_ 参数指定要删除的筛选器。 
  
## <a name="more-information"></a>详细信息

- **搜索权限筛选功能的工作原理是什么？** 运行内容搜索时权限筛选器添加到搜索查询中。 "权限" 筛选器通过 **AND** Boolean 运算符加入搜索查询。 例如，您有一个权限筛选器，它允许王俊元对工作人员通讯组的成员邮箱执行所有搜索操作。 然后，Bob 使用搜索查询在组织中的所有邮箱上运行内容搜索  `sender:jerry@adatum.com` 。 由于权限筛选器和搜索查询通过 **and** 运算符逻辑组合，因此搜索将返回由 jerry@adatum.com 发送给工作人员通讯组的任何成员的任何邮件。 
    
- **如果您有多个搜索权限筛选器会怎么样？** 在内容搜索查询中，多个权限筛选器通过 **OR** 布尔运算符组合在一起。 因此，如果满足任意筛选器，将会返回结果。 在内容搜索中，所有筛选器（通过 **OR** 运算符组合在一起）会通过 **AND** 运算符与搜索查询组合在一起。 我们采用上面的示例，其中的搜索筛选器允许 Bob 仅搜索工作人员通讯组的成员的邮箱。 然后，我们创建另一个筛选器来阻止 Bob 搜索 Phil 的邮箱（“Mailbox_Alias -ne 'Phil'”）。 并且，让我们假设 Phil 是工作人员组的成员。 当王俊元在组织中的所有邮箱上运行内容搜索 (时) 对 Phil 的邮箱返回搜索结果，即使您应用了筛选器以防止王俊元搜索 Phil 的邮箱也是如此。 这是因为满足允许 Bob 搜索工作人员组的第一个筛选器的条件。 还因为 Phil 是工作人员组的成员，所以 Bob 可以搜索 Phil 的邮箱。 
    
- **搜索权限筛选是否适用于非活动邮箱？** 是的，您可以使用邮箱和邮箱内容筛选器来限制谁可以搜索组织中的非活动邮箱。 与常规邮箱一样，非活动邮箱必须使用用于创建权限筛选器的收件人属性进行配置。 如有必要，可以使用 **InactiveMailboxOnly** 命令来显示非活动邮箱的属性。 有关详细信息，请参阅 [在 Office 365 中创建和管理非活动邮箱](create-and-manage-inactive-mailboxes.md)。
    
- **搜索权限筛选是否适用于公用文件夹？** 不正确。 如上文所述，不能使用搜索权限筛选来限制可以在 Exchange 中搜索公用文件夹的成员身份。 例如，无法通过权限筛选器从搜索结果中排除公用文件夹位置中的项目。 
    
- **允许用户搜索特定服务中的所有内容位置也会阻止他们搜索不同服务中的内容位置吗？** 不正确。 如前所述，您必须创建搜索权限筛选器，以明确阻止用户搜索特定服务中的内容位置 (如阻止用户搜索任何 Exchange 邮箱或任何 SharePoint 网站) 。 换言之，创建搜索权限筛选器，允许用户搜索组织中的所有 SharePoint 网站并不会阻止该用户搜索邮箱。 例如，若要允许 SharePoint 管理员仅搜索 SharePoint 网站，您必须创建一个阻止他们搜索邮箱的筛选器。 同样，若要仅允许 Exchange 管理员搜索邮箱，您必须创建筛选器以防止他们搜索网站。
