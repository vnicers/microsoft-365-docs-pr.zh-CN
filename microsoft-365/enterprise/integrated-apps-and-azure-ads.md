---
title: 适用于 Microsoft 365 管理员的集成应用和 Azure AD
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: 了解如何在 Azure AD 中注册和管理 Office 365 集成的应用程序，从而允许全局管理员级别的应用程序授权。
ms.openlocfilehash: 3d9ded2ba2819d0e957586b6c49811ec932dee31
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46688117"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a><span data-ttu-id="9b335-103">适用于 Microsoft 365 管理员的集成应用和 Azure AD</span><span class="sxs-lookup"><span data-stu-id="9b335-103">Integrated Apps and Azure AD for Microsoft 365 administrators</span></span>

<span data-ttu-id="9b335-104">除了仅 [打开或关闭集成应用](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)之外，还可以管理集成的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b335-104">There's more to managing integrated apps than just [Turning Integrated Apps on or off](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114).</span></span> <span data-ttu-id="9b335-105">随着 Microsoft 365 REST Api 的出现，用户可以向应用授予对其 Microsoft 365 数据（如邮件、日历、联系人、用户、组、文件和文件夹）的访问权限。</span><span class="sxs-lookup"><span data-stu-id="9b335-105">With the advent of the Microsoft 365 REST APIs, users can grant apps access to their Microsoft 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="9b335-106">默认情况下，用户需要单独向每个应用程序授予权限，但如果要在全局管理员级别对应用程序进行授权，并通过应用启动器将其部署到整个组织，则不能很好地进行扩展。</span><span class="sxs-lookup"><span data-stu-id="9b335-106">By default, users need to individually grant permissions to each app, but this doesn't scale well if you want to authorize an app once at the global administrator level and roll it out to your whole organization through the app launcher.</span></span> <span data-ttu-id="9b335-107">若要执行此操作，必须在 Azure AD 中注册应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b335-107">To do this, you must register the app in Azure AD.</span></span> <span data-ttu-id="9b335-108">在 Azure AD 中注册应用程序之前需要执行一些步骤，以及你应该知道哪些可帮助你管理 Microsoft 365 组织中的应用程序的背景信息。</span><span class="sxs-lookup"><span data-stu-id="9b335-108">There are some steps you need to take before you can register an app in Azure AD and some background information you should know that can help you manage apps in your Microsoft 365 organization.</span></span> <span data-ttu-id="9b335-109">本文将向您指出这些资源。</span><span class="sxs-lookup"><span data-stu-id="9b335-109">This article points you to those resources.</span></span>
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a><span data-ttu-id="9b335-110">适用于 Microsoft 365 管理员的 Azure AD 资源</span><span class="sxs-lookup"><span data-stu-id="9b335-110">Azure AD resources for Microsoft 365 admins</span></span>

<span data-ttu-id="9b335-111">您必须先执行以下两个步骤，然后才能在 Azure AD 中管理 Microsoft 365 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b335-111">You have to do these two procedures before you can manage your Microsoft 365 apps in Azure AD.</span></span>
  
|<span data-ttu-id="9b335-112">**先决条件**</span><span class="sxs-lookup"><span data-stu-id="9b335-112">**Prerequisites**</span></span>|<span data-ttu-id="9b335-113">**Comments**</span><span class="sxs-lookup"><span data-stu-id="9b335-113">**Comments**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="9b335-114">使用免费的 Azure Active Directory 订阅</span><span class="sxs-lookup"><span data-stu-id="9b335-114">Use your free Azure Active Directory subscription</span></span>](https://docs.microsoft.com/microsoft-365/compliance/use-your-free-azure-ad-subscription-in-office-365) <br/> |<span data-ttu-id="9b335-115">对 Microsoft 365 的每个付费订阅都提供了 Azure Active Directory (Azure AD) 的免费订阅。</span><span class="sxs-lookup"><span data-stu-id="9b335-115">Every paid subscription to Microsoft 365 comes with a free subscription to Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="9b335-116">您可以使用 Azure AD 管理您的应用程序，并创建和管理用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="9b335-116">You can use Azure AD to manage your apps and to create and manage user and group accounts.</span></span> <span data-ttu-id="9b335-117">若要使用 Azure AD，请转到 Azure 门户，并使用 Microsoft 365 帐户登录。</span><span class="sxs-lookup"><span data-stu-id="9b335-117">To use Azure AD, just go to the Azure portal and sign in using your Microsoft 365 account.</span></span>  <br/> |
|[<span data-ttu-id="9b335-118">打开或关闭集成应用</span><span class="sxs-lookup"><span data-stu-id="9b335-118">Turning Integrated Apps on or off</span></span>](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |<span data-ttu-id="9b335-119">您必须为您的用户启用集成应用程序，以允许第三方应用访问其 Microsoft 365 信息，并让您在 Azure AD 中注册应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b335-119">You must turn on Integrated Apps for your users to allow third-party apps to access their Microsoft 365 information and for you to register apps in Azure AD.</span></span> <span data-ttu-id="9b335-120">例如，当某人使用第三方应用程序时，该应用可能会请求权限来访问其日历，并编辑 OneDrive for business 文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="9b335-120">For example, when someone uses a third-party app, that app might ask for permission to access their calendar and to edit files that are in a OneDrive for Business folder.</span></span>  <br/> |
   
<span data-ttu-id="9b335-121">管理 Microsoft 365 应用程序需要你了解 Azure AD 中的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b335-121">Managing Microsoft 365 apps requires you to have knowledge of apps in Azure AD.</span></span> <span data-ttu-id="9b335-122">这些文章可帮助你为你提供所需的背景。</span><span class="sxs-lookup"><span data-stu-id="9b335-122">These articles help give you the background you need.</span></span>
  
|<span data-ttu-id="9b335-123">**背景文章**</span><span class="sxs-lookup"><span data-stu-id="9b335-123">**Background article**</span></span>|<span data-ttu-id="9b335-124">**Comments**</span><span class="sxs-lookup"><span data-stu-id="9b335-124">**Comments**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="9b335-125">满足 Microsoft 365 应用启动器</span><span class="sxs-lookup"><span data-stu-id="9b335-125">Meet the Microsoft 365 app launcher</span></span>](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |<span data-ttu-id="9b335-126">如果你不熟悉应用启动器，你可能会想知道它是什么以及如何使用它。</span><span class="sxs-lookup"><span data-stu-id="9b335-126">If you're new to the app launcher, you might be wondering what it is and how to use it.</span></span> <span data-ttu-id="9b335-127">应用启动器旨在帮助你从 Microsoft 365 中的任何位置访问你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b335-127">The app launcher is designed to help you get to your apps from anywhere in Microsoft 365.</span></span>  <br/> |
|[<span data-ttu-id="9b335-128">Office 365 管理 API 概述</span><span class="sxs-lookup"><span data-stu-id="9b335-128">Office 365 Management APIs overview</span></span>](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) <br/> |<span data-ttu-id="9b335-129">Microsoft 365 Api 允许你提供对 Microsoft 365 数据的访问权限，包括他们最关心的事情—他们的邮件、日历、联系人、用户和组、文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="9b335-129">The Microsoft 365 APIs let you provide access to your Microsoft 365 data, including the things they care about most—their mail, calendars, contacts, users and groups, files, and folders.</span></span> <span data-ttu-id="9b335-130">本文中有一个很棒的关系图，说明了 Microsoft 365 应用程序、Azure AD 和应用程序访问的数据之间的关系。</span><span class="sxs-lookup"><span data-stu-id="9b335-130">There is a good diagram in this article that illustrates the relationship among Microsoft 365 apps, Azure AD, and the data that the apps access.</span></span>  <br/> |
|[<span data-ttu-id="9b335-131">在 Azure Active Directory 中集成应用程序</span><span class="sxs-lookup"><span data-stu-id="9b335-131">Integrating Applications in Azure Active Directory</span></span>](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | <span data-ttu-id="9b335-132">了解与 Azure AD 集成的应用程序，以及如何注册您的应用程序，了解已注册应用程序背后的概念，并了解多租户应用程序的品牌打造指南。</span><span class="sxs-lookup"><span data-stu-id="9b335-132">Learn about applications that are integrated with Azure AD, and how to register your application, understand concepts behind a registered application, and learn about branding guidelines for multi tenant applications.</span></span>  <br/> |
|[<span data-ttu-id="9b335-133">将自定义磁贴添加到应用启动器</span><span class="sxs-lookup"><span data-stu-id="9b335-133">Add custom tiles to the app launcher</span></span>](https://docs.microsoft.com/office365/admin/manage/customize-the-app-launcher)  <br/> |<span data-ttu-id="9b335-134">Microsoft 365 中的应用启动器使用户能够更轻松地查找和访问其应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b335-134">The app launcher in Microsoft 365 makes it easier for users to find and access their apps.</span></span> <span data-ttu-id="9b335-135">本文介绍了您作为开发人员可以在用户的应用程序启动器中显示您的应用程序的方法，同时还为他们提供了使用其 Microsoft 365 凭据的单一登录 (SSO) 体验。</span><span class="sxs-lookup"><span data-stu-id="9b335-135">This article describes the ways you as a developer can get your apps to appear in users' app launchers and also give them a single sign-on (SSO) experience using their Microsoft 365 credentials.</span></span>  <br/> |
|[<span data-ttu-id="9b335-136">Azure Active Directory 集成教程</span><span class="sxs-lookup"><span data-stu-id="9b335-136">Azure Active Directory Integration Tutorials</span></span>](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |<span data-ttu-id="9b335-137">这些教程的目标是向您介绍如何为第三方 SaaS 应用程序配置 Azure AD SSO。</span><span class="sxs-lookup"><span data-stu-id="9b335-137">The objective of these tutorials is to show you how to configure Azure AD SSO for third-party SaaS applications.</span></span>  <br/> |
|[<span data-ttu-id="9b335-138">Azure AD 的身份验证场景</span><span class="sxs-lookup"><span data-stu-id="9b335-138">Authentication Scenarios for Azure AD</span></span>](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |<span data-ttu-id="9b335-139">Azure AD 通过提供标识作为一项服务来简化对开发人员的身份验证，并支持对行业标准协议（如 OAuth 2.0 和 OpenID Connect）以及针对不同平台的开放源库，以帮助您快速开始编码。</span><span class="sxs-lookup"><span data-stu-id="9b335-139">Azure AD simplifies authentication for developers by providing identity as a service, with support for industry-standard protocols such as OAuth 2.0 and OpenID Connect, as well as open source libraries for different platforms to help you quickly start coding.</span></span> <span data-ttu-id="9b335-140">本文档可帮助您了解 Azure AD 支持的各种方案，并说明如何开始。</span><span class="sxs-lookup"><span data-stu-id="9b335-140">This document helps you understand the various scenarios Azure AD supports and shows you how to get started.</span></span>  <br/> |
|[<span data-ttu-id="9b335-141">应用程序访问</span><span class="sxs-lookup"><span data-stu-id="9b335-141">Application access</span></span>](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |<span data-ttu-id="9b335-142">通过 Azure AD，可以轻松地将当今流行软件的许多与服务 (SaaS) 应用程序集成在一起。它提供了标识和访问管理，并为用户提供了一个访问面板，用户可在其中发现他们拥有的应用程序访问权限以及它们可以使用 SSO 访问其应用程序的位置。</span><span class="sxs-lookup"><span data-stu-id="9b335-142">Azure AD enables easy integration to many of today's popular software as a service (SaaS) applications; it provides identity and access management, and it delivers an Access Panel for users where they can discover what application access they have and where they can use SSO to access their applications.</span></span> <span data-ttu-id="9b335-143">本文为您提供了相关资源的链接，这些资源使您能够详细了解 Azure AD 的应用程序访问增强功能，以及如何参与这些增强。</span><span class="sxs-lookup"><span data-stu-id="9b335-143">This article provides you with links to the related resources that enable you to learn more about the application access enhancements for Azure AD and how you can contribute to them.</span></span>  <br/> |
|[<span data-ttu-id="9b335-144">个性化设置 Office 365 体验</span><span class="sxs-lookup"><span data-stu-id="9b335-144">Personalize your Office 365 experience</span></span>](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |<span data-ttu-id="9b335-145">您可以通过在 Microsoft 365 应用启动器中添加或删除应用程序，快速访问您每天使用的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b335-145">You can get quick access to the apps you use every day by adding or removing apps in the Microsoft 365 app launcher.</span></span>  <br/> |
   
