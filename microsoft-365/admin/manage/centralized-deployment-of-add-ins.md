---
title: 确定加载项的集中部署是否适用于你的组织
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: 确定您的 Office 365 租户和用户是否符合要求，以便您可以使用集中部署来部署 Office 外接程序。
ms.openlocfilehash: 4351658f2637b86c9b3233f55916d8e0ac0f8cfb
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/24/2020
ms.locfileid: "42251132"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a><span data-ttu-id="854de-103">确定加载项的集中部署是否适用于你的组织</span><span class="sxs-lookup"><span data-stu-id="854de-103">Determine if Centralized Deployment of add-ins works for your organization</span></span>

<span data-ttu-id="854de-104">对于大多数客户来说，集中部署是为 Office 365 组织中的用户和组部署 Office 加载项值得推荐且功能最丰富的方式。</span><span class="sxs-lookup"><span data-stu-id="854de-104">Centralized Deployment is the recommended and most feature-rich way for most customers to deploy Office add-ins to users and groups within your Office 365 organization.</span></span> <span data-ttu-id="854de-105">如果你是管理员，请使用本指南来确定你的租户和用户是否符合要求，以便你可以使用集中部署。</span><span class="sxs-lookup"><span data-stu-id="854de-105">If you're an admin, use this guidance to determine if your tenant and users meet the requirements so that you can use Centralized Deployment.</span></span>
<span data-ttu-id="854de-106">集中部署支持 Windows、Mac、iOS、Android 和 Online Office 应用。</span><span class="sxs-lookup"><span data-stu-id="854de-106">Centralized Deployment supports Windows, Mac, iOS, Android and Online Office apps.</span></span>
<span data-ttu-id="854de-107">加载项最长可能需要12个小时才能为所有用户显示客户端。</span><span class="sxs-lookup"><span data-stu-id="854de-107">It can take up to 12 hours for an add-in to show up for client for all users.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="854de-108">Requirements</span><span class="sxs-lookup"><span data-stu-id="854de-108">Requirements</span></span>

<span data-ttu-id="854de-109">集中部署加载项需要用户使用 Office 365 专业增强版（并使用其组织 ID 登录到 Office），并拥有 Exchange Online 和活动 Exchange Online 邮箱。</span><span class="sxs-lookup"><span data-stu-id="854de-109">Centralized deployment of add-ins requires that the users are using Office 365 ProPlus (and are signed into Office using their Organizational ID), and have Exchange Online and active Exchange Online mailboxes.</span></span> <span data-ttu-id="854de-110">你的订阅目录目录必须处于或联合到 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="854de-110">Your subscription'd directory must either be in, or federated to Azure Active Directory.</span></span>
<span data-ttu-id="854de-111">您可以查看以下 Office 和 Exchange 的特定要求，或使用[office 365 集中部署兼容性检查器](https://docs.microsoft.com/office365/admin/manage/centralized-deployment-of-add-ins?view=o365-worldwide#office-365-centralized-deployment-compatibility-checker)。</span><span class="sxs-lookup"><span data-stu-id="854de-111">You can view specific requirements for Office and Exchange below, or use the [Office 365 Centralized Deployment Compatibility Checker](https://docs.microsoft.com/office365/admin/manage/centralized-deployment-of-add-ins?view=o365-worldwide#office-365-centralized-deployment-compatibility-checker).</span></span>

<span data-ttu-id="854de-112">集中部署不支持以下内容：</span><span class="sxs-lookup"><span data-stu-id="854de-112">Centralized Deployment doesn't support the following:</span></span>
  
- <span data-ttu-id="854de-113">针对 Office 2013 中 Word、Excel 或 PowerPoint 的加载项</span><span class="sxs-lookup"><span data-stu-id="854de-113">Add-ins that target Word, Excel, or PowerPoint in Office 2013</span></span>
    
- <span data-ttu-id="854de-114">本地目录服务</span><span class="sxs-lookup"><span data-stu-id="854de-114">An on-premises directory service</span></span>
    
- <span data-ttu-id="854de-115">部署到 SharePoint 的加载项</span><span class="sxs-lookup"><span data-stu-id="854de-115">Add-in deployment to SharePoint</span></span>  

- <span data-ttu-id="854de-116">团队应用程序</span><span class="sxs-lookup"><span data-stu-id="854de-116">Teams apps</span></span>
   
- <span data-ttu-id="854de-117">组件对象模型 (COM) 或 Visual Studio Tools for Office (VSTO) 的加载项的部署</span><span class="sxs-lookup"><span data-stu-id="854de-117">Deployment of Component Object Model (COM) or Visual Studio Tools for Office (VSTO) add-ins</span></span>
    
- <span data-ttu-id="854de-118">不包含 Exchange 的 Office 365 的部署，如 Office 365 商业版</span><span class="sxs-lookup"><span data-stu-id="854de-118">Deployments of Office 365 that do not include Exchange such as Office 365 Business</span></span>

### <a name="office-requirements"></a><span data-ttu-id="854de-119">Office 要求</span><span class="sxs-lookup"><span data-stu-id="854de-119">Office Requirements</span></span>

- <span data-ttu-id="854de-120">对于 Word、Excel 和 PowerPoint 外接程序，您的用户必须使用下列项之一：</span><span class="sxs-lookup"><span data-stu-id="854de-120">For Word, Excel, and PowerPoint add-ins, your users must be using one of the following:</span></span>
  - <span data-ttu-id="854de-121">在 Windows 设备上，版本1704或更高版本的 Office 365 专业增强版。</span><span class="sxs-lookup"><span data-stu-id="854de-121">On a Windows device, Version 1704 or later of Office 365 ProPlus.</span></span>
  - <span data-ttu-id="854de-122">在 Mac 上，版本15.34 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="854de-122">On a Mac, Version 15.34 or later.</span></span>
      - <span data-ttu-id="854de-123">在 iOS （仅限 iPad）上，版本2.9.18010804 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="854de-123">On iOS (iPad only), Version 2.9.18010804 or later.</span></span>
- <span data-ttu-id="854de-124">对于 Outlook，您的用户必须使用以下各项之一：</span><span class="sxs-lookup"><span data-stu-id="854de-124">For Outlook, your users must be using one of the following:</span></span> 
  - <span data-ttu-id="854de-125">Office 365 专业增强版的版本1701或更高版本。</span><span class="sxs-lookup"><span data-stu-id="854de-125">Version 1701 or later of Office 365 ProPlus.</span></span>
  - <span data-ttu-id="854de-126">Office Professional Plus 2019 或 Office Standard 2019 的版本1808或更高版本。</span><span class="sxs-lookup"><span data-stu-id="854de-126">Version 1808 or later of Office Professional Plus 2019 or Office Standard 2019.</span></span>
  - <span data-ttu-id="854de-127">Office Professional Plus 2016 （MSI）或 Office Standard 2016 （MSI）的版本16.0.4494.1000 或更高版本\*</span><span class="sxs-lookup"><span data-stu-id="854de-127">Version 16.0.4494.1000 or later of Office Professional Plus 2016 (MSI) or Office Standard 2016 (MSI)\*</span></span>
  - <span data-ttu-id="854de-128">Office Professional Plus 2013 （MSI）或 Office Standard 2013 （MSI）的版本15.0.4937.1000 或更高版本\*</span><span class="sxs-lookup"><span data-stu-id="854de-128">Version 15.0.4937.1000 or later of Office Professional Plus 2013 (MSI) or Office Standard 2013 (MSI)\*</span></span>
  - <span data-ttu-id="854de-129">版本16.0.9318.1000 或更高版本的 Office 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="854de-129">Version 16.0.9318.1000 or later of Office 2016 for Mac</span></span> 
- <span data-ttu-id="854de-130">版本2.75.0 或更高版本的 Outlook mobile for iOS</span><span class="sxs-lookup"><span data-stu-id="854de-130">Version 2.75.0 or later of Outlook mobile for iOS</span></span> 
- <span data-ttu-id="854de-131">适用于 Android 的 Outlook mobile 版本2.2.145 或更高版本</span><span class="sxs-lookup"><span data-stu-id="854de-131">Version 2.2.145 or later of Outlook mobile for Android</span></span> 
    
    <span data-ttu-id="854de-132">\* MSI 版本的 Outlook 在相应的 Outlook 功能区中显示管理员安装的加载项，而不是 "我的外接程序" 部分。</span><span class="sxs-lookup"><span data-stu-id="854de-132">\*MSI versions of Outlook show admin-installed add-ins in the appropriate Outlook ribbon, not the "My add-ins" section.</span></span>
    

#### <a name="find-out-if-office-365-proplus-is-installed"></a><span data-ttu-id="854de-133">查明是否已安装 Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="854de-133">Find out if Office 365 ProPlus is installed</span></span>

<span data-ttu-id="854de-134">若要使用 Office 365 专业增强版，用户必须拥有 Office 365 帐户，并且必须已分配有许可证。</span><span class="sxs-lookup"><span data-stu-id="854de-134">To use Office 365 ProPlus, a user must have an Office 365 account and must have been assigned a license.</span></span> <span data-ttu-id="854de-135">有关详细信息，请参阅 [Office 365 ProPlus 概述](https://go.microsoft.com/fwlink/p/?linkid=846328)。</span><span class="sxs-lookup"><span data-stu-id="854de-135">For more information, see [Overview of Office 365 ProPlus](https://go.microsoft.com/fwlink/p/?linkid=846328).</span></span>

<span data-ttu-id="854de-136">检测用户是否已安装 Office 365 专业增强版并最近使用过的最简单方法是使用 Microsoft Office 激活报告，该报告在 Microsoft 365 管理中心中提供。</span><span class="sxs-lookup"><span data-stu-id="854de-136">The simplest way to detect if a user has Office 365 ProPlus installed and has been using it recently is to use the Microsoft Office Activations report, which is available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="854de-137">此报表提供一张列表，列出最近 7 天、30 天、90 天或 180 天内已激活 Office 365 专业增强订阅版 的所有用户。</span><span class="sxs-lookup"><span data-stu-id="854de-137">The report provides a list of all users who have activated Office 365 ProPlus within the last 7 days, 30 days, 90 days, or 180 days.</span></span> <span data-ttu-id="854de-138">出于集中部署目的，Windows 或 Mac 的桌面激活是报表中的重要列。</span><span class="sxs-lookup"><span data-stu-id="854de-138">For centralized deployment purposes, the desktop activations for Windows or Mac are the important columns in the report.</span></span> <span data-ttu-id="854de-139">可将报表导出至 Excel。</span><span class="sxs-lookup"><span data-stu-id="854de-139">You can export the report to Excel.</span></span> <span data-ttu-id="854de-140">有关报表的详细信息，请参阅[管理中心内的 Office 365 报表 - Microsoft Office 激活](../activity-reports/microsoft-office-activations.md)。</span><span class="sxs-lookup"><span data-stu-id="854de-140">For more information about the report, see [Office 365 Reports in the Admin Center - Microsoft Office activations](../activity-reports/microsoft-office-activations.md).</span></span>
  
<span data-ttu-id="854de-141">如果不想使用激活报告，可以让用户在其计算机上打开 Office 应用程序（如 Word），然后选择 "**文件** \> **帐户**"。</span><span class="sxs-lookup"><span data-stu-id="854de-141">If you don't want to use the Activations report, you can ask a user to open an Office application such as Word on their machine, and then choose **File** \> **Account**.</span></span> <span data-ttu-id="854de-142">在" **产品信息**"下，应看到" **订阅产品**"和" **Microsoft Office 365 专业增强订阅版**"，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="854de-142">Under **Product Information**, you should see **Subscription Product** and **Microsoft Office 365 ProPlus**, as shown in the following image.</span></span>

![Office 应用程序中的产品信息](../media/4bff2bb8-0690-4d22-ac1f-b8881807fa39.png)
  
<span data-ttu-id="854de-144">有关 Office 365 专业增强订阅版 的帮助，请参阅 [Office 365 ProPlus 疑难解答提示](https://go.microsoft.com/fwlink/p/?linkid=846339)。</span><span class="sxs-lookup"><span data-stu-id="854de-144">For help with Office 365 ProPlus, see [Troubleshooting tips for Office 365 ProPlus](https://go.microsoft.com/fwlink/p/?linkid=846339).</span></span>


### <a name="exchange-requirements"></a><span data-ttu-id="854de-145">Exchange 要求</span><span class="sxs-lookup"><span data-stu-id="854de-145">Exchange requirements</span></span>

<span data-ttu-id="854de-p106">Microsoft Exchange 存储组织的租户中的加载项清单。部署加载项的管理员和接收这些加载项的用户必须使用支持 OAuth 身份验证的 Exchange Server 版本。默认情况下，Exchange 多租户和专用 VNext 部署支持 OAuth。可将 Exchange 专用旧版和混合本地部署配置为支持 OAuth；但它不是默认配置。</span><span class="sxs-lookup"><span data-stu-id="854de-p106">Microsoft Exchange stores the add-in manifests within your organization's tenant. The admin deploying add-ins and the users receiving those add-ins must be on a version of Exchange Server that supports OAuth authentication. By default, Exchange Multi-Tenant and Dedicated VNext deployments support OAuth. Exchange Dedicated Legacy and hybrid on-premises deployments can be configured to support OAuth; however, it isn't the default configuration.</span></span>
  
<span data-ttu-id="854de-p107">请与组织的 Exchange 管理员联系，了解正在使用哪个配置。可使用 [Test-OAuthConnectivity](https://go.microsoft.com/fwlink/p/?linkid=846351) PowerShell cmdlet 验证每个用户的 OAuth 连接。</span><span class="sxs-lookup"><span data-stu-id="854de-p107">Check with your organization's Exchange admin to find out which configuration is in use. OAuth connectivity per user can be verified by using the [Test-OAuthConnectivity](https://go.microsoft.com/fwlink/p/?linkid=846351) PowerShell cmdlet.</span></span> 


### <a name="office-365-centralized-deployment-compatibility-checker"></a><span data-ttu-id="854de-152">Office 365 集中部署兼容性检查器</span><span class="sxs-lookup"><span data-stu-id="854de-152">Office 365 Centralized Deployment Compatibility Checker</span></span>

<span data-ttu-id="854de-p108">通过使用 Office 365 集中部署兼容性检查器，可验证是否已经针对 Word、Excel 和 PowerPoint 将租户上的用户设置为使用集中部署。Outlook 支持不需要兼容性检查器。在[此处](https://aka.ms/officeaddindeploymentorgcompatibilitychecker)下载兼容性检查器。</span><span class="sxs-lookup"><span data-stu-id="854de-p108">Using the Office 365 Centralized Deployment Compatibility Checker, you can verify whether the users on your tenant are set up to use Centralized Deployment for Word, Excel and PowerPoint. The Compatibility Checker is not required for Outlook support. Download the compatibility checker [here](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).</span></span>
  
#### <a name="run-the-compatibility-checker"></a><span data-ttu-id="854de-156">运行兼容性检查器</span><span class="sxs-lookup"><span data-stu-id="854de-156">Run the compatibility checker</span></span>
  
1. <span data-ttu-id="854de-157">启动提升的 PowerShell .exe 窗口。</span><span class="sxs-lookup"><span data-stu-id="854de-157">Start an elevated PowerShell.exe window.</span></span>
    
2. <span data-ttu-id="854de-158">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="854de-158">Run the following command:</span></span>

```powershell
Import-Module O365CompatibilityChecker
```
    
3. <span data-ttu-id="854de-159">运行**CompatabilityCheck**命令：</span><span class="sxs-lookup"><span data-stu-id="854de-159">Run the **Invoke-CompatabilityCheck** command:</span></span>

```powershell
Invoke-CompatibilityCheck
```
   <span data-ttu-id="854de-160">这将提示您输入*_TenantDomain_* （例如， *TailspinToysIncorporated。</span>com*）和*_TenantAdmin_* 凭据（使用您的全局管理员凭据），然后请求许可。</span><span class="sxs-lookup"><span data-stu-id="854de-160">which prompts you for  *_TenantDomain_* (for example, *TailspinToysIncorporated.onmicrosoft.</span>com*) and  *_TenantAdmin_* credentials (use your global admin credentials), and then requests consent.</span></span>
    
> [!NOTE]
> <span data-ttu-id="854de-161">检查器可能需要数分钟或数小时时间来完成检查，具体取决于租户中的用户数。</span><span class="sxs-lookup"><span data-stu-id="854de-161">Depending on the number of users in your tenant, the checker could complete in minutes or hours.</span></span> 
  
<span data-ttu-id="854de-162">工具运行完毕后，会生成逗号分隔格式的输出文件 (.csv)。</span><span class="sxs-lookup"><span data-stu-id="854de-162">When the tool finishes running, it produces an output file in comma-separated (.csv) format.</span></span> <span data-ttu-id="854de-163">默认情况下，该文件保存到**C:\windows\system32** 。</span><span class="sxs-lookup"><span data-stu-id="854de-163">The file is saved to **C:\windows\system32** by default.</span></span> <span data-ttu-id="854de-164">输出文件包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="854de-164">The output file contains the following information:</span></span>
  
- <span data-ttu-id="854de-165">用户名</span><span class="sxs-lookup"><span data-stu-id="854de-165">User Name</span></span>
    
- <span data-ttu-id="854de-166">用户 ID（用户的电子邮件地址）</span><span class="sxs-lookup"><span data-stu-id="854de-166">User ID (User's email address)</span></span>
    
- <span data-ttu-id="854de-167">集中部署准备就绪 - 如果剩余的项为 true</span><span class="sxs-lookup"><span data-stu-id="854de-167">Centralized Deployment ready - If the remaining items are true</span></span>
    
- <span data-ttu-id="854de-168">Office plan-授权的 Office 计划</span><span class="sxs-lookup"><span data-stu-id="854de-168">Office plan - The plan of Office they are licensed for</span></span>
    
- <span data-ttu-id="854de-169">Office 已激活 - 如果已激活 Office</span><span class="sxs-lookup"><span data-stu-id="854de-169">Office Activated - If they have activated Office</span></span>
    
- <span data-ttu-id="854de-170">支持的邮箱 - 如果使用已启用 OAuth 的邮箱</span><span class="sxs-lookup"><span data-stu-id="854de-170">Supported Mailbox - If they are on an OAuth-enabled mailbox</span></span>


  
## <a name="user-and-group-assignments"></a><span data-ttu-id="854de-171">用户和组分配</span><span class="sxs-lookup"><span data-stu-id="854de-171">User and group assignments</span></span>

<span data-ttu-id="854de-172">集中部署功能当前支持 Azure Active Directory 支持的大多数组，包括 Office 365 组、通讯组列表和安全组。</span><span class="sxs-lookup"><span data-stu-id="854de-172">The Centralized Deployment feature currently supports the majority of groups supported by Azure Active Directory, including Office 365 Groups, distribution lists, and security groups.</span></span>
  
> [!NOTE]
> <span data-ttu-id="854de-173">当前不支持未启用邮件的安全组。</span><span class="sxs-lookup"><span data-stu-id="854de-173">Non-mail enabled security groups are not currently supported.</span></span> 
  
<span data-ttu-id="854de-174">集中部署支持对租户中的单个用户、组和每个人的工作分配。</span><span class="sxs-lookup"><span data-stu-id="854de-174">Centralized Deployment supports assignments to individual users, groups, and everyone in the tenant.</span></span> <span data-ttu-id="854de-175">集中部署支持顶级组或没有父组的组中的用户，但不支持嵌套组或有父组的组中的用户。</span><span class="sxs-lookup"><span data-stu-id="854de-175">Centralized Deployment supports users in top-level groups or groups without parent groups, but not users in nested groups or groups that have parent groups.</span></span>
   
<span data-ttu-id="854de-p111">请查看以下示例，在这里，柏隼、康霓以及销售部门组被分配了加载项。由于西海岸销售部门是嵌套组，赵强和熊飞未被分配加载项。</span><span class="sxs-lookup"><span data-stu-id="854de-p111">Take a look at the following example where Sandra, Sheila, and the Sales Department group are assigned to an add-in. Because the West Coast Sales Department is a nested group, Bert and Fred aren't assigned to an add-in.</span></span>
  
![销售部门的关系图](../media/683094bb-1160-4cce-810d-26ef7264c592.png)

   
### <a name="find-out-if-a-group-contains-nested-groups"></a><span data-ttu-id="854de-179">找出一个组是否包含嵌套组</span><span class="sxs-lookup"><span data-stu-id="854de-179">Find out if a group contains nested groups</span></span>

<span data-ttu-id="854de-180">若要找出一个组是否包含嵌套组，最简单的方法是查看 Outlook 内的组联系人卡片。</span><span class="sxs-lookup"><span data-stu-id="854de-180">The easiest way to detect if a group contains nested groups is to view the group contact card within Outlook.</span></span> <span data-ttu-id="854de-181">如果您在电子邮件的 " **To** " 字段中输入组名称，然后在解析时选择组名称，将显示它是否包含用户或嵌套组。</span><span class="sxs-lookup"><span data-stu-id="854de-181">If you enter the group name within the **To** field of an email and then select the group name when it resolves, it will show you if it contains users or nested groups.</span></span> <span data-ttu-id="854de-182">在以下示例中，测试组 Outlook 联系人卡片的" **成员**"选项卡显示没有用户且只有两个子组。</span><span class="sxs-lookup"><span data-stu-id="854de-182">In the example below, the **Members** tab of the Outlook contact card for the Test Group shows no users and only two sub groups.</span></span> 
  
![Outlook 联系人卡片的 "成员" 选项卡](../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)
  
<span data-ttu-id="854de-p113">可以解析某个组，查看该组是否是任何组的成员，从而进行反向查询。在以下示例中，可以在 Outlook 联系人卡片的" **成员身份**"选项卡下看到子组 1 是测试组的成员。</span><span class="sxs-lookup"><span data-stu-id="854de-p113">You can do the opposite query by resolving the group to see if it's a member of any group. In the example below, you can see under the **Membership** tab of the Outlook contact card that Sub Group 1 is a member of the Test Group.</span></span> 
  
![Outlook 联系人卡片的 "成员资格" 选项卡](../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)
  
<span data-ttu-id="854de-p114">或者，可以使用 Azure Active Directory 图形 API 运行查询，查找组内的组列表。有关详细信息，请参阅 [Operations on groups | Graph API reference](https://go.microsoft.com/fwlink/p/?linkid=846342)（组操作 | 图形 API 参考）。</span><span class="sxs-lookup"><span data-stu-id="854de-p114">Alternately, you can use the Azure Active Directory Graph API to run queries to find the list of groups within a group. For more information, see [Operations on groups | Graph API reference](https://go.microsoft.com/fwlink/p/?linkid=846342).</span></span>
  
### <a name="contacting-microsoft-for-support"></a><span data-ttu-id="854de-189">联系 Microsoft 以获取支持</span><span class="sxs-lookup"><span data-stu-id="854de-189">Contacting Microsoft for support</span></span>

<span data-ttu-id="854de-190">如果您或您的用户在使用 Office 应用程序（Word、Excel 等）中加载外接程序时遇到问题，则可能需要与 Microsoft 支持人员联系（[了解如何](../contact-support-for-business-products.md)）。</span><span class="sxs-lookup"><span data-stu-id="854de-190">If you or your users encounter problems loading the add-in while using Office apps for the web (Word, Excel, etc.), which were centrally deployed, you may need to contact Microsoft support ([learn how](../contact-support-for-business-products.md)).</span></span> <span data-ttu-id="854de-191">在支持票证中提供与 Office 365 环境相关的以下信息。</span><span class="sxs-lookup"><span data-stu-id="854de-191">Provide the following information about your Office 365 environment in the support ticket.</span></span>
  
|<span data-ttu-id="854de-192">**平台**</span><span class="sxs-lookup"><span data-stu-id="854de-192">**Platform**</span></span>|<span data-ttu-id="854de-193">**调式信息**</span><span class="sxs-lookup"><span data-stu-id="854de-193">**Debug information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="854de-194">Office</span><span class="sxs-lookup"><span data-stu-id="854de-194">Office</span></span>  <br/> | <span data-ttu-id="854de-195">Charles/Fiddler 日志</span><span class="sxs-lookup"><span data-stu-id="854de-195">Charles/Fiddler logs</span></span>  <br/>  <span data-ttu-id="854de-196">租户 ID（ [了解如何操作](https://support.office.com/article/6891b561-a52d-4ade-9f39-b492285e2c9b.aspx)）</span><span class="sxs-lookup"><span data-stu-id="854de-196">Tenant ID ( [learn how](https://support.office.com/article/6891b561-a52d-4ade-9f39-b492285e2c9b.aspx))</span></span>  <br/>  <span data-ttu-id="854de-197">CorrelationID.</span><span class="sxs-lookup"><span data-stu-id="854de-197">CorrelationID.</span></span> <span data-ttu-id="854de-198">查看其中一个 office 页面的来源，查找相关 ID 值并将其发送给支持人员：</span><span class="sxs-lookup"><span data-stu-id="854de-198">View the source of one of the office pages and look for the Correlation ID value and send it to support:</span></span>  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">`  <br/>  `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`  <br/> |
|<span data-ttu-id="854de-199">丰富的客户端（Windows、Mac）</span><span class="sxs-lookup"><span data-stu-id="854de-199">Rich clients (Windows, Mac)</span></span>  <br/> | <span data-ttu-id="854de-200">Charles/Fiddler 日志</span><span class="sxs-lookup"><span data-stu-id="854de-200">Charles/Fiddler logs</span></span>  <br/>  <span data-ttu-id="854de-201">客户端应用程序的内部版本号（最好是从**文件/帐户**中的屏幕截图）</span><span class="sxs-lookup"><span data-stu-id="854de-201">Build numbers of the client app (preferably as a screenshot from **File/Account**)</span></span>  <br/> |
   
