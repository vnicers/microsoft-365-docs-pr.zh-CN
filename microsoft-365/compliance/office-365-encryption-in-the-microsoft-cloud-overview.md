---
title: Microsoft 云中的加密
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: 在本文中，阅读了用于将客户数据安全保存在 Microsoft 云中的各种形式的加密的概述。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e48cc4fc54f0bc4553bab655611900523e11bd4d
ms.sourcegitcommit: 1c90bcc5c56f24895f01c3e0423c3f6b73715c13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "44214270"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Microsoft 云中的加密

Microsoft 企业云服务中的客户数据受各种技术和过程（包括各种形式的加密）的保护。 本文档中 (客户数据包括 Exchange Online 邮箱内容、电子邮件正文、日历条目和电子邮件附件的内容，如果适用，则 Skype for Business 内容) SharePoint Online 网站内容和存储在网站中的文件，以及上传到 OneDrive for business 或 Skype for business 的文件。 ) Microsoft 在其产品和服务中使用多个加密方法、协议和密码，以帮助为客户数据提供安全路径以通过我们的云服务，并帮助保护存储在云服务中的客户数据的机密性。 Microsoft 使用一些最强大、最安全的加密协议来抵御对客户数据的未授权访问的障碍。 正确的密钥管理也是加密最佳实践的重要元素，Microsoft 可以确保所有 Microsoft 托管的加密密钥都得到了适当的保护。

无论客户配置如何，存储在 Microsoft 企业云服务中的客户数据都使用一种或多种形式的加密进行保护。 对加密策略的 (验证及其强制实施将独立于多个第三方审计员进行验证，并且这些审核的报告在 [服务信任门户](https://aka.ms/stp)上可用。 ) 

Microsoft 提供了在 rest 和途对客户数据进行加密的服务端技术。 例如，对于 rest 上的客户数据，Microsoft Azure 使用 [bitlocker](https://docs.microsoft.com/windows/device-security/bitlocker/bitlocker-overview) 和 [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt)，而 microsoft 365 使用 Bitlocker、 [Azure 存储服务加密](https://docs.microsoft.com/azure/)、 [分布式密钥管理器](https://docs.microsoft.com/microsoft-365/compliance/exchange-online-secures-email-secrets) (DKM) 和 Microsoft 365 服务加密。 对于传输中的客户数据，Azure、Office 365、Microsoft 商业支持、Microsoft Dynamics 365、Microsoft Power BI 和 Visual Studio Team Services 使用行业标准安全传输协议，如 Internet 协议安全 (IPsec) 和传输层安全性 (TLS) ，在 Microsoft 数据中心之间和用户设备与 Microsoft 数据中心之间。

除了 Microsoft 提供的加密安全的基准级别之外，我们的云服务还包括您可以管理的其他加密选项。 例如，您可以对其 Azure 虚拟机 (Vm) 及其用户之间的流量启用加密。 使用 [Azure 虚拟网络](https://azure.microsoft.com/services/virtual-network/)，您可以使用行业标准 IPsec 协议来加密公司 VPN 网关和 Azure 之间以及位于虚拟网络上的虚拟机之间的通信。 此外， [新的 Office 365 邮件加密功能](set-up-new-message-encryption-capabilities.md) 允许您向任何人发送加密邮件。

根据公钥基础结构运营安全标准（这是 [Microsoft 安全策略](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers)的一个组件），Microsoft 利用 Windows 操作系统中包含的用于证书和身份验证机制的加密功能，其中包括使用符合美国政府的 [联邦信息处理标准](https://csrc.nist.gov/publications/PubsFIPS.html) 的加密模块 (FIPS) 140-2 标准。 可在上找到适用于 Microsoft 的相关 NIST 证书号码 (https://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401vend.htm.)

> 便笺若要将 Microsoft 安全策略作为资源进行访问，必须使用工作或学校帐户登录。 如果你还没有订阅， [可以注册免费试用版](https://servicetrust.microsoft.com/Home/TrialSubscriptions)。

FIPS 140-2 是一种标准，专门用于验证实施加密的产品模块，而不是使用它们的产品。 在服务内实施的加密模块可以通过符合哈希强度、密钥管理等的要求进行认证。 任何时间都使用加密功能来保护 Microsoft 云服务中的数据的机密性、完整性或可用性，使用的模块和密码符合 FIPS 140-2 标准。

Microsoft 通过每个新版本的 Windows 操作系统证明在云服务中使用的基础加密模块：

- Azure 和 Azure 美国政府版
- Dynamics 365 和 Dynamics 365 美国政府
- Office 365、Office 365 U.S. Government 和 Office 365 U.S. Government Defense

静态客户数据的加密由多个服务端技术提供，其中包括 BitLocker、DKM、Azure 存储服务加密和 Exchange Online 中的服务加密、Skype for business、OneDrive for business 和 SharePoint Online。 Office 365 服务加密包含一个选项，可使用存储在 Azure Key Vault 中的客户托管的加密密钥。 此客户管理的密钥选项称为 " [客户密钥](https://docs.microsoft.com/microsoft-365/compliance/customer-key-overview)"，适用于 Exchange Online、SharePoint Online、Skype for Business 和 OneDrive for business。

对于传输中的客户数据，所有 Office 365 服务器在默认情况下将使用 TLS 与客户端计算机协商安全会话以保护客户数据。  这适用于客户端使用的任何设备（如 Skype for Business、Outlook 和 Outlook 网页版、移动客户端和 web 浏览器）上的协议。

默认情况下，所有面向客户的服务器都将协商为 TLS 1.2，但如果需要，我们还支持对低标准进行协商。 )  (

## <a name="related-links"></a>相关链接

- [Azure 中的加密](office-365-azure-encryption.md)
- [用于加密的 BitLocker 和 Distributed Key Manager (DKM)](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Office 365 服务加密](office-365-service-encryption.md)
- [适用于 Skype for business、OneDrive for Business、SharePoint Online 和 Exchange Online 的 Office 365 加密](office-365-encryption-for-skype-onedrive-sharepoint-and-exchange.md)
- [传输中的数据的加密](office-365-encryption-for-data-in-transit.md)
- [客户管理的加密功能](office-365-customer-managed-encryption-features.md)
- [加密风险和保护](office-365-encryption-risks-and-protections.md)
- [Microsoft Dynamics 365 中的加密](office-365-encryption-in-microsoft-dynamics-365.md)
