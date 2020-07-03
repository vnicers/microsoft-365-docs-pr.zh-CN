---
title: 在 Office 365 和 Office 365 GCC 中准备 TLS 1.2
description: 在停止对 TLS 1.0 和 1.1 的支持后，如何让 Office 365 和 Office 365 GCC 中的所有客户端-服务器和浏览器-服务器组合准备好使用 TLS 1.2。
author: simonxjx
manager: dcscontentpm
localization_priority: Normal
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: v-six
appliesto:
- Office 365 Business
ms.openlocfilehash: d3086c85adf76a322775ce53697504b77e672f9a
ms.sourcegitcommit: 51a9f34796535309b8ca8b52da92da0a3621327b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "45024814"
---
# <a name="preparing-for-tls-12-in-office-365-and-office-365-gcc"></a><span data-ttu-id="3eec8-103">在 Office 365 和 Office 365 GCC 中准备 TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="3eec8-103">Preparing for TLS 1.2 in Office 365 and Office 365 GCC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3eec8-104">世界正处于病毒大流行之中，Microsoft 意识到这对我们的客户和合作伙伴会有很大影响。</span><span class="sxs-lookup"><span data-stu-id="3eec8-104">The world is in the middle of a pandemic, and we at Microsoft are aware of the impact on our customers and partners.</span></span> <span data-ttu-id="3eec8-105">为了减轻商业客户的负担，我们暂时停止了 TLS 1.0 和 1.1 的任何强制弃用。</span><span class="sxs-lookup"><span data-stu-id="3eec8-105">To lighten the burden on our commercial customers, we have temporarily halted any deprecation enforcement of TLS 1.0 and 1.1.</span></span> <span data-ttu-id="3eec8-106">在当前危机稳定后，将基于修订后的时间表发送更新。</span><span class="sxs-lookup"><span data-stu-id="3eec8-106">An update will be sent on a revised timeline after the current crisis stabilizes.</span></span> <span data-ttu-id="3eec8-107">（本文经过修订以反映更改。）</span><span class="sxs-lookup"><span data-stu-id="3eec8-107">(This article is revised to reflect the change.)</span></span>

## <a name="summary"></a><span data-ttu-id="3eec8-108">摘要</span><span class="sxs-lookup"><span data-stu-id="3eec8-108">Summary</span></span>

<span data-ttu-id="3eec8-109">为了向我们的客户提供一流的加密，Microsoft 计划在 Office 365 和 Office 365 GCC 中弃用传输层安全 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="3eec8-109">To provide the best-in-class encryption to our customers, Microsoft plans to deprecate Transport Layer Security (TLS) versions 1.0 and 1.1 in Office 365 and Office 365 GCC.</span></span> <span data-ttu-id="3eec8-110">我们知道您的数据的安全性非常重要，并且我们承诺对可能影响使用 TLS 服务的更改保持透明公开。</span><span class="sxs-lookup"><span data-stu-id="3eec8-110">We understand that the security of your data is important, and we're committed to transparency about changes that may affect your use of the TLS service.</span></span>

<span data-ttu-id="3eec8-111">[Microsoft TLS 1.0 实现](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n)没有已知安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="3eec8-111">The [Microsoft TLS 1.0 implementation](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n) has no known security vulnerabilities.</span></span> <span data-ttu-id="3eec8-112">但是，由于未来的潜在协议降级攻击和其他 TLS 漏洞，我们将停止在 Microsoft Office 365 和 Office 365 GCC 中提供 TLS 1.0 和 1.1 支持。</span><span class="sxs-lookup"><span data-stu-id="3eec8-112">But because of the potential for future protocol downgrade attacks and other TLS vulnerabilities, we are discontinuing support for TLS 1.0 and 1.1 in Microsoft Office 365 and Office 365 GCC.</span></span>

<span data-ttu-id="3eec8-113">有关如何删除 TLS 1.0 和 1.1 依赖项的信息，请参阅以下白皮书：[解决 TLS 1.0 问题](https://www.microsoft.com/download/details.aspx?id=55266)。</span><span class="sxs-lookup"><span data-stu-id="3eec8-113">For information about how to remove TLS 1.0 and 1.1 dependencies, see the following white paper: [Solving the TLS 1.0 problem](https://www.microsoft.com/download/details.aspx?id=55266).</span></span>

## <a name="more-information"></a><span data-ttu-id="3eec8-114">更多信息</span><span class="sxs-lookup"><span data-stu-id="3eec8-114">More information</span></span>

<span data-ttu-id="3eec8-115">自 2020 年 1 月起，我们已经开始弃用 TLS 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="3eec8-115">We have already begun deprecation of TLS 1.0 and 1.1 as of January 2020.</span></span> <span data-ttu-id="3eec8-116">不支持通过 TLS 1.0 或 1.1 在我们的 DoD 或 GCC High 实例中连接到 Office 365 的任何客户端、设备或服务。</span><span class="sxs-lookup"><span data-stu-id="3eec8-116">Any clients, devices, or services that connect to Office 365 through TLS 1.0 or 1.1 in our DoD or GCC High instances are unsupported.</span></span> <span data-ttu-id="3eec8-117">对于我们的 Office 365 商业客户，我们将停止 TLS 1.0 和 1.1 的任何强制弃用，直到有关 COVID-19 的情况稳定下来。</span><span class="sxs-lookup"><span data-stu-id="3eec8-117">For our commercial customers of Office 365, we will halt any deprecation enforcement of TLS 1.0 and 1.1 until the situation regarding COVID-19 stabilizes.</span></span>

<span data-ttu-id="3eec8-118">我们建议所有客户端-服务器和浏览器-服务器组合使用 TLS1.2（或更高版本）以保持与 Office 365 服务的连接。</span><span class="sxs-lookup"><span data-stu-id="3eec8-118">We recommend that all client-server and browser-server combinations use TLS 1.2 (or a later version) in order to maintain connection to Office 365 services.</span></span> <span data-ttu-id="3eec8-119">你可能必须更新某些客户端-服务器和浏览器-服务器组合。</span><span class="sxs-lookup"><span data-stu-id="3eec8-119">You might have to update certain client-server and browser-server combinations.</span></span>

<span data-ttu-id="3eec8-120">以下是已知的无法使用 TLS 1.2 的客户端。</span><span class="sxs-lookup"><span data-stu-id="3eec8-120">The following clients are known to be unable to use TLS 1.2.</span></span> <span data-ttu-id="3eec8-121">更新这些客户端以确保对服务的访问不会间断。</span><span class="sxs-lookup"><span data-stu-id="3eec8-121">Update these clients to ensure uninterrupted access to the service.</span></span>

- <span data-ttu-id="3eec8-122">Android 4.3 和更低的版本</span><span class="sxs-lookup"><span data-stu-id="3eec8-122">Android 4.3 and earlier versions</span></span>
- <span data-ttu-id="3eec8-123">Firefox 版本 5.0 及更低版本</span><span class="sxs-lookup"><span data-stu-id="3eec8-123">Firefox version 5.0 and earlier versions</span></span>
- <span data-ttu-id="3eec8-124">Windows 7 上的 Internet Explorer 8-10 及更早版本</span><span class="sxs-lookup"><span data-stu-id="3eec8-124">Internet Explorer 8-10 on Windows 7 and earlier versions</span></span>
- <span data-ttu-id="3eec8-125">Windows Phone 8 上的 Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="3eec8-125">Internet Explorer 10 on Windows Phone 8</span></span>
- <span data-ttu-id="3eec8-126">Safari 6.0.4/OS X10.8.4 及更早版本</span><span class="sxs-lookup"><span data-stu-id="3eec8-126">Safari 6.0.4/OS X10.8.4 and earlier versions</span></span>

### <a name="tls-12-for-microsoft-teams-rooms-and-surface-hub"></a><span data-ttu-id="3eec8-127">适用于 Microsoft Teams Rooms 和 Surface Hub 的 TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="3eec8-127">TLS 1.2 for Microsoft Teams Rooms and Surface Hub</span></span>

<span data-ttu-id="3eec8-128">自 2018 年 12 月以来，Microsoft Teams Room（以前称为 Skype Room System V2 SRS V2）就一直支持 TLS 1.2。</span><span class="sxs-lookup"><span data-stu-id="3eec8-128">Microsoft Teams Rooms (previously known as Skype Room System V2 SRS V2) have supported TLS 1.2 since December 2018.</span></span> <span data-ttu-id="3eec8-129">我们建议 Room 设备安装 Microsoft Teams Rooms 应用版本 4.0.64.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="3eec8-129">We recommend that Rooms devices have Microsoft Teams Rooms app version 4.0.64.0 or later installed.</span></span> <span data-ttu-id="3eec8-130">有关更多信息，请参阅[发行说明](https://docs.microsoft.com/microsoftteams/room-systems/srs2-release-note)。</span><span class="sxs-lookup"><span data-stu-id="3eec8-130">For more information, see the [Release notes](https://docs.microsoft.com/microsoftteams/room-systems/srs2-release-note).</span></span> <span data-ttu-id="3eec8-131">更改是向后和向前兼容的。</span><span class="sxs-lookup"><span data-stu-id="3eec8-131">The changes are backward and forward compatible.</span></span>

<span data-ttu-id="3eec8-132">2019 年 5 月，Surface Hub 发布了 TLS 1.2 支持。</span><span class="sxs-lookup"><span data-stu-id="3eec8-132">Surface Hub released TLS 1.2 support in May 2019.</span></span>

<span data-ttu-id="3eec8-133">对 Microsoft Teams Rooms 和 Surface Hub 产品的 TLS 1.2 支持还要求更改以下服务器端代码：</span><span class="sxs-lookup"><span data-stu-id="3eec8-133">TLS 1.2 support for Microsoft Teams Rooms and Surface Hub products also requires the following server-side code changes:</span></span>

- <span data-ttu-id="3eec8-134">Skype for Business Online 服务器更改已于 2019 年 4 月上线。</span><span class="sxs-lookup"><span data-stu-id="3eec8-134">Skype for Business Online server changes were made live in April 2019.</span></span> <span data-ttu-id="3eec8-135">现在，Skype for Business Online 支持使用 TLS 1.2 连接 Microsoft Teams Room 和 Surface Hub 设备。</span><span class="sxs-lookup"><span data-stu-id="3eec8-135">Now, Skype for Business Online supports connecting Microsoft Teams Rooms and Surface Hub devices by using TLS 1.2.</span></span>
- <span data-ttu-id="3eec8-136">Skype for Business Server 客户必须安装累积更新 (CU) 才能对 Teams Rooms Systems 和 Surface Hub 使用 TLS 1.2。</span><span class="sxs-lookup"><span data-stu-id="3eec8-136">Skype for Business Server customers must install a cumulative update (CU) to use TLS 1.2 for Teams Rooms Systems and Surface Hub.</span></span>

  - <span data-ttu-id="3eec8-137">对于 Skype for Business Server 2015，CU9 已于 2019 年 5 月发布。</span><span class="sxs-lookup"><span data-stu-id="3eec8-137">For Skype for Business Server 2015, CU9 is already released in May 2019.</span></span>
  - <span data-ttu-id="3eec8-138">对于 Skype for Business Server 2019，CU1 先前计划于 2019 年 4 月发布，但推迟到 2019 年 6 月。</span><span class="sxs-lookup"><span data-stu-id="3eec8-138">For Skype for Business Server 2019, CU1 was previously planned for April 2019 but is delayed to June 2019.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3eec8-139">在为 Skype for Business Server 安装特定的 CU 之前，Skype for Business 本地客户不应禁用 TLS 1.0 / 1.1。</span><span class="sxs-lookup"><span data-stu-id="3eec8-139">Skype for Business on-premises customers should not disable TLS 1.0/1.1 before installing specific CUs for Skype for Business Server.</span></span>

<span data-ttu-id="3eec8-140">如果您正在使用混合式场景的本地基础架构或 Active Directory 联合身份验证服务，确保该基础架构同时支持使用 TLS 1.2 的进站和出站连接。</span><span class="sxs-lookup"><span data-stu-id="3eec8-140">If you are using any on-premises infrastructure for hybrid scenarios or Active Directory Federation Services, make sure that the infrastructure can support both inbound and outbound connections that use TLS 1.2.</span></span>

## <a name="references"></a><span data-ttu-id="3eec8-141">参考</span><span class="sxs-lookup"><span data-stu-id="3eec8-141">References</span></span>

<span data-ttu-id="3eec8-142">以下资源提供帮助确保客户端正在使用 TLS 1.2 或更高版本及禁用 TLS 1.0 和 1.1 的指导。</span><span class="sxs-lookup"><span data-stu-id="3eec8-142">The following resources provide guidance to help make sure that your clients are using TLS 1.2 or a later version and to disable TLS 1.0 and 1.1.</span></span>

- <span data-ttu-id="3eec8-143">对于连接到 Office 365 的 Windows 7 客户端，请确保 TLS 1.2 是 Windows WinHTTP 中的默认安全协议。</span><span class="sxs-lookup"><span data-stu-id="3eec8-143">For Windows 7 clients that connect to Office 365, make sure that TLS 1.2 is the default secure protocol in WinHTTP in Windows.</span></span> <span data-ttu-id="3eec8-144">有关更多信息，请参阅 [KB 3140245 - 更新以在 Windows 的 WinHTTP 中启用 TLS 1.1 和 TLS 1.2 作为默认安全协议](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in)。</span><span class="sxs-lookup"><span data-stu-id="3eec8-144">For more information see [KB 3140245 - Update to enable TLS 1.1 and TLS 1.2 as a default secure protocols in WinHTTP in Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).</span></span>
- <span data-ttu-id="3eec8-145">要通过删除 TLS 1.0 和 1.1 依赖项解决 TLS 使用弱点问题，请参阅 [Microsoft TLS 1.2 支持](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/)。</span><span class="sxs-lookup"><span data-stu-id="3eec8-145">To start addressing weak TLS use by removing TLS 1.0 and 1.1 dependencies, see [TLS 1.2 support at Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).</span></span>
- <span data-ttu-id="3eec8-146">[新的 IIS 功能](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/)可更加方便地在 [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) 和 [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) 上查找通过使用弱安全协议连接服务的客户端。</span><span class="sxs-lookup"><span data-stu-id="3eec8-146">[New IIS functionality](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) makes it easier to find clients on [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) and [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) that connect to the service by using weak security protocols.</span></span>
- <span data-ttu-id="3eec8-147">获取有关如何 [解决 TLS 1.0 问题](https://www.microsoft.com/download/details.aspx?id=55266)的更多信息。</span><span class="sxs-lookup"><span data-stu-id="3eec8-147">Get more information about how to [solve the TLS 1.0 problem](https://www.microsoft.com/download/details.aspx?id=55266).</span></span>
- <span data-ttu-id="3eec8-148">有关安全性方法的一般信息，请转到[Office 365 信任中心](https://www.microsoft.com/trustcenter/cloudservices/office365)。</span><span class="sxs-lookup"><span data-stu-id="3eec8-148">For general information about our approach to security, go to the [Office 365 Trust Center](https://www.microsoft.com/trustcenter/cloudservices/office365).</span></span>
- [<span data-ttu-id="3eec8-149">准备 TLS 1.0/1.1 弃用 - Office 365 Skype for Business</span><span class="sxs-lookup"><span data-stu-id="3eec8-149">Preparing for TLS 1.0/1.1 Deprecation - Office 365 Skype for Business</span></span>](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [<span data-ttu-id="3eec8-150">Exchange Server TLS 指南，第 1 部分：为 TLS 1.2 做好准备</span><span class="sxs-lookup"><span data-stu-id="3eec8-150">Exchange Server TLS guidance, part 1: Getting Ready for TLS 1.2</span></span>](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [<span data-ttu-id="3eec8-151">Exchange Server TLS 指南，第 2 部分：启用 TLS 1.2 并识别不使用它的客户端</span><span class="sxs-lookup"><span data-stu-id="3eec8-151">Exchange Server TLS guidance Part 2: Enabling TLS 1.2 and Identifying Clients Not Using It</span></span>](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [<span data-ttu-id="3eec8-152">Exchange Server TLS 指南，第 3 部分：关闭 TLS 1.0/1.1</span><span class="sxs-lookup"><span data-stu-id="3eec8-152">Exchange Server TLS guidance Part 3: Turning Off TLS 1.0/1.1</span></span>](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [<span data-ttu-id="3eec8-153">在 Office Online Server 中启用 TLS 1.1 和 TLS 1.2 支持</span><span class="sxs-lookup"><span data-stu-id="3eec8-153">Enable TLS 1.1 and TLS 1.2 support in Office Online Server</span></span>](https://docs.microsoft.com/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)