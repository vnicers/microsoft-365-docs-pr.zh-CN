---
title: 设置 Office 365 企业版中的加密
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: 使用 Office 365 时，某些加密功能在默认情况下处于打开状态。可以配置其他功能以满足某些合规性或法律要求。
ms.openlocfilehash: 268bd7b57884549b7ab4abb45a7b69485498f1cb
ms.sourcegitcommit: 89636f35b0194986f156302fc1bb96af25d4805b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "44799987"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>设置 Office 365 企业版中的加密

加密可以防止未经授权的用户读取您的内容。 由于可以使用各种技术和方法完成[Office 365 中的加密](encryption.md)，因此没有一个用于打开或设置加密的单一位置。 本文提供了有关在信息保护策略中设置或配置加密的各种方法的信息。
  
> [!TIP]
> 如果要查看有关加密的更多技术详细信息，请参阅[Office 365 中有关加密的技术参考详细信息](technical-reference-details-about-encryption.md)。
  
在 Office 365 中，默认情况下提供几种加密功能。 可以配置其他加密功能，以满足某些合规性或法律要求。 下表介绍了用于不同方案的几种加密方法。
  
|**应用场景**|**加密方法**|
|:-----|:-----|
|文件保存在 Windows 计算机上  <br/> |可以使用 Windows 设备上的 BitLocker 完成在计算机级别加密。 作为企业管理员或 IT 专业人员，你可以使用 Microsoft 部署工具包（MDT）进行设置。 请参阅[设置适用于 BitLocker 的 MDT](https://go.microsoft.com/fwlink/?linkid=849282)。  <br/> |
|文件保存在移动设备上  <br/> |某些类型的移动设备会对默认情况下保存到这些设备的文件进行加密。 通过[内置的 Office 365 移动设备管理功能](https://support.microsoft.com/en-us/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0)，您可以设置策略，以确定是否允许移动设备访问 Office 365 中的数据。 例如，您可以设置一个只允许加密内容的设备访问 Office 365 数据的策略。 请参阅[创建和部署设备安全策略](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6)。  <br/> 若要更好地控制移动设备与 Office 365 的交互方式，可以考虑添加[Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/setup-steps)。  <br/> |
|您需要控制用于加密 Microsoft 数据中心中的数据的加密密钥  <br/> | 作为 Office 365 管理员，您可以控制组织的加密密钥，然后将 Office 365 配置为使用它们在 Microsoft 数据中心中对静态数据进行加密。  <br/> [使用 Office 365 中的客户密钥执行服务加密](customer-key-overview.md) <br/> |
|用户通过电子邮件进行通信（Exchange Online）  <br/> | 作为 Exchange Online 管理员，你有多种配置电子邮件加密的方法。 具体包括：  <br/>  使用[Office 365 邮件加密（OME）](set-up-new-message-encryption-capabilities.md)和 Azure 权限管理（azure RMS）使用户能够在组织内部或外部发送加密的邮件  <br/>  使用[用于邮件签名和加密的 S/MIME](https://aka.ms/c6dozg)对电子邮件进行加密和数字签名  <br/>  使用 TLS[设置连接器以实现与其他组织的安全邮件流](https://aka.ms/hs809p) <br/>  请参阅[Office 365 中的电子邮件加密](https://aka.ms/hic3f7)。  <br/> |
|可从工作组网站或文档库（OneDrive for Business 或 SharePoint Online）访问文件  <br/> |当用户使用已保存到 OneDrive for Business 或 SharePoint Online 的文件时，将使用 TLS 连接。 这将自动内置到 Office 365 中。 请参阅[OneDrive For business 和 SharePoint Online 中的数据加密](https://go.microsoft.com/fwlink/?linkid=526379)。  <br/> |
|联机会议和即时消息对话中共享文件（Skype for Business Online）  <br/> |当用户使用 Skype for Business Online 处理文件时，TLS 将用于该连接。 这将自动内置到 Office 365 中。 请参阅[安全性和存档（Skype For Business Online）](https://aka.ms/nuq4ws)。  <br/> |
|联机会议和即时消息对话中共享文件（Microsoft 团队）  <br/> |当用户使用 Microsoft 团队处理文件时，TLS 用于连接。 这将自动内置到 Office 365 中。 Microsoft 团队目前不支持加密电子邮件的内联呈现。 若要在 Microsoft 团队中阻止加密电子邮件的登录，请参阅[邮件加密 FAQ](https://docs.microsoft.com/microsoft-365/compliance/ome-faq?view=o365-worldwide#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail)。  <br/> 

## <a name="additional-information"></a>其他信息

若要了解有关包含加密选项的文件保护解决方案的详细信息，请参阅[Office 365 中的文件保护解决方案](https://www.microsoft.com/download/details.aspx?id=55523)。
 
