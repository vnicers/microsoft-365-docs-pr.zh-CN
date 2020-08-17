---
title: Microsoft 365 拒绝服务防护策略
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 在本文中，您可以找到针对拒绝服务 (DoS) 攻击的 Microsoft 防护策略的概述。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f28f7bcb9c6241404c8101bffe7268c5a1917ffa
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46688062"
---
# <a name="microsoft-365-denial-of-service-defense-strategy"></a><span data-ttu-id="b1917-103">Microsoft 365 拒绝服务防护策略</span><span class="sxs-lookup"><span data-stu-id="b1917-103">Microsoft 365 denial-of-service defense strategy</span></span>

<span data-ttu-id="b1917-104">Microsoft 针对基于网络的拒绝服务的策略防御 (DoS) 攻击因规模和全球占用量而独特。</span><span class="sxs-lookup"><span data-stu-id="b1917-104">Microsoft's strategy to defend against network-based denial-of-service (DoS) attacks is unique due to our scale and global footprint.</span></span> <span data-ttu-id="b1917-105">此扩展使 Microsoft 能够利用策略和技术（组织、提供商或客户组织）可以与之相匹配。</span><span class="sxs-lookup"><span data-stu-id="b1917-105">This scale allows Microsoft to utilize strategies and techniques few organizations, providers, or customer organizations can match.</span></span> <span data-ttu-id="b1917-106">DoS 策略的基础是我们的全球状态。</span><span class="sxs-lookup"><span data-stu-id="b1917-106">The cornerstone of the DoS strategy is our global presence.</span></span> <span data-ttu-id="b1917-107">Microsoft 与 Internet 提供商（对等提供商） (公共和私有) ，以及世界各地的专用公司。</span><span class="sxs-lookup"><span data-stu-id="b1917-107">Microsoft engages with Internet providers, peering providers (public and private), and private corporations all over the world.</span></span> <span data-ttu-id="b1917-108">这为 Microsoft 提供了很大的 Internet 状态，使 Microsoft 能够吸收跨大型 surface 区域的攻击。</span><span class="sxs-lookup"><span data-stu-id="b1917-108">This gives Microsoft a significant Internet presence and enables Microsoft to absorb attacks across a large surface area.</span></span>

<span data-ttu-id="b1917-109">由于这种独特的特点，Microsoft 使用不同于大型企业使用的检测和缓解过程。</span><span class="sxs-lookup"><span data-stu-id="b1917-109">Given this unique nature, Microsoft uses detection and mitigation processes that differ from ones used by large enterprises.</span></span> <span data-ttu-id="b1917-110">该策略基于多个网络边缘的检测和全局分布式缓解的分离。</span><span class="sxs-lookup"><span data-stu-id="b1917-110">The strategy is based on a separation of detection and global distributed mitigation through many network edges.</span></span> <span data-ttu-id="b1917-111">许多企业使用第三方解决方案来检测和缓解边缘的攻击。</span><span class="sxs-lookup"><span data-stu-id="b1917-111">Many enterprises use third-party solutions to detect and mitigate attacks at the edge.</span></span> <span data-ttu-id="b1917-112">随着 Microsoft 的边缘容量增长，它会清楚对单个或特定边缘的任何攻击的重要性。</span><span class="sxs-lookup"><span data-stu-id="b1917-112">As the edge capacity for Microsoft grew, it became clear the significance of any attack against individual or particular edges was low.</span></span> <span data-ttu-id="b1917-113">由于这种独特的配置，Microsoft 将检测和缓解组件分开。</span><span class="sxs-lookup"><span data-stu-id="b1917-113">Because of this unique configuration, Microsoft separated the detection and mitigation components.</span></span> <span data-ttu-id="b1917-114">Microsoft 部署多层检测系统，以检测更接近其饱和点的攻击，同时在边缘维护全局缓解。</span><span class="sxs-lookup"><span data-stu-id="b1917-114">Microsoft deploys multi-tiered detection systems to detect attacks closer to their saturation points while maintaining global mitigation at the edge.</span></span> <span data-ttu-id="b1917-115">此策略可确保我们可以同时处理多个并发攻击。</span><span class="sxs-lookup"><span data-stu-id="b1917-115">This strategy ensures we can handle multiple simultaneous attacks.</span></span>

<span data-ttu-id="b1917-116">Microsoft 对 DoS 攻击所采用的最有效和低成本的防护之一是减少服务攻击面。</span><span class="sxs-lookup"><span data-stu-id="b1917-116">One of the most effective and low-cost defenses employed by Microsoft against DoS attacks is reducing service attack surfaces.</span></span> <span data-ttu-id="b1917-117">不需要的流量会在网络边缘断开，而无需对数据进行直接分析、处理和清理。</span><span class="sxs-lookup"><span data-stu-id="b1917-117">Unwanted traffic is dropped at the network edge instead of analyzing, processing, and scrubbing the data inline.</span></span>

<span data-ttu-id="b1917-118">在与公用网络的接口上，Microsoft 使用专用安全设备进行防火墙、网络地址转换和 IP 筛选功能。</span><span class="sxs-lookup"><span data-stu-id="b1917-118">At the interface with the public network, Microsoft uses special-purpose security devices for firewall, network address translation, and IP filtering functions.</span></span> <span data-ttu-id="b1917-119">Microsoft 还使用全局同等成本多路径 (ECMP) 路由。</span><span class="sxs-lookup"><span data-stu-id="b1917-119">Microsoft also uses global equal-cost multi-path (ECMP) routing.</span></span> <span data-ttu-id="b1917-120">全局 ECMP 路由是一个网络框架，可确保有多个用于访问服务的全局路径。</span><span class="sxs-lookup"><span data-stu-id="b1917-120">Global ECMP routing is a network framework to ensure that there are multiple global paths to reach a service.</span></span> <span data-ttu-id="b1917-121">使用这些多路径，针对服务的攻击仅限于攻击源自的地区。</span><span class="sxs-lookup"><span data-stu-id="b1917-121">With these multiple paths, attacks against services are limited to the region from which the attack originates.</span></span> <span data-ttu-id="b1917-122">其他区域应受到此攻击的影响，因为最终用户将使用其他路径到达这些区域中的服务。</span><span class="sxs-lookup"><span data-stu-id="b1917-122">Other regions should be unaffected by this attack, as end users would use other paths to reach the service in those regions.</span></span> <span data-ttu-id="b1917-123">Microsoft 还开发了内部 DoS 关联和检测系统，它们使用流数据、性能指标和其他信息。</span><span class="sxs-lookup"><span data-stu-id="b1917-123">Microsoft has also developed internal DoS correlation and detection systems that use flow data, performance metrics, and other information.</span></span> <span data-ttu-id="b1917-124">这是 Microsoft Azure 中的超大型云服务，它将分析从 Microsoft 网络和服务上的各个点收集的数据。</span><span class="sxs-lookup"><span data-stu-id="b1917-124">This is a hyperscale cloud service in Microsoft Azure, which analyzes data collected from various points on Microsoft networks and services.</span></span> <span data-ttu-id="b1917-125">跨工作负载 DoS 事件响应团队确定团队中的角色和职责、升级条件以及用于参与各种团队和事件处理的协议。</span><span class="sxs-lookup"><span data-stu-id="b1917-125">A cross-workload DoS incident response team identifies the roles and responsibilities across teams, the criteria for escalations, and the protocols for engaging various teams and for incident handling.</span></span> <span data-ttu-id="b1917-126">这些解决方案针对 DoS 攻击提供了基于网络的保护。</span><span class="sxs-lookup"><span data-stu-id="b1917-126">These solutions provide network-based protection against DoS attacks.</span></span>

<span data-ttu-id="b1917-127">最后，基于云的工作负载根据其协议和带宽使用情况配置优化的阈值，以唯一保护该工作负载。</span><span class="sxs-lookup"><span data-stu-id="b1917-127">Finally, cloud-based workloads are configured with optimized thresholds based on their protocol and bandwidth usage needs to uniquely protect that workload.</span></span>