---
title: Office 365 邮件加密的旧信息
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 05/22/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.assetid: 5986b9e1-c824-4f8f-9b7d-a2b0ae2a7fe9
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 了解如何将旧版文件转换为 Office 365 邮件加密 (组织的 OME) 。
ms.openlocfilehash: 06c0e41d6c3b7cbf7d06bf6aae82742211bd2542
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2020
ms.locfileid: "47306501"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Office 365 邮件加密的旧信息

如果尚未将组织移动到新的 OME 功能，但已部署了 OME，则本文中的信息适用于您的组织。 Microsoft 建议您制定一个计划，尽快移动到新的 OME 功能，因为它对您的组织合理。 有关说明，请参阅 [设置基于 Azure 信息保护基础构建的新 Office 365 邮件加密功能](set-up-new-message-encryption-capabilities.md)。 如果您想要详细了解新功能的工作方式，请参阅 [Office 365 邮件加密](ome.md)。 本文的其余部分是在发布新的 OME 功能之前的 OME 行为。
  
使用 Office 365 邮件加密，组织可以在组织内部和外部的人员之间发送和接收加密的电子邮件。 Office 365 邮件加密适用于 Outlook.com、Yahoo、Gmail 和其他电子邮件服务。 电子邮件加密有助于确保只有预期的收件人可以查看邮件内容。
  
下面是一些示例：
  
- 银行员工向客户发送信用卡对帐单

- 保险业公司代表向客户提供策略详细信息

- 抵押经纪人请求来自客户的贷款申请的财务信息

- 医疗保健提供商向患者发送卫生保健信息

- 律师向客户或其他律师发送机密信息

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>如何在没有新功能的情况下运行 Office 365 邮件加密

Office 365 邮件加密是基于 Microsoft Azure 权限管理 (Azure RMS) 构建的联机服务。 使用 Azure RMS，管理员可以定义邮件流规则，以确定加密的条件。 例如，规则可以要求对发送到特定收件人的所有邮件进行加密。
  
观看此简短视频，了解 Office 365 邮件加密如何工作而无需新功能。
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c55540e7-f7f0-42f5-b254-4b2d2fbb1d63?autoplay=false]
  
当某人在 Exchange Online 中发送与加密规则匹配的电子邮件时，将使用 HTML 附件发送邮件。 收件人打开 HTML 附件并按照说明在 Office 365 邮件加密门户中查看加密邮件。 收件人可以选择使用 Microsoft 帐户或与 Office 365 关联的工作或学校登录，或使用一次性的 pass 代码来查看邮件。 两个选项均可以确保只有目标收件人可以查看加密邮件。 此过程对于新的 OME 功能非常不同。
  
下方的图表总结了电子邮件是如何通过加密和解密过程的。
  
![显示加密电子邮件路径的图表](../media/O365-Office365MessageEncryption-Concept.png)
  
有关详细信息，请参阅 [早期版本的 Office 365 邮件加密的服务信息，然后再发布新的 OME 功能](legacy-information-for-message-encryption.md#LegacyServiceInfo)。
  
## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities"></a>为不使用新 OME 功能的 Office 365 邮件加密定义邮件流规则

若要在不使用新功能的情况下启用 Office 365 邮件加密，Exchange Online 和 Exchange Online Protection 管理员将定义 Exchange 邮件流规则。 这些规则确定应在哪些条件下加密电子邮件，以及删除邮件加密的条件。 为规则设置加密操作后，与规则条件匹配的任何邮件在发送之前都会被加密。
  
邮件流规则是灵活的，允许您将条件组合在一起，以便您可以在单个规则中满足特定的安全要求。 例如，您可以创建一个规则，对包含特定关键字且发送给外部收件人的所有邮件进行加密。 Office 365 邮件加密还对加密邮件的收件人的回复进行加密；您可以创建一个规则来对这些回复进行解密，为您的电子邮件用户提供方便。 这样，组织中的用户无需登录到加密门户即可查看答复。
  
有关如何创建 Exchange 邮件流规则的详细信息，请参阅 [定义 Office 365 邮件加密的规则](define-mail-flow-rules-to-encrypt-email.md)。
  
## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>发送、查看和回复加密电子邮件

使用 Office 365 邮件加密时，电子邮件将根据管理员定义的规则自动加密。 携带加密邮件的电子邮件到达收件人的收件箱，并附带一个 HTML 文件。
  
收件人按照邮件中的说明打开附件，并使用 Microsoft 帐户或与 Office 365 相关联的工作或学校进行身份验证。 如果收件人没有任何帐户，则会将其定向到创建一个 Microsoft 帐户，让他们登录以查看加密邮件。 或者，收件人可以选择获取一次性传递代码来查看邮件。 登录或使用一次性传递代码后，收件人可以查看解密的邮件并发送加密答复。
  
## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>使用 Office 365 邮件加密自定义加密邮件

作为 Exchange Online 和 Exchange Online Protection 管理员，您可以自定义加密邮件。 例如，您可以添加公司的品牌和徽标，指定简介，并在加密邮件中以及在收件人查看加密邮件的门户中添加免责声明文本。 您可以使用 Windows PowerShell cmdlet 为加密的电子邮件的收件人自定义视觉体验的以下方面：
  
- 包含加密邮件的电子邮件介绍性文本

- 包含加密邮件的电子邮件免责声明文本

- 显示在邮件查看门户中的门户文本

- 显示在电子邮件和查看门户中的徽标

您也可以随时还原到默认的外观。
  
以下示例显示电子邮件附件中的 ContosoPharma 的自定义徽标：
  
![查看加密消息页面的示例](../media/TA-OME-3attachment2.jpg)
  
 **自定义加密电子邮件以及与组织品牌的加密门户**
  
1. 使用远程 PowerShell 连接到 Exchange Online，如 [connect To Exchange Online Using Remote powershell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)中所述。

2. 按照如下所述使用 Set-omeconfiguration cmdlet： [set-omeconfiguration](https://technet.microsoft.com/3ef0aec0-ce28-411d-abe8-7236f082af1b) 或使用下表进行指南。

   **加密自定义选项**

|**自定义加密体验的这一功能**|**使用这些 Windows PowerShell 命令**|
|:-----|:-----|
|加密电子邮件随附的默认文本  <br/> 默认文本显示在说明的上方，以查看加密邮件  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <br/> **示例：** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"` <br/> |
|包含加密邮件的电子邮件中的免责声明  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <br/> **示例：** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"` <br/> |
|显示在加密邮件查看门户顶部的文本  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <br/> **示例：** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"` <br/> |
|徽标  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <br/> **示例：** `Set-OMEConfiguration -Identity "OME configuration" -Image (Get-Content "C:\Temp\contosologo.png" -Encoding byte)` <br/> 支持的文件格式：.png、.jpg、.bmp 或 .tiff  <br/> 徽标文件的最佳大小：小于 40 KB  <br/> 徽标图像的最佳大小：170x70 像素  <br/> |

 **从加密电子邮件和加密门户中删除品牌自定义**
  
1. 使用远程 PowerShell 连接到 Exchange Online，如 [connect To Exchange Online Using Remote powershell](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx)中所述。

2. 按照如下所述使用 Set-omeconfiguration cmdlet： [set-omeconfiguration](https://technet.microsoft.com/3ef0aec0-ce28-411d-abe8-7236f082af1b)。 若要从 DisclaimerText、EmailText 和 PortalText 值中删除您的组织的标记自定义项，请将该值设置为一个空字符串  `""` 。 对于所有图像值（如 "徽标"），请将值设置为  `"$null"` 。

   **加密自定义选项**

|**将加密体验的此功能还原到默认的文本和图片**|**使用这些 Windows PowerShell 命令**|
|:-----|:-----|
|加密电子邮件随附的默认文本  <br/> 默认文本显示在说明的上方，以查看加密邮件  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <br/> **示例：** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""` <br/> |
|包含加密邮件的电子邮件中的免责声明  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <br/> **示例：** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""` <br/> |
|显示在加密邮件查看门户顶部的文本  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <br/> **将恢复为默认值的示例：**`Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""` <br/> |
|徽标  <br/> | `Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <br/> **将恢复为默认值的示例：**`Set-OMEConfiguration -Identity "OME configuration" -Image $null` <br/> |

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>在新的 OME 功能发布之前的旧版 Office 365 邮件加密的服务信息
<a name="LegacyServiceInfo"> </a>

下表提供了在发布新的 OME 功能之前的 Office 365 邮件加密服务的技术详细信息。
  
|**服务详细信息**|**说明**|
|:-----|:-----|
|客户端设备要求  <br/> |只要 HTML 附件可以在支持窗体发布的现代浏览器中打开，就可以在任何客户端设备上查看加密邮件。  <br/> |
|加密算法和美国联邦信息处理标准 (FIPS) 合规性  <br/> |Office 365 邮件加密使用与 Windows Azure 信息权限管理 (IRM) 相同的加密密钥，并支持加密模式 2（对于 RSA 是 2K 密钥，对于 SHA-1 系统是 256 位密钥）。 有关基础 IRM 加密模式的详细信息，请参阅 [AD RMS 加密模式](https://technet.microsoft.com/library/hh867439%28WS.10%29.aspx)。  <br/> |
|支持的邮件类型  <br/> |如果是针对那些具有 **IPM.Note** 的邮件类 ID 项，才支持使用 Office 365 邮件加密。 有关详细信息，请参阅 [项目类型和邮件类](https://msdn.microsoft.com/library/office/ff861573.aspx)。  <br/> |
|邮件大小限制  <br/> |Office 365 邮件加密可以加密最多 25 兆字节的邮件。 有关邮件大小限制的详细信息，请参阅 [Exchange Online 限制](https://technet.microsoft.com/library/exchange-online-limits.aspx)。  <br/> |
|Exchange Online 电子邮件保留策略  <br/> |Exchange Online 不存储加密的邮件。  <br/> |
|Office 365 邮件加密的语言支持  <br/> | Office 365 邮件加密支持 Microsoft 365 语言，如下所示：  <br/>  传入的电子邮件和附加的 HTML 文件根据发件人的语言设置进行本地化。  <br/>  查看门户根据收件人的浏览器设置进行本地化。  <br/>  加密邮件的正文（内容）不进行本地化。  <br/> |
|OME 门户和 OME 查看器应用的隐私信息  <br/> |[Office 365 Messaging Encryption Portal privacy statement](https://privacy.microsoft.com/privacystatement)提供了有关 Microsoft 如何处理您的隐私信息的详细信息。  <br/> |

## <a name="frequently-asked-questions-about-legacy-ome"></a>有关旧 OME 的常见问题
<a name="LegacyServiceInfo"> </a>

遇到有关 Office 365 邮件加密的问题？ 下面对一些问题进行了解答。 如果找不到所需的内容，请查看 [适用于 Office 365 的 Microsoft 技术社区论坛](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365)。
  
 **增长率.我的用户将加密的电子邮件发送给组织外部的收件人。外部收件人是否有需要执行哪些操作才能阅读并回复通过 Office 365 邮件加密加密的电子邮件？**
  
组织外部接收 Microsoft 365 加密邮件的收件人可以通过以下两种方式之一查看：
  
- 通过使用与 Office 365 关联的 Microsoft 帐户或工作或学校帐户登录。

- 通过使用一次性的 pass 代码。

 **增长率.Microsoft 365 加密邮件是否存储在云中或 Microsoft 服务器上？**
  
否，加密的邮件将保留在收件人的电子邮件系统中，当收件人打开邮件时，它将暂时发布，以便在 Microsoft 服务器上进行查看。 邮件并不存储在其中。
  
 **问：能否使用我的品牌自定义加密电子邮件？**
  
正确。 您可以使用 Windows PowerShell cmdlet 自定义在加密的电子邮件顶部显示的默认文本、免责声明文本以及要用于电子邮件和加密门户的徽标。 有关详细信息，请参阅 [将品牌添加到加密邮件](add-your-organization-brand-to-encrypted-messages.md)。
  
 **问：该服务是否要求我的组织中的每个用户都有许可证？**
  
组织中发送加密电子邮件的每个用户都必须有许可证。
  
 **问：外部收件人是否需要订阅？**
  
否，外部收件人不需要订阅即可阅读或回复加密邮件。
  
 **增长率.Office 365 邮件加密与 Rights Management Services (RMS) 的不同之处？**
  
RMS 通过提供内置模板（例如：不要转发和公司机密）为组织的内部电子邮件提供信息权限保护功能。 Office 365 邮件加密支持对发送给外部以及内部收件人的邮件进行加密。
  
 **增长率.Office 365 邮件加密与 S/MIME 有何不同？**
  
S/MIME 实质上是一种客户端加密技术，需要复杂的证书管理和发布基础结构。 Office 365 邮件加密使用邮件流规则 (也称为传输规则) ，而不依赖于证书发布。
  
 **问：能否通过移动设备阅读加密邮件？**
  
可以，通过从 Google Play 商店和 Apple App store 下载 OME 查看器应用程序，可以查看 Android 和 iOS 上的邮件。 在 OME 查看器应用程序中打开 HTML 附件，然后按照说明打开加密邮件。 对于其他移动设备，只要您的邮件客户端支持表单发布，就可以打开 HTML 附件。
  
 **问：是否对回复和转发的邮件进行加密？**
  
是，在整个线程期限内，响应都会继续进行加密。
  
 **增长率.Office 365 邮件加密是否提供本地化？**
  
传入电子邮件和 HTML 内容会进行本地化，具体取决于发件人电子邮件设置。查看门户根据收件人的浏览器设置进行本地化。不过，加密邮件的实际正文（内容）不会进行本地化。
  
 **增长率.Office 365 邮件加密使用什么加密方法？**
  
Office 365 邮件加密使用 Rights Management Services (RMS) 作为其加密基础结构。 所使用的加密方法取决于从何处获取用来加密和解密邮件的 RMS 密钥。
  
- 如果使用 Microsoft Azure RMS 获取密钥，则使用加密模式2。 加密模式 2 是更新和增强的 AD RMS 加密实现。 它支持 RSA 2048 签名和加密，并支持 sha-256 签名。

- 如果您使用 Active Directory (AD) RMS 获取这些密钥，则可以使用加密模式 1，也可以使用加密模式 2。使用的方法取决于您的本地 AD RMS 部署。加密模式 1 是原始的 AD RMS 加密实现。它支持 RSA 1024 签名和加密，并支持 sha-1 签名。该模式继续支持 RMS 的所有当前版本。

有关详细信息，请参阅 [AD RMS 加密模式](https://go.microsoft.com/fwlink/p/?LinkId=398616)。
  
 **问：为什么有些加密邮件说它们** 来自 Office365@messaging.microsoft.com？
  
当加密回复从加密门户或通过 OME 查看器应用发送时，发送电子邮件地址将设为 Office365@messaging.microsoft.com，因为该加密邮件是通过 Microsoft 终结点发送的。这有助于防止加密邮件被标记为垃圾邮件。电子邮件上显示的名称和加密门户内的地址不会因为这个标签而更改。此外，该标签仅适用于通过门户而不是通过任何其他电子邮件客户端发送的邮件。
  
 **增长率.我是 Exchange 托管加密 (EHE) 订阅者。在哪里可以了解有关升级到 Office 365 邮件加密的更多信息？**
  
所有 EHE 客户已升级为 Office 365 邮件加密客户。 有关详细信息，请访问 [Exchange 托管加密升级中心](https://go.microsoft.com/fwlink/p/?LinkID=511077)。
  
 **增长率.我是否需要在组织的防火墙中打开任何 Url、IP 地址或端口以支持 Office 365 邮件加密？**
  
正确。 您必须将 Exchange Online 的 Url 添加到组织的允许列表，以便为通过 Office 365 邮件加密加密的邮件启用身份验证。 有关 Exchange Online Url 的列表，请参阅 [Microsoft 365 url 和 IP 地址范围](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges)。
  
 **增长率.有多少个收件人可以向其发送 Microsoft 365 加密邮件？**
  
每封 **邮件的收件人** 数限制为500个收件人，或者，在通讯组列表展开后加上11980个字符（无论哪种情况先发生）。
  
 **问：是否可以取消发送给特定收件人的邮件？**
  
否。 发送邮件后，不能向该用户撤销邮件。
  
 **问：是否可以查看已接收和阅读的加密邮件报告吗？**
  
没有显示已查看加密邮件的报告，但有 Microsoft 365 报告可用于确定与特定邮件流规则匹配的邮件数 (也称为传输规则) ，例如 "传输规则"）。
  
 **问：Microsoft 会如何处理我通过 OME 门户和 OME 查看器应用提供的信息？**
  
[Office 365 邮件加密门户隐私声明](https://privacy.microsoft.com/privacystatement)提供了有关 Microsoft 在你的私人信息方面所做的操作和不会执行的操作的详细信息。

## <a name="what-do-i-do-if-i-dont-receive-the-one-time-pass-code-after-i-requested-it"></a>如果我在请求一次性处理后未收到此代码，我该怎么办？

首先，检查电子邮件客户端中的 "垃圾邮件" 或 "垃圾邮件" 文件夹。 您的组织的 DKIM 和 DMARC 设置可能会导致这些电子邮件最终被筛选为垃圾邮件。

接下来，检查安全性 & 合规性中心中的 "隔离"。 通常情况下，包含一次性传递代码的邮件（尤其是您的组织收到的第一次代码）将最终成为隔离。
