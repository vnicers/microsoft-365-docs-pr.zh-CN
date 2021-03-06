---
title: 您的组织中的 Power BI
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- PWB150
ms.assetid: d7941332-8aec-4e5e-87e8-92073ce73dc5
ROBOTS: NOINDEX
description: 了解 Power BI 以及组织中的用户可以如何使用此业务分析服务。
ms.openlocfilehash: 5a5e7516800b2010f79296d758aeaeef80194bfd
ms.sourcegitcommit: a005395165db8896f4109674443b5e5e9209861d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2020
ms.locfileid: "44432167"
---
# <a name="power-bi-in-your-organization"></a>您的组织中的 Power BI

本页面介绍组织中的用户可以如何使用 Power BI，以及您可以如何控制组织获取此服务的方式。
    
## <a name="what-is-power-bi"></a>什么是 Power BI？

Microsoft Power BI 使用户能够以全新的直观方法可视化数据、共享发现、开展协作。 若要了解详细信息，请参阅 [Power BI 网站](https://powerbi.microsoft.com/en-us/)。
  
## <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI 是否符合国家、地区和特定于行业的合规性要求？

若要了解有关 Power BI 合规性的详细信息，请参阅[Microsoft 信任中心](https://go.microsoft.com/fwlink/?LinkId=785324)。
  
## <a name="how-do-users-sign-up-for-power-bi"></a>用户如何注册 Power BI？

作为管理员，你可以通过[POWER bi 网站](https://powerbi.microsoft.com/en-us/)注册 power bi。 您还可以通过 Microsoft 365 管理中心的 "购买服务" 页进行注册。 当管理员注册 Power BI 时，他们可以将用户订阅许可证分配给应具有访问权限的用户。
  
此外，您的组织中的个人用户可以通过 [Power BI 网站](https://powerbi.microsoft.com/en-us/)注册 Power BI。 当您的组织中的用户注册 Power BI 时，将自动为该用户分配 Power BI 许可证。
  
## <a name="how-do-individual-users-in-my-organization-sign-up"></a>我的组织内的个人用户如何注册？

有三种方案可能适用于您的组织内的用户：
  
### <a name="scenario-1-your-organization-already-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-already-has-an-microsoft-365-account"></a>方案1：您的组织已有一个现有的 Microsoft 365 环境，而 Power BI 的用户注册已拥有 Microsoft 365 帐户。

在此方案中，如果用户已经在租户（例如，contoso.com）中拥有工作或学校帐户但没有 Power BI，Microsoft 只会为该帐户激活计划，系统将自动通知用户如何使用 Power BI 服务。
  
### <a name="scenario-2-your-organization-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-doesnt-have-an-microsoft-365-account"></a>方案2：您的组织有一个现有的 Microsoft 365 环境，注册 Power BI 的用户没有 Microsoft 365 帐户。

在这种情况下，用户在您的组织的域中有电子邮件地址（例如，contoso.com），但还没有 Microsoft 365 帐户。 在这种情况下，用户可以注册 Power BI，并将自动获得帐户。 这使用户能够访问 Power BI 服务。 例如，如果名为张颖的员工使用她的工作电子邮件地址（例如，Nancy@contoso.com）进行注册，Microsoft 会自动将南希添加为 Contoso Microsoft 365 环境中的用户，并为该帐户激活 Power BI。
  
### <a name="scenario-3-your-organization-does-not-have-a-microsoft-365-environment-connected-to-your-email-domain"></a>方案3：您的组织没有连接到您的电子邮件域的 Microsoft 365 环境。

您的组织不需要执行任何管理操作即可利用 Power BI。
  
> [!IMPORTANT]
> 如果您的组织具有多个电子邮件域，并且您希望所有电子邮件地址扩展都位于同一个租户中，则在任何用户创建您的主租户之前，请先将所有电子邮件地址域添加到该租户，然后再创建您的主租户。 创建用户后，无需通过租户移动用户的自动化机制。 有关此过程的详细信息，请参阅本文后面的 "[如果我有多个域，可以控制将用户添加到的租户"](#if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to) ，并[将域添加到 Office 365](../setup/add-domain.md) online。 
  
## <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>这将如何更改我目前管理组织中用户的身份的方式？

如果您的组织已有一个现有的 Microsoft 365 环境，并且组织中的所有用户都有 Microsoft 365 帐户，则身份管理将不会更改。
  
如果您的组织已有一个现有的 Microsoft 365 环境，但并不是组织中的所有用户都有 Microsoft 365 帐户，我们将在租户中创建一个用户，并根据用户的工作或学校的电子邮件地址分配许可证。 这意味着，您在任何特定时间管理的用户数量将随着您的组织内的用户注册服务而增长。
  
如果您是在本地管理目录并使用 Active Directory 联合身份验证服务 (AD FS)，Microsoft 不会将用户添加到您的租户，并且任何尝试加入您的租户的用户将收到一条消息，指示他们联系其组织的管理员。
  
如果您的组织没有连接到您的电子邮件域的 Microsoft 365 环境，则管理身份的方式将不会有任何变化。 用户将被添加到新的仅限云用户目录，您可以选择作为租户管理员接管并管理他们。
  
## <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>管理 Microsoft 为我的用户创建的租户应遵循什么过程？

如果租户是由 Microsoft 创建的，您可以通过执行下列步骤来申请和管理该租户：
  
1. 通过使用与您要管理的租户域相匹配的电子邮件地址域[注册 Power BI](https://go.microsoft.com/fwlink/?LinkId=522448) 来加入租户。例如，如果 Microsoft 创建了 contoso.edu 租户，那么您需要使用以 @contoso.edu 结尾的电子邮件地址加入租户。 
    
2. 通过验证域所有权来申请管理员控制：一旦您位于租户中，您可以通过验证域所有权来将自己提升为管理员角色。为此，请执行以下步骤：
 
::: moniker range="o365-worldwide"
   
3. 转到 [https://admin.microsoft.com](https://admin.microsoft.com)。
 

::: moniker-end

::: moniker range="o365-germany"

3. 转到 [https://portal.office.de](https://portal.office.de)。

::: moniker-end

::: moniker range="o365-21vianet"

3. 转到 [https://portal.partner.microsoftonline.cn](https://portal.partner.microsoftonline.cn)。

::: moniker-end

    
4. 选择左上角的应用启动器图标，然后选择“**管理员**”。
    
    ![突出显示了管理应用程序的应用启动器](../../media/4eea9dbc-591b-48be-9916-322d41c6525b.png)
  
5. 阅读 "**成为管理"** 页面上的说明，然后选择 **"是，我想要成为管理员"**。
    
    > [!NOTE]
    >  如果未显示此选项，则表示已有一个管理员。 
  
## <a name="if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to"></a>如果我有多个域，我是否可以控制将用户添加到的租户？

如果您不执行任何操作，则将为每个用户电子邮件域和子域创建一个租户。
  
如果您希望所有用户都位于同一个租户中，而不考虑其电子邮件地址扩展名：
  
- 事先创建一个目标租户或使用现有租户，并添加希望在该租户中整合的所有现有域和子域。然后，电子邮件地址以这些域和子域结尾的所有用户在注册时将自动加入目标租户。
    
> [!IMPORTANT]
> 创建用户后，不提供在租户中移动用户的受支持的自动化机制。 若要了解如何向单个 Microsoft 365 租户添加域，请参阅[将域添加到 Office 365](../setup/add-domain.md)。 
  
> [!IMPORTANT]
> 有关管理租户的其他信息和指导，请参阅[什么是 POWER BI administration？](https://docs.microsoft.com/power-bi/service-admin-administering-power-bi-in-your-organization)。 
  
## <a name="how-can-i-prevent-users-from-joining-my-existing-tenant"></a>如何防止用户加入我的现有租户？

您可以作为管理员执行的步骤，以阻止用户加入您的现有租户。 如果你确实阻止这种情况，用户登录的尝试将失败，并将被定向到与组织的管理员联系。如果已在之前禁用了自动许可证分发（例如，Office 365 教育版、教职员和教职员工），则无需重复此过程。
  
以下步骤需要使用 Windows PowerShell。 要开始使用 Windows PowerShell，请参阅 [PowerShell 入门指南](https://go.microsoft.com/fwlink/p/?LinkID=286814)。
  
若要执行以下步骤，您必须安装最新的64位版本的[Azure Active Directory V2 PowerShell 模块](https://www.powershellgallery.com/packages/AzureADPreview/2.0.2.5)。
  
选择链接后，选择 "**运行**" 以运行安装程序包。 
  
 **禁用自动租户加入**：使用此 Windows PowerShell 命令可防止新用户加入托管租户：
  
要禁用新用户的自动租户加入，请执行下列操作： `Set-MsolCompanySettings -AllowEmailVerifiedUsers $false`
  
要启用新用户的自动租户加入，请执行下列操作： `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
> [!NOTE]
> 此阻止功能可防止组织中的新用户注册 Power BI。 在禁用组织的新 signups 之前注册 Power BI 的用户仍将保留其许可证。 请参阅[如何为已注册的用户删除 POWER bi？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)有关如何为之前注册该服务的用户删除 power bi 访问权限的说明，请参阅。 
  
## <a name="how-can-i-allow-users-to-join-my-existing-tenant"></a>如何允许用户加入我的现有租户？

若要允许用户加入你的租户，请运行相反的命令，如上面的问题中所述：  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
## <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>如何验证是否在租户中设置了阻止？

使用下列 PowerShell 脚本： `Get-MsolCompanyInformation | fl allow*`
  
## <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>如何防止现有用户开始使用 Power BI？

 **禁用自动许可证分发：** 使用此 Windows PowerShell 脚本可禁用现有用户的自动许可证分发。 如果已在之前禁用了自动许可证分发（例如，Office 365 教育版、教职员和教职员工），则无需重复此过程。 
  
要禁用现有用户的自动许可证分发，请执行下列操作： `Set-MsolCompanySettings -AllowAdHocSubscriptions $false`
  
要启用现有用户的自动许可证分发，请执行下列操作： `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
> [!NOTE]
> *AllowAdHocSubscriptions*标志用于控制组织中的多个用户功能，包括用户注册 Azure 权限管理服务的能力。 更改此标志将影响所有这些功能。 
  
## <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>如何允许我的现有用户注册 Power BI？

若要允许你的现有用户注册 Power BI，请运行相反命令，如上面的问题中所述：  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
## <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>如何为已注册的用户删除 Power BI？

如果用户注册了 Power BI，但是您不再希望该用户访问 Power BI，则可以删除该用户的 Power BI 许可证。

::: moniker range="o365-worldwide"
  
1. 在管理中心，转到“**用户**\><a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">活动用户</a>”页面。
    
2. 查找要删除其许可证的用户，然后选择其名称。
    
3. 在 "**许可证和应用**" 选项卡上，清除 " **Microsoft Power BI** " 复选框。
    
4. 选择“**保存更改**”。

::: moniker-end

  
::: moniker range="o365-germany"

1. 在管理中心，转到“**用户**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">活动用户</a>”页面。

2. 查找要删除其许可证的用户，然后选择其名称。
    
3. 在 "**产品许可证**" 旁边，选择 "**编辑**"。 
    
4. 切换**Microsoft POWER BI**选项。
    
5. 选择“**保存**”。

::: moniker-end

::: moniker range="o365-21vianet"

1. 在管理中心，转到“**用户**\><a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">活动用户</a>”页面。

2. 查找要删除其许可证的用户，然后选择其名称。
    
3. 在 "**产品许可证**" 旁边，选择 "**编辑**"。 
    
4. 切换**Microsoft POWER BI**选项。
    
5. 选择“**保存**”。

::: moniker-end 


## <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>我如何知道新用户何时加入我的租户？

作为此计划的一部分加入您的租户的用户将被分配一个唯一许可证，您可以在管理仪表板的活动用户窗格中对其进行筛选。
  
若要创建此新视图，请在管理中心内执行 "[创建自定义用户视图](../add-users/create-edit-or-delete-a-custom-user-view.md#create-a-custom-user-view)" 中的步骤。 在 "**分配的产品许可证**" 下，选择 " **Microsoft Power BI**"。 创建新视图后，你将能够查看租户中已注册此计划的所有用户。
  
## <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>我应准备其他任何内容吗？

您可能会遭遇密码重置请求不断增加的情形。 有关此过程的信息，请参阅[重置用户密码](../add-users/reset-passwords.md)。
  
您可以通过管理中心中的标准流程从租户中删除用户。 但是，如果用户仍使用您的组织中的活动电子邮件地址，则除非您阻止所有用户加入，否则他们仍能重新加入。
  
## <a name="why-did-1-million-licenses-for-microsoft-power-bi-show-up-in-my-tenant"></a>为什么 Microsoft Power BI 的1000000许可证在我的租户中显示？

作为一个合格的组织，您组织中的用户有资格使用 Microsoft Power BI 服务，这些许可证代表您的租户中新的 Power BI 用户的可用容量。 这些许可证是免费的。 如果你已选择允许用户注册 Power BI，则在完成注册过程时，将为他们分配这些免费许可证中的一个。 您还可以选择通过管理中心将这些许可证分配给用户。
  
## <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>这是免费的吗？ 我应支付这些许可证的费用吗？

这些许可证适用于 Power BI 的免费版本。 如果你希望了解其他功能，请查看 Power BI Pro 版本。
  
## <a name="why-1-million-licenses"></a>为什么有一百万个许可证？

我们选择了一个足够大的数字，大多数组织都有充足的许可证来提供这种好处，而不会延迟给用户。
  
## <a name="what-if-i-need-more-than-1-million-licenses"></a>如果需要一百万个以上的许可证，该怎么办？

如果需要获取附加许可证，请与您的 Microsoft 客户代表联系以了解更多信息。
