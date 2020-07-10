---
title: 修正在 Office 365 中传递的恶意电子邮件
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.service: Microsoft Threat Protection
audience: admin
f1.keywords:
- NOCSH
localization_priority: Normal
MS.collection: ''
search.appverid: MET150
description: 威胁补救措施
appliesto:
- Microsoft Threat Protection
ms.openlocfilehash: eb86c0b8e5368a42daa1002de5ac361613037090
ms.sourcegitcommit: 41bc923bb31598cea8f02923792c1cd786e39616
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "45086687"
---
# <a name="remediate-malicious-email-that-was-delivered-in-office-365"></a><span data-ttu-id="a1ffe-103">修正在 Office 365 中传递的恶意电子邮件</span><span class="sxs-lookup"><span data-stu-id="a1ffe-103">Remediate malicious email that was delivered in Office 365</span></span>

<span data-ttu-id="a1ffe-104">修正是指针对威胁采取禁止操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-104">Remediation means taking a proscribed action against a threat.</span></span> <span data-ttu-id="a1ffe-105">发送到组织中的恶意邮件可能会通过系统、ZAP （零小时自动清除）或安全团队（如 "移动到收件箱"、"移动到垃圾邮件"、"移动到已删除邮件" 文件夹、"软删除" 或 "硬删除"）清除。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-105">Malicious mails sent into your organization may be cleaned up either by the system, through ZAP (Zero-hour Auto-Purge), or by the security teams through remediation actions like move to inbox, move to junk, move to deleted items folder, soft delete, or hard delete.</span></span> <span data-ttu-id="a1ffe-106">Office 高级威胁防护（Office ATP） P2/E5 为安全操作团队提供了通过手动搜寻和自动调查来调解电子邮件和协作问题中的威胁的能力。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-106">Office Advanced Threat Protection (Office ATP) P2 / E5 offers security operations teams the ability to mediate threats in emails and collaboration issues through manual hunting and automated investigations.</span></span>

> [!NOTE]
> <span data-ttu-id="a1ffe-107">为了使安全小组能够修正电子邮件，需要向其分配搜索和清除角色。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-107">For security teams to remediate emails, they need to have search and purge role assigned to them.</span></span> <span data-ttu-id="a1ffe-108">角色分配通过安全与合规中心中的权限完成。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-108">Role assignment is done through permissions in security and compliance center.</span></span> <p>

## <a name="what-you-need-to-know-before-you-begin"></a><span data-ttu-id="a1ffe-109">开始之前需要了解的内容</span><span class="sxs-lookup"><span data-stu-id="a1ffe-109">What you need to know before you begin</span></span>

<span data-ttu-id="a1ffe-110">若要执行某些操作（如查看邮件头或下载电子邮件内容），您必须具有一个名为*Preview*的新角色，并将其添加到另一个相应的角色组。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-110">To perform certain actions, such as viewing message headers or downloading email message content, you must have a new role called *Preview* added to another appropriate role group.</span></span> <span data-ttu-id="a1ffe-111">下表阐明了所需的角色和权限。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-111">The following table clarifies required roles and permissions.</span></span>

|<span data-ttu-id="a1ffe-112">活动</span><span class="sxs-lookup"><span data-stu-id="a1ffe-112">Activity</span></span>  |<span data-ttu-id="a1ffe-113">角色组</span><span class="sxs-lookup"><span data-stu-id="a1ffe-113">Role group</span></span> |<span data-ttu-id="a1ffe-114">是否需要预览角色？</span><span class="sxs-lookup"><span data-stu-id="a1ffe-114">Preview role needed?</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="a1ffe-115">使用威胁浏览器（和实时检测）分析威胁</span><span class="sxs-lookup"><span data-stu-id="a1ffe-115">Use Threat Explorer (and real-time detections) to analyze threats</span></span>     |<span data-ttu-id="a1ffe-116">全局管理员</span><span class="sxs-lookup"><span data-stu-id="a1ffe-116">Global Administrator</span></span> <br> <span data-ttu-id="a1ffe-117">安全管理员</span><span class="sxs-lookup"><span data-stu-id="a1ffe-117">Security Administrator</span></span> <br> <span data-ttu-id="a1ffe-118">安全读取者</span><span class="sxs-lookup"><span data-stu-id="a1ffe-118">Security Reader</span></span>     | <span data-ttu-id="a1ffe-119">否</span><span class="sxs-lookup"><span data-stu-id="a1ffe-119">No</span></span>   |
|<span data-ttu-id="a1ffe-120">使用威胁资源管理器（和实时检测）查看电子邮件的邮件头，以及预览和下载隔离的电子邮件</span><span class="sxs-lookup"><span data-stu-id="a1ffe-120">Use Threat Explorer (and real-time detections) to view headers for email messages as well as preview and download quarantined email messages</span></span>    |<span data-ttu-id="a1ffe-121">全局管理员</span><span class="sxs-lookup"><span data-stu-id="a1ffe-121">Global Administrator</span></span> <br> <span data-ttu-id="a1ffe-122">安全管理员</span><span class="sxs-lookup"><span data-stu-id="a1ffe-122">Security Administrator</span></span> <br><span data-ttu-id="a1ffe-123">安全读取者</span><span class="sxs-lookup"><span data-stu-id="a1ffe-123">Security Reader</span></span>   |       <span data-ttu-id="a1ffe-124">否</span><span class="sxs-lookup"><span data-stu-id="a1ffe-124">No</span></span>  |
|<span data-ttu-id="a1ffe-125">使用威胁浏览器查看邮件头并下载传递给邮箱的电子邮件</span><span class="sxs-lookup"><span data-stu-id="a1ffe-125">Use Threat Explorer to view headers and download email messages delivered to mailboxes</span></span>     |<span data-ttu-id="a1ffe-126">全局管理员</span><span class="sxs-lookup"><span data-stu-id="a1ffe-126">Global Administrator</span></span> <br><span data-ttu-id="a1ffe-127">安全管理员</span><span class="sxs-lookup"><span data-stu-id="a1ffe-127">Security Administrator</span></span> <br> <span data-ttu-id="a1ffe-128">安全读取者</span><span class="sxs-lookup"><span data-stu-id="a1ffe-128">Security Reader</span></span> <br> <span data-ttu-id="a1ffe-129">Preview</span><span class="sxs-lookup"><span data-stu-id="a1ffe-129">Preview</span></span>   |   <span data-ttu-id="a1ffe-130">是</span><span class="sxs-lookup"><span data-stu-id="a1ffe-130">Yes</span></span>      |

> [!NOTE]
> <span data-ttu-id="a1ffe-131">*预览*是一个角色，而不是角色组;必须将预览角色添加到 Office 365 的现有角色组中。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-131">*Preview* is a role and not a role group; the Preview role must be added to an existing role group for Office 365.</span></span> <span data-ttu-id="a1ffe-132">全局管理员角色分配了 Microsoft 365 管理中心（ [https://admin.microsoft.com](https://admin.microsoft.com) ），安全管理员和安全读者角色是在安全 & 合规中心（）中分配的 [https://protection.office.com](https://protection.office.com) 。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-132">The Global Administrator role is assigned the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and the Security Administrator and Security Reader roles are assigned in the Security & Compliance Center ([https://protection.office.com](https://protection.office.com)).</span></span> <span data-ttu-id="a1ffe-133">若要了解有关角色和权限的详细信息，请参阅[Security & 合规性中心中的权限。](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center?view=o365-worldwide)</span><span class="sxs-lookup"><span data-stu-id="a1ffe-133">To learn more about roles and permissions, see [Permissions in the Security & Compliance Center.](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center?view=o365-worldwide)</span></span>

> [!NOTE]
> <span data-ttu-id="a1ffe-134">管理员可以对电子邮件执行所需的操作，但若要获得批准的操作，必须通过安全和合规中心 > 权限为其分配 "搜索和清除" 角色。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-134">Admins can take required actions on emails but to get their action approved, they must have the "Search and Purge" role assigned to them via Security and Compliance Center > Permissions.</span></span>

## <a name="manual-and-automated-remediation"></a><span data-ttu-id="a1ffe-135">手动和自动修正</span><span class="sxs-lookup"><span data-stu-id="a1ffe-135">Manual and automated remediation</span></span>

<span data-ttu-id="a1ffe-136">当安全团队使用威胁资源管理器中的搜索和筛选功能手动识别威胁时，将进行**手动搜寻**。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-136">**Manual hunting** takes place when security teams identify threats manually, using the search and filtering capabilities in Threat Explorer.</span></span> <span data-ttu-id="a1ffe-137">在找到需要修正的一组电子邮件之后，可以通过任何电子邮件视图（恶意软件、网络钓鱼或所有电子邮件）触发电子邮件的手动修正。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-137">Manual remediation on emails can be triggered through any email view (Malware, Phish, or All email) after finding a set of emails which need to be remediated.</span></span>

<span data-ttu-id="a1ffe-138">![按日期手动搜寻 Office 365 中的威胁资源管理器。](../../../media/tp-RemediationArticle1.png "威胁资源管理器")</span><span class="sxs-lookup"><span data-stu-id="a1ffe-138">![Manual hunting in Office 365 Threat Explorer by date.](../../../media/tp-RemediationArticle1.png "Threat Explorer")</span></span>

<span data-ttu-id="a1ffe-139">可以通过威胁资源管理器以多种方式完成电子邮件的选择：</span><span class="sxs-lookup"><span data-stu-id="a1ffe-139">The selection of emails can be done in multiple ways through Threat Explorer:</span></span>

1. <span data-ttu-id="a1ffe-140">手动选择电子邮件：这意味着安全操作团队可以在各自的视图中使用筛选器，并从需要修正的威胁资源管理器中选择几封电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-140">Choosing emails by hand: This means security operations teams can use filters in respective views and select a few emails from Threat Explorer that need to be remediated.</span></span> <span data-ttu-id="a1ffe-141">选择电子邮件的上限值为100（100）。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-141">The upper limit to selecting emails is one hundred (100).</span></span> <span data-ttu-id="a1ffe-142">安全操作团队无法手动挑选超过一百封电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-142">Security operations teams cannot pick more than hundred emails, manually.</span></span>

2. <span data-ttu-id="a1ffe-143">查询选择：安全操作团队可以使用顶部的 "全选" 按钮来选择整个查询。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-143">Query selection: Security operations teams can select an entire query by using the top “select all” button.</span></span> <span data-ttu-id="a1ffe-144">同样的查询也会显示在操作中心邮件提交详细信息中。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-144">The same query is shown in action center mail submission details as well.</span></span>

3. <span data-ttu-id="a1ffe-145">具有排除的查询选择：有时，安全操作团队决定通过选择整个查询并从查询中排除几封电子邮件来修正电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-145">Query selection with exclusion: There may be times when security operations teams decide to remediate emails by both selecting an entire query and excluding a few emails from the query, manually.</span></span> <span data-ttu-id="a1ffe-146">若要执行此操作，管理员可以使用 "全选" 复选框，然后向下滚动以手动排除几封电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-146">To do so, an admin can use “Select All” check box and scroll down to exclude a few emails, manually.</span></span> <span data-ttu-id="a1ffe-147">查询可以容纳的最大电子邮件数为1000（1000），最大排除数为100（100），在此示例中。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-147">The maximum number of emails the query can hold is one thousand (1,000), and the maximum number of exclusions is one hundred (100), in this case.</span></span>

<span data-ttu-id="a1ffe-148">从威胁 Explorer 中选择电子邮件后，修复创建可以通过直接操作来开始，也可以通过对电子邮件进行排队以进行操作：</span><span class="sxs-lookup"><span data-stu-id="a1ffe-148">Once emails are selected from Threat Explorer, remediation creation can begin by taking direct action, or by queuing up emails for an action:</span></span>

1. <span data-ttu-id="a1ffe-149">直接批准：当使用适当权限的安全人员选择 "移动到收件箱"、"移动到垃圾邮件"、"移动到已删除的项目"、"软删除"、"硬删除" 等操作时，安全人员将选择具有适当权限的操作，修正过程将开始执行选定的操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-149">Direct approval: When actions like ‘Move to inbox’, ‘Move to junk’, ‘Move to deleted items’, ‘Soft delete’, ‘Hard delete’ are selected by security personnel with appropriate permissions, and next steps are followed till remediation creation, the remediation process begins to execute a selected action.</span></span> <span data-ttu-id="a1ffe-150">临时浮出控件将显示正在进行的修正。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-150">A temporary flyout shows remediation in progress.</span></span>

2. <span data-ttu-id="a1ffe-151">两步批准：不具有适当权限的管理员或需要等待更长时间执行该操作的管理员可以采取 "添加到修正" 操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-151">Two step approval: ‘Add to remediation’ action can be taken by an admin who does not have appropriate permissions or who needs to wait longer to execute the action.</span></span> <span data-ttu-id="a1ffe-152">在这种情况下，不会直接执行修正操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-152">In this case, the remediation action is not executed directly.</span></span> <span data-ttu-id="a1ffe-153">相反，电子邮件将添加到必须经过审批才能执行的修正容器中。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-153">Instead, emails are added to a remediation container that must be approved to execute.</span></span> <span data-ttu-id="a1ffe-154">在对修正进行批准之前，将不会修正该电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-154">Until the remediation is approved, the email will not be remediated.</span></span> <span data-ttu-id="a1ffe-155">在批准了补救措施之后，将对电子邮件执行操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-155">Once the remediation is approved, actions will be taken on the email.</span></span>

<span data-ttu-id="a1ffe-156">**自动调查和响应（空中）** 操作由警报资源管理器中的警报或安全操作团队触发。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-156">**Automated investigation and response (AIR)** actions are triggered by alerts or by security operations teams from inside Threat Explorer.</span></span> <span data-ttu-id="a1ffe-157">它们可能包括安全操作团队必须批准的一些建议中介。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-157">They may include some recommended mediation that must be approved by security operations teams.</span></span> <span data-ttu-id="a1ffe-158">自动调查中的 "操作" 选项卡上包含这些修正操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-158">These remediation actions are included on the Action tab within the automated investigation.</span></span>  

:::image type="content" source="../../../media/tp-RemediationArticle3.png" alt-text="包含恶意软件的邮件是 Zapped 页，显示了 Zap 执行的时间。":::

<span data-ttu-id="a1ffe-160">通过威胁浏览器创建的所有中介（直接批准或两步审批）以及来自自动调查的批准的操作将显示在操作中心中，可通过 "*审阅* >  **操作中心**" 下的左侧导航进行访问。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-160">All mediation (either direct approval or two-step approval) created through Threat Explorer, and approved actions coming from automated investigations, show up in the Action Center, which can be accessed via the left navigation under *Review*> **Action Center**.</span></span>

:::image type="content" source="../../../media/tp-RemediationArticle4.png" alt-text="包含受日期和严重性的威胁列表的操作中心。":::

<span data-ttu-id="a1ffe-162">操作中心显示过去30天内的所有修正操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-162">Action Center shows all remediation actions for the past 30 days.</span></span> <span data-ttu-id="a1ffe-163">通过资源管理器执行的操作显示在创建修正时由安全操作团队提供的相同名称。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-163">Actions taken through Explorer show up with the same name provided by the security operations teams when the remediation was created.</span></span> <span data-ttu-id="a1ffe-164">通过自动调查进行的操作是通过与触发调查的相关警报（例如 "Zap 电子邮件群集 ..."）开始的标题共同展示的。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-164">Actions taken through automated investigations are surfaced with titles that begin with the related alert that triggered the investigation – for e.g. “Zap email cluster…”.</span></span>

<span data-ttu-id="a1ffe-165">可以打开每个补救项以查看有关它的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-165">Each remediation item can be opened to view details about it.</span></span> <span data-ttu-id="a1ffe-166">在打开修正项目时，将显示基本修正详细信息、修正名称、创建日期、说明、威胁严重性和状态。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-166">When a remediation item is opened, it shows basic remediation details, the remediation name, creation date, description, threat severity, and status.</span></span> <span data-ttu-id="a1ffe-167">它还显示两个选项卡。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-167">It also shows two tabs.</span></span> 

1. <span data-ttu-id="a1ffe-168">**"邮件提交" 选项卡**：这些是通过威胁浏览器提交的电子邮件数或要修正的自动调查数。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-168">**Mail submission tab**: These are the number of emails submitted through Threat Explorer or automated investigations to be remediated.</span></span> <span data-ttu-id="a1ffe-169">这些电子邮件可以是：</span><span class="sxs-lookup"><span data-stu-id="a1ffe-169">These emails can be:</span></span>

<span data-ttu-id="a1ffe-170">可操作：可对以下云邮箱位置中的电子邮件进行**操作**和移动，即 remediable 类别中的任何电子邮件都可以从一个位置移动到另一个位置：</span><span class="sxs-lookup"><span data-stu-id="a1ffe-170">**Actionable**: Emails in the following cloud mailbox locations can be acted upon and moved i.e. any email within the remediable category can be moved from one location to another:</span></span>
  - <span data-ttu-id="a1ffe-171">Inbox</span><span class="sxs-lookup"><span data-stu-id="a1ffe-171">Inbox</span></span> 
  - <span data-ttu-id="a1ffe-172">可疑</span><span class="sxs-lookup"><span data-stu-id="a1ffe-172">Junk</span></span>  
  - <span data-ttu-id="a1ffe-173">已删除文件夹</span><span class="sxs-lookup"><span data-stu-id="a1ffe-173">Deleted folder</span></span>
  - <span data-ttu-id="a1ffe-174">软删除文件夹</span><span class="sxs-lookup"><span data-stu-id="a1ffe-174">Soft deleted folder</span></span>

>[!NOTE]
> <span data-ttu-id="a1ffe-175">目前，只有拥有邮箱访问权限的最终用户才能恢复软删除文件夹中的项目。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-175">Currently, only an end user with access to the mailbox can recover items from a soft delete folder.</span></span>

<span data-ttu-id="a1ffe-176">**不可行**：以下位置的电子邮件不能作为电子邮件操作的一部分进行操作或移动，例如，非 remediable 类别中的电子邮件不能移动到非 remediable 类别中，也不能移动到 remediable 中。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-176">**Not actionable**: Emails in the following locations cannot be acted upon or moved as a part of the email actions i.e. emails in non-remediable category cannot be moved either in the non-remediable category, nor in remediable.</span></span> <span data-ttu-id="a1ffe-177">非 remediable 位置为：</span><span class="sxs-lookup"><span data-stu-id="a1ffe-177">Non-remediable locations are:</span></span>

  - <span data-ttu-id="a1ffe-178">隔离</span><span class="sxs-lookup"><span data-stu-id="a1ffe-178">Quarantine</span></span>
  - <span data-ttu-id="a1ffe-179">硬删除文件夹</span><span class="sxs-lookup"><span data-stu-id="a1ffe-179">Hard deleted folder</span></span>
  - <span data-ttu-id="a1ffe-180">本地/external</span><span class="sxs-lookup"><span data-stu-id="a1ffe-180">On-prem / external</span></span>
  - <span data-ttu-id="a1ffe-181">失败/丢弃</span><span class="sxs-lookup"><span data-stu-id="a1ffe-181">Failed / dropped</span></span>
  
<span data-ttu-id="a1ffe-182">提交的可疑邮件被分类为 remediable 或非 remediable。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-182">Suspicious messages submitted are categorized as either remediable or non-remediable.</span></span> <span data-ttu-id="a1ffe-183">在大多数情况下，remediable 和非 remediable 邮件应添加到提交的邮件总数。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-183">In most cases, remediable and non-remediable messages should add up to the total messages submitted.</span></span> <span data-ttu-id="a1ffe-184">但是，在极少数情况下，提交的邮件可能不会添加到 remediable 和非 remediable 项目的总和，并且可以高于或低于提交的邮件总数。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-184">However, there can be rare cases where messages submitted may not add up to the sum of remediable and non-remediable items, and could be either higher or lower than the total submitted message count.</span></span> <span data-ttu-id="a1ffe-185">出现这种情况的原因可能是系统延迟、超时或过期邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-185">This can happen due to system delays, time-outs, or expired messages.</span></span> <span data-ttu-id="a1ffe-186">邮件将根据您的组织的浏览器保留期而过期。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-186">Messages expire based on Explorer’s retention period for your organization.</span></span>

<span data-ttu-id="a1ffe-187">除非您在组织的浏览器保留期之后修正旧邮件，否则，如果您发现数字不一致，则建议重新尝试修正项目。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-187">Unless you are remediating old messages after your organization’s Explorer retention period, if you see inconsistencies in numbers, it is advisable to re-try remediating items.</span></span> <span data-ttu-id="a1ffe-188">对于系统延迟，修复更新通常在几小时内进行刷新。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-188">For system delays, remediation updates are typically refreshed within a few hours.</span></span>

<span data-ttu-id="a1ffe-189">如果组织在浏览器中的电子邮件保留期为30天，并且您正在修正29-30 天后的电子邮件，则邮件提交次数可能不会因为电子邮件可能已开始移出保留期而无法总添加。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-189">If your organization’s retention period for email in Explorer is 30 days, and you are remediating emails going 29-30 days back, mail submission counts may not always add up as the emails might have started moving out of retention period already.</span></span>

<span data-ttu-id="a1ffe-190">如果中介在一段时间内处于 "正在进行" 状态，则可能是由于系统延迟。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-190">If mediation is stuck in an “In progress” state for a while, it’s likely due to system delays.</span></span> <span data-ttu-id="a1ffe-191">修正可能需要几个小时的时间。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-191">It could take up to a few hours to remediate.</span></span> <span data-ttu-id="a1ffe-192">由于系统延迟，在邮件提交计数中可能会发现，由于某些电子邮件不是查询的一部分，因此可能会出现在邮件提交计数方面的变化。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-192">There can be a variation observed in mail submission counts as some of the emails were not a part of the query while starting remediation, due to system delays.</span></span> <span data-ttu-id="a1ffe-193">在这种情况下，最好重新尝试修正。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-193">It is a good idea to re-try remediating in such cases.</span></span>  

<span data-ttu-id="a1ffe-194">为获得最佳结果，应在50k 或更低的电子邮件的较小批次中完成补救措施。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-194">For best results, remediation should be done in smaller batches of around 50k or lesser emails.</span></span>  

<span data-ttu-id="a1ffe-195">在邮件提交过程中的所有电子邮件中，remediable 电子邮件是在修正期间将对其进行处理的唯一电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-195">Of all emails in mail submission, remediable emails are the only ones that will be acted upon during remediation.</span></span> <span data-ttu-id="a1ffe-196">Office 365 电子邮件系统无法修正非 remediable 电子邮件，因为它们不存储在云邮箱中。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-196">Non-remediable emails cannot be remediated by the Office 365 email system, as they are not stored in cloud mailboxes.</span></span>

<span data-ttu-id="a1ffe-197">对于隔离中找到的电子邮件，管理员可以转到隔离，以对这些电子邮件采取操作（如果需要），但如果不手动清除，电子邮件将过期。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-197">For emails found in quarantine, admins can go to quarantine to take actions on those emails if required, but the emails will expire out of quarantine if not manually purged.</span></span> <span data-ttu-id="a1ffe-198">最终用户无法访问由于恶意内容而隔离的电子邮件，因此安全人员无需采取任何特定操作来消除隔离威胁。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-198">Emails quarantined due to malicious content are not accessible by end-users, so security personnel need not take any specific action to get rid of the threat in quarantine.</span></span> <span data-ttu-id="a1ffe-199">如果电子邮件是本地或外部电子邮件，则可以联系最终用户来解决可疑电子邮件，或使用单独的电子邮件服务器/安全工具进行删除。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-199">If the emails are on-prem or external, the end-user can be contacted to address the suspicious email or use separate email server/security tools for removal.</span></span> <span data-ttu-id="a1ffe-200">可以通过在威胁资源管理器中应用传递位置 = 本地/external filter 来识别这些电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-200">These emails can be identified by applying delivery location = on-prem / external filter in Threat Explorer.</span></span> <span data-ttu-id="a1ffe-201">对于失败或丢失的电子邮件，或者最终用户无法访问的电子邮件，由于无法访问邮箱，因此不应使用电子邮件进行缓解。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-201">For failed or dropped email, or email not accessible by the end-user, there shouldn’t be email to mitigate, since they don’t reach the mailbox.</span></span>

<span data-ttu-id="a1ffe-202">这是提交在操作中心中显示的方式。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-202">This is how a submission shows up in Action Center.</span></span> <span data-ttu-id="a1ffe-203">修正可以包含多个提交。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-203">A remediation can contain multiple submissions.</span></span> <span data-ttu-id="a1ffe-204">如果通过一次自动调查批准了多个操作，则每个电子邮件或电子邮件群集操作将显示与不同提交相同的补救措施。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-204">If multiple actions get approved through one automated investigation, each email or email cluster action shows up in the same remediation as a different submission.</span></span>

:::image type="content" source="../../../media/tp-RemediationArticle6.png" alt-text="Zap 电子邮件群集飞出面板。":::

<span data-ttu-id="a1ffe-206">单击邮件提交项将显示该修正的详细信息，如查询（在通过选择查询的自动调查或威胁资源管理器触发修正）、开始时间和结束时间（修正）。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-206">Clicking on a mail submission item will show details of that remediation such as the query (when remediation is triggered through automated investigations or Threat Explorer through selecting a query), start time, and end time, of remediation.</span></span> <span data-ttu-id="a1ffe-207">它还显示提交以进行修正的邮件的列表。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-207">It also displays a list of messages that were submitted for remediation.</span></span> <span data-ttu-id="a1ffe-208">当邮件移出浏览器保留期时，邮件将从该列表中消失。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-208">As messages move out of the Explorer retention period, the messages will disappear from this list.</span></span> <span data-ttu-id="a1ffe-209">此列表还显示了列表中 remediable 的单个邮件。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-209">This list also shows individual messages from the list which are remediable.</span></span>

2. <span data-ttu-id="a1ffe-210">"**操作日志" 选项卡**：此选项卡显示修正的邮件的结果，包括 "批准日期"、"审批者" （"批准操作的管理员"）、"操作"、"状态" 和 "计数"。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-210">**Action logs tab**: This tab shows the result of messages remediated, including details like approved date, approver (admin who approved the action), action, status, and counts.</span></span>  

<span data-ttu-id="a1ffe-211">状态是修正的总体状态。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-211">Status is the overall status of the remediation.</span></span> <span data-ttu-id="a1ffe-212">状态可以是：</span><span class="sxs-lookup"><span data-stu-id="a1ffe-212">Status can be:</span></span>

  - <span data-ttu-id="a1ffe-213">**已启动**：触发修正时。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-213">**Started**: When a remediation gets triggered.</span></span>
  - <span data-ttu-id="a1ffe-214">已**排队**：在修补程序排队等待电子邮件缓解时。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-214">**Queued**: When the remediation is queued up for mitigation of emails.</span></span>
  - <span data-ttu-id="a1ffe-215">**正在进行**：正在进行缓解。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-215">**In progress**: When the mitigation is in progress.</span></span>
  - <span data-ttu-id="a1ffe-216">**已完成**：当所有 remediable 电子邮件的缓解成功完成或发生故障时。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-216">**Completed**: When the mitigation on all remediable emails is done either successfully or with some failures.</span></span> 
  - <span data-ttu-id="a1ffe-217">**失败**：当没有 remediations 成功时。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-217">**Failed**: When no remediations are successful.</span></span>

<span data-ttu-id="a1ffe-218">由于只能对 remediable 电子邮件进行操作，因此会将每封电子邮件的清除视为成功或失败。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-218">As only remediable emails can be acted upon, each email’s cleanup is looked at as successful or failed.</span></span> <span data-ttu-id="a1ffe-219">从 total remediable 电子邮件中，我们公开了成功和失败的缓解。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-219">From the total remediable emails, we expose the successful and failed mitigations.</span></span>

  - <span data-ttu-id="a1ffe-220">**成功**：当 remediable 电子邮件上的所需操作完成并与管理员的意图相匹配时。例如：管理员希望删除邮箱中的电子邮件，以便执行软删除电子邮件的操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-220">**Success**: When the desired action on remediable emails is accomplished and matches the intention of admin. For example: An admin wants to remove emails from mailboxes, so they take the action of soft deleting emails.</span></span> <span data-ttu-id="a1ffe-221">如果在执行操作后原始文件夹中找不到 remediable 电子邮件，则状态将显示为 "成功"。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-221">If a remediable email is not found in the original folder after the action is taken, the Status will show as successful.</span></span>  

  - <span data-ttu-id="a1ffe-222">**失败**：当 remediable 电子邮件上的所需操作失败时。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-222">**Failure**: When the desired action on remediable emails fails.</span></span> <span data-ttu-id="a1ffe-223">例如：管理员想要删除邮箱中的电子邮件，以便执行软删除电子邮件的操作。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-223">For example: An admin wants to remove emails from mailboxes, so he takes the action of soft deleting emails.</span></span> <span data-ttu-id="a1ffe-224">如果仍在邮箱中找到 remediable 电子邮件，则状态将显示为 "失败"。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-224">If a remediable email is still found in the mailbox, Status will show as failed.</span></span>

<span data-ttu-id="a1ffe-225">单击 "操作日志" 中的任何项将显示修正的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-225">Clicking on any item in action log, displays details of remediation.</span></span> <span data-ttu-id="a1ffe-226">对于成功的项目，如果详细信息说、成功或未在邮箱中找到，则表示已从邮箱中删除了项目。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-226">For successful items, if the details say, successful, or not found in mailbox, it means that item was already removed from the mailbox.</span></span> <span data-ttu-id="a1ffe-227">有时，由于修正过程中出现系统错误而发生故障，在这些情况下，最好重新尝试修正。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-227">Sometimes there are failures that happen due to a systemic error during remediation, and in those cases, it is a good idea to re-try remediation.</span></span>  

<span data-ttu-id="a1ffe-228">修正是缓解威胁和解决可疑电子邮件的强大工具。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-228">Remediation is a powerful tool to mitigate threats, and address suspicious, emails.</span></span> <span data-ttu-id="a1ffe-229">它有助于确保组织的安全和安全。</span><span class="sxs-lookup"><span data-stu-id="a1ffe-229">It helps keep an organization safe and secure.</span></span>  

## <a name="more-info"></a><span data-ttu-id="a1ffe-230">详细信息</span><span class="sxs-lookup"><span data-stu-id="a1ffe-230">More info</span></span>

<span data-ttu-id="a1ffe-231">参考<https://docs.microsoft.com/microsoft-365/security/office-365-security/investigate-malicious-email-that-was-delivered?view=o365-worldwide></span><span class="sxs-lookup"><span data-stu-id="a1ffe-231">See <https://docs.microsoft.com/microsoft-365/security/office-365-security/investigate-malicious-email-that-was-delivered?view=o365-worldwide></span></span>