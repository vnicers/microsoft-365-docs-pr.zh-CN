---
title: Set up Information Rights Management (IRM) in SharePoint admin center
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- SPO_Content
localization_priority: Normal
search.appverid:
- SPO160
- MET150
ms.assetid: 239ce6eb-4e81-42db-bf86-a01362fed65c
description: 了解如何通过 Microsoft Azure Active Directory 权限管理服务（RMS）使用 SharePoint Online IRM 来保护 SharePoint 列表和文档库。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 33e5a72ea1d0733656379bc4efdca7dd14f78cb1
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "44819192"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Set up Information Rights Management (IRM) in SharePoint admin center

在 SharePoint Online 中，IRM 保护应用于列表和库级别的文件。 您的组织可以使用 IRM 保护之前，必须先设置权限管理。 IRM 依赖 azure 权限管理服务（来自 Azure 信息保护）来加密和分配使用限制。 一些 Microsoft 365 计划包括 Azure 权限管理，但并非全部。 若要了解详细信息，请参阅[Office 应用程序和服务如何支持 Azure 权限管理](https://docs.microsoft.com/azure/information-protection/understand-explore/office-apps-services-support)。
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>使用 SharePoint 管理中心打开 IRM 服务

在您的组织可以对 SharePoint 列表和库进行 IRM 保护之前，必须首先为您的组织激活权限管理服务。 若要了解如何查看 "[激活 Azure 权限管理](https://docs.microsoft.com/information-protection/deploy-use/activate-service)"。 您必须使用具有全局管理员权限的工作或学校帐户来启用 Rights Management service。 否则，将无法将 IRM 功能与 SharePoint Online 一起使用。
  
激活 Rights Management service 后，登录到 SharePoint 管理中心以打开 IRM。
  
1. 以全局管理员或 SharePoint 管理员身份登录。
    
2. 依次选择左上角的应用启动器图标 ![Office 365 中的应用启动器图标](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) 和“管理员”****，以打开 Microsoft 365 管理中心。 （如果看不到 "管理员" 磁贴，则您的组织中不具有管理员权限。） 
    
3. 在左窗格中，选择 "**管理中心**" " \> **SharePoint**"。
    
4. 在左窗格中，选择 "**设置**"，然后选择 "**经典设置" 页**。
    
5. 在 "**信息权限管理（IRM）** " 部分中，选择 "**使用您的配置中指定的 IRM 服务**"，然后选择 "**刷新 IRM 设置**"。 刷新 IRM 设置后，组织中的用户可以开始在其 SharePoint 列表和文档库中使用 IRM。 但是，执行此操作的选项可能需要一个小时才能显示在 "库设置" 和 "列表设置" 中。
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>IRM-启用 SharePoint 文档库和列表
<a name="__toc220831191"> </a>

刷新 IRM 设置后，网站所有者可以对其 SharePoint 列表和文档库进行 IRM 保护。 有关详细信息，请参阅[将信息权限管理应用于列表或库](apply-irm-to-a-list-or-library.md)。
  
当网站所有者为列表或库启用 IRM 时，他们可以保护该列表或库中的任何受支持的文件类型。 对库启用 IRM 时，权限管理将应用于该库中的所有文件。 为列表启用 IRM 时，权限管理仅适用于附加到列表项（而不是实际列表项）的文件。
  
当用户下载启用 IRM 的列表或库中的文件时，将对这些文件进行加密，以便仅获得授权的用户可以查看这些文件。 每个权限管理文件还包含一个发布许可证，该许可证对查看文件的人员施加限制。 典型限制包括将文件设为只读、禁用文本复制、阻止用户保存本地副本以及阻止用户打印文件。 可以读取受 IRM 支持的文件类型的客户端程序使用权限管理文件中的发布许可证来强制实施这些限制。 这是权限管理文件在下载后仍保留其保护的方式。 若要对列表或库启用 IRM，请参阅[将信息权限管理应用于列表或库](apply-irm-to-a-list-or-library.md)。
  
无法在浏览器中使用 Office 在启用 IRM 的库中创建或编辑文档。 相反，一次只能有一个人下载和编辑 IRM 加密文件。 使用签入和签出管理*共同创作*，或跨多个用户进行创作。 
  
当您从受 IRM 保护的库下载 PDF 文件时，Microsoft 365 将创建一个受保护的 PDF 文件。 文件的分机号码不会改变，但文件是受保护的。 若要查看此文件，你将需要 Azure 信息保护查看器、完整的 Azure 信息保护客户端或其他支持查看受保护的 PDF 文件的应用程序。 
  
SharePoint Online 支持对以下文件类型进行加密：
  
- PDF
    
- 以下 Microsoft Office 程序的97-2003 文件格式： Word、Excel 和 PowerPoint
    
- 适用于以下 Microsoft Office 程序的 Office Open XML 格式： Word、Excel 和 PowerPoint
    
- XML 纸张规范（XPS）格式
 
> [!NOTE]
> IRM 保护无法应用于受保护的文档（如数字签名的 PDF 文件），因为 SharePoint 需要在上载时打开文档。 

## <a name="next-steps"></a>后续步骤
<a name="__toc220831191"> </a>

为 SharePoint Online 启用 IRM 后，可以开始将权限管理应用于列表和库。 有关信息，请参阅[将信息权限管理应用于列表或库](apply-irm-to-a-list-or-library.md)。
  
新的 OneDrive 同步客户端现在支持同步受 IRM 保护的 SharePoint 文档库和 OneDrive 位置（只要库的 IRM 设置未设置为 "过期文档访问权限"）。 有关详细信息，或者若要开始部署新的同步客户端，请参阅[部署新的 OneDrive 同步客户端 For Windows](https://docs.microsoft.com/onedrive/deploy-on-windows)。
  
[页面顶部](set-up-irm-in-sp-admin-center.md)
