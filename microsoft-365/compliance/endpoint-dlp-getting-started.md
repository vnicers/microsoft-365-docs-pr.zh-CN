---
title: Microsoft 365 终结点数据丢失防护（预览）入门
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: 设置 Microsoft 365 终结点数据丢失防护，以监视文件活动并将针对这些文件的保护措施实施到终结点。
ms.openlocfilehash: ee276c81a0ebfbf44dd77f6016172f9bf7ed3022
ms.sourcegitcommit: a08103bc120bdec7cfeaf67c1be4e221241e69ad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "45200002"
---
# <a name="get-started-with-endpoint-data-loss-prevention-preview"></a><span data-ttu-id="31f56-103">终结点数据丢失防护（预览）入门</span><span class="sxs-lookup"><span data-stu-id="31f56-103">Get started with Endpoint data loss prevention (preview)</span></span>

<span data-ttu-id="31f56-104">Microsoft 终结点数据丢失防护（终结点 DLP）是 Microsoft 365 数据丢失防护 (DLP) 功能套件的一部分，可用于发现和保护 Microsoft 365 服务中的敏感项目。</span><span class="sxs-lookup"><span data-stu-id="31f56-104">Microsoft Endpoint data loss prevention (Endpoint DLP) is part of the Microsoft 365 data loss prevention (DLP) suite of features you can use to discover and protect sensitive items across Microsoft 365 services.</span></span> <span data-ttu-id="31f56-105">有关 Microsoft 所有 DLP 产品/服务的更多信息，请参阅[数据丢失防护概述](data-loss-prevention-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="31f56-105">For more information about all of Microsoft’s DLP offerings, see [Overview of data loss prevention](data-loss-prevention-policies.md).</span></span> <span data-ttu-id="31f56-106">若要了解有关终结点 DLP 的详细信息，请参阅[了解终结点数据丢失防护（预览）](endpoint-dlp-learn-about.md)</span><span class="sxs-lookup"><span data-stu-id="31f56-106">To learn more about Endpoint DLP, see [Learn about Endpoint data loss prevention (preview)](endpoint-dlp-learn-about.md)</span></span>

<span data-ttu-id="31f56-107">通过 Microsoft 终结点 DLP，你可以监视 Windows 10 设备并检测何时使用和共享敏感项目。</span><span class="sxs-lookup"><span data-stu-id="31f56-107">Microsoft Endpoint DLP allows you to monitor Windows 10 devices and detect when sensitive items are used and shared.</span></span> <span data-ttu-id="31f56-108">这为你提供了所需的可见性和控制力，以确保正确使用和保护它们，并帮助防止可能危害它们的危险行为。</span><span class="sxs-lookup"><span data-stu-id="31f56-108">This gives you the visibility and control you need to ensure that they are used and protected properly, and to help prevent risky behavior that might compromise them.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="31f56-109">准备工作</span><span class="sxs-lookup"><span data-stu-id="31f56-109">Before you begin</span></span>

### <a name="skusubscriptions-licensing"></a><span data-ttu-id="31f56-110">SKU/订阅许可</span><span class="sxs-lookup"><span data-stu-id="31f56-110">SKU/subscriptions licensing</span></span>

<span data-ttu-id="31f56-111">在开始使用终结点 DLP 之前，应该先确认 [Microsoft 365 订阅](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)以及任何加载项。</span><span class="sxs-lookup"><span data-stu-id="31f56-111">Before you get started with Endpoint DLP, you should confirm your [Microsoft 365 subscription](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) and any add-ons.</span></span> <span data-ttu-id="31f56-112">若要访问和使用终结点 DLP 功能，必须具有这些订阅或加载项中的一个。</span><span class="sxs-lookup"><span data-stu-id="31f56-112">To access and use Endpoint DLP functionality, you must have one of these subscriptions or add-ons.</span></span>

- <span data-ttu-id="31f56-113">Microsoft 365 E5</span><span class="sxs-lookup"><span data-stu-id="31f56-113">Microsoft 365 E5</span></span>
- <span data-ttu-id="31f56-114">Microsoft 365 A5 (EDU)</span><span class="sxs-lookup"><span data-stu-id="31f56-114">Microsoft 365 A5 (EDU)</span></span>
- <span data-ttu-id="31f56-115">Microsoft 365 E5 合规</span><span class="sxs-lookup"><span data-stu-id="31f56-115">Microsoft 365 E5 compliance</span></span>
- <span data-ttu-id="31f56-116">Microsoft 365 A5 合规</span><span class="sxs-lookup"><span data-stu-id="31f56-116">Microsoft 365 A5 compliance</span></span>
- <span data-ttu-id="31f56-117">Microsoft 365 E5 信息保护和治理</span><span class="sxs-lookup"><span data-stu-id="31f56-117">Microsoft 365 E5 information protection and governance</span></span>
- <span data-ttu-id="31f56-118">Microsoft 365 A5 信息保护和治理</span><span class="sxs-lookup"><span data-stu-id="31f56-118">Microsoft 365 A5 information protection and governance</span></span>

### <a name="permissions"></a><span data-ttu-id="31f56-119">权限</span><span class="sxs-lookup"><span data-stu-id="31f56-119">Permissions</span></span>

<span data-ttu-id="31f56-120">若要启用设备管理，你使用的帐户必须是以下任何一个角色的成员：</span><span class="sxs-lookup"><span data-stu-id="31f56-120">To enable device management, the account you use must be a member of any one of these roles:</span></span>

- <span data-ttu-id="31f56-121">全局管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-121">Global admin</span></span>
- <span data-ttu-id="31f56-122">安全管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-122">Security admin</span></span>
- <span data-ttu-id="31f56-123">合规性管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-123">Compliance admin</span></span>

<span data-ttu-id="31f56-124">如果要使用自定义帐户查看设备管理设置，该帐户必须具有以下角色之一：</span><span class="sxs-lookup"><span data-stu-id="31f56-124">If you want to use a custom account to view the device management settings, it must be in one of these roles:</span></span>

- <span data-ttu-id="31f56-125">全局管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-125">Global admin</span></span>
- <span data-ttu-id="31f56-126">合规性管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-126">Compliance admin</span></span>
- <span data-ttu-id="31f56-127">合规性数据管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-127">Compliance data admin</span></span>
- <span data-ttu-id="31f56-128">全局读取者</span><span class="sxs-lookup"><span data-stu-id="31f56-128">Global reader</span></span>

<span data-ttu-id="31f56-129">如果要使用自定义帐户访问载入/载出页面，该帐户必须具有以下角色之一：</span><span class="sxs-lookup"><span data-stu-id="31f56-129">If you want to use a custom account to access the onboarding/offboarding page, it must be in one of these roles:</span></span>

- <span data-ttu-id="31f56-130">全局管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-130">Global admin</span></span>
- <span data-ttu-id="31f56-131">合规性管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-131">Compliance admin</span></span>

<span data-ttu-id="31f56-132">如果要使用自定义帐户打开/关闭设备监视，该帐户必须具有以下角色之一：</span><span class="sxs-lookup"><span data-stu-id="31f56-132">If you want to use a custom account to turn on/off device monitoring, it must be in one of these roles:</span></span>

- <span data-ttu-id="31f56-133">全局管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-133">Global admin</span></span>
- <span data-ttu-id="31f56-134">合规性管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-134">Compliance admin</span></span>

<span data-ttu-id="31f56-135">可在[活动资源管理器](data-classification-activity-explorer.md)中查看终结点 DLP 中的数据。</span><span class="sxs-lookup"><span data-stu-id="31f56-135">Data from Endpoint DLP can be viewed in [Activity explorer](data-classification-activity-explorer.md).</span></span> <span data-ttu-id="31f56-136">有四个角色可向活动资源管理器授予权限，用于访问数据的帐户必须是其中任何一个的成员。</span><span class="sxs-lookup"><span data-stu-id="31f56-136">There are four roles that grant permission to activity explorer, the account you use for accessing the data must be a member of any one of them.</span></span>

- <span data-ttu-id="31f56-137">全局管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-137">Global admin</span></span>
- <span data-ttu-id="31f56-138">合规性管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-138">Compliance admin</span></span>
- <span data-ttu-id="31f56-139">安全管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-139">Security admin</span></span>
- <span data-ttu-id="31f56-140">合规性数据管理员</span><span class="sxs-lookup"><span data-stu-id="31f56-140">Compliance data admin</span></span>

### <a name="prepare-your-endpoints"></a><span data-ttu-id="31f56-141">准备终结点</span><span class="sxs-lookup"><span data-stu-id="31f56-141">Prepare your endpoints</span></span>

<span data-ttu-id="31f56-142">确保你计划部署终结点 DLP 的 Windows 10 设备满足这些要求。</span><span class="sxs-lookup"><span data-stu-id="31f56-142">Make sure that the Windows 10 devices that you plan on deploying Endpoint DLP to meet these requirements.</span></span>

1. <span data-ttu-id="31f56-143">必须运行 Windows 10 内部版本 1809 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="31f56-143">Must be running Windows 10 build 1809 or up.</span></span>
2. <span data-ttu-id="31f56-144">所有设备必须[已加入 Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-ad-join)。</span><span class="sxs-lookup"><span data-stu-id="31f56-144">All devices must be [Azure Active Directory (AAD) joined](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-ad-join).</span></span>
3. <span data-ttu-id="31f56-145">在终结点设备上安装 Microsoft Chromium Edge 浏览器，以对上传到云活动执行策略操作。</span><span class="sxs-lookup"><span data-stu-id="31f56-145">Install Microsoft Chromium Edge browser on the endpoint device to enforce policy actions for the the upload to cloud activity.</span></span> <span data-ttu-id="31f56-146">请参见[下载基于 Chromium 的新 Microsoft Edge](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)。</span><span class="sxs-lookup"><span data-stu-id="31f56-146">See, [Download the new Microsoft Edge based on Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).</span></span>

## <a name="onboarding-devices-into-device-management"></a><span data-ttu-id="31f56-147">将设备载入设备管理</span><span class="sxs-lookup"><span data-stu-id="31f56-147">Onboarding devices into device management</span></span>

 <span data-ttu-id="31f56-148">必须先启用设备监视功能并载入终结点，然后才能监视和保护设备上的敏感项目。</span><span class="sxs-lookup"><span data-stu-id="31f56-148">You must enable device monitoring and onboard your endpoints before you can monitor and protect sensitive items on a device.</span></span> <span data-ttu-id="31f56-149">这两项操作都在 Microsoft 365 合规门户中完成。</span><span class="sxs-lookup"><span data-stu-id="31f56-149">Both of these actions are done in the Microsoft 365 Compliance portal.</span></span>

<span data-ttu-id="31f56-150">当你想载入尚未载入的设备时，你需要下载适当的脚本并将其部署到那些设备上。</span><span class="sxs-lookup"><span data-stu-id="31f56-150">When you want to onboard devices that haven't been onboarded yet, you'll download the appropriate script and deploy it to those devices.</span></span> <span data-ttu-id="31f56-151">按照[载入设备程序](endpoint-dlp-getting-started.md#onboarding-devices)进行操作。</span><span class="sxs-lookup"><span data-stu-id="31f56-151">Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).</span></span>

<span data-ttu-id="31f56-152">已载入到 [Microsoft Defender 高级威胁防护 (MDATP)](https://docs.microsoft.com/windows/security/threat-protection/) 的设备将显示在“托管设备”列表中。</span><span class="sxs-lookup"><span data-stu-id="31f56-152">If you already have devices onboarded into [Microsoft Defender Advanced Threat Protection (MDATP)](https://docs.microsoft.com/windows/security/threat-protection/), they will already appear in the managed devices list.</span></span> <span data-ttu-id="31f56-153">按照[设备已载入 MDATP 的程序](endpoint-dlp-getting-started.md#with-devices-onboarded-into-mdatp)进行操作</span><span class="sxs-lookup"><span data-stu-id="31f56-153">Follow the [With devices onboarded into MDATP procedure](endpoint-dlp-getting-started.md#with-devices-onboarded-into-mdatp).</span></span>

### <a name="onboarding-devices"></a><span data-ttu-id="31f56-154">载入设备</span><span class="sxs-lookup"><span data-stu-id="31f56-154">Onboarding devices</span></span>

<span data-ttu-id="31f56-155">在此部署方案中，你将载入尚未载入的设备，并且只想监视和保护敏感项目，防止 Windows 10 设备上发生意外共享。</span><span class="sxs-lookup"><span data-stu-id="31f56-155">In this deployment scenario, you'll onboard devices that have not been onboarded yet, and you just want to monitor and protect sensitive items from unintentional sharing on Windows 10 devices.</span></span>

1. <span data-ttu-id="31f56-156">打开“[Microsoft 合规中心](https://compliance.microsoft.com)”。</span><span class="sxs-lookup"><span data-stu-id="31f56-156">Open the [Microsoft compliance center](https://compliance.microsoft.com).</span></span>
2. <span data-ttu-id="31f56-157">打开合规中心设置页面，然后选择“**载入设备**”。</span><span class="sxs-lookup"><span data-stu-id="31f56-157">Open the Compliance Center settings page and choose **Onboard devices**.</span></span> 

![启用设备管理](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

> [!NOTE]
> <span data-ttu-id="31f56-159">设备载入通常需要大约 60 秒才能启用，请先等待 30 分钟，然后再与 Microsoft 支持人员接洽。</span><span class="sxs-lookup"><span data-stu-id="31f56-159">While it usually takes about 60 seconds for device onboarding to be enabled, please allow up to 30 minutes before engaging with Microsoft support.</span></span>

3. <span data-ttu-id="31f56-160">选择“**设备管理**”，以打开“**设备**”列表。</span><span class="sxs-lookup"><span data-stu-id="31f56-160">Choose **Device management** to open the **Devices** list.</span></span> <span data-ttu-id="31f56-161">在载入设备之前，此列表将为空。</span><span class="sxs-lookup"><span data-stu-id="31f56-161">The list will be empty until you onboard devices.</span></span>
4. <span data-ttu-id="31f56-162">选择“**载入**”以开始载入流程。</span><span class="sxs-lookup"><span data-stu-id="31f56-162">Choose **Onboarding** to begin the onboarding process.</span></span>
5. <span data-ttu-id="31f56-163">从“**部署方法**”列表中选择要部署到这些额外设备的方式，然后**下载程序包**。</span><span class="sxs-lookup"><span data-stu-id="31f56-163">Choose the way you want to deploy to these additional devices from the **Deployment method** list and then **download package**.</span></span>

![部署方法](../media/endpoint-dlp-getting-started-3-deployment-method.png)
1. <span data-ttu-id="31f56-165">按照[适用于 Windows 10 计算机的载入工具和方法](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)中的相应程序进行操作。</span><span class="sxs-lookup"><span data-stu-id="31f56-165">Follow the appropriate procedures in [Onboarding tools and methods for Windows 10 machines](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).</span></span> <span data-ttu-id="31f56-166">此链接会将你定位到登录页面，你可以在其中访问与在步骤 5 中选择的部署程序包相匹配的 MDATP 程序：</span><span class="sxs-lookup"><span data-stu-id="31f56-166">This link take you to a landing page where you can access MDATP procedures that match the deployment package you selected in step 5:</span></span>
    - <span data-ttu-id="31f56-167">使用组策略载入 Windows 10 计算机</span><span class="sxs-lookup"><span data-stu-id="31f56-167">Onboard Windows 10 machines using Group Policy</span></span>
    - <span data-ttu-id="31f56-168">使用 Microsoft Endpoint Configuration Manager 载入 Windows 10 计算机</span><span class="sxs-lookup"><span data-stu-id="31f56-168">Onboard Windows machines using Microsoft Endpoint Configuration Manager</span></span>
    - <span data-ttu-id="31f56-169">使用移动设备管理工具载入 Windows 10 计算机</span><span class="sxs-lookup"><span data-stu-id="31f56-169">Onboard Windows 10 machines using Mobile Device Management tools</span></span>
    - <span data-ttu-id="31f56-170">使用本地脚本载入 Windows 10 计算机</span><span class="sxs-lookup"><span data-stu-id="31f56-170">Onboard Windows 10 machines using a local script</span></span>
    - <span data-ttu-id="31f56-171">载入非持久性虚拟桌面基础结构 (VDI) 计算机。</span><span class="sxs-lookup"><span data-stu-id="31f56-171">Onboard non-persistent virtual desktop infrastructure (VDI) machines.</span></span>

<span data-ttu-id="31f56-172">完成操作并启用终结点后，它应该在设备列表中可见，并且还应开始向活动资源管理器报告审核活动日志。</span><span class="sxs-lookup"><span data-stu-id="31f56-172">Once done and endpoint is onboarded, it should be visible in the devices list and also start reporting audit activity logs to Activity explorer.</span></span>

> [!NOTE]
> <span data-ttu-id="31f56-173">此体验根据许可证强制实施。</span><span class="sxs-lookup"><span data-stu-id="31f56-173">This experience is under license enforcement.</span></span> <span data-ttu-id="31f56-174">如果没有所需的许可证，数据将不可见或不可访问。</span><span class="sxs-lookup"><span data-stu-id="31f56-174">Without the required license, data will not be visible or accessible.</span></span>

### <a name="with-devices-onboarded-into-mdatp"></a><span data-ttu-id="31f56-175">设备已载入 MDATP</span><span class="sxs-lookup"><span data-stu-id="31f56-175">With devices onboarded into MDATP</span></span>

<span data-ttu-id="31f56-176">在此方案中，已经部署了 MDATP，并且在其中报告了终结点。</span><span class="sxs-lookup"><span data-stu-id="31f56-176">In this scenario, MDATP is already deployed and there are endpoints reporting in.</span></span> <span data-ttu-id="31f56-177">所有这些终结点都将显示在托管设备列表中。</span><span class="sxs-lookup"><span data-stu-id="31f56-177">All these endpoints will appear in the managed devices list.</span></span> <span data-ttu-id="31f56-178">可通过使用[载入设备程序](endpoint-dlp-getting-started.md#onboarding-devices)将新设备继续载入到终结点 DLP 中，以扩展覆盖范围。</span><span class="sxs-lookup"><span data-stu-id="31f56-178">You can continue to onboard new devices into Endpoint DLP to expand coverage by using the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).</span></span>

1. <span data-ttu-id="31f56-179">打开“[Microsoft 合规中心](https://compliance.microsoft.com)”。</span><span class="sxs-lookup"><span data-stu-id="31f56-179">Open the [Microsoft compliance center](https://compliance.microsoft.com).</span></span>
2. <span data-ttu-id="31f56-180">打开合规中心设置页面，然后选择“**启用设备监视**”。</span><span class="sxs-lookup"><span data-stu-id="31f56-180">Open the Compliance Center settings page and choose **Enable device monitoring**.</span></span>
3. <span data-ttu-id="31f56-181">选择“**设备管理**”，以打开“**设备**”列表。</span><span class="sxs-lookup"><span data-stu-id="31f56-181">Choose **Device management** to open the **Devices** list.</span></span> <span data-ttu-id="31f56-182">你应该看到已经向 MDATP 报告的设备列表。</span><span class="sxs-lookup"><span data-stu-id="31f56-182">You should see the list of devices that are already reporting in to MDATP.</span></span> <span data-ttu-id="31f56-183">![设备管理](../media/endpoint-dlp-getting-started-2-device-management.png)</span><span class="sxs-lookup"><span data-stu-id="31f56-183">![device management](../media/endpoint-dlp-getting-started-2-device-management.png)</span></span>
4. <span data-ttu-id="31f56-184">如果需要载入附加设备，请选择“**载入**”。</span><span class="sxs-lookup"><span data-stu-id="31f56-184">Choose **Onboarding** if you need to onboard additional devices.</span></span>
5. <span data-ttu-id="31f56-185">从“**部署方法**”列表中选择要部署到这些额外设备的方式，然后**下载程序包**。</span><span class="sxs-lookup"><span data-stu-id="31f56-185">Choose the way you want to deploy to these additional devices from the **Deployment method** list and then **Download package**.</span></span>
6. <span data-ttu-id="31f56-186">按照[适用于 Windows 10 计算机的载入工具和方法](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)中的相应程序进行操作。</span><span class="sxs-lookup"><span data-stu-id="31f56-186">Follow the appropriate procedures in [Onboarding tools and methods for Windows 10 machines](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).</span></span> <span data-ttu-id="31f56-187">此链接会将你定位到登录页面，你可以在其中访问与在步骤 5 中选择的部署程序包相匹配的 MDATP 程序：</span><span class="sxs-lookup"><span data-stu-id="31f56-187">This link take you to a landing page where you can access MDATP procedures that match the deployment package you selected in step 5:</span></span>
    - <span data-ttu-id="31f56-188">使用组策略载入 Windows 10 计算机</span><span class="sxs-lookup"><span data-stu-id="31f56-188">Onboard Windows 10 machines using Group Policy</span></span>
    - <span data-ttu-id="31f56-189">使用 Microsoft Endpoint Configuration Manager 载入 Windows 10 计算机</span><span class="sxs-lookup"><span data-stu-id="31f56-189">Onboard Windows machines using Microsoft Endpoint Configuration Manager</span></span>
    - <span data-ttu-id="31f56-190">使用移动设备管理工具载入 Windows 10 计算机</span><span class="sxs-lookup"><span data-stu-id="31f56-190">Onboard Windows 10 machines using Mobile Device Management tools</span></span>
    - <span data-ttu-id="31f56-191">使用本地脚本载入 Windows 10 计算机</span><span class="sxs-lookup"><span data-stu-id="31f56-191">Onboard Windows 10 machines using a local script</span></span>
    - <span data-ttu-id="31f56-192">载入非持久性虚拟桌面基础结构 (VDI) 计算机。</span><span class="sxs-lookup"><span data-stu-id="31f56-192">Onboard non-persistent virtual desktop infrastructure (VDI) machines.</span></span>

<span data-ttu-id="31f56-193">完成操作并载入终结点后，它应该在“**设备**”表下可见，并且还应开始向**活动资源管理器**报告审核日志。</span><span class="sxs-lookup"><span data-stu-id="31f56-193">Once done and endpoint is onboarded, it should be visible under the **Devices** table and also start reporting audit logs to the **Activity Explorer**.</span></span>

> [!NOTE]
><span data-ttu-id="31f56-194">此体验根据许可证强制实施。</span><span class="sxs-lookup"><span data-stu-id="31f56-194">This experience is under license enforcement.</span></span> <span data-ttu-id="31f56-195">如果没有所需的许可证，数据将不可见或不可访问。</span><span class="sxs-lookup"><span data-stu-id="31f56-195">Without the required license, data will not be visible or accessible.</span></span>

### <a name="viewing-endpoint-dlp-data-in-activity-explorer"></a><span data-ttu-id="31f56-196">在活动资源管理器中查看终结点 DLP 数据</span><span class="sxs-lookup"><span data-stu-id="31f56-196">Viewing Endpoint DLP data in activity explorer</span></span>

1. <span data-ttu-id="31f56-197">在 Microsoft 365 合规中心中打开域的“[数据分类页面](https://compliance.microsoft.com/dataclassification?viewid=overview)”，然后选择“活动资源管理器”。</span><span class="sxs-lookup"><span data-stu-id="31f56-197">Open the [Data classification page](https://compliance.microsoft.com/dataclassification?viewid=overview) for your domain in the Microsoft 365 Compliance center and choose Activity explorer.</span></span>
2. <span data-ttu-id="31f56-198">请参考[活动资源管理器入门](data-classification-activity-explorer.md)中的程序，以访问和筛选终结点设备的所有数据。</span><span class="sxs-lookup"><span data-stu-id="31f56-198">Refer to the procedures in [Get started with Activity explorer](data-classification-activity-explorer.md) to access and filter all the data for your Endpoint devices.</span></span>

![终结点设备的活动资源管理器筛选器](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

## <a name="next-steps"></a><span data-ttu-id="31f56-200">后续步骤</span><span class="sxs-lookup"><span data-stu-id="31f56-200">Next steps</span></span>
<span data-ttu-id="31f56-201">现在，你已载入设备，并且可以在“活动资源管理器”中查看活动数据，那么就可以继续下一步，在其中创建保护敏感项目的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="31f56-201">Now that you have onboarded devices and can view the activity data in Activity explorer, you are ready to move on to your next step where you create DLP policies that protect your sensitive items.</span></span>

1) [<span data-ttu-id="31f56-202">使用终结点数据丢失防护（预览）</span><span class="sxs-lookup"><span data-stu-id="31f56-202">Using Endpoint data loss prevention (preview)</span></span>](endpoint-dlp-using.md)

## <a name="see-also"></a><span data-ttu-id="31f56-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31f56-203">See also</span></span>

- [<span data-ttu-id="31f56-204">了解终结点数据丢失防护（预览）</span><span class="sxs-lookup"><span data-stu-id="31f56-204">Learn about Endpoint data loss prevention (preview)</span></span>](endpoint-dlp-learn-about.md)
- [<span data-ttu-id="31f56-205">使用终结点数据丢失防护（预览）</span><span class="sxs-lookup"><span data-stu-id="31f56-205">Using Endpoint data loss prevention (preview)</span></span>](endpoint-dlp-using.md)
- [<span data-ttu-id="31f56-206">数据丢失防护概述</span><span class="sxs-lookup"><span data-stu-id="31f56-206">Overview of data loss prevention</span></span>](data-loss-prevention-policies.md)
- [<span data-ttu-id="31f56-207">创建、测试和优化 DLP 策略</span><span class="sxs-lookup"><span data-stu-id="31f56-207">Create, test, and tune a DLP policy</span></span>](create-test-tune-dlp-policy.md)
- [<span data-ttu-id="31f56-208">活动资源管理器入门</span><span class="sxs-lookup"><span data-stu-id="31f56-208">Get started with Activity explorer</span></span>](data-classification-activity-explorer.md)
- [<span data-ttu-id="31f56-209">Microsoft Defender 高级威胁防护 (Microsoft Defender ATP)</span><span class="sxs-lookup"><span data-stu-id="31f56-209">Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)</span></span>](https://docs.microsoft.com/windows/security/threat-protection/)
- [<span data-ttu-id="31f56-210">Windows 10 设备的装载工具和方法</span><span class="sxs-lookup"><span data-stu-id="31f56-210">Onboarding tools and methods for Windows 10 machines</span></span>](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [<span data-ttu-id="31f56-211">Microsoft 365 订阅</span><span class="sxs-lookup"><span data-stu-id="31f56-211">Microsoft 365 subscription</span></span>](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [<span data-ttu-id="31f56-212">已加入 Azure Active Directory (AAD)</span><span class="sxs-lookup"><span data-stu-id="31f56-212">Azure Active Directory (AAD) joined</span></span>](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-ad-join)
- [<span data-ttu-id="31f56-213">下载基于 Chromium 的新 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="31f56-213">Download the new Microsoft Edge based on Chromium</span></span>](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)