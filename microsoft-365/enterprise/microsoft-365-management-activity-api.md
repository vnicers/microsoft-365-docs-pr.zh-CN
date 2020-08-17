---
title: Office 365 管理活动 API
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-analytics
f1.keywords:
- NOCSH
description: 在本文中，您可以找到有关 Office 365 管理活动 API 的简要摘要以及它在活动日志中提供的信息。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ea08673f4c26c9ee4b7093ba420b69bed91abc81
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46688063"
---
# <a name="office-365-management-activity-api"></a><span data-ttu-id="1270a-103">Office 365 管理活动 API</span><span class="sxs-lookup"><span data-stu-id="1270a-103">Office 365 Management Activity API</span></span>

<span data-ttu-id="1270a-104">Microsoft 提供了可用于获取有关 Office 365 租户的聚合事务性信息的 reporting services。</span><span class="sxs-lookup"><span data-stu-id="1270a-104">Microsoft provides reporting services you can use to obtain aggregated transactional information about your Office 365 tenant.</span></span> <span data-ttu-id="1270a-105">[Office 365 管理活动 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview#office-365-management-activity-api)使用行业标准的 RESTful 设计和 OAuth v2 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1270a-105">The [Office 365 Management Activity API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview#office-365-management-activity-api) uses an industry-standard RESTful design and OAuth v2 for authentication.</span></span> <span data-ttu-id="1270a-106">这使您可以轻松开始体验检索数据，并将数据 ingesting 到可视化工具和应用程序中。</span><span class="sxs-lookup"><span data-stu-id="1270a-106">This makes it easy to start experimenting with retrieving data and ingesting it into visualization tools and applications.</span></span> <span data-ttu-id="1270a-107">API 提供了包含 Office 365 中的用户、管理员、操作和安全活动的信息的数据源。</span><span class="sxs-lookup"><span data-stu-id="1270a-107">The API provides a data feed with information about user, administrator, operations, and security activity in Office 365.</span></span> <span data-ttu-id="1270a-108">数据可出于法规目的而保留，也可与本地基础结构或其他源中的日志数据采购相结合。</span><span class="sxs-lookup"><span data-stu-id="1270a-108">The data can be kept for regulatory purposes, or combined with log data procured from an on-premises infrastructure or other sources.</span></span> <span data-ttu-id="1270a-109">这有助于在整个企业中构建针对运营、安全性和合规性的监控解决方案。</span><span class="sxs-lookup"><span data-stu-id="1270a-109">This helps build a monitoring solution for operations, security, and compliance across the enterprise.</span></span>

<span data-ttu-id="1270a-110">使用 Office 365 管理活动 API，可从 Office 365 和 Azure Active Directory 活动日志中获取各个用户、管理员、系统以及策略操作和事件的相关信息。</span><span class="sxs-lookup"><span data-stu-id="1270a-110">The Office 365 Management Activity API provides information about various user, admin, system, and policy actions and events from Office 365 and Azure Active Directory activity logs.</span></span> <span data-ttu-id="1270a-111">API 提供了一致的审核架构，其中10个以上的字段在所有服务中都很常见。</span><span class="sxs-lookup"><span data-stu-id="1270a-111">The API provides a consistent audit schema with over 10 fields common across all the services.</span></span> <span data-ttu-id="1270a-112">API 使组织能够在事件之间建立轻松的连接，并启用了新的方法来对数据进行原因。</span><span class="sxs-lookup"><span data-stu-id="1270a-112">The API allows organizations to make easy connections between events, and enables new ways to reason over the data.</span></span>

<span data-ttu-id="1270a-113">许多独立的软件供应商 (Isv) 与 Microsoft 合作，并具有基于 API 的构建解决方案。</span><span class="sxs-lookup"><span data-stu-id="1270a-113">Dozens of Independent Software Vendors (ISVs) partnered with Microsoft and have built solutions based on the API.</span></span> <span data-ttu-id="1270a-114">一些解决方案仅重点关注 Office 365 数据和来自多个云提供商和本地系统的其他源数据，以创建与操作、安全性和合规性相关的活动的统一视图。</span><span class="sxs-lookup"><span data-stu-id="1270a-114">Some solutions focus solely on Office 365 data and others source data from multiple cloud providers and on-premises systems to create a unified view of operations, security, and compliance-related activity.</span></span> 

<span data-ttu-id="1270a-115">有关详细信息，请参阅 [Office 365 管理活动 API 参考](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)。</span><span class="sxs-lookup"><span data-stu-id="1270a-115">For more information, see the [Office 365 Management Activity API reference](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference).</span></span>