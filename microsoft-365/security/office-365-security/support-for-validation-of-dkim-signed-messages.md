---
title: 支持 DKIM 签名邮件验证
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a4c95148-a00c-4d12-85ed-88520b547d97
ms.collection:
- M365-security-compliance
description: 了解 Exchange Online Protection 和 Exchange Online 中的 DKIM 签名邮件验证
ms.openlocfilehash: e2e91fe426348487fa4dfa8ef929d2d8129ffddc
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48202133"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>支持 DKIM 签名邮件验证

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Exchange Online Protection (EOP) 和 Exchange Online 支持对域密钥进行入站验证，从而识别邮件 ([DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt)) 邮件。 DKIM 是一种方法，用于验证邮件是否已从其发出的域发送，以及其他人未被别人盗用。 这将电子邮件绑定到负责发送它的组织上。 DKIM 验证将自动用于通过 IPv6 通信发送的所有邮件。 在通过 IPv4 发送邮件时，Microsoft 365 现在也支持 DKIM。  (有关 IPv6 支持的详细信息，请参阅 [通过 ipv6 对匿名入站电子邮件的支持](support-for-anonymous-inbound-email-messages-over-ipv6.md)。 ) 

DKIM 可在邮件标头中验证出现在 DKIM 签名标头中的数字签名邮件。DKIM 签名验证的结果将标记在符合 RFC 7001（[用于指示邮件身份验证状态的邮件标头字段](https://www.rfc-editor.org/rfc/rfc7001.txt)）的身份验证结果标头中。邮件标头文本将如下所示（其中 contoso.com 是发件人）：

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

管理员可以创建 Exchange [邮件流规则](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (也称为传输规则) 在 DKIM 验证的结果中，以根据需要筛选或路由邮件。
