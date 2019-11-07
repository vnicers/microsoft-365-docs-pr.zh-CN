---
title: 用于高度管控数据的 Teams
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 10/31/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: 创建安全团队来存储最有价值的敏感文件。
ms.openlocfilehash: c4a7c724b6fbb4515deba1a207eea31902f822e0
ms.sourcegitcommit: 6dfa646b9de30336dedfd0cac7320c57ad74ae11
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "37929216"
---
# <a name="teams-for-highly-regulated-data"></a><span data-ttu-id="1c787-103">用于高度管控数据的 Teams</span><span class="sxs-lookup"><span data-stu-id="1c787-103">Teams for highly regulated data</span></span>

<span data-ttu-id="1c787-104">本文为你提供在 Microsoft Teams 中配置私人团队的建议和步骤，它只允许 Office 365 团队组的成员和所有者访问 Teams 功能 — 例如聊天、会议和文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-104">This article provides you with recommendations and steps to configure a private team in Microsoft Teams that locks down access to Teams features—such as chats, meetings, and files—to only members and owners of the Office 365 group for the team.</span></span> 

<span data-ttu-id="1c787-105">除了基于 Office 365 组的专用访问之外，本文还介绍了如何配置基础专用 SharePoint 团队网站，你可以从团队频道的“**文件**”部分进行访问，以获得存储高度管控数据所需的其他安全性。</span><span class="sxs-lookup"><span data-stu-id="1c787-105">Beyond the private access based on the Office 365 group, this article describes how to configure the underlying private SharePoint team site, which you can access from the **Files** section of a team channel, for the additional security needed to store highly regulated data.</span></span> <span data-ttu-id="1c787-106">在此 SharePoint 团队网站上，可存储和协作处理文件、页面、共享日历、任务、笔记本和列表。</span><span class="sxs-lookup"><span data-stu-id="1c787-106">On this SharePoint team site, you can store and collaborate on files, pages, a shared calendar, tasks, a notebook, and lists.</span></span>

>[!Note]
> <span data-ttu-id="1c787-107">[此处](teams-sharepoint-online-sites-highly-regulated-data.md)是使用 SharePoint 的类似方案。</span><span class="sxs-lookup"><span data-stu-id="1c787-107">A similar scenario using Microsoft Teams is [here](teams-sharepoint-online-sites-highly-regulated-data.md).</span></span>
>

<span data-ttu-id="1c787-108">针对高度管控数据的团队的配置元素如下：</span><span class="sxs-lookup"><span data-stu-id="1c787-108">The elements of configuration for a team for highly regulated data are:</span></span>

- <span data-ttu-id="1c787-109">具有相应的 Office 365 组的私人团队，该组具有所有者和成员用户帐户。</span><span class="sxs-lookup"><span data-stu-id="1c787-109">A private team with a corresponding Office 365 group that has owner and member user accounts.</span></span>
- <span data-ttu-id="1c787-110">基础 SharePoint 团队网站上的其他安全性：</span><span class="sxs-lookup"><span data-stu-id="1c787-110">Additional security on the underlying SharePoint site for the team that:</span></span>
  - <span data-ttu-id="1c787-111">阻止网站成员向其他人授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="1c787-111">Prevents members of the site from granting access to others.</span></span>
  - <span data-ttu-id="1c787-112">阻止非网站成员请求访问该网站。</span><span class="sxs-lookup"><span data-stu-id="1c787-112">Prevents non-members of the site from requesting access to the site.</span></span>
- <span data-ttu-id="1c787-113">基础 SharePoint 网站的 Office 365 保留标签，作为定义保留策略的默认方法，该标签将自动应用于该网站上的新文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-113">An Office 365 retention label for the underlying SharePoint site that is automatically applied to new files on the site as a default way to define retention policies.</span></span>
- <span data-ttu-id="1c787-114">数据丢失防护 (DLP) 策略，该策略使用保留标签并阻止用户在组织外部共享或发送文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-114">A Data Loss Prevention (DLP) policy that uses the retention label and blocks users from sharing or sending files outside the organization.</span></span>
- <span data-ttu-id="1c787-115">Office 365 敏感度标签或高度管控标签的子标签，它已启用加密并且为 Office 365 团队组提供了共同创作权限。</span><span class="sxs-lookup"><span data-stu-id="1c787-115">An Office 365 sensitivity label or a sublabel of a highly regulated label that has encryption enabled and Co-Author permissions for the Office 365 group of the team.</span></span> <span data-ttu-id="1c787-116">通过 Word、Excel 和 PowerPoint 中的“敏感度”菜单栏选项，用户可以为团队的“**文件**”部分中存储的文件应用标签或子标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-116">Users apply the label or sublabel to files stored in **Files** section of the team from the Sensitivity menu bar option in Word, Excel, and PowerPoint.</span></span>

<span data-ttu-id="1c787-117">下面是使用敏感度标签生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1c787-117">Here is the resulting configuration with a sensitivity label.</span></span>

![安全团队方案配置](./media/secure-teams-highly-regulated-data-scenario/secure-team-final.png)

<a name="poster"></a> <span data-ttu-id="1c787-119">有关这种情况的 1 页摘要，请参阅[针对高度管控数据海报的 Teams](./media/secure-teams-highly-regulated-data-scenario/TeamsHighlyRegulatedData.pdf)。</span><span class="sxs-lookup"><span data-stu-id="1c787-119">For a 1-page summary of this scenario, see the [Teams for highly regulated data poster](./media/secure-teams-highly-regulated-data-scenario/TeamsHighlyRegulatedData.pdf).</span></span>

<span data-ttu-id="1c787-120">[![针对高度管控数据海报的 Teams](././media/secure-teams-highly-regulated-data-scenario/teams-highly-regulated-data-poster.png)](./media/secure-teams-highly-regulated-data-scenario/TeamsHighlyRegulatedData.pdf)</span><span class="sxs-lookup"><span data-stu-id="1c787-120">[![Teams for highly regulated data](././media/secure-teams-highly-regulated-data-scenario/teams-highly-regulated-data-poster.png)](./media/secure-teams-highly-regulated-data-scenario/TeamsHighlyRegulatedData.pdf)</span></span>

<span data-ttu-id="1c787-121">你还可以下载此海报的 [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/secure-teams-highly-regulated-data-scenario/TeamsHighlyRegulatedData.pdf) 版本并按 letter、legal 或 tabloid (11 x 17) 格式打印。</span><span class="sxs-lookup"><span data-stu-id="1c787-121">You can also download this poster in [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/secure-teams-highly-regulated-data-scenario/TeamsHighlyRegulatedData.pdf) or PowerPoint formats and print it in letter, legal, or tabloid (11 x 17) formats.</span></span>

## <a name="phase-1-configure-a-team-for-highly-regulated-data"></a><span data-ttu-id="1c787-122">阶段 1：为高度管控数据配置团队</span><span class="sxs-lookup"><span data-stu-id="1c787-122">Phase 1: Configure a team for highly regulated data</span></span>

<span data-ttu-id="1c787-123">端到端配置包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="1c787-123">The end-to-end configuration consists of these steps:</span></span>

1. <span data-ttu-id="1c787-124">配置标识和设备访问。</span><span class="sxs-lookup"><span data-stu-id="1c787-124">Configure identity and device access.</span></span>
2. <span data-ttu-id="1c787-125">创建私人团队。</span><span class="sxs-lookup"><span data-stu-id="1c787-125">Create a private team.</span></span>
3. <span data-ttu-id="1c787-126">配置基础 SharePoint 网站的其他安全性。</span><span class="sxs-lookup"><span data-stu-id="1c787-126">Configure the underlying SharePoint site for additional security.</span></span>
4. <span data-ttu-id="1c787-127">创建保留标签和 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="1c787-127">Create a retention label and DLP policy.</span></span>
5. <span data-ttu-id="1c787-128">创建标签或高度管控标签的子标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-128">Create the label or sublabel of the highly regulated label.</span></span>

### <a name="step-1-configure-identity-and-device-access"></a><span data-ttu-id="1c787-129">步骤 1：配置标识和设备访问</span><span class="sxs-lookup"><span data-stu-id="1c787-129">Step 1: Configure identity and device access</span></span>

<span data-ttu-id="1c787-130">若要保护对团队及其基础 SharePoint 网站的访问，请确保已配置[标识和设备访问策略](https://docs.microsoft.com/microsoft-365/enterprise/identity-access-policies)以及建议的 [SharePoint Online 访问策略](https://docs.microsoft.com/microsoft-365/enterprise/sharepoint-file-access-policies)。</span><span class="sxs-lookup"><span data-stu-id="1c787-130">To protect access to the team and its underlying SharePoint site, ensure that you have configured [identity and device access policies](https://docs.microsoft.com/microsoft-365/enterprise/identity-access-policies) and the recommended [SharePoint Online access policies](https://docs.microsoft.com/microsoft-365/enterprise/sharepoint-file-access-policies).</span></span>

### <a name="step-2-create-a-private-team"></a><span data-ttu-id="1c787-131">步骤 2：创建私人团队</span><span class="sxs-lookup"><span data-stu-id="1c787-131">Step 2: Create a private team</span></span>

<span data-ttu-id="1c787-132">请按照[这些说明](https://support.office.com/article/create-a-team-from-scratch-174adf5f-846b-4780-b765-de1a0a737e2b)创建私人团队。</span><span class="sxs-lookup"><span data-stu-id="1c787-132">Use [these instructions](https://support.office.com/article/create-a-team-from-scratch-174adf5f-846b-4780-b765-de1a0a737e2b) to create a private team.</span></span>

<span data-ttu-id="1c787-133">创建私人团队时，以下是默认权限：</span><span class="sxs-lookup"><span data-stu-id="1c787-133">When you create a private team, here are the default permissions:</span></span>

- <span data-ttu-id="1c787-134">Office 365 团队组（团队组）具有组所有者和组成员</span><span class="sxs-lookup"><span data-stu-id="1c787-134">The Office 365 group for the team (the Team Group) has group owners and group members</span></span>
- <span data-ttu-id="1c787-135">对于基础 SharePoint 团队网站（团队网站）：</span><span class="sxs-lookup"><span data-stu-id="1c787-135">For the underlying SharePoint site for the team (the Team Site):</span></span>
  - <span data-ttu-id="1c787-136">已为团队组所有者配置网站集管理员</span><span class="sxs-lookup"><span data-stu-id="1c787-136">The Site Collection Administrators is configured for the Team Group owners</span></span>
  - <span data-ttu-id="1c787-137">对于团队网站：</span><span class="sxs-lookup"><span data-stu-id="1c787-137">For the Team Site:</span></span> 
    - <span data-ttu-id="1c787-138">具有“完全控制”权限级别的团队网站所有者 SharePoint 组已设置为团队组所有者</span><span class="sxs-lookup"><span data-stu-id="1c787-138">The Team Site Owners SharePoint group—with the Full Control permission level—is set to the Team Group owners</span></span>
    - <span data-ttu-id="1c787-139">具有“编辑”权限级别的团队网站成员 SharePoint 组已设置为团队组成员</span><span class="sxs-lookup"><span data-stu-id="1c787-139">The Team Site Members SharePoint group—with the Edit permission level—is set to the Team Group members</span></span>
    - <span data-ttu-id="1c787-140">具有“读取”权限级别的团队网站访问者 SharePoint 组没有任何组或用户帐户</span><span class="sxs-lookup"><span data-stu-id="1c787-140">The Team Site Visitors SharePoint group—with the Read permission level—has no groups or user accounts</span></span>

<span data-ttu-id="1c787-141">下面是团队网站的默认权限。</span><span class="sxs-lookup"><span data-stu-id="1c787-141">Here are the default permissions for the Team Site.</span></span>

![团队网站的默认权限](./media/secure-teams-highly-regulated-data-scenario/secure-team-default-site-permissions.png)
 
>[!Note]
><span data-ttu-id="1c787-143">如果查看“编辑”权限级别的\<团队名称 > 所有者 SharePoint 组，则不会显示\<团队名称 > 所有者。</span><span class="sxs-lookup"><span data-stu-id="1c787-143">If you view the \<team name> Owners SharePoint group for the Edit permission level, it does not display \<team name> Owners.</span></span>
>

<span data-ttu-id="1c787-144">生成的权限允许：</span><span class="sxs-lookup"><span data-stu-id="1c787-144">The resulting permissions allow:</span></span>

- <span data-ttu-id="1c787-145">团队组所有者管理网站，并对网站内容拥有完全控制权。</span><span class="sxs-lookup"><span data-stu-id="1c787-145">Team Group owners to administer the site and have full control over the site contents.</span></span>
- <span data-ttu-id="1c787-146">团队组成员在网站上创建和编辑文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-146">Team Group members to create and edit files on the site.</span></span> 

<span data-ttu-id="1c787-147">权限维护与团队成员和所有者维护相同。</span><span class="sxs-lookup"><span data-stu-id="1c787-147">Permissions maintenance is the same as team member and owner maintenance.</span></span>

<span data-ttu-id="1c787-148">下面是到目前为止生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1c787-148">Here’s the resulting configuration so far.</span></span>

![安全团队方案配置的步骤 2](./media/secure-teams-highly-regulated-data-scenario/secure-team-step2.png)
 
### <a name="step-3-configure-the-underlying-sharepoint-site-for-additional-security"></a><span data-ttu-id="1c787-150">步骤 3：配置基础 SharePoint 网站的其他安全性</span><span class="sxs-lookup"><span data-stu-id="1c787-150">Step 3: Configure the underlying SharePoint site for additional security</span></span>

<span data-ttu-id="1c787-151">对于团队网站，请配置以下权限设置。</span><span class="sxs-lookup"><span data-stu-id="1c787-151">From the Team Site, configure these permission settings.</span></span>

1. <span data-ttu-id="1c787-152">在工具栏中，依次单击设置图标和“**网站权限**”。</span><span class="sxs-lookup"><span data-stu-id="1c787-152">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="1c787-153">在“**网站权限**”窗格的“**共享设置**”下方，单击“**更改共享设置**”。</span><span class="sxs-lookup"><span data-stu-id="1c787-153">In the **Site permissions** pane, under **Sharing Settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="1c787-154">在“**共享权限**”下方，选择“**仅网站所有者可以共享文件、文件夹和网站**”。</span><span class="sxs-lookup"><span data-stu-id="1c787-154">Under **Sharing permissions**, choose **Only site owners can share files, folders, and the site**.</span></span>
4. <span data-ttu-id="1c787-155">关闭“**允许访问请求**”，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="1c787-155">Turn off **Allow access requests**, and then click **Save**.</span></span>

<span data-ttu-id="1c787-156">使用这些设置，可以禁止团队组成员与其他成员共享团队网站以及非成员请求访问团队网站。</span><span class="sxs-lookup"><span data-stu-id="1c787-156">With these settings, the ability for Team Group members to share the Team Site with other members or for non-members to request access to the Team Site is disabled.</span></span>

<span data-ttu-id="1c787-157">下面是到目前为止生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1c787-157">Here’s the resulting configuration so far.</span></span>

![安全团队方案配置的步骤 3](./media/secure-teams-highly-regulated-data-scenario/secure-team-step3.png)

 
### <a name="step-4-create-a-retention-label-and-dlp-policy"></a><span data-ttu-id="1c787-159">步骤 4：创建保留标签和 DLP 策略</span><span class="sxs-lookup"><span data-stu-id="1c787-159">Step 4: Create a retention label and DLP policy</span></span>

<span data-ttu-id="1c787-160">按照[这些说明](https://docs.microsoft.com/microsoft-365/compliance/protect-sharepoint-online-files-with-office-365-labels-and-dlp)执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1c787-160">Use [these instructions](https://docs.microsoft.com/microsoft-365/compliance/protect-sharepoint-online-files-with-office-365-labels-and-dlp) to:</span></span>

1. <span data-ttu-id="1c787-161">创建并发布高度管控数据的保留标签（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="1c787-161">Create and publish a retention label for highly regulated data (if needed).</span></span>
2. <span data-ttu-id="1c787-162">为团队网站配置步骤 1 中创建的保留标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-162">Configure the Team Site for the retention label created in step 1.</span></span>
3. <span data-ttu-id="1c787-163">为高度管控数据创建 DLP 策略以使用步骤 2 中创建的保留标签并阻止用户将文件发送到组织外部。</span><span class="sxs-lookup"><span data-stu-id="1c787-163">Create a DLP policy for highly regulated data that uses the retention label created in step 2 and blocks users from sending files outside the organization.</span></span> <span data-ttu-id="1c787-164">你还可以基于 [DLP 策略模板](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies#dlp-policy-templates)，根据其他要求（例如健康和金融行业的法规要求）来配置策略。</span><span class="sxs-lookup"><span data-stu-id="1c787-164">You can also configure the policy for additional requirements, such as those for health and financial industry regulations, based on [DLP policy templates](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies#dlp-policy-templates).</span></span>

<span data-ttu-id="1c787-165">下面是到目前为止生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1c787-165">Here’s the resulting configuration so far.</span></span>

![安全团队方案配置的步骤 4](./media/secure-teams-highly-regulated-data-scenario/secure-team-step4.png)
 
### <a name="step-5-create-the-label-or-a-sublabel-of-the-highly-regulated-label"></a><span data-ttu-id="1c787-167">步骤 5：创建标签或高度管控标签的子标签</span><span class="sxs-lookup"><span data-stu-id="1c787-167">Step 5: Create the label or a sublabel of the highly regulated label</span></span>

<span data-ttu-id="1c787-168">与可由任何人应用于任何文件的高度管控数据敏感度标签不同，安全团队需要其自己的标签或子标签，以使分配的文件：</span><span class="sxs-lookup"><span data-stu-id="1c787-168">Unlike a sensitivity label for highly regulated data that anyone can apply to any file, a secure team needs its own label or sublabel so that assigned files:</span></span>

- <span data-ttu-id="1c787-169">启用加密，并且加密信息将与文件一起移动。</span><span class="sxs-lookup"><span data-stu-id="1c787-169">Are encrypted and the encryption travels with the file.</span></span>
- <span data-ttu-id="1c787-170">包含自定义权限，以便只有团队组的成员能打开文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-170">Contain custom permissions so that only members of the Team Group can open it.</span></span>

<span data-ttu-id="1c787-171">若要以这种方式为团队网站中存储的文件实现更高的安全级别，必须配置一个新的敏感度标签，以用作其自身标签，或作为高度管控文件的常规标签的子标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-171">To accomplish this additional level of security for files stored in the Team Site, you must configure a new sensitivity label that is either its own label a sublabel of the general label for highly regulated files.</span></span> <span data-ttu-id="1c787-172">只有团队组成员才能在其标签列表中看到它。</span><span class="sxs-lookup"><span data-stu-id="1c787-172">Only Team Group members will see it in their list of labels.</span></span>

<span data-ttu-id="1c787-173">如果需要将少量标签应用于全局和各个私人团队，请使用敏感度标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-173">Use a sensitivity label when you need a small number of labels for both global use and individual private teams.</span></span> <span data-ttu-id="1c787-174">如果你拥有大量标签，或者希望在高度管控标签下整理私人团队的标签，请使用敏感度子标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-174">Use a sensitivity sublabel when you have a large number of labels or want to organize labels for private teams under the highly regulated label.</span></span>

<span data-ttu-id="1c787-175">[按照这些说明](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)，使用以下设置配置单独的标签或子标签：</span><span class="sxs-lookup"><span data-stu-id="1c787-175">[Use these instructions](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) to configure a separate label or a sublabel with the following settings:</span></span>

- <span data-ttu-id="1c787-176">标签名称包含团队名称</span><span class="sxs-lookup"><span data-stu-id="1c787-176">The name of the label contains the name of the team</span></span>
- <span data-ttu-id="1c787-177">启用加密</span><span class="sxs-lookup"><span data-stu-id="1c787-177">Encryption is enabled</span></span>
- <span data-ttu-id="1c787-178">团队组具有共同创作权限</span><span class="sxs-lookup"><span data-stu-id="1c787-178">The Team Group has Co-Author permissions</span></span>

<span data-ttu-id="1c787-179">下面是使用新标签生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1c787-179">Here’s the resulting configuration with the new label.</span></span>

![安全团队方案配置的步骤 5](./media/secure-teams-highly-regulated-data-scenario/secure-team-final.png)

<span data-ttu-id="1c787-181">下面是敏感度标签与团队组之间的关系。</span><span class="sxs-lookup"><span data-stu-id="1c787-181">Here’s the relationship between the sensitivity label and the Team Group.</span></span>

![团队组与标签权限之间的关系](./media/secure-teams-highly-regulated-data-scenario/secure-team-label-permissions.png)


>[!Note]
><span data-ttu-id="1c787-183">如果为用户定义的权限配置敏感度标签或子标签或具有到期日期，则无法从 Teams 或 SharePoint 中打开文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-183">If you configure the sensitivity label or sublabel for user-defined permissions or with an expiration date, you cannot open the file from Teams or SharePoint.</span></span> <span data-ttu-id="1c787-184">必须使用 Office 应用。</span><span class="sxs-lookup"><span data-stu-id="1c787-184">You must use an Office app.</span></span>
>

### <a name="custom-permissions"></a><span data-ttu-id="1c787-185">自定义权限</span><span class="sxs-lookup"><span data-stu-id="1c787-185">Custom permissions</span></span>

<span data-ttu-id="1c787-186">你还可以为团队网站配置自定义 SharePoint 网站权限，并根据需要配置其相应的敏感度标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-186">You can also configure custom SharePoint site permissions for the Team Site and, if needed, its corresponding sensitivity label.</span></span> <span data-ttu-id="1c787-187">下面是两个示例。</span><span class="sxs-lookup"><span data-stu-id="1c787-187">Here are two examples.</span></span>

#### <a name="example-1-delegating-sharepoint-site-administration"></a><span data-ttu-id="1c787-188">示例 1：委派 SharePoint 网站管理</span><span class="sxs-lookup"><span data-stu-id="1c787-188">Example 1: Delegating SharePoint site administration</span></span>

<span data-ttu-id="1c787-189">如果团队所有者没有 SharePoint 管理经验，或者希望委派团队网站的管理，则他们可以将 SharePoint 管理员的用户帐户添加到团队所有者列表中。</span><span class="sxs-lookup"><span data-stu-id="1c787-189">If the team owner does not have SharePoint administration experience or wants to delegate administration of the Team Site, they could add the user account of a SharePoint administrator to the list of team owners.</span></span> <span data-ttu-id="1c787-190">但是，SharePoint 管理员可以完全访问团队及其所有资源，并且可以打开应用了敏感度标签的文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-190">But then the SharePoint administrator would have full access to the team and all its resources and would be able to open a file with the sensitivity label applied.</span></span> 

<span data-ttu-id="1c787-191">为了防止过度授予特权，请在网站的高级权限设置中将 SharePoint 管理员的用户帐户添加到团队网站所有者 SharePoint 组中。</span><span class="sxs-lookup"><span data-stu-id="1c787-191">To prevent this over-granting of privileges, add the user account of the SharePoint administrator to the Team Site Owners SharePoint group in the advanced permissions settings of the site.</span></span> <span data-ttu-id="1c787-192">SharePoint 管理员可以管理网站，但是将无法访问团队及其任何资源，也无法打开分配了敏感度标签的文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-192">The SharePoint administrator can administer the site but will not be able to access the team and any of its resources or open the files with the sensitivity label assigned.</span></span>

#### <a name="example-2-allowing-view-only-access-to-labeled-files"></a><span data-ttu-id="1c787-193">示例 2：允许仅查看带标签的文件</span><span class="sxs-lookup"><span data-stu-id="1c787-193">Example 2: Allowing view-only access to labeled files</span></span>

<span data-ttu-id="1c787-194">如果某些员工只需要查看团队网站中带标签的文件内容，可将其个人用户帐户添加到：</span><span class="sxs-lookup"><span data-stu-id="1c787-194">If some staff only need to view the contents of labeled files in the Team Site, add their individual user accounts to the:</span></span>

- <span data-ttu-id="1c787-195">\<团队名称 > 访问者 SharePoint 组，默认情况下它具有“读取”权限级别。</span><span class="sxs-lookup"><span data-stu-id="1c787-195">\<team name> Visitors SharePoint group, which by default has the Read permission level.</span></span> 
- <span data-ttu-id="1c787-196">具有查看者权限的敏感度标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-196">The sensitivity label with the Viewer permissions.</span></span>

<span data-ttu-id="1c787-197">下面是标签上生成的权限。</span><span class="sxs-lookup"><span data-stu-id="1c787-197">Here are the resulting permissions on the label.</span></span>

![用于查看带标签的文件的自定义权限示例](./media/secure-teams-highly-regulated-data-scenario/secure-team-custom-view-permissions.png)
 
<span data-ttu-id="1c787-199">网站访问者将能够直接访问团队网站，并查看已应用子标签的文件内容。</span><span class="sxs-lookup"><span data-stu-id="1c787-199">The site visitors will be able to access the Team Site directly and view the contents of files that have the sublabel applied.</span></span> <span data-ttu-id="1c787-200">但是，由于它们不是团队组的成员，因此不能访问团队或其任何资源。</span><span class="sxs-lookup"><span data-stu-id="1c787-200">But because they are not members of the Team Group, they will not be able to access the team or any of its resources.</span></span>


## <a name="phase-2-drive-user-adoption-for-team-members"></a><span data-ttu-id="1c787-201">阶段 2：驱动团队成员的用户采用</span><span class="sxs-lookup"><span data-stu-id="1c787-201">Phase 2: Drive user adoption for team members</span></span>

<span data-ttu-id="1c787-202">随着团队的建立，是时候驱动该团队的采用以及提升它对团队成员的额外安全性。</span><span class="sxs-lookup"><span data-stu-id="1c787-202">With the team in place, it’s time to drive the adoption of this team and its additional security to team members.</span></span>

### <a name="step-1-train-your-users"></a><span data-ttu-id="1c787-203">步骤 1：培训用户</span><span class="sxs-lookup"><span data-stu-id="1c787-203">Step 1: Train your users</span></span>

<span data-ttu-id="1c787-204">团队组成员可以访问团队及其所有资源，包括聊天、会议和其他应用。</span><span class="sxs-lookup"><span data-stu-id="1c787-204">Members of the Team Group can access the team and all of its resources, including chats, meetings, and other apps.</span></span> <span data-ttu-id="1c787-205">使用频道的“**文件**”部分中的文件时，团队组成员必须将敏感度标签或子标签分配给为安全团队创建的文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-205">When working with files from the **Files** section of a channel, members of the Team Group must assign the sensitivity label or sublabel to files created for the secure team.</span></span> <span data-ttu-id="1c787-206">下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="1c787-206">Here’s an example.</span></span>

![将标签应用于安全团队中的文件的示例](./media/secure-teams-highly-regulated-data-scenario/secure-team-label-applied.png)
 
<span data-ttu-id="1c787-208">将标签应用于受保护的文件时。</span><span class="sxs-lookup"><span data-stu-id="1c787-208">When the label gets applied to the file it is secured.</span></span> <span data-ttu-id="1c787-209">团队组成员可以在 Teams 中打开它并进行实时协作。</span><span class="sxs-lookup"><span data-stu-id="1c787-209">Members of the Team Group can open it in Teams and collaborate in real time.</span></span> <span data-ttu-id="1c787-210">它已加密，并且包含为团队组成员提供的共同创作权限集。</span><span class="sxs-lookup"><span data-stu-id="1c787-210">It is encrypted and includes the Co-Author permissions set to the Team Group members.</span></span> <span data-ttu-id="1c787-211">如果文件离开网站并转发给恶意用户，则他们必须提供作为团队组成员的用户帐户的凭据，这样才能打开文件并查看其内容。</span><span class="sxs-lookup"><span data-stu-id="1c787-211">If the file leaves the site and gets forwarded to a malicious user, they will have to supply credentials of a user account that is member of the Team Group to open the file and view its contents.</span></span> 

<span data-ttu-id="1c787-212">培训团队成员：</span><span class="sxs-lookup"><span data-stu-id="1c787-212">Train your team members:</span></span>

- <span data-ttu-id="1c787-213">了解使用新团队访问聊天、会议、文件和团队网站的其他资源的重要性以及高度管控数据泄露的后果，例如法律后果、监管罚款、勒索软件或失去竞争优势。</span><span class="sxs-lookup"><span data-stu-id="1c787-213">On the importance of using the new team for chats, meetings, files, and the other resources of the Team Site and the consequences of a highly regulated data leak, such as legal ramifications, regulatory fines, ransomware, or loss of competitive advantage.</span></span>
- <span data-ttu-id="1c787-214">如何访问团队。</span><span class="sxs-lookup"><span data-stu-id="1c787-214">How to access the team.</span></span>
- <span data-ttu-id="1c787-215">如何在网站上创建新文件和上传本地存储的新文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-215">How to create new files on the site and upload new files stored locally.</span></span>
- <span data-ttu-id="1c787-216">DLP 策略如何阻止它们在外部共享文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-216">How the DLP policy blocks them from sharing files externally.</span></span>
- <span data-ttu-id="1c787-217">如何使用团队的自定义标签或子标签来标记文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-217">How to label files with the custom label or sublabel for the team.</span></span>
- <span data-ttu-id="1c787-218">标签或子标签如何保护文件（即使文件泄露到网站外部）。</span><span class="sxs-lookup"><span data-stu-id="1c787-218">How the label or sublabel protects files even when they are leaked off the site.</span></span>

<span data-ttu-id="1c787-219">此培训应包括实践练习，让团队成员可以体验这些功能及其结果。</span><span class="sxs-lookup"><span data-stu-id="1c787-219">This training should include hands-on exercises so that your team members can experience these capabilities and their results.</span></span>

### <a name="step-2-conduct-periodic-reviews-of-usage-and-address-team-member-feedback"></a><span data-ttu-id="1c787-220">步骤 2：定期审查使用情况并处理团队成员的反馈意见</span><span class="sxs-lookup"><span data-stu-id="1c787-220">Step 2: Conduct periodic reviews of usage and address team member feedback</span></span>

<span data-ttu-id="1c787-221">在培训后的几周内：</span><span class="sxs-lookup"><span data-stu-id="1c787-221">In the weeks after training:</span></span>

- <span data-ttu-id="1c787-222">快速处理团队成员的反馈意见并微调相关策略和配置。</span><span class="sxs-lookup"><span data-stu-id="1c787-222">Quickly address team member feedback and fine tune polices and configurations.</span></span>
- <span data-ttu-id="1c787-223">分析团队的使用情况，并将其与预期使用情况进行比较。</span><span class="sxs-lookup"><span data-stu-id="1c787-223">Analyze usage for the team and compare it with usage expectations.</span></span>
- <span data-ttu-id="1c787-224">验证是否使用自定义敏感度标签或子标签正确标记了高度管控的文件。</span><span class="sxs-lookup"><span data-stu-id="1c787-224">Verify that highly regulated files have been properly labeled with the custom sensitivity label or sublabel.</span></span>

  <span data-ttu-id="1c787-225">通过查看 SharePoint 中的文件夹并使用“**添加列**”的“**显示/隐藏列**”选项添加“**敏感度**”列，可以查看为哪些文件分配了标签。</span><span class="sxs-lookup"><span data-stu-id="1c787-225">You can see which files have a label assigned by viewing a folder in SharePoint and adding the **Sensitivity** column through the **Show/hide columns** option of **Add column**.</span></span>

<span data-ttu-id="1c787-226">根据需要重新培训用户。</span><span class="sxs-lookup"><span data-stu-id="1c787-226">Retrain your users as needed.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c787-227">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c787-227">See also</span></span>

[<span data-ttu-id="1c787-228">用于高度管控数据的 SharePoint 网站</span><span class="sxs-lookup"><span data-stu-id="1c787-228">SharePoint sites for highly regulated data</span></span>](teams-sharepoint-online-sites-highly-regulated-data.md)

[<span data-ttu-id="1c787-229">Microsoft 365 企业版工作负载和方案</span><span class="sxs-lookup"><span data-stu-id="1c787-229">Microsoft 365 Enterprise workloads and scenarios</span></span>](deploy-workloads.md)

<span data-ttu-id="1c787-230">[Microsoft 365 工作效率库](https://aka.ms/productivitylibrary) https://aka.ms/productivitylibrary)</span><span class="sxs-lookup"><span data-stu-id="1c787-230">[Microsoft 365 Productivity Library](https://aka.ms/productivitylibrary) (https://aka.ms/productivitylibrary)</span></span>

[<span data-ttu-id="1c787-231">部署指南</span><span class="sxs-lookup"><span data-stu-id="1c787-231">Deployment guide</span></span>](deploy-microsoft-365-enterprise.md)