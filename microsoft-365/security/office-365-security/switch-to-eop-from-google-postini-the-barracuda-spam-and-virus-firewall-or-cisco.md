---
title: 从另一保护服务切换到 EOP
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
ms.assetid: 81b75194-3b04-48da-8b81-951afbabedde
ms.custom:
- seo-marvel-apr2020
description: 在本文中，您将了解如何从本地电子邮件清洁设备或基于云的保护服务切换到 Exchange Online Protection (EOP) 。
ms.openlocfilehash: 25669982c06127331369fdb595c6614733681047
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48202121"
---
# <a name="switch-to-eop-from-google-postini-the-barracuda-spam-and-virus-firewall-or-cisco-ironport"></a>从 Google Postini、Barracuda 垃圾邮件和病毒防火墙或 Cisco IronPort 切换到 EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


 本主题的目的是帮助您了解从内部部署电子邮件卫生设备或基于云的保护服务切换到 Exchange Online Protection (EOP) 的过程，然后为您提供开始操作的帮助资源。有许多垃圾邮件筛选解决方案，但是在大多数情况下切换到 EOP 的过程是相似的。

如果您刚开始使用 EOP，并且想要在决定切换之前阅读其功能的概述，请从 [Exchange Online Protection 概述](exchange-online-protection-overview.md) 主题开始。

在切换到 EOP 之前，有必要考虑是要在云中、Exchange Online、内部部署还是在混合方案中托管 EOP 保护的邮箱。（混合方案意味着某些邮箱在内部部署中托管，其他一些邮箱使用 Exchange Online 托管。）各托管方案：可能是云、内部部署和混合，但安装步骤可能有所不同。有一些考虑事项可帮助您选择合适的部署：

- **使用本地邮箱的 EOP 保护**：如果您有要使用的现有邮件托管基础结构，或者您有业务要求将邮箱保留在本地，并且您希望将 EOP 用作基于云的电子邮件保护，则此方案适用。 [独立切换到 EOP](#switch-to-eop-standalone)详细描述了此方案。

- **使用 Exchange Online 邮箱的 EOP 保护**：如果您希望 EOP 保护和在云中托管的所有邮箱，则此方案适用。 它可以帮助您降低复杂性，因为您不必维护内部部署邮件传递服务器。 [切换到 Exchange Online](#switch-to-exchange-online) 描述了此方案。

- **使用混合邮箱的 EOP 保护**：或许您需要云邮箱，但您需要为本地的一些用户保留邮箱。 如果您希望在内部部署中托管某些邮箱并使用 Exchange Online 托管其他邮箱，则选择此方案。 [切换到混合解决方案](#switch-to-a-hybrid-solution)描述了此方案。

## <a name="switch-to-eop-standalone"></a>独立切换到 EOP

如果当前在内部部署中托管邮箱，并使用内部部署保护设备或云邮件传递保护服务，则可以切换到 EOP 以利用其保护功能和可用性。要在独立方案中设置 EOP（这意味着在内部部署中托管邮箱并使用 EOP 提供电子邮件保护），可以按照[设置 EOP 服务](set-up-your-eop-service.md)中所述的步骤执行操作。该主题概述了设置 EOP 保护的步骤，包括注册、添加域和使用连接器设置邮件流。

## <a name="switch-to-exchange-online"></a>切换到 Exchange Online

或许您有本地邮箱受本地设备保护，并且您希望跳转到 Exchange Online 云托管邮箱和 EOP 保护以利用 Microsoft 365 云邮件和保护功能。 若要开始，你可以注册 Microsoft 365 并添加你的域。 此方案不需要设置连接器，因为不存在到本地邮箱的任何路由。 请从 [使用 Microsoft 365 获取最新的高级功能](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans) 开始注册并熟悉其功能。

在 Microsoft 365 安装过程中，将创建基于云的邮箱用户。

## <a name="switch-to-a-hybrid-solution"></a>切换到混合解决方案

出于业务需要或法规考虑，您可能希望仅将一部分邮箱移动到云。当部署混合方案时，可以根据业务需要指示，将邮箱移动到云。迁移到具有 EOP 保护的混合方案比移动到全云方案更复杂，但是 Microsoft 提供了完全的混合支持和广泛的资源以使移动到混合方案更加简便。

如果考虑使用混合部署，最好的起点是 [Exchange Server 混合部署](https://docs.microsoft.com/exchange/exchange-hybrid)。 另外，有几种不同的在混合方案中路由邮件的方式需要重点了解。 [Exchange 混合部署中的传输路由](https://docs.microsoft.com/exchange/transport-routing) 对每种类型进行了说明，因此您可以根据业务需求选择最佳的路由方案。

## <a name="migration-planning"></a>迁移计划

当决定切换到 EOP 时，请确保特别留意下列几个方面：

- **自定义筛选规则**：如果您有自定义筛选或业务策略规则来捕获特定垃圾邮件，我们建议您在迁移规则之前，尝试使用默认设置 EOP 一段时间。 EOP 提供了具有默认设置的企业级垃圾邮件保护，这可能表示您不需要将某些规则迁移到 EOP。 当然，如果您有现成的强制特定自定义业务策略的规则，则可以创建这些规则。 [ (传输规则) 在 Exchange Online Protection 中的邮件流规则](mail-flow-rules-transport-rules-0.md) 提供了有关在 EOP 中创建邮件流规则的详细说明。

- **Ip 允许列表和 ip 阻止列表**：如果您具有每用户允许列表和阻止列表，请在设置过程中允许一些时间将列表复制到 EOP。 有关 IP 允许列表和 IP 阻止列表的详细信息，请参阅 [Configure the connection filter policy](configure-the-connection-filter-policy.md)。

- **安全通信**：如果有需要加密消息的合作伙伴，我们建议您在 Exchange 管理中心中对此进行设置。 若要配置此方案，请参阅 [设置连接器以确保与合作伙伴组织的安全邮件流](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)。

> [!TIP]
> 从内部部署设备切换到 EOP 时，可以就地离开执行业务规则检查的设备或服务器。 例如，如果您的设备对出站邮件执行自定义筛选，并且您希望它继续执行此操作，则可以将 EOP 配置为将邮件直接发送到设备，以便在将邮件路由到 internet 之前进行其他筛选。
