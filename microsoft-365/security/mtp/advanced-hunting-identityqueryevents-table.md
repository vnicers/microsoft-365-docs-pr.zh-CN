---
title: 高级搜寻架构中的 IdentityQueryEvents 表
description: 了解高级搜寻架构的 IdentityQueryEvents 表中的 Active Directory 查询事件
keywords: 高级搜寻、威胁搜寻、网络威胁搜寻、microsoft 威胁防护、microsoft 365、mtp、m365、搜索、查询、遥测、架构参考、kusto、表、列、数据类型、说明、IdentityQueryEvents、Azure AD、Active Directory、AzureATP、标识、LDAP 查询
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: b2fc94d6ac6606c97b4824bc556b7299a2bd8ec7
ms.sourcegitcommit: 3b2fdf159d7dd962493a3838e3cf0cf429ee2bf2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "42929109"
---
# <a name="identityqueryevents"></a><span data-ttu-id="d0cbf-104">IdentityQueryEvents</span><span class="sxs-lookup"><span data-stu-id="d0cbf-104">IdentityQueryEvents</span></span>

<span data-ttu-id="d0cbf-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="d0cbf-105">**Applies to:**</span></span>
- <span data-ttu-id="d0cbf-106">Microsoft 威胁防护</span><span class="sxs-lookup"><span data-stu-id="d0cbf-106">Microsoft Threat Protection</span></span>

<span data-ttu-id="d0cbf-107">`IdentityQueryEvents` [高级搜寻](advanced-hunting-overview.md)架构中的表包含针对 Active Directory 对象（如用户、组、设备和域）执行的查询的相关信息。</span><span class="sxs-lookup"><span data-stu-id="d0cbf-107">The `IdentityQueryEvents` table in the [advanced hunting](advanced-hunting-overview.md) schema contains information about queries performed against Active Directory objects, such as users, groups, devices, and domains.</span></span> <span data-ttu-id="d0cbf-108">使用此参考来构建从此表返回信息的查询。</span><span class="sxs-lookup"><span data-stu-id="d0cbf-108">Use this reference to construct queries that return information from this table.</span></span>

<span data-ttu-id="d0cbf-109">有关高级搜寻架构中其他表的信息，请[参阅高级搜寻参考](advanced-hunting-schema-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="d0cbf-109">For information on other tables in the advanced hunting schema, [see the advanced hunting reference](advanced-hunting-schema-tables.md).</span></span>

| <span data-ttu-id="d0cbf-110">列名称</span><span class="sxs-lookup"><span data-stu-id="d0cbf-110">Column name</span></span> | <span data-ttu-id="d0cbf-111">数据类型</span><span class="sxs-lookup"><span data-stu-id="d0cbf-111">Data type</span></span> | <span data-ttu-id="d0cbf-112">说明</span><span class="sxs-lookup"><span data-stu-id="d0cbf-112">Description</span></span> |
|-------------|-----------|-------------|
| `Timestamp` | <span data-ttu-id="d0cbf-113">datetime</span><span class="sxs-lookup"><span data-stu-id="d0cbf-113">datetime</span></span> | <span data-ttu-id="d0cbf-114">记录事件的日期和时间</span><span class="sxs-lookup"><span data-stu-id="d0cbf-114">Date and time when the event was recorded</span></span> |
| `ActionType` | <span data-ttu-id="d0cbf-115">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-115">string</span></span> | <span data-ttu-id="d0cbf-116">触发事件的活动类型</span><span class="sxs-lookup"><span data-stu-id="d0cbf-116">Type of activity that triggered the event</span></span> |
| `Application` | <span data-ttu-id="d0cbf-117">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-117">string</span></span> | <span data-ttu-id="d0cbf-118">执行录制操作的应用程序</span><span class="sxs-lookup"><span data-stu-id="d0cbf-118">Application that performed the recorded action</span></span> |
| `Query` | <span data-ttu-id="d0cbf-119">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-119">string</span></span> | <span data-ttu-id="d0cbf-120">查询类型： QueryGroup、QueryUser 或 EnumerateUsers</span><span class="sxs-lookup"><span data-stu-id="d0cbf-120">Type of query: QueryGroup, QueryUser, or EnumerateUsers</span></span> |
| `QueryObject` | <span data-ttu-id="d0cbf-121">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-121">string</span></span> | <span data-ttu-id="d0cbf-122">要查询的用户、组、设备、域或任何其他实体类型的名称</span><span class="sxs-lookup"><span data-stu-id="d0cbf-122">Name of the user, group, device, domain, or any other entity type being queried</span></span> |
| `Protocol` | <span data-ttu-id="d0cbf-123">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-123">string</span></span> | <span data-ttu-id="d0cbf-124">通信过程中使用的协议</span><span class="sxs-lookup"><span data-stu-id="d0cbf-124">Protocol used during the communication</span></span> |
| `AccountName` | <span data-ttu-id="d0cbf-125">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-125">string</span></span> | <span data-ttu-id="d0cbf-126">帐户的用户名</span><span class="sxs-lookup"><span data-stu-id="d0cbf-126">User name of the account</span></span> |
| `AccountDomain` | <span data-ttu-id="d0cbf-127">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-127">string</span></span> | <span data-ttu-id="d0cbf-128">帐户的域</span><span class="sxs-lookup"><span data-stu-id="d0cbf-128">Domain of the account</span></span> |
| `AccountUpn` | <span data-ttu-id="d0cbf-129">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-129">string</span></span> | <span data-ttu-id="d0cbf-130">帐户的用户主体名称（UPN）</span><span class="sxs-lookup"><span data-stu-id="d0cbf-130">User principal name (UPN) of the account</span></span> |
| `AccountSid` | <span data-ttu-id="d0cbf-131">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-131">string</span></span> | <span data-ttu-id="d0cbf-132">帐户的安全标识符（SID）</span><span class="sxs-lookup"><span data-stu-id="d0cbf-132">Security Identifier (SID) of the account</span></span> |
| `AccountObjectId` | <span data-ttu-id="d0cbf-133">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-133">string</span></span> | <span data-ttu-id="d0cbf-134">Azure AD 中的帐户的唯一标识符</span><span class="sxs-lookup"><span data-stu-id="d0cbf-134">Unique identifier for the account in Azure AD</span></span> |
| `AccountDisplayName` | <span data-ttu-id="d0cbf-135">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-135">string</span></span> | <span data-ttu-id="d0cbf-136">通讯簿中显示的帐户用户的名称。</span><span class="sxs-lookup"><span data-stu-id="d0cbf-136">Name of the account user displayed in the address book.</span></span> <span data-ttu-id="d0cbf-137">通常是给定的或名的名称、中间初始名称和姓氏的组合。</span><span class="sxs-lookup"><span data-stu-id="d0cbf-137">Typically a combination of a given or first name, a middle initiation, and a last name or surname.</span></span> |
| `DeviceName` | <span data-ttu-id="d0cbf-138">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-138">string</span></span> | <span data-ttu-id="d0cbf-139">终结点的完全限定的域名（FQDN）</span><span class="sxs-lookup"><span data-stu-id="d0cbf-139">Fully qualified domain name (FQDN) of the endpoint</span></span> |
| `IPAddress` | <span data-ttu-id="d0cbf-140">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-140">string</span></span> | <span data-ttu-id="d0cbf-141">分配给终结点的 IP 地址，并在相关的网络通信过程中使用</span><span class="sxs-lookup"><span data-stu-id="d0cbf-141">IP address assigned to the endpoint and used during related network communications</span></span> |
| `Location` | <span data-ttu-id="d0cbf-142">string</span><span class="sxs-lookup"><span data-stu-id="d0cbf-142">string</span></span> | <span data-ttu-id="d0cbf-143">与事件关联的城市、国家或其他地理位置</span><span class="sxs-lookup"><span data-stu-id="d0cbf-143">City, country, or other geographic location associated with the event</span></span> |

## <a name="related-topics"></a><span data-ttu-id="d0cbf-144">相关主题</span><span class="sxs-lookup"><span data-stu-id="d0cbf-144">Related topics</span></span>
- [<span data-ttu-id="d0cbf-145">主动搜寻威胁</span><span class="sxs-lookup"><span data-stu-id="d0cbf-145">Proactively hunt for threats</span></span>](advanced-hunting-overview.md)
- [<span data-ttu-id="d0cbf-146">了解查询语言</span><span class="sxs-lookup"><span data-stu-id="d0cbf-146">Learn the query language</span></span>](advanced-hunting-query-language.md)
- [<span data-ttu-id="d0cbf-147">使用共享查询</span><span class="sxs-lookup"><span data-stu-id="d0cbf-147">Use shared queries</span></span>](advanced-hunting-shared-queries.md)
- [<span data-ttu-id="d0cbf-148">跨设备和电子邮件搜寻威胁</span><span class="sxs-lookup"><span data-stu-id="d0cbf-148">Hunt for threats across devices and emails</span></span>](advanced-hunting-query-emails-devices.md)
- [<span data-ttu-id="d0cbf-149">了解架构</span><span class="sxs-lookup"><span data-stu-id="d0cbf-149">Understand the schema</span></span>](advanced-hunting-schema-tables.md)
- [<span data-ttu-id="d0cbf-150">应用查询最佳做法</span><span class="sxs-lookup"><span data-stu-id="d0cbf-150">Apply query best practices</span></span>](advanced-hunting-best-practices.md)