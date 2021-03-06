---
title: 部署独立的 SharePoint Online 团队网站
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/30/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: 本分步部署指南可用于在 Microsoft Office 365 中创建和配置独立的 SharePoint Online 团队网站。
ms.openlocfilehash: f2800e74149e79e5c3f0444799f454ab8b3caf69
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203127"
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>部署独立的 SharePoint Online 团队网站

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


 **摘要：** 按照这些分步说明部署一个新的独立 SharePoint Online 团队网站。
  
本文是在 Microsoft Office 365 中创建和配置独立的 SharePoint Online 团队网站的分步部署指南。 这些步骤假设使用了三个默认 SharePoint 组和相应的权限级别，每个级别的每个访问级别都有一个 Azure Active Directory (基于 AD) 的访问组。
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>第1阶段：创建和填充团队网站访问组

在此阶段中，您将为三个默认 SharePoint 组创建三个基于 Azure AD 的访问组，并使用适当的用户帐户填充它们。
  
> [!NOTE]
> 以下步骤假定所有必需的用户帐户都已存在，并为其分配了适当的许可证。 如果不是，请先添加它们并分配许可证，然后再继续执行步骤1。 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>步骤1：列出网站的 SharePoint Online 管理员

确定对应于独立团队网站的 SharePoint Online 管理员的用户帐户集。
  
如果您通过 Microsoft 365 管理用户帐户和组，并且想要使用 Windows PowerShell，请将其用户主体名称列表 (Upn)  (示例 UPN： belindan@contoso.com) 。
  
### <a name="step-2-list-the-members-for-the-site"></a>步骤2：列出网站的成员

确定与独立团队网站的成员对应的用户帐户集，这些用户帐户将对存储在网站中的资源进行协作。
  
如果您通过 Microsoft 365 管理用户帐户和组，并且想要使用 PowerShell，请创建其 Upn 的列表。 如果有大量的网站成员，则可以将 Upn 列表存储在一个文本文件中，并将它们全部添加到一个 PowerShell 命令中。
  
### <a name="step-3-list-the-viewers-for-the-site"></a>步骤3：列出网站的查看者

确定与独立团队网站的查看者相对应的用户帐户集，这些用户可以查看存储在网站中的资源，但不能对其内容进行修改，也不能直接对其内容进行协作。
  
如果您通过 Microsoft 365 管理用户帐户和组，并且想要使用 PowerShell，请创建其 Upn 的列表。 如果有大量的网站成员，则可以将 Upn 列表存储在一个文本文件中，并将它们全部添加到一个 PowerShell 命令中。
  
网站的查看者可能包括行政管理、法律顾问或部门间利益干系人。
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>步骤4：在 Azure AD 中为网站创建三个访问组

您需要在 Azure AD 中创建以下访问组：
  
- 将包含步骤1中的列表的网站管理员 () 
    
- 将包含步骤2中的列表的网站成员 () 
    
- 将包含步骤3中的列表的网站查看器 () 
    
1. 在浏览器中，转到 Azure 门户， [https://portal.azure.com](https://portal.azure.com) 并使用已分配给用户管理管理员或公司管理员角色的帐户的凭据进行登录。
    
2. 在 Azure 门户中，单击“**Azure Active Directory”>“组**”。
    
3. 在“**组 - 所有组**”边栏选项卡上，单击“**+ 新建组**”。
    
4. 在 **新组** 边栏上：
    
    - 在“组类型”中选择“安全性”********。

    - 在 " **名称**" 中键入组名称。

    - 在 " **组说明**" 中键入组的说明。

    - 在“**成员身份**”类型中，选择“**已分配**”。
    
5. 单击“**创建**”，然后关闭“**组**”边栏选项卡。
    
6. 对其他组重复步骤3-5。
    
> [!NOTE]
> 您需要使用 Azure 门户来创建组，以便他们启用 Office 功能。 如果后来将 SharePoint Online 独立网站配置为具有 Azure 信息保护标签的高度机密网站来加密文件，并为特定组分配权限，则必须已在启用 Office 功能的情况下创建允许的组。 Azure AD 组创建后，无法更改其 Office 功能设置。 
  
下面是具有三个网站访问组的结果配置。
  
![用于部署独立 SharePoint Online 网站的三个访问组。](../../media/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>步骤 5. 将用户帐户添加到访问组

在此步骤中，请执行以下操作：
  
1. 将步骤1中的用户列表添加到网站管理员访问组
    
2. 将步骤2中的用户列表添加到网站成员访问组
    
3. 将步骤3中的用户列表添加到 "网站查看者访问" 组
    
如果通过 Active Directory 域服务 (AD DS) 管理用户帐户和组，请使用常规 AD DS 用户和组管理程序将用户添加到相应的访问组，并等待与 Microsoft 365 订阅同步。
  
如果通过 Office 365 管理用户帐户和组，则可以使用 Microsoft 365 管理中心或 PowerShell。 如果有任何访问组的组名称重复，则应使用 Microsoft 365 管理中心。
  
对于 Microsoft 365 管理中心，使用已分配有用户帐户管理员或公司管理员角色的用户帐户登录，并使用组将相应的用户帐户和组添加到相应的访问组。
  
对于 PowerShell，首先 [与 Azure Active Directory PowerShell For Graph 模块进行连接](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell?view=o365-worldwide#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
接下来，使用以下命令块将单个用户帐户添加到访问组中：
  
```powershell
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```
如果您为文本文件中的任何访问组存储了用户帐户的 Upn，则可以使用下面的 PowerShell 命令块一次添加所有这些组：
  
```powershell
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

对于 PowerShell，使用以下命令块将单个组添加到访问组中：
  
```powershell
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

结果应如下所示：
  
- 网站管理员 Azure AD 组包含网站管理员用户帐户或组
    
- 网站成员 Azure AD 组包含网站成员用户帐户或组
    
- 网站查看器 Azure AD 组包含仅可查看网站内容的用户帐户或组
    
使用 Microsoft 365 管理中心或以下 PowerShell 命令块验证每个访问组的组成员列表：
  
```powershell
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

下面是通过使用用户帐户或组填充的三个网站访问组生成的配置。
  
![三个使用用户帐户填充的访问组。](../../media/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>阶段2：创建和配置独立的团队网站

在此阶段中，您将创建独立的 SharePoint Online 网站，并将默认 SharePoint Online 权限级别的权限配置为使用新的基于 Azure AD 的访问组。 默认情况下，新的工作组网站包含 Microsoft 365 组和其他相关资源，但在这种情况下，我们将在没有 Microsoft 365 组的情况下创建团队网站。 这样可以完全通过 SharePoint 维护权限。
  
首先，使用这些步骤创建 SharePoint Online 团队网站。
  
1. 使用将用于管理 SharePoint Online 团队网站 (SharePoint Online 管理员) 的帐户登录到 Microsoft 365 管理中心。 如需帮助，请参阅[如何登录到 Office 365](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4)。

2. 在 Microsoft 365 管理中心的 " **管理中心**" 下，单击 " **SharePoint**"。

3. 在 SharePoint 管理中心中，展开 " **网站** "，然后单击 " **活动网站**"。

4. 单击 " **创建**"，然后选择 " **其他选项**"。

5. 在 " **选择模板** " 列表中，选择 " **团队网站**"。
   
6. 在 " **网站名称**" 中，键入团队网站的名称。 
    
7. 在 **主管理员**中，键入您登录时使用的帐户。
 
8. 单击“完成”****。
    
接下来，从新的 SharePoint Online 团队网站配置权限。
  
1. 在工具栏中，依次单击设置图标和“**网站权限**”。

2. 在 " **网站共享**" 下，单击 " **更改成员可以共享的方式**"。

3. 选择 " **仅网站所有者" 可以共享文件、文件夹和网站**。

4. 将 " **允许访问请求** " 设置为 " **关闭**"。

5. 单击“**保存**”。
    
6. 在 " **权限** " 窗格中，单击 " **高级权限设置**"。
    
7. 在浏览器的 "**权限**" 选项卡上，单击列表中的 " ** \<site name> 成员**"。
    
8. 在“人员和组”中，单击“新建”********。
    
9. 在 " **共享** " 对话框中，键入网站成员访问组的名称，选择它，然后单击 " **共享**"。
    
10. 单击浏览器上的后退按钮。
    
11. 单击列表中的 " ** \<site name> 所有者**"。
    
12. 在“人员和组”中，单击“新建”********。
    
13. 在 " **共享** " 对话框中，键入 "网站管理员" 访问组的名称，选择它，然后单击 " **共享**"。
    
14. 单击浏览器上的后退按钮。
    
15. 单击列表中的 " ** \<site name> 访问者**"。
    
16. 在“人员和组”中，单击“新建”********。
    
17. 在 " **共享** " 对话框中，键入 "网站查看者访问" 组的名称，选择它，然后单击 " **共享**"。
    
18. 关闭浏览器的“权限”标签页****。
    
以下是这些权限设置的结果：
  
- " ** \<site name> 所有者**" SharePoint 组包含 "网站管理员" 访问组，其中所有成员都具有 "**完全控制**" 权限级别。
    
- " ** \<site name> 成员**" SharePoint 组包含 "网站成员" 访问组，其中所有成员都具有 "**编辑**" 权限级别。
    
- ** \<site name> 访问者**SharePoint 组包含 "网站查看者" 访问组，其中所有成员都具有 "**读取**" 权限级别。
    
- 禁用成员邀请其他成员或非成员请求访问的功能已被禁用。
    
下面是配置了三个 SharePoint 组的网站的结果配置，该网站配置为使用三个访问组，其中填充了用户帐户或 Azure AD 组。
  
![使用访问组和用户帐户的独立 SharePoint Online 网站的最终配置。](../../media/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
您和网站成员（通过其中一个访问组中的组成员身份）现在可以使用网站的资源进行协作。
  
## <a name="next-step"></a>后续步骤

如果需要更改网站访问组成员身份或创建具有自定义权限的文档文件夹，请参阅 [管理独立的 SharePoint Online 团队网站](manage-an-isolated-sharepoint-online-team-site.md)。
  
## <a name="see-also"></a>另请参阅

[独立 SharePoint Online 团队网站](isolated-sharepoint-online-team-sites.md)
  
[设计单独的 SharePoint Online 团队网站](design-an-isolated-sharepoint-online-team-site.md)
  
[管理独立 SharePoint Online 团队网站](manage-an-isolated-sharepoint-online-team-site.md)
  



