---
title: 使用 PowerShell 管理 Microsoft 365 组
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: 在本文中，您将了解如何在 PowerShell 中为 Microsoft 365 组执行常见的管理任务。
ms.openlocfilehash: a9c25fc4fbc2fb1f39c6e7b9e7e5de0e778fd513
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687716"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a><span data-ttu-id="3e2de-103">使用 PowerShell 管理 Microsoft 365 组</span><span class="sxs-lookup"><span data-stu-id="3e2de-103">Manage Microsoft 365 Groups with PowerShell</span></span>
 
<span data-ttu-id="3e2de-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="3e2de-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="3e2de-105">本文提供在 Microsoft PowerShell 中对组执行常见管理任务的步骤。</span><span class="sxs-lookup"><span data-stu-id="3e2de-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="3e2de-106">此外，它还列出了组的 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e2de-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="3e2de-107">有关管理 SharePoint 网站的信息，请参阅 [使用 PowerShell 管理 Sharepoint Online 网站](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)。</span><span class="sxs-lookup"><span data-stu-id="3e2de-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a><span data-ttu-id="3e2de-108">链接到 Microsoft 365 组使用指南</span><span class="sxs-lookup"><span data-stu-id="3e2de-108">Link to your Microsoft 365 Groups usage guidelines</span></span>
<span data-ttu-id="3e2de-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="3e2de-109"><a name="BK_LinkToGuideLines"> </a></span></span>

<span data-ttu-id="3e2de-110">当用户 [在 Outlook 中创建或编辑组](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)时，您可以向他们显示您的组织使用指南的链接。</span><span class="sxs-lookup"><span data-stu-id="3e2de-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="3e2de-111">例如，如果需要将特定的前缀或后缀添加到组名称中。</span><span class="sxs-lookup"><span data-stu-id="3e2de-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="3e2de-112">使用 Azure Active Directory (Azure AD) PowerShell 将用户指向你的 Microsoft 365 组的组织使用指南。</span><span class="sxs-lookup"><span data-stu-id="3e2de-112">Use the Azure Active Directory (Azure AD) PowerShell to point your users to your organization's usage guidelines for Microsoft 365 groups.</span></span> <span data-ttu-id="3e2de-113">请查看 [Azure Active Directory cmdlet 以配置组设置](https://go.microsoft.com/fwlink/?LinkID=827484) ，并按照在 **目录级别创建设置** 中的步骤定义使用情况准则超链接。</span><span class="sxs-lookup"><span data-stu-id="3e2de-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="3e2de-114">一旦运行 AAD cmdlet，当用户在 Outlook 中创建或编辑组时，用户将看到指向您的指导方针的链接。</span><span class="sxs-lookup"><span data-stu-id="3e2de-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![创建具有使用指南链接的新组](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![单击 "组使用指南" 查看组织的 Office 365 组指南](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-microsoft-365-group"></a><span data-ttu-id="3e2de-117">允许用户以 Microsoft 365 组的形式发送</span><span class="sxs-lookup"><span data-stu-id="3e2de-117">Allow users to Send as the Microsoft 365 Group</span></span>
<span data-ttu-id="3e2de-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="3e2de-118"><a name="BK_LinkToGuideLines"> </a></span></span>
  
<span data-ttu-id="3e2de-119">如果要将 Microsoft 365 组启用为 "代理发送"，请使用 [add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) 和 [add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) cmdlet 对此进行配置。</span><span class="sxs-lookup"><span data-stu-id="3e2de-119">If you want to enable your Microsoft 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="3e2de-120">一旦启用此设置，Microsoft 365 组用户可以使用 Outlook 或 web 上的 Outlook 以 Microsoft 365 组的形式发送和回复电子邮件。</span><span class="sxs-lookup"><span data-stu-id="3e2de-120">Once you enable this setting, Microsoft 365 group users can use Outlook or Outlook on the web to send and reply to email as the Microsoft 365 group.</span></span> <span data-ttu-id="3e2de-121">用户可以转到组，创建新的电子邮件，并将 "代理发送" 字段更改为组的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="3e2de-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="3e2de-122"> ([您也可以在 Exchange 管理中心中执行此操作](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)。 ) </span><span class="sxs-lookup"><span data-stu-id="3e2de-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="3e2de-123">使用下面的脚本替换为 *\<GroupAlias\>* 您要更新的组的别名，以及 *\<UserAlias\>* 要向其授予权限的用户的别名。</span><span class="sxs-lookup"><span data-stu-id="3e2de-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permissions.</span></span> <span data-ttu-id="3e2de-124">[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 以运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="3e2de-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="3e2de-125">一旦执行 cmdlet，用户就可以通过将组电子邮件地址添加到 " **发件** 人" 字段，转到要作为组发送的 outlook 或 web 上的 outlook。</span><span class="sxs-lookup"><span data-stu-id="3e2de-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="3e2de-126">为组织中的 Office 组创建分类</span><span class="sxs-lookup"><span data-stu-id="3e2de-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="3e2de-127">您可以创建您的组织中的用户在创建 Microsoft 365 组时可以设置的敏感度标签。</span><span class="sxs-lookup"><span data-stu-id="3e2de-127">You can create sensitivity labels that the users in your organization can set when they create a Microsoft 365 Group.</span></span> <span data-ttu-id="3e2de-128">如果要对组进行分类，我们建议使用敏感度标签，而不是以前的组分类功能。</span><span class="sxs-lookup"><span data-stu-id="3e2de-128">If you want to classify groups, we recommend using sensitivity labels instead of the previous groups classification feature.</span></span> <span data-ttu-id="3e2de-129">有关使用敏感度标签的信息，请参阅 [使用敏感度标签保护 Microsoft 团队、microsoft 365 组和 SharePoint 网站中的内容](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)。</span><span class="sxs-lookup"><span data-stu-id="3e2de-129">For information about using sensitivity labels, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e2de-130">如果你当前正在使用分类标签，则在启用灵敏度标签后，创建组的用户将无法再使用这些标签。</span><span class="sxs-lookup"><span data-stu-id="3e2de-130">If you are currently using classification labels, they will no longer be available to users who create groups once sensitivity labels are enabled.</span></span>

<span data-ttu-id="3e2de-131">您仍可以使用以前的组分类功能。</span><span class="sxs-lookup"><span data-stu-id="3e2de-131">You can still use the previous groups classification feature.</span></span> <span data-ttu-id="3e2de-132">您可以创建组织中的用户在创建 Office 365 组时可以设置的分类。</span><span class="sxs-lookup"><span data-stu-id="3e2de-132">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="3e2de-133">例如，您可以允许用户在其创建的组上设置 "Standard"、"Secret" 和 "Top Secret"。</span><span class="sxs-lookup"><span data-stu-id="3e2de-133">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="3e2de-134">默认情况下，不会设置组分类，您需要创建它才能使用户对其进行设置。</span><span class="sxs-lookup"><span data-stu-id="3e2de-134">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="3e2de-135">使用 Azure Active Directory PowerShell 将用户指向组织的 Office 365 组的使用指南。</span><span class="sxs-lookup"><span data-stu-id="3e2de-135">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="3e2de-136">查看 [用于配置组设置的 Azure Active Directory cmdlet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) ，并按照在 **目录级别创建设置** 中的步骤定义 Office 365 组的分类。</span><span class="sxs-lookup"><span data-stu-id="3e2de-136">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="3e2de-137">为了将说明与每个分类相关联，您可以使用 settings 属性  *ClassificationDescriptions* 来定义。</span><span class="sxs-lookup"><span data-stu-id="3e2de-137">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="3e2de-138">其中，分类与 ClassificationList 中的字符串匹配。</span><span class="sxs-lookup"><span data-stu-id="3e2de-138">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="3e2de-139">示例：</span><span class="sxs-lookup"><span data-stu-id="3e2de-139">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="3e2de-140">在运行上述 Azure Active Directory cmdlet 以设置分类之后，如果您想要为特定组设置分类，请运行 [remove-unifiedgroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e2de-140">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="3e2de-141">或创建一个具有分类的新组。</span><span class="sxs-lookup"><span data-stu-id="3e2de-141">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="3e2de-142">请查看 [使用 PowerShell With Exchange online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) ，并 [连接到 Exchange online powershell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) ，了解有关使用 exchange online powershell 的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="3e2de-142">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="3e2de-143">启用这些设置后，组所有者将能够从 Web 上的 Outlook 和 Outlook 中的下拉菜单中选择一个分类，并将其保存在 " **编辑** 组" 页面中。</span><span class="sxs-lookup"><span data-stu-id="3e2de-143">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![选择 Office 365 组分类](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="3e2de-145">隐藏 GAL 中的 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="3e2de-145">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="3e2de-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="3e2de-146"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="3e2de-147">您可以指定 Office 365 组是否出现在全局地址列表中 (GAL) 和组织中的其他列表。</span><span class="sxs-lookup"><span data-stu-id="3e2de-147">You can specify whether an Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="3e2de-148">例如，如果您有一个您不想在地址列表中显示的法律部门组，您可以阻止该组出现在 GAL 中。</span><span class="sxs-lookup"><span data-stu-id="3e2de-148">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="3e2de-149">运行 "设置统一组" cmdlet 以将组从地址列表中隐藏，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3e2de-149">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="3e2de-150">仅允许内部用户向 Office 365 组发送邮件</span><span class="sxs-lookup"><span data-stu-id="3e2de-150">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="3e2de-151"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="3e2de-151"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="3e2de-152">如果不希望其他组织中的用户向 Office 365 组发送电子邮件，您可以更改该组的设置。</span><span class="sxs-lookup"><span data-stu-id="3e2de-152">If you don't want users from other organization to send email to an Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="3e2de-153">仅允许内部用户向你的组发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="3e2de-153">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="3e2de-154">如果外部用户尝试向该组发送邮件，则会被拒绝。</span><span class="sxs-lookup"><span data-stu-id="3e2de-154">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="3e2de-155">运行 Remove-unifiedgroup cmdlet 以更新此设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3e2de-155">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="3e2de-156">向 Office 365 组添加邮件提示</span><span class="sxs-lookup"><span data-stu-id="3e2de-156">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="3e2de-157"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="3e2de-157"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="3e2de-158">当发件人尝试向 Office 365 组发送电子邮件时，可以向其显示邮件提示。</span><span class="sxs-lookup"><span data-stu-id="3e2de-158">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="3e2de-159">运行 "设置统一组" cmdlet 以将邮件提示添加到组中：</span><span class="sxs-lookup"><span data-stu-id="3e2de-159">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="3e2de-160">除了邮件提示，还可以设置 MailTipTranslations，后者为邮件提示指定其他语言。</span><span class="sxs-lookup"><span data-stu-id="3e2de-160">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="3e2de-161">假设您想要进行西班牙语转换，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3e2de-161">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="3e2de-162">更改 Office 365 组的显示名称</span><span class="sxs-lookup"><span data-stu-id="3e2de-162">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="3e2de-163">"显示名称" 指定 Office 365 组的名称。</span><span class="sxs-lookup"><span data-stu-id="3e2de-163">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="3e2de-164">您可以在 exchange 管理中心或 Microsoft 365 管理中心中看到此名称。</span><span class="sxs-lookup"><span data-stu-id="3e2de-164">You can see this name in your exchange admin center or Microsoft 365 admin center.</span></span> <span data-ttu-id="3e2de-165">您可以编辑组的显示名称，或通过运行 Remove-unifiedgroup 命令为现有的 Office 365 组分配显示名称：</span><span class="sxs-lookup"><span data-stu-id="3e2de-165">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="3e2de-166">将适用于 Outlook 的 Office 365 组的默认设置更改为公共或专用</span><span class="sxs-lookup"><span data-stu-id="3e2de-166">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="3e2de-167"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="3e2de-167"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="3e2de-168">默认情况下，Outlook 中的 Office 365 组创建为私有。</span><span class="sxs-lookup"><span data-stu-id="3e2de-168">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="3e2de-169">如果您的组织希望默认情况下将 Office 365 组创建为 Public (或返回到私有) ，请使用以下 PowerShell cmdlet 语法：</span><span class="sxs-lookup"><span data-stu-id="3e2de-169">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="3e2de-170">设置为专用：</span><span class="sxs-lookup"><span data-stu-id="3e2de-170">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="3e2de-171">若要验证设置，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3e2de-171">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="3e2de-172">若要了解详细信息，请参阅 [set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) 和 [set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig)。</span><span class="sxs-lookup"><span data-stu-id="3e2de-172">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="3e2de-173">Office 365 组 cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e2de-173">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="3e2de-174">以下 cmdlet 可与 Office 365 组一起使用。</span><span class="sxs-lookup"><span data-stu-id="3e2de-174">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="3e2de-175">**Cmdlet 名称**</span><span class="sxs-lookup"><span data-stu-id="3e2de-175">**Cmdlet name**</span></span>|<span data-ttu-id="3e2de-176">**说明**</span><span class="sxs-lookup"><span data-stu-id="3e2de-176">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="3e2de-177">Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="3e2de-177">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="3e2de-178">使用此 cmdlet 可查找现有的 Office 365 组，并查看组对象的属性</span><span class="sxs-lookup"><span data-stu-id="3e2de-178">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="3e2de-179">Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="3e2de-179">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="3e2de-180">更新特定 Office 365 组的属性</span><span class="sxs-lookup"><span data-stu-id="3e2de-180">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="3e2de-181">新 Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="3e2de-181">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="3e2de-182">创建新的 Office 365 组。</span><span class="sxs-lookup"><span data-stu-id="3e2de-182">Create a new Office 365 group.</span></span> <span data-ttu-id="3e2de-183">此 cmdlet 提供了一组最少的参数，用于设置扩展属性的值在创建新组后使用 Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="3e2de-183">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="3e2de-184">Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="3e2de-184">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="3e2de-185">删除现有的 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="3e2de-185">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="3e2de-186">UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="3e2de-186">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="3e2de-187">检索 Office 365 组的成员资格和所有者信息</span><span class="sxs-lookup"><span data-stu-id="3e2de-187">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="3e2de-188">外接 UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="3e2de-188">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="3e2de-189">向现有 Office 365 组添加成百上千个用户或新所有者</span><span class="sxs-lookup"><span data-stu-id="3e2de-189">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="3e2de-190">UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="3e2de-190">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="3e2de-191">从现有 Office 365 组中删除所有者和成员</span><span class="sxs-lookup"><span data-stu-id="3e2de-191">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="3e2de-192">Set-userphoto</span><span class="sxs-lookup"><span data-stu-id="3e2de-192">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="3e2de-193">用于查看有关与帐户关联的用户照片的信息。</span><span class="sxs-lookup"><span data-stu-id="3e2de-193">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="3e2de-194">用户照片存储在 Active Directory 中</span><span class="sxs-lookup"><span data-stu-id="3e2de-194">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="3e2de-195">Set-userphoto</span><span class="sxs-lookup"><span data-stu-id="3e2de-195">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="3e2de-196">用于将用户照片与帐户关联。</span><span class="sxs-lookup"><span data-stu-id="3e2de-196">Used to associate a user photo with an account.</span></span> <span data-ttu-id="3e2de-197">用户照片存储在 Active Directory 中</span><span class="sxs-lookup"><span data-stu-id="3e2de-197">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="3e2de-198">Set-userphoto</span><span class="sxs-lookup"><span data-stu-id="3e2de-198">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="3e2de-199">删除 Office 365 组的照片</span><span class="sxs-lookup"><span data-stu-id="3e2de-199">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="3e2de-200">相关主题</span><span class="sxs-lookup"><span data-stu-id="3e2de-200">Related topics</span></span>

[<span data-ttu-id="3e2de-201">将通讯组列表升级到 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="3e2de-201">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="3e2de-202">管理可以创建 Office 365 组的用户</span><span class="sxs-lookup"><span data-stu-id="3e2de-202">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="3e2de-203">管理对 Office 365 组的来宾访问</span><span class="sxs-lookup"><span data-stu-id="3e2de-203">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="3e2de-204">将静态组成员身份更改为中的动态</span><span class="sxs-lookup"><span data-stu-id="3e2de-204">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)