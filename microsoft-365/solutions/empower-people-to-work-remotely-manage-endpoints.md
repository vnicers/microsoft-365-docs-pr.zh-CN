---
title: 步骤 4. 部署设备、电脑和其他终结点的终结点管理
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 06/03/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: 使用 Microsoft Endpoint Manager 管理管理设备、电脑和其他终结点。
ms.openlocfilehash: 5c6e433918709a55f03d786891ec0fd7ac62a26b
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2020
ms.locfileid: "48377231"
---
# <a name="step-4-deploy-endpoint-management-for-your-devices-pcs-and-other-endpoints"></a>步骤 4. 部署设备、电脑和其他终结点的终结点管理

使用远程工作者，需要支持越来越多的个人设备。 终结点管理是一种基于策略的安全方法，要求设备在获得对资源的访问权限之前满足特定条件。 Microsoft Endpoint Manager 提供新式管理功能，使你的数据在云中和本地保持安全。 

Endpoint Manager 通过结合以下可能已知和正在使用的服务，提供用于管理移动设备、台式计算机、虚拟机、嵌入式设备和服务器的服务和工具。

![用于终结点管理的组件](../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png)

## <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune 是一种基于云的服务，侧重于 Microsoft 365 所包含的移动设备管理 (MDM) 和移动应用程序管理 (MAM)。 

- **MDM：** 针对组织所拥有的设备，可执行完全控制，包括设置、功能和安全性。 设备将在 Intune 中进行“注册”，并在这里接收带有规则和设置的 Intune 策略。 例如，可以设置密码和 PIN 要求、创建 VPN 连接以及设置威胁防护等。

- **MAM：** 远程工作者可能不希望你对他们的个人设备（也称为自带 (BYOD) 设备）拥有完全控制权。 你可以为你的远程工作者提供各种选项，但仍保护你的组织。 例如，如果远程工作者希望拥有对组织资源的完整访问权限，则可以注册其设备。 或者，如果这些用户仅希望访问电子邮件或 Microsoft Teams，则可使用需要多重身份验证 (MFA) 的应用保护策略来使用这些应用。

有关详细信息，请参阅此 [Microsoft Intune 概述](https://docs.microsoft.com/intune/fundamentals/what-is-intune)。

## <a name="configuration-manager"></a>Configuration Manager

Configuration Manager 是一种本地管理解决方案，可用于管理网络上或基于 Internet 的台式机、服务器和笔记本电脑。 使用 Configuration Manager 部署应用程序、软件更新和操作系统。 还可以实时监视客户端上的合规性、查询和操作等。 可通过云使其与 Intune、Azure AD、Microsoft Defender ATP 和其他云服务集成。 

有关详细信息，请参阅此 [Configuration Manager 概述](https://docs.microsoft.com/mem/configmgr/core/understand/introduction)。

## <a name="co-management"></a>协同管理

协同管理使用 Intune 和其他 Microsoft 365 云服务，将现有的 Configuration Manager 投资与云相结合。 由你选择将 Configuration Manager 还是 Intune 作为不同工作负载的管理机构。 

合作管理将使用基于 Intune 的云功能，包括条件访问和强制实施设备合规性。 你可以将某些任务保留在本地，同时在云中运行其他任务。

有关详细信息，请参阅此[协同管理概述](https://docs.microsoft.com/mem/configmgr/comanage/overview)。

## <a name="desktop-analytics"></a>桌面分析

桌面分析是一种基于云的服务，可与 Configuration Manager 集成并为你提供洞察和情报，以便就 Windows 客户端作出明智决策。 它将组织中的数据与连接到 Microsoft 云服务的数百万台设备的数据合并。 

借助桌面分析，你可以：

- 创建组织中运行的应用的清单。
- 评估应用程序与最新 Windows 10 功能更新的兼容性。
- 确定兼容性问题，并根据启用了云的数据见解获取缓解建议。
- 创建可在最小的一组设备内代表全部应用程序和驱动程序的试点组。
- 将 Windows 10 部署到试点设备和生产管理设备。

有关详细信息，请参阅此[桌面分析概述](https://docs.microsoft.com/mem/configmgr/desktop-analytics/overview)。

## <a name="windows-autopilot"></a>Windows Autopilot

Windows Autopilot 是一个零接触、自助式的 Windows 部署平台。 它包括一组用于设置和预配置新设备，以使它们可供高效使用的技术。 还可以使用 Windows Autopilot 来重置、恢复设备并重新调整其用途。 

借助 Windows Autopilot，IT 部门可以预配置设备，而几乎不需要管理任何基础结构，而且过程轻松简单。 

- 从用户的角度来看，只需几个简单操作便可以使其设备准备就绪，以供使用。 
- 从 IT 专业人员的角度来看，最终用户所需的交互将只有连接到网络并验证其凭据。

有关详细信息，请参阅此 [Windows Autopilot 概述](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot)。

## <a name="admin-technical-resources-for-endpoint-management"></a>用于终结点管理的管理员技术资源

- [有关管理面向远程工作者的 Windows 10 设备的第 3 部分视频](https://resources.techcommunity.microsoft.com/enabling-remote-work/#security)
- [有关管理面向远程工作者的用户桌面和浏览器的第 5 部分视频](https://resources.techcommunity.microsoft.com/enabling-remote-work/#security)
- [部署适用于 Microsoft 365 的移动基础结构](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure)
- [如何注册用于移动设备管理的不同类型的设备](https://docs.microsoft.com/mem/intune/enrollment/device-enrollment)
- [如何向最终用户讲解 Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/end-user-educate)
 
## <a name="results-of-step-3"></a>步骤 3 的结果

你正在使用 Endpoint Manager 功能套件来管理移动设备、台式计算机、虚拟机、嵌入式设备和服务器。

## <a name="next-step"></a>后续步骤

继续[步骤 5](empower-people-to-work-remotely-teams-productivity-apps.md)，让远程工作者能够使用 Microsoft 365 生产力应用（如 Microsoft Teams）。
