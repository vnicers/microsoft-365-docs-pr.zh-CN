---
title: 从组织删除用户
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
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: d5155593-3bac-4d8d-9d8b-f4513a81479e
description: 了解如何删除用户帐户。 决定如何处理用户的电子邮件、OneDrive 内容以及是否保留产品许可证或停止付款。
ms.openlocfilehash: f54d0d4a39ff116b4bee6aceb10233344835a455
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/24/2020
ms.locfileid: "42238164"
---
# <a name="delete-a-user-from-your-organization"></a><span data-ttu-id="62881-104">从组织删除用户</span><span class="sxs-lookup"><span data-stu-id="62881-104">Delete a user from your organization</span></span>
  
||
|:-----|
|<span data-ttu-id="62881-105">**想要了解如何删除您*自己*在工作或学校中使用的 Office 365 用户帐户吗？请与你的工作或大学的技术支持部门联系，为你执行这些步骤。**</span><span class="sxs-lookup"><span data-stu-id="62881-105">**Looking for how to delete your *own* Office 365 user account that you use at work or school? Contact the technical support at your work or university to do these steps for you.**</span></span>|
   
## <a name="what-you-need-to-know-about-deleting-users"></a><span data-ttu-id="62881-106">删除用户需知事项</span><span class="sxs-lookup"><span data-stu-id="62881-106">What you need to know about deleting users</span></span>

- <span data-ttu-id="62881-107">仅拥有企业或学校 [Office 365 全局管理员](about-admin-roles.md)或用户管理权限的人员才可删除用户帐户。</span><span class="sxs-lookup"><span data-stu-id="62881-107">Only people who have [Office 365 global admin](about-admin-roles.md) or User management permissions for the business or school can delete user accounts.</span></span> 
    
- <span data-ttu-id="62881-108">永久删除用户数据前 30 天内可[还原](restore-user.md)帐户。</span><span class="sxs-lookup"><span data-stu-id="62881-108">You have 30 days to [restore](restore-user.md) the account before the user's data is permanently deleted.</span></span> 
    
- <span data-ttu-id="62881-p102">若要保留用户的 OneDrive 数据，请将其移动到其他位置。甚至可在删除帐户后 30 天内执行此操作。请参阅[访问并备份以往用户的数据](get-access-to-and-back-up-a-former-user-s-data.md)。无需移动其 SharePoint 文件；仍将有权访问它们。</span><span class="sxs-lookup"><span data-stu-id="62881-p102">If you want to keep the user's OneDrive data, move it to a different location. You can even do this up to 30 days after deleting the account. See [Get access to and back up a former user's data](get-access-to-and-back-up-a-former-user-s-data.md). You don't need to move their SharePoint files; you'll still have access to them.</span></span>
    
- <span data-ttu-id="62881-p103">若要保留用户的电子邮件，请在删除帐户 **之前** ，将电子邮件移动到其他位置。如果已删除该帐户：如果删除时间未超过 30 天，可恢复该帐户，然后移动电子邮件数据，最后删除该帐户。请参阅 [访问并备份以往用户的数据](get-access-to-and-back-up-a-former-user-s-data.md)。</span><span class="sxs-lookup"><span data-stu-id="62881-p103">If you want to keep the user's email, **BEFORE** you delete the account, move the email to a different location. If you've already deleted the account: if it's been less than 30 days you can restore it, then move the email data, then delete the account. See [Get access to and back up a former user's data](get-access-to-and-back-up-a-former-user-s-data.md).</span></span>
    
- <span data-ttu-id="62881-116">如果您有一个企业订阅（如 Office 365 企业版 E3），则可以通过将已删除的 Office 365 用户帐户转换为*非活动邮箱*来保留邮箱数据。</span><span class="sxs-lookup"><span data-stu-id="62881-116">If you have an Enterprise subscription like Office 365 Enterprise E3, you can preserve the mailbox data of a deleted Office 365 user account by turning it into an *inactive mailbox*.</span></span> <span data-ttu-id="62881-117">若要了解详细信息，请参阅 [管理 Exchange Online 中的非活动邮箱](https://docs.microsoft.com/microsoft-365/compliance/inactive-mailboxes-in-office-365)。</span><span class="sxs-lookup"><span data-stu-id="62881-117">To learn more, see [Manage inactive mailboxes in Exchange Online](https://docs.microsoft.com/microsoft-365/compliance/inactive-mailboxes-in-office-365).</span></span>


## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a><span data-ttu-id="62881-118">全局管理员：删除用户，停止为其许可证付款，并选择要对其电子邮件和 OneDrive 内容执行的操作</span><span class="sxs-lookup"><span data-stu-id="62881-118">Global admin: Delete a user, stop paying for their license, and choose what to do with their email and OneDrive content</span></span>

<span data-ttu-id="62881-119">如果您是全局管理员，则在删除用户时，还可以向其他用户授予对其电子邮件的访问权限，并选择要对其 OneDrive 内容执行的操作。</span><span class="sxs-lookup"><span data-stu-id="62881-119">If you are a global administrator, when you delete a user you can also give another user access to their email, and choose what to do with their OneDrive content.</span></span> 

  
### <a name="things-to-consider"></a><span data-ttu-id="62881-120">要考虑的事项...</span><span class="sxs-lookup"><span data-stu-id="62881-120">Things to consider...</span></span>

<span data-ttu-id="62881-121">在开始之前，请考虑要对用户的电子邮件和 OneDrive 内容执行的操作，以及是否要保留许可证或停止付款。</span><span class="sxs-lookup"><span data-stu-id="62881-121">Before you begin, think about what you want to do with the user's email and OneDrive content, and whether you want to keep the license or stop paying for it.</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="62881-122">产品许可证</span><span class="sxs-lookup"><span data-stu-id="62881-122">Product licenses</span></span>  <br/> |<span data-ttu-id="62881-123">您可以从用户中删除该许可证并将其从订阅中删除，以停止对该许可证付款。</span><span class="sxs-lookup"><span data-stu-id="62881-123">You can remove the license from the user and remove it from your subscriptions to stop paying for that license.</span></span> <span data-ttu-id="62881-124">如果选择此选项，将从你的订阅中自动删除许可证。</span><span class="sxs-lookup"><span data-stu-id="62881-124">If you select this option, the license will be removed automatically from your subscriptions.</span></span>  <br/><br/> <span data-ttu-id="62881-125">如果许可证是通过合作伙伴或批量许可购买**的，则无法删除许可证**。</span><span class="sxs-lookup"><span data-stu-id="62881-125">**You can't remove the license** if you bought it through a Partner or volume licensing.</span></span> <span data-ttu-id="62881-126">如果你正在支付年度计划，或者你正在付费周期中间，你将无法从订阅中删除许可证，直到你的承诺完成。</span><span class="sxs-lookup"><span data-stu-id="62881-126">If you are paying for an annual plan or if you are in the middle of a billing cycle, you won't be able to remove the license from your subscription until your commitment is completed.</span></span>  <br/> |
|<span data-ttu-id="62881-127">OneDrive 内容</span><span class="sxs-lookup"><span data-stu-id="62881-127">OneDrive content</span></span>  <br/> |<span data-ttu-id="62881-128">如果用户将文件保存到 OneDrive，则可以向其他用户授予对这些文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="62881-128">If the user saved their files to OneDrive, you can give another user access to these files.</span></span>  <br/><br/> <span data-ttu-id="62881-129">您需要将您想要保留的文件移到为 OneDrive 文件设置的保留期内。</span><span class="sxs-lookup"><span data-stu-id="62881-129">You'll need to move the files you want to keep within the retention period that is set for OneDrive files.</span></span> <span data-ttu-id="62881-130">**默认情况下，保留期为30天。**</span><span class="sxs-lookup"><span data-stu-id="62881-130">**By default, the retention period is 30 days.**</span></span> <span data-ttu-id="62881-131">如果您在删除用户后不在保留期内移动文件，则 OneDrive 内容将被永久删除。</span><span class="sxs-lookup"><span data-stu-id="62881-131">If you don't move the files within the retention period after deleting the user, the OneDrive content will be permanently deleted.</span></span> <span data-ttu-id="62881-132">若要增加您为已删除帐户保留的 OneDrive 文件的天数，请参阅[设置已删除用户的 onedrive 保留](https://support.office.com/article/fa1641ea-9f03-4f34-a826-dbd8697e76fe.aspx)值。</span><span class="sxs-lookup"><span data-stu-id="62881-132">To increase the number of days that you retain OneDrive files for deleted accounts, see [Set the OneDrive retention for deleted users](https://support.office.com/article/fa1641ea-9f03-4f34-a826-dbd8697e76fe.aspx).</span></span>  <br/><br/> <span data-ttu-id="62881-133">**重要说明！**</span><span class="sxs-lookup"><span data-stu-id="62881-133">**Important!**</span></span> <span data-ttu-id="62881-134">如果已删除的用户使用个人计算机从 SharePoint 和 OneDrive 下载文件，则无法擦除它们存储在计算机上的文件。</span><span class="sxs-lookup"><span data-stu-id="62881-134">If the deleted user used a personal computer to download files from SharePoint and OneDrive, there's no way for you to wipe those files they stored on their computer.</span></span> <span data-ttu-id="62881-135">他们将继续拥有从 OneDrive 中同步的任何文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="62881-135">They will continue to have access to any files that were synced from OneDrive.</span></span>           |
|<span data-ttu-id="62881-136">电子邮件</span><span class="sxs-lookup"><span data-stu-id="62881-136">Email</span></span>  <br/> | <span data-ttu-id="62881-137">授予另一个用户对已删除用户的电子邮件的访问权限会将已删除用户的邮箱转换为共享邮箱。</span><span class="sxs-lookup"><span data-stu-id="62881-137">Giving another user access to the deleted user's email will convert the deleted user's mailbox to a shared mailbox.</span></span> <span data-ttu-id="62881-138">然后，新邮箱所有者可以访问邮箱并监视新电子邮件。</span><span class="sxs-lookup"><span data-stu-id="62881-138">The new mailbox owner can then access the mailbox and monitor for new email.</span></span> <span data-ttu-id="62881-139">此外，还将提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="62881-139">You'll also have the following options:</span></span>  <br/>  <br/><span data-ttu-id="62881-140">更改显示名称-建议您更改显示名称，以便在活动用户列表中识别共享邮箱。</span><span class="sxs-lookup"><span data-stu-id="62881-140">Change the display name - We recommend changing the display name so that it will be easy to identify the shared mailbox in the Active users list.</span></span>  <br/>  <span data-ttu-id="62881-141">打开自动答复-我们已经为你编写了礼貌的自动答复。</span><span class="sxs-lookup"><span data-stu-id="62881-141">Turn on automatic replies - We've already written a polite automatic reply for you.</span></span> <span data-ttu-id="62881-142">您可以向组织中的人员和组织外部的人员发送不同的自动答复。</span><span class="sxs-lookup"><span data-stu-id="62881-142">You can send a different automatic replies to people within your organization and people from outside your organization.</span></span>  <br/> <br/> <span data-ttu-id="62881-143">清除别名-别名是用户的其他电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="62881-143">Clean up aliases - Aliases are additional email addresses for users.</span></span> <span data-ttu-id="62881-144">有些组织不使用它们，因此，如果你没有任何人，则无需在此处执行任何其他操作。</span><span class="sxs-lookup"><span data-stu-id="62881-144">Some organizations don't use them, so if you don't have any you don't need to do anything else here.</span></span> <span data-ttu-id="62881-145">如果用户确实拥有别名，我们建议将其删除，以便您可以重新使用这些电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="62881-145">If the user does have aliases, we recommend removing them so that you can re-use those email addresses.</span></span> <span data-ttu-id="62881-146">否则，将无法重新使用这些电子邮件地址，直到已删除邮箱的保留期通过。</span><span class="sxs-lookup"><span data-stu-id="62881-146">Otherwise, you can’t re-use those email addresses until the retention period for deleted mailboxes has passed.</span></span> <span data-ttu-id="62881-147">默认情况下，已删除的邮箱可恢复30天。</span><span class="sxs-lookup"><span data-stu-id="62881-147">By default, a deleted mailbox is recoverable for 30 days.</span></span> <span data-ttu-id="62881-148">有关详细信息，请参阅[Delete or restore user 邮箱 In Exchange Online](https://docs.microsoft.com/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox)。</span><span class="sxs-lookup"><span data-stu-id="62881-148">For more information, see  [Delete or restore user mailboxes in Exchange Online](https://docs.microsoft.com/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox).</span></span> <br/> |
|<span data-ttu-id="62881-149">Active Directory</span><span class="sxs-lookup"><span data-stu-id="62881-149">Active Directory</span></span>  <br/> |<span data-ttu-id="62881-150">如果你的公司使用与 Azure AD 同步的 **Active Directory** ，则需要从 Active Directory 中删除用户帐户。</span><span class="sxs-lookup"><span data-stu-id="62881-150">If your business uses **Active Directory** that is synchronizing with Azure AD, you need to delete the user account from Active Directory.</span></span> <span data-ttu-id="62881-151">无法通过 Office 365 删除帐户。</span><span class="sxs-lookup"><span data-stu-id="62881-151">You can't do it through Office 365.</span></span> <span data-ttu-id="62881-152">有关说明，请参阅[删除用户帐户](https://go.microsoft.com/fwlink/p/?linkid=841808)。</span><span class="sxs-lookup"><span data-stu-id="62881-152">For instructions, see [Delete a User Account](https://go.microsoft.com/fwlink/p/?linkid=841808).</span></span>  <br/> |
   
### <a name="get-started"></a><span data-ttu-id="62881-153">入门</span><span class="sxs-lookup"><span data-stu-id="62881-153">Get started</span></span>

::: moniker range="o365-worldwide"

> [!NOTE]
> <span data-ttu-id="62881-154">如果未使用新的 Microsoft 365 管理中心，可通过选择“**试用新的管理中心**”切换按钮（位于主页顶部）将其打开。</span><span class="sxs-lookup"><span data-stu-id="62881-154">If you're not using the new Microsoft 365 admin center, you can turn it on by selecting the **Try the new admin center** toggle located at the top of the Home page.</span></span>

::: moniker-end

<span data-ttu-id="62881-155">由于引导式体验会逐步完成删除用户的步骤，下面介绍了如何入门。</span><span class="sxs-lookup"><span data-stu-id="62881-155">Since the guided experience walks through the steps to delete a user, here's how to get started.</span></span>

::: moniker range="o365-worldwide"

1. <span data-ttu-id="62881-156">在管理中心，转到“**用户**\><a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">活动用户</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="62881-156">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Active users</a> page.</span></span>

::: moniker-end

::: moniker range="o365-germany"

1. <span data-ttu-id="62881-157">在管理中心，转到“**用户**\><a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">活动用户</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="62881-157">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Active users</a> page.</span></span>

::: moniker-end

::: moniker range="o365-21vianet"

1. <span data-ttu-id="62881-158">在管理中心，转到“**用户**\><a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">活动用户</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="62881-158">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Active users</a> page.</span></span>

::: moniker-end

2. <span data-ttu-id="62881-159">选择要删除的用户，然后选择 "**删除用户**"。</span><span class="sxs-lookup"><span data-stu-id="62881-159">Select the user you want to delete, and then select **Delete user**.</span></span>

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a><span data-ttu-id="62881-160">用户管理管理员：从 Office 365 中删除一个或多个用户</span><span class="sxs-lookup"><span data-stu-id="62881-160">User management admin: Delete one or more users from Office 365</span></span>


 <span data-ttu-id="62881-p113">**重要提示** ：如果已将用户帐户 [转换为共享邮箱](../email/convert-user-mailbox-to-shared-mailbox.md)或在该帐户上设置了电子邮件转发，则不要删除该帐户。保留该帐户才能使用那些功能。如果已将其转换为共享邮箱，可以从其中[停止支付许可证费用](#stop-paying-for-the-license)，以避免支付费用。如果设置电子邮件转发，则不能删除许可证。执行此操作将导致电子邮件无法转发并导致邮箱停用。</span><span class="sxs-lookup"><span data-stu-id="62881-p113">**IMPORTANT**: Don't delete a user's account if you've [converted it to a shared mailbox](../email/convert-user-mailbox-to-shared-mailbox.md) or if you've set up email forwarding on the account. Those functions need the account there. If you've converted it to a shared mailbox, you can [Stop paying for the license](#stop-paying-for-the-license) from it so you aren't paying for it. If you set up email forwarding, you cannot remove the license. Doing so will stop the email forwarding and inactivate the mailbox.</span></span> 
  
::: moniker range="o365-worldwide"

1. <span data-ttu-id="62881-166">在管理中心，转到“**用户**\><a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">活动用户</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="62881-166">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Active users</a> page.</span></span>  

2. <span data-ttu-id="62881-167">选择要删除的用户的名称，选择 "**更多选项**（**...**）"，然后选择 "**删除用户**"。</span><span class="sxs-lookup"><span data-stu-id="62881-167">Select the names of the users that you want to delete, select **More options** (**...**), and then choose  **Delete user**.</span></span>

   <span data-ttu-id="62881-168">虽然你删除了用户帐户，但你**仍在支付许可证费用**。</span><span class="sxs-lookup"><span data-stu-id="62881-168">Although you deleted the user's account, **you're still paying for the license**.</span></span> <span data-ttu-id="62881-169">请参阅下一个过程以停止付款许可证。</span><span class="sxs-lookup"><span data-stu-id="62881-169">See the next procedure to stop paying for the license.</span></span>  <span data-ttu-id="62881-170">或者，可以将许可证分配给其他用户。</span><span class="sxs-lookup"><span data-stu-id="62881-170">Or, you can assign the license to another user.</span></span> <span data-ttu-id="62881-171">不会自动将其分配给某人。</span><span class="sxs-lookup"><span data-stu-id="62881-171">It won't be assigned to someone automatically.</span></span>

::: moniker-end

::: moniker range="o365-germany"

1. <span data-ttu-id="62881-172">在管理中心，转到“**用户**\><a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">活动用户</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="62881-172">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Active users</a> page.</span></span>

2. <span data-ttu-id="62881-173">选择要删除的用户的名称，然后在 "**批量操作**" 窗格中选择 "**删除用户**"。</span><span class="sxs-lookup"><span data-stu-id="62881-173">Select the names of the users that you want to delete, and in the **Bulk actions** pane, choose **Delete users**.</span></span>

   <span data-ttu-id="62881-174">虽然你删除了用户帐户，但你**仍在支付许可证费用**。</span><span class="sxs-lookup"><span data-stu-id="62881-174">Although you deleted the user's account, **you're still paying for the license**.</span></span> <span data-ttu-id="62881-175">请参阅下一个过程以停止付款许可证。</span><span class="sxs-lookup"><span data-stu-id="62881-175">See the next procedure to stop paying for the license.</span></span>  <span data-ttu-id="62881-176">或者，可以将许可证分配给其他用户。</span><span class="sxs-lookup"><span data-stu-id="62881-176">Or, you can assign the license to another user.</span></span> <span data-ttu-id="62881-177">不会自动将其分配给某人。</span><span class="sxs-lookup"><span data-stu-id="62881-177">It won't be assigned to someone automatically.</span></span>

::: moniker-end

::: moniker range="o365-21vianet"

1. <span data-ttu-id="62881-178">在管理中心，转到“**用户**\><a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">活动用户</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="62881-178">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Active users</a> page.</span></span>

2. <span data-ttu-id="62881-179">选择要删除的用户的名称，然后在 "**批量操作**" 窗格中选择 "**删除用户**"。</span><span class="sxs-lookup"><span data-stu-id="62881-179">Select the names of the users that you want to delete, and in the **Bulk actions** pane, choose **Delete users**.</span></span>

   <span data-ttu-id="62881-180">虽然你删除了用户帐户，但你**仍在支付许可证费用**。</span><span class="sxs-lookup"><span data-stu-id="62881-180">Although you deleted the user's account, **you're still paying for the license**.</span></span> <span data-ttu-id="62881-181">请参阅下一个过程以停止付款许可证。</span><span class="sxs-lookup"><span data-stu-id="62881-181">See the next procedure to stop paying for the license.</span></span>  <span data-ttu-id="62881-182">或者，可以将许可证分配给其他用户。</span><span class="sxs-lookup"><span data-stu-id="62881-182">Or, you can assign the license to another user.</span></span> <span data-ttu-id="62881-183">不会自动将其分配给某人。</span><span class="sxs-lookup"><span data-stu-id="62881-183">It won't be assigned to someone automatically.</span></span>

::: moniker-end

### <a name="stop-paying-for-the-license"></a><span data-ttu-id="62881-184">停止支付许可证费用</span><span class="sxs-lookup"><span data-stu-id="62881-184">Stop paying for the license</span></span>

<span data-ttu-id="62881-185">减少许可证的数量是一个单独的步骤，仅可由全局管理员或帐单管理员执行。</span><span class="sxs-lookup"><span data-stu-id="62881-185">Reducing the number of licenses is a separate step that can only be performed by the global admin or billing admin.</span></span> 
  
::: moniker range="o365-worldwide"

1. <span data-ttu-id="62881-186">在管理中心，转到“**账单**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">产品和服务</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="62881-186">In the admin center, go to the **Billing** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Products & services</a> page.</span></span> <span data-ttu-id="62881-187">如果看不到此选项，则不是全局管理员或帐单管理员，无法执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="62881-187">If you don't see this option, you aren't a global admin or billing admin, and can't do this step.</span></span>

2. <span data-ttu-id="62881-188">选择订阅（如果您有多个订阅），然后选择 "**添加/删除许可证**" 以删除许可证，以便在您雇用其他人之前不支付。</span><span class="sxs-lookup"><span data-stu-id="62881-188">Select the subscription (if you have more than one) and then select **Add/Remove licenses** to delete the license so you don't pay for it until you hire another person.</span></span>  

   <span data-ttu-id="62881-189">稍后当您完成将其他人添加到您的企业的步骤时，系统将提示您同时购买许可证，只需一步即可！</span><span class="sxs-lookup"><span data-stu-id="62881-189">Later when you go through the steps to add another person to your business, you'll be prompted to buy a license at the same time, with just one step!</span></span>

::: moniker-end

::: moniker range="o365-germany"

1. <span data-ttu-id="62881-190">在管理中心中，转到 "**记帐** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">订阅</a>" 页。</span><span class="sxs-lookup"><span data-stu-id="62881-190">In the admin center, go to the **Billing** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Subscriptions</a> page.</span></span> <span data-ttu-id="62881-191">如果看不到此选项，则不是全局管理员或帐单管理员，无法执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="62881-191">If you don't see this option, you aren't a global admin or billing admin, and can't do this step.</span></span>

2. <span data-ttu-id="62881-192">选择订阅（如果您有多个订阅），然后选择 "**添加/删除许可证**" 以删除许可证，以便在您雇用其他人之前不支付。</span><span class="sxs-lookup"><span data-stu-id="62881-192">Select the subscription (if you have more than one) and then select **Add/Remove licenses** to delete the license so you don't pay for it until you hire another person.</span></span>  

   <span data-ttu-id="62881-193">稍后当您完成将其他人添加到您的企业的步骤时，系统将提示您同时购买许可证，只需一步即可！</span><span class="sxs-lookup"><span data-stu-id="62881-193">Later when you go through the steps to add another person to your business, you'll be prompted to buy a license at the same time, with just one step!</span></span>

::: moniker-end

::: moniker range="o365-21vianet"

1. <span data-ttu-id="62881-194">在管理中心中，转到 "**记帐** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">订阅</a>" 页。</span><span class="sxs-lookup"><span data-stu-id="62881-194">In the admin center, go to the **Billing** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Subscriptions</a> page.</span></span> <span data-ttu-id="62881-195">如果看不到此选项，则不是全局管理员或帐单管理员，无法执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="62881-195">If you don't see this option, you aren't a global admin or billing admin, and can't do this step.</span></span>

2. <span data-ttu-id="62881-196">选择订阅（如果您有多个订阅），然后选择 "**添加/删除许可证**" 以删除许可证，以便在您雇用其他人之前不支付。</span><span class="sxs-lookup"><span data-stu-id="62881-196">Select the subscription (if you have more than one) and then select **Add/Remove licenses** to delete the license so you don't pay for it until you hire another person.</span></span>  

   <span data-ttu-id="62881-197">稍后当您完成将其他人添加到您的企业的步骤时，系统将提示您同时购买许可证，只需一步即可！</span><span class="sxs-lookup"><span data-stu-id="62881-197">Later when you go through the steps to add another person to your business, you'll be prompted to buy a license at the same time, with just one step!</span></span>

::: moniker-end 

## <a name="delete-many-users-at-the-same-time"></a><span data-ttu-id="62881-198">同时删除多个用户</span><span class="sxs-lookup"><span data-stu-id="62881-198">Delete many users at the same time</span></span>

<span data-ttu-id="62881-199">请参阅[Get-msoluser](https://go.microsoft.com/fwlink/p/?linkid=842230) PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="62881-199">See the [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?linkid=842230) PowerShell cmdlet.</span></span>

## <a name="fix-issues-with-deleting-a-user"></a><span data-ttu-id="62881-200">解决删除用户时遇到的问题</span><span class="sxs-lookup"><span data-stu-id="62881-200">Fix issues with deleting a user</span></span>

<span data-ttu-id="62881-201">以下是人们删除用户时遇到的最常见的问题：</span><span class="sxs-lookup"><span data-stu-id="62881-201">Here are the most common issues people encounter when deleting a user:</span></span>
  
- <span data-ttu-id="62881-202">**将收到一条错误消息，其中 "无法删除用户" 一线。请稍后再试。 "**</span><span class="sxs-lookup"><span data-stu-id="62881-202">**You get an error message along the lines of "User cannot be deleted. Please try again later."**</span></span> <span data-ttu-id="62881-203">Doublecheck 帐户是否设置了电子邮件转发功能，或者是否已将其转换为共享邮箱。</span><span class="sxs-lookup"><span data-stu-id="62881-203">Doublecheck whether the account has email forwarding set up on it, or it's been converted to a shared mailbox.</span></span> <span data-ttu-id="62881-204">这两种情况都将导致该错误。</span><span class="sxs-lookup"><span data-stu-id="62881-204">Both of these will cause that error.</span></span> <span data-ttu-id="62881-205">如果帐户有电子邮件转发或已转换为共享邮箱，请不要删除该帐户。</span><span class="sxs-lookup"><span data-stu-id="62881-205">Don't delete the account if it has email forwarding or it's been converted to a shared mailbox.</span></span>

- <span data-ttu-id="62881-206">**你没有删除用户的相应权限** 。</span><span class="sxs-lookup"><span data-stu-id="62881-206">**You don't have the appropriate permissions to delete a user**.</span></span> <span data-ttu-id="62881-207">只有属于[Office 365 全局管理员或用户管理管理员](about-admin-roles.md)的人员才能删除用户。</span><span class="sxs-lookup"><span data-stu-id="62881-207">Only people who are [Office 365 global admins or user management admins](about-admin-roles.md) can delete users.</span></span> <span data-ttu-id="62881-208">该管理员通常是学校或企业中的技术支持人员。</span><span class="sxs-lookup"><span data-stu-id="62881-208">Usually this is the technical support in your school or business.</span></span>

- <span data-ttu-id="62881-p122">**删除用户后，用户姓名继续显示在全局通讯录中** 。企业使用 Active Directory 时会出现这种情况。必须从 Active Directory 中删除用户帐户。有关说明，请参阅 TechNet 文章： [删除用户帐户](https://go.microsoft.com/fwlink/p/?linkid=841808)。</span><span class="sxs-lookup"><span data-stu-id="62881-p122">**You delete the user but their name continues appear in your global address book**. This happens when a business is using Active Directory. You have to delete the users account from Active Directory. For instructions, see this TechNet article: [Delete a User Account.](https://go.microsoft.com/fwlink/p/?linkid=841808)</span></span>

||
|:-----|
|<span data-ttu-id="62881-213">**是否要从计算机中删除 Office 365？请转到[取消订阅](../../commerce/subscriptions/cancel-your-subscription.md)。**</span><span class="sxs-lookup"><span data-stu-id="62881-213">**Do you want to delete Office 365 from your computer? Go to [Cancel your subscription](../../commerce/subscriptions/cancel-your-subscription.md).**</span></span>|
   
## <a name="related-articles"></a><span data-ttu-id="62881-214">相关文章</span><span class="sxs-lookup"><span data-stu-id="62881-214">Related articles</span></span>

[<span data-ttu-id="62881-215">还原用户</span><span class="sxs-lookup"><span data-stu-id="62881-215">Restore a user</span></span>](restore-user.md)
  
[<span data-ttu-id="62881-216">永久删除邮箱</span><span class="sxs-lookup"><span data-stu-id="62881-216">Permanently delete a mailbox</span></span>](https://technet.microsoft.com/library/jj863440%28v=exchg.150%29.aspx)

[<span data-ttu-id="62881-217">从 Office 365 中删除以前的员工</span><span class="sxs-lookup"><span data-stu-id="62881-217">Remove a former employee from Office 365</span></span>](remove-former-employee.md)

[<span data-ttu-id="62881-218">向 Office 365 添加新员工</span><span class="sxs-lookup"><span data-stu-id="62881-218">Add a new employee to Office 365</span></span>](add-new-employee.md)

<span data-ttu-id="62881-219">[删除用户帐户](https://go.microsoft.com/fwlink/p/?linkid=841808)：如果您的公司使用与 Azure AD 同步的**Active Directory** ，请使用这些说明。</span><span class="sxs-lookup"><span data-stu-id="62881-219">[Delete a User Account](https://go.microsoft.com/fwlink/p/?linkid=841808): Use these instructions if your business uses **Active Directory** that is synchronizing with Azure AD.</span></span> <span data-ttu-id="62881-220">无法通过 Office 365 删除帐户。</span><span class="sxs-lookup"><span data-stu-id="62881-220">You can't do it through Office 365.</span></span>