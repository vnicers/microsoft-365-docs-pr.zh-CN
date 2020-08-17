---
title: 使用 PowerShell 查看已授权和未授权的 Microsoft 365 用户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/21/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 本文介绍如何使用 PowerShell 查看已授权和未授权的 Microsoft 365 用户帐户。
ms.openlocfilehash: 8a99ba2a80f1d814ec5268c4f8f479837eb54dc0
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687764"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a><span data-ttu-id="1ddcb-103">使用 PowerShell 查看已授权和未授权的 Microsoft 365 用户</span><span class="sxs-lookup"><span data-stu-id="1ddcb-103">View licensed and unlicensed Microsoft 365 users with PowerShell</span></span>

<span data-ttu-id="1ddcb-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="1ddcb-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1ddcb-105">Microsoft 365 组织中的用户帐户可能会从组织中提供的许可计划中为其分配一些、全部或无可用许可证。</span><span class="sxs-lookup"><span data-stu-id="1ddcb-105">User accounts in your Microsoft 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization.</span></span> <span data-ttu-id="1ddcb-106">可以使用适用于 Microsoft 365 的 PowerShell 快速查找组织中已授权和未授权的用户。</span><span class="sxs-lookup"><span data-stu-id="1ddcb-106">You can use PowerShell for Microsoft 365 to quickly find the licensed and unlicensed users in your organization.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1ddcb-107">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ddcb-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1ddcb-108">首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="1ddcb-108">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="1ddcb-109">若要查看组织中尚未向其分配任何许可计划的所有用户帐户的列表 (未经许可的用户) ，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="1ddcb-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="1ddcb-110">若要查看组织中已向其分配了任何许可计划的所有用户帐户的列表 (许可用户) ，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="1ddcb-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
><span data-ttu-id="1ddcb-111">若要列出订阅中的所有用户，请使用 `Get-AzureAdUser -All $true` 命令。</span><span class="sxs-lookup"><span data-stu-id="1ddcb-111">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1ddcb-112">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="1ddcb-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1ddcb-113">首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="1ddcb-113">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="1ddcb-114">若要查看组织中所有用户帐户及其授权状态的列表，请在 PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="1ddcb-114">To view the list of all user accounts and their licensing status in your organization, run the following command in PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

>[!Note]
><span data-ttu-id="1ddcb-115">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="1ddcb-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="1ddcb-116">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="1ddcb-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="1ddcb-117">若要查看组织中所有未授权用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="1ddcb-117">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="1ddcb-118">若要查看组织中所有授权用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="1ddcb-118">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="1ddcb-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ddcb-119">See also</span></span>

[<span data-ttu-id="1ddcb-120">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="1ddcb-120">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="1ddcb-121">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1ddcb-121">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="1ddcb-122">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="1ddcb-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)