---
title: Azure 信息保护中的保护功能向现有租户推出
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 7ad6f58e-65d7-4c82-8e65-0b773666634d
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 本文介绍了在 Azure 信息保护中向保护功能推出的更改
ms.openlocfilehash: 070b0d1af0576391ce5f22a827975d1541646454
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203595"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Azure 信息保护中的保护功能向现有租户推出

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


为了帮助保护你的信息的初始步骤，从2018年7月起，所有 Azure 信息保护符合条件的租户在默认情况下将启用 Azure 信息保护中的保护功能。 Azure 信息保护中的保护功能以前在 Office 365 中称为 "权限管理" 或 "Azure RMS"。 如果你的组织具有 Office E3 服务计划或更高的服务计划，你现在将通过 Azure 信息保护在我们推出这些功能时获取一个头开始保护信息。

## <a name="changes-beginning-july-1-2018"></a>2018年7月1日开始的更改

从2018年6月1日起，Microsoft 将为具有以下订阅计划之一的所有组织启用 Azure 信息保护中的保护功能：

- Office 365 邮件加密作为 Office 365 E3 和 E5、Microsoft E3 和 E5、Office 365 A1、A3 和 A5 以及 Office 365 G3 和 G5 的一部分提供。 您无需额外的许可证即可接收 Azure 信息保护支持的新保护功能。

- 您还可以将 Azure 信息保护计划1添加到以下计划，以接收新的 Office 365 邮件加密功能： Exchange Online 计划1、Exchange Online 计划2、Office 365 F1、Microsoft 365 Business Basic、Microsoft 365 商业标准或 Office 365 Enterprise E1。

- 每个用户从 Office 365 邮件加密中受益的人都需要获得功能的许可。

- 有关完整列表，请参阅 [Exchange Online 服务说明](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) For the Office 365 邮件加密。

租户管理员可以在 Office 365 管理员门户中检查保护状态。

![显示已激活 Office 365 中的权限管理的屏幕截图。](../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png)

## <a name="why-are-we-making-this-change"></a>为什么要进行此更改？

Office 365 邮件加密利用了 Azure 信息保护中的保护功能。 在对 Office 365 邮件加密的最新改进以及我们对 Microsoft 365 中的信息保护的广泛投资的核心，我们将使组织能够更轻松地打开和使用我们的保护功能（就像以往一样，加密技术很难设置）。 通过在默认情况下启用 "Azure 信息保护" 中的保护功能，可以快速开始保护敏感数据。

## <a name="does-this-impact-me"></a>这会对我造成影响吗？

如果你的组织已购买符合条件的 Office 365 许可证，则你的租户将受此更改影响。

 **重要!** 如果你在本地环境中使用 Active Directory 权限管理服务 (AD RMS) ，则必须立即退出此更改或迁移到 Azure 信息保护，然后再在接下来的30天内推出此更改。 有关如何选择退出的信息，请参阅 "我使用 AD RMS，如何选择退出？" ”中所述的过程安装本地化文件。 如果你更喜欢迁移，请参阅 [从 AD RMS 迁移到 Azure 信息保护。](https://docs.microsoft.com/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>是否可以将 Azure 信息保护用于 Active Directory 权限管理服务 (AD RMS) ？

否。 这不是一种受支持的部署方案。 在不考虑其他自愿退出步骤的情况下，某些计算机可能会自动开始使用 Azure 权限管理服务，同时还会连接到 AD RMS 群集。 此方案不受支持且具有不可靠的结果，因此，在接下来的30天内，在我们推出这些新功能之前，请务必选择退出此更改。 有关如何选择退出的信息，请参阅 "我使用 AD RMS，如何选择退出？" ”中所述的过程安装本地化文件。 如果你更喜欢迁移，请参阅 [从 AD RMS 迁移到 Azure 信息保护。](https://docs.microsoft.com/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>如何知道我是否在使用 AD RMS？

如果 [你还具有 Active Directory 权限管理服务 (AD rms) ](https://docs.microsoft.com/azure/information-protection/deploy-use/prepare-environment-adrms) 以检查是否已部署 ad rms，请使用以下说明来准备 Azure 权限管理的环境：

1. 尽管可选，大多数 AD RMS 部署都将 (SCP) 的服务连接点发布到 Active Directory，以便域计算机可以发现 AD RMS 群集。

使用 ADSI Edit 查看是否已在 Active Directory 中发布 SCP： CN = Configuration [server name]、CN = Services、CN = RightsManagementServices、CN = SCP

2. 如果未使用 SCP，则必须使用 Windows 注册表为客户端服务发现或授权重定向配置连接到 AD RMS 群集的 Windows 计算机： HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\MSIPC\ServiceLocation 或 HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation

有关这些注册表配置的详细信息，请参阅使用 Windows 注册表和[重定向授权服务器流量](https://docs.microsoft.com/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic)[启用客户端服务发现](https://docs.microsoft.com/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry)。

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>我使用 AD RMS，如何选择退出？

若要退出即将进行的更改，请完成以下步骤：

1. 使用组织中具有全局管理员权限的工作或学校帐户，启动 Windows PowerShell 会话并连接到 Exchange Online。 有关说明，请参阅[连接 PowerShell Exchange Online](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)。

2. 使用以下语法运行 Get-irmconfiguration cmdlet：

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>进行此更改后，我可以预期什么？

启用此功能后，如果你未选择，则可以开始使用 [Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) 中宣布推出的新版本的 Office 365 邮件加密，并利用 Azure 信息保护的加密和保护功能。

![在 Outlook 网页版中显示 OME 保护邮件的屏幕截图。](../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png)

有关新的增强功能的详细信息，请参阅 [Office 365 邮件加密](../../compliance/ome.md)。
