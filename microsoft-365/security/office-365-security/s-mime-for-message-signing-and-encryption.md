---
title: Exchange Online 中用于加密的 S/MIME-Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 887c710b-0ec6-4ff0-8065-5f05f74afef3
description: 管理员可以了解如何使用 S/MIME (安全/多用途 Internet 邮件扩展在 Exchange Online 中) 加密电子邮件并对其进行数字签名。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8dce3e3fa3d24e1773f51f96e19a58d8a3b2efce
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48200603"
---
# <a name="smime-for-message-signing-and-encryption-in-exchange-online"></a>Exchange Online 中的邮件签名和加密的 S/MIME

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


S/MIME (安全/多用途 Internet 邮件扩展) 是一种广泛接受的方法， (更准确地说是发送数字签名和加密邮件的协议) 。 S/MIME 允许你加密电子邮件，并对它们进行数字签名。 当您在电子邮件中使用 S/MIME 时，将会帮助接收该邮件的人确信他们在 "收件箱" 中看到的内容与发件人启动的邮件完全一致。 它还将帮助接收邮件的用户确信邮件来自特定发件人，而不是假装为发件人的人。 为此，S/MIME 提供了加密安全服务，例如身份验证、邮件完整性和防发送方抵赖（使用数字签名）。 它还有助于增强隐私和数据安全 (使用电子邮件的加密) 。 有关电子邮件上下文中 S/MIME 的历史记录和体系结构的更多完整背景，请参阅[了解 S/MIMEE](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65))。

作为 Exchange Online 管理员，您可以为组织中的邮箱启用基于 S/MIME 的安全性。 使用此处链接的主题和 Exchange Online PowerShell 中的指导设置 S/MIME。 若要在受支持的电子邮件客户端中使用 S/MIME，组织中的用户必须为签名和加密目的颁发证书，并将发布到内部部署 Active Directory 域服务 (AD DS) 的数据。 您的 AD DS 必须位于您控制的物理位置的计算机上，而不是位于 internet 上某个位置的远程设施或基于云的服务中。 有关 AD DS 的详细信息，请参阅 [Active Directory 域服务概述](https://docs.microsoft.com/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)。

## <a name="supported-scenarios-and-technical-considerations"></a>支持的方案和技术注意事项

可以将 S/MIME 设置为用于以下任一终结点：

- Outlook 2010 或更高版本
- Web 上的 Outlook（以前称为 Outlook Web App）
- Exchange ActiveSync (EAS)

为每个终结点设置 S/MIME 所遵循的步骤略有不同。 通常，您需要执行以下步骤：

1. 安装基于 Windows 的证书颁发机构 (CA) 并设置公钥基础结构，以颁发 S/MIME 证书。 此外，还支持第三方证书提供商颁发的证书。 有关详细信息，请参阅 [Active Directory 证书服务概述](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831740(v=ws.11))。

   **注意**：

   - 由第三方 CA 颁发的证书具有由所有客户端和设备自动信任的优势。 由内部专用 CA 颁发的证书不会由客户端和设备自动信任，并不是所有设备 (例如，可以将电话) 配置为信任专用证书。

   - 考虑使用中间证书而不是根证书向用户颁发证书。 这样，如果您需要吊销和重新颁发证书，根证书仍保持不变。

2. 在 **UserSMIMECertificate** 和/或 **UserCertificate** 属性中的本地 AD DS 帐户中发布用户证书。

3. 对于 Exchange Online 组织，使用相应版本的 Azure AD Connect 将用户证书从 AD DS 同步到 Azure Active Directory。 然后，这些证书将从 Azure Active Directory 同步到 Exchange Online 目录，并将在将邮件加密给收件人时使用。

4. 设置虚拟证书集合以验证 S/MIME。此信息供 Web 上的 Outlook 用于验证电子邮件的签名并确保它是由可信证书签名的。

5. 将 Outlook 或 EAS 终结点设置为使用 S/MIME。

> [!NOTE]
> 无法在 Mac、iOS、Android 或其他非 Windows 设备上的 web 上的 Outlook 中安装 S/MIME 控件。 有关详细信息，请参阅 [web 上的在 Outlook 中使用 S/MIME 加密邮件](https://support.microsoft.com/office/878c79fc-7088-4b39-966f-14512658f480)。

## <a name="setup-smime-with-outlook-on-the-web"></a>设置 web 上的 Outlook 的 S/MIME

使用 web 上的 Outlook 为 Exchange Online 设置 S/MIME 涉及以下关键步骤：

1. [配置 Outlook 网页版的 S/MIME 设置](configure-s-mime-settings-for-outlook-web-app.md)
2. [设置虚拟证书集合以验证 S/MIME](set-up-virtual-certificate-collection-to-validate-s-mime.md)
3. [出于 S/MIME 目的将用户证书同步到 Office 365](sync-user-certificates-to-office-365-for-s-mime.md)

## <a name="related-message-encryption-technologies"></a>相关邮件加密技术

随着邮件安全性变得更加重要，管理员需要了解安全邮件的原则和概念。 此理解尤其重要，因为在不断增多的保护相关技术 (包括 S/MIME) 可用。 若要详细了解 S/MIME 以及它在电子邮件上下文中的工作方式，请参阅 [了解 s/mime](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65))。 各种加密技术协同工作，为静态和传输中的邮件提供保护。 S/MIME 可以同时与以下技术一起使用，但不依赖于它们：

- **传输层安全性 (TLS) ** 对电子邮件服务器之间的隧道或路由进行加密，以帮助防止窥探和窃听。

- **安全套接字层 (SSL) ** 对电子邮件客户端和 Microsoft 365 服务器之间的连接进行加密。

- **BitLocker** 将对数据中心中的硬盘驱动器上的数据进行加密，以便在有人未经授权访问的情况下对其进行读取。

### <a name="smime-compared-with-office-365-message-encryption"></a>S/MIME 与 Office 365 邮件加密进行比较

S/MIME 需要证书和发布基础结构，通常用于企业到企业和企业到消费者的情况。 用户控制 S/MIME 中的加密密钥，并且可以选择是否为他们发送的每封邮件使用密钥。 Outlook 等电子邮件程序搜索可信任根证书颁发机构位置，以执行数字签名和签名验证。 Office 365 邮件加密是一种基于策略的加密服务，可由管理员而不是单个用户配置，以加密发送给组织内部或外部的任何人的邮件。 它是基于 Azure 权限管理 (RMS) 构建的在线服务，不依赖公钥基础结构。 Office 365 邮件加密还提供了其他功能，例如，使用组织品牌自定义邮件的功能。 有关 Office 365 邮件加密的详细信息，请参阅 [office 365 中的加密](https://docs.microsoft.com/microsoft-365/compliance/encryption)。

## <a name="more-information"></a>更多信息

[Outlook 网页版](https://docs.microsoft.com/exchange/exchange-admin-center)

[安全邮件 (2000) ](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc962043(v=technet.10))
