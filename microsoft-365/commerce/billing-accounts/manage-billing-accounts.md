---
title: 管理帐单帐户
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- commerce
ms.custom: ''
search.appverid:
- MET150
description: 了解有关计费帐户以及如何管理这些帐户的信息。
ms.openlocfilehash: 9ea96a0187a1f4bec9c71dc02478375a4c13b371
ms.sourcegitcommit: 95a07b328166f637a481c8b5c53669eaf8ff0db8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2019
ms.locfileid: "39837955"
---
# <a name="manage-billing-accounts"></a>管理帐单帐户

在你注册以试用或购买 Microsoft 产品时，将创建一个帐单帐户。 您可以使用付费帐户管理帐户设置、发票、付款方式和购买。 您可以访问多个记帐帐户。 例如，您直接注册了 Microsoft 365，或者您有权访问组织的企业协议、Microsoft 产品 & 服务协议或 Microsoft 客户协议。 对于上述每个方案，您都有一个单独的帐单帐户。

Microsoft 365 admin center 目前支持以下类型的计费帐户：

- Microsoft Online Services 程序：当您直接注册 Microsoft 365 订阅时，将创建此帐单帐户。
- Microsoft Products & Services 协议（MPSA）程序：当您的组织签署 MPSA 批量许可协议以购买软件和在线服务时，会创建此帐单帐户。
- Microsoft 客户协议：当组织与 Microsoft 代表、授权合作伙伴或单独购买时，将创建此帐单帐户。

"<a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">记帐帐户</a>" 页面提供了使用 Microsoft 的商业帐户视图。 默认情况下，您的组织至少有一个与协议关联的帐单帐户，该帐户在直接购买时或通过批量许可排列接受。

## <a name="understand-billing-account-details"></a>了解帐单帐户详细信息

"**付费帐户**详细信息" 页的顶部是您的帐户配置文件，其中包含有关您的组织的法律和税务信息。 您可以更新您的配置文件，以更改您的合法地址和电话号码。 此帐户是支付所购买产品的法定法人。

下表列出了您在**记帐帐户**详细信息页面中看到的重要术语。

| 字段名 | 说明 |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 售出地址 | 负责在发票上付款和标识的法人。 此处提供的地址用于确定您的税率，除非您在购买过程中选择提供备选送货地址。 有关详细信息，请参阅[税务信息](#tax-information)。 |
| 段落 | 一个只读字段，用于标识组织的业务部门（商业、教育、政府或非盈利）。 |
| 帐户状态 | 一个只读字段，用于指定你的商业帐户与 Microsoft 的状态。 |
| 税号 | 如果你不在美国，则必须提供 VAT 或当地的等价国家/地区。 有关详细信息，请参阅[税务信息](#tax-information)。 |
| 本 | 在创建计费帐户（通过直接购买或批量许可安排）时，组织的签字人接受或签署一个协议，该协议描述了帐户 & 条件的条款。 如果适用，此视图列出协议历史记录。 如果需要接受更新的术语，则显示 "**审批协议**" 的链接。 |
| 计费配置文件 | 计费配置文件定义发票的属性，如接收帐单的用户、帐单的交货方式、付款期限和采购订单编号。 若要在组织中分发帐单，可以创建多个记帐配置文件，并在购买时标识相应的记帐配置文件。 有关计费配置文件以及如何使用它们为组织生成更灵活的记帐选项的详细信息，请[管理计费配置文件](../billing-and-payments/manage-billing-profiles.md)。 |

## <a name="shipping-addresses"></a>送货地址

此部分列出了与您的付费帐户关联的送货地址。 在购买产品时，您可以使用此地址来确定购买或使用购买的位置。 送货地址是可编辑的。 您可以添加送货地址或更新现有地址。 此地址用于确定购买的税率。

## <a name="understand-access-to-billing-accounts"></a>了解对帐单帐户的访问权限

你可以通过角色和权限向其他人提供对 Microsoft 365 管理中心中的帐单帐户的访问权限。 只有付费帐户所有者可以授予对帐单帐户的访问权限。 您可以向用户分配以下角色之一：

- **帐单帐户所有者** &mdash;可以分配权限、编辑帐户、签署协议和查看帐户。
- **帐单帐户参与者** &mdash;可以编辑帐户、签署协议和查看帐户。
- **帐单帐户读取器** &mdash;可以查看帐户。

> [!Note]
> 帐单帐户角色仅适用于付费帐户，不适用于其他 Microsoft 365 管理中心方案。

## <a name="tax-information"></a>税务信息

通过 Microsoft 进行的 Microsoft 365 管理中心购买的税款由你的公司地址确定，如果你的发货地址不同，则由你的发货地址确定。 如果你使用的是美国，则必须提供联邦雇主标识号（FEIN）。

这些国家/地区的企业可以提供其 VAT 号码：

:::row:::
    :::column:::
- 奥地利
- 比利时
- 保加利亚语
- 克罗地亚
- 塞浦路斯
- 捷克共和国
- 丹麦
- 爱沙尼亚
- 芬兰
- 法国
- 德国
- 希腊
- 匈牙利
- 爱尔兰
- 意大利
- 拉脱维亚
    :::column-end:::
    :::column:::
- Liechtenstein（列支敦士登）
- 立陶宛
- 卢森堡
- 马耳他
- Monaco（摩纳哥）
- 荷兰
- 挪威
- 波兰
- 葡萄牙
- 罗马尼亚
- 斯洛伐克
- 南非
- 西班牙
- 瑞典
- 瑞士
- 英国
    :::column-end:::
:::row-end:::

这些国家/地区可在其付费帐户信息中提供其 VAT 号码或当地等价号码。

|宣传| 税标识符 |
|------|----------------|
| 澳大利亚 | ABN （可选） |
| 巴西 | CNPJ （必需） |
| 印度 | GSTIN （可选），PAN ID （必需） |
| 马恩岛 | VAT ID （可选） |
| JPRatingExplicitAllowed | GST 注册号码（可选） |
| Monaco（摩纳哥） | VAT ID （可选） |
| 中国台湾 | VAT ID （可选） |

> [!Note]
> 如果需要联系支持人员，请将您的 FEIN、VAT 号码或当地等效项准备就绪，以提供给支持代理。

## <a name="tax-exempt-status"></a>免税状态

如果您在市场上有资格享受免税状态，请[启动服务请求](https://docs.microsoft.com/office365/admin/contact-support-for-business-products)来为您的组织建立免税状态。

准备好以下文档：

|国家或地区 | 文档 |
|------------------|----------------|
| 美国 | 销售税豁免证书 |
| 加拿大 | 豁免证书（或等效的授权书） |
| 爱尔兰 | 13B/56A 税务豁免证书|
| 持有免税的国际组织 | 来自当地税务主管机构的认证/信函确认 |
| 波多黎各 | Certificado de Compras Exentas |

## <a name="calculate-taxes"></a>计算税金

增值税按单价计算，然后进行聚合。

例如：

>*（单价 X 税率）X 数量 = 总销售税*

- 或 -

>（$1.29 X 0.095）X 100 = $12.25