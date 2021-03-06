---
title: Autopilot 设备错误疑难解答
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
f1_keywords:
- ZTDTroubleshootDeviceErrors
- O365E_ZTDTroubleshootDeviceErrors
- BCS365_ZTDTroubleshootDeviceErrors
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1f468690-530c-47ea-918f-fede24607c53
description: 了解如何解决在 Microsoft 365 商业高级版中使用 AutoPilot 设备文件时可能会看到的错误。
ms.openlocfilehash: bec5126696ee322db42e4b7c5cd8e0df485ab2c9
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "44403402"
---
# <a name="troubleshoot-autopilot-device-errors"></a>Autopilot 设备错误疑难解答

## <a name="device-file-error-messages"></a>设备文件错误消息

以下是在使用 Microsoft 365 商业高级版中的 AutoPilot 设备文件时可能会看到的一些错误的相关信息。 
  
|**错误代码**|**修复以试用**|
|:-----|:-----|
|请求正文无效  <br/> |此错误应该很少发生，如果您看到此错误，请再次尝试该操作。  <br/> |
|设备的硬件哈希值不正确。  <br/> |如果看到此错误，则表示你在 CSV 文件中为一个设备的硬件哈希提供的值不正确。 首先，请验证是否正确键入了值。 如果你认为该值是正确的，但仍会发生此错误，请向你的硬件供应商寻求帮助。  <br/> |
|分配给另一个租户的设备  <br/> |如果看到此错误，则表示你在 CSV 文件中提供的值是一个或多个设备的序列号或产品密钥不正确。 首先，请验证是否正确键入了值。 如果你认为该值是正确的，但仍会发生此错误，请向你的硬件供应商寻求帮助。  <br/> |
|CSV 文件包含无效的序列号或产品密钥  <br/> |如果看到此错误，则表示您尝试注册的设备已由另一个组织注册。 若要修复此错误，请向硬件供应商寻求帮助。  <br/> |
|此设备不支持通过使用 AutoPilot 进行安装  <br/> | 此错误表示设备不符合 AutoPilot 部署要求。 设备需要满足以下要求：  <br/>  Windows 10 版本 1703 或更高版本。  <br/>  尚未通过 Windows 开箱即用体验的新设备。  <br/> |
|找不到设备  <br/> |此错误表示 CSV 文件中的一个或多个设备未注册到您的组织。 若要解决此问题，请向硬件供应商寻求帮助。  <br/> |
