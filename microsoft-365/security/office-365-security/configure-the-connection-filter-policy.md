---
title: 配置默认连接筛选器策略
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
ms.assetid: 6ae78c12-7bbe-44fa-ab13-c3768387d0e3
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 管理员可以了解如何在 Exchange Online Protection (EOP) 中配置连接筛选，以允许或阻止来自电子邮件服务器的电子邮件。
ms.openlocfilehash: 95e178e34c944c13cd99e4d4a0e9f30ed083842c
ms.sourcegitcommit: 61ef32f802a1fb6d1e3a3aa005764ead32a7951e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2020
ms.locfileid: "48318248"
---
# <a name="configure-connection-filtering"></a>配置连接筛选

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


如果您是在 Exchange Online 中使用邮箱的 Microsoft 365 客户或独立 Exchange Online Protection (EOP) 不含 Exchange Online 邮箱的客户，请使用 EOP 中的连接筛选 (具体来说，默认的连接筛选器策略) 以根据其 IP 地址识别好或坏的源电子邮件服务器。 默认连接筛选器策略的关键组件为：

- **IP 允许列表**：跳过来自您通过 ip 地址或 ip 地址范围指定的源电子邮件服务器的所有传入邮件的垃圾邮件筛选。 对于来自这些来源的邮件，可能仍会出现垃圾邮件筛选的情况，请参阅本主题后面的 " [仍在筛选 IP 允许列表中的邮件"](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) 部分中的 "来自此来源的邮件" 部分。 有关 IP 允许列表应适合您的整体安全发件人策略的详细信息，请参阅 [在 EOP 中创建安全发件人列表](create-safe-sender-lists-in-office-365.md)。

- **Ip 阻止列表**：阻止来自您通过 ip 地址或 ip 地址范围指定的源电子邮件服务器的所有传入邮件。 传入的邮件将被拒绝，不会被标记为垃圾邮件，并且不会发生其他筛选。 有关 IP 阻止列表应适合您的总体阻止发件人策略的详细信息，请参阅 [EOP 中的创建阻止发件人列表](create-block-sender-lists-in-office-365.md)。

- **安全列表**： *安全列表* 是 Microsoft 数据中心中不需要客户配置的动态允许列表。 Microsoft 会将这些受信任的电子邮件源标识为对各种第三方列表的订阅。 启用或禁用安全列表的使用;您不能在安全列表上配置源电子邮件服务器。 从安全列表上的电子邮件服务器传入的邮件中跳过垃圾邮件筛选。

本主题介绍了如何在 Exchange Online 中使用邮箱在安全 & 合规中心或 PowerShell (Exchange Online PowerShell 中配置默认连接筛选器策略; 在 Exchange Online 中，可使用邮箱来配置 Microsoft 365 组织;没有 Exchange Online 邮箱) 组织的独立 EOP PowerShell。 有关 EOP 如何使用连接筛选的详细信息，请参阅贵组织的整体反垃圾邮件设置的一部分。请参阅 [反垃圾邮件保护](anti-spam-protection.md)。

> [!NOTE]
> IP 允许列表、安全列表和 IP 阻止列表是您在组织中允许或阻止电子邮件的总体策略中的一个部分。 有关详细信息，请参阅 [创建安全发件人列表](create-safe-sender-lists-in-office-365.md) 和 [创建阻止的发件人列表](create-block-sender-lists-in-office-365.md)。

## <a name="what-do-you-need-to-know-before-you-begin"></a>开始前，有必要了解什么？

- 安全与合规中心的打开网址为 <https://protection.office.com/>。 若要直接转到 **“反垃圾邮件设置”** 页，请访问 <https://protection.office.com/antispam>。

- 若要连接到 Exchange Online PowerShell，请参阅[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)。 若要连接到独立 EOP PowerShell，请参阅[连接到 Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell)。

- 你必须首先分配有权限，然后才能执行本主题中的步骤：

  - 若要修改默认连接筛选器策略，您必须是下列角色组之一的成员：

    - [安全和合规中心](permissions-in-the-security-and-compliance-center.md)中的“**组织管理**”或“**安全管理员**”。
    - [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) 中的“**组织管理**”或“**清洁管理**”。

  - 若要对默认连接筛选器策略进行只读访问，您必须是下列角色组之一的成员：

    - [安全与合规中心](permissions-in-the-security-and-compliance-center.md)内的“**安全读取者**”。
    - [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) 中的“**仅查看组织管理**”。

- 若要查找要允许或阻止的电子邮件服务器 (发件人) 的源 IP 地址，可以检查邮件头中的 "连接 IP (**CIP**) 标头" 字段。 若要查看各种电子邮件客户端中的邮件头，请参阅 [在 Outlook 中查看 internet 邮件头](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c)。

- IP 允许列表的优先级高于 IP 阻止列表 (两个列表上的地址不会被阻止) 。

- 每个 IP 允许列表和 IP 阻止列表都支持最多1273个条目，其中条目是单个 IP 地址、IP 地址范围或无类别域间路由 (CIDR) IP。

## <a name="use-the-security--compliance-center-to-modify-the-default-connection-filter-policy"></a>使用安全 & 合规性中心修改默认连接筛选器策略

1. 在安全 & 合规性中心并转到 **威胁管理** \> **策略** \> **反垃圾邮件**。

2. 在 "**反垃圾邮件设置**" 页上，单击 "展开图标"，然后单击 "编辑策略"，展开 "**连接筛选器策略** ![ ](../../media/scc-expand-icon.png) "。 **Edit policy**

3. 在出现的 **默认** 浮出控件中，配置以下任一设置：

   - **说明**：输入可选的描述性文本。

   - **IP 允许列表**：单击 " **编辑**"。 在出现的 **IP 允许列表** 浮出控件中，使用以下语法在 " **地址" 或 "地址范围** " 框中输入 IPV4 地址：

     - 单个 IP：例如192.168.1.1。

     - IP 范围：例如，192.168.0.1-192.168.0.254。

     - CIDR IP：例如 192.168.0.1/25。 有效的网络掩码值为/24 到/32。 若要跳过 CIDR IP 掩码值/1 到/23 的垃圾邮件筛选，请参阅本主题后面的 " [跳过对 CIDR ip 的垃圾邮件筛选](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) "。在本主题后面的 "可用范围" 部分之外。

     若要添加 IP 地址或地址范围，请单击 " **添加** ![ 添加图标" ](../../media/ITPro-EAC-AddIcon.png) 。 若要删除条目，请选择 " **允许的 IP 地址** " 中的条目，然后单击 " **删除** ![ 删除" ](../../media/scc-remove-icon.png) 。 完成时，请单击“保存”****。

   - **IP 阻止列表**：单击 " **编辑**"。 在出现的 " **IP 阻止列表**" 浮出控件中，按照**ip 允许列表**设置中的前面所述，在 "**地址" 或 "地址范围**" 框中输入单个 ip 地址、ip 地址范围或 CIDR IP。

     若要添加 IP 地址或地址范围，请单击 " **添加** ![ 添加图标" ](../../media/ITPro-EAC-AddIcon.png) 。 若要删除条目，请选择 " **阻止的 IP 地址** " 中的条目，然后单击 " **删除** ![ 删除" ](../../media/scc-remove-icon.png) 。 完成时，请单击“保存”****。

   - **打开安全列表**：启用或禁用安全列表的使用，以确定将跳过垃圾邮件筛选的已知、良好的发件人。

4. 完成时，请单击“保存”****。

## <a name="use-the-security--compliance-center-to-view-the-default-connection-filter-policy"></a>使用安全 & 合规性中心查看默认连接筛选器策略

1. 在安全 & 合规性中心并转到 **威胁管理** \> **策略** \> **反垃圾邮件**。

2. 在 " **反垃圾邮件设置** " 页上，单击名为 " **连接筛选器策略**" 的默认策略旁边的下拉箭头。

3. 策略设置显示在打开的下拉菜单中。

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>使用 Exchange Online PowerShell 或独立 EOP PowerShell 修改默认连接筛选器策略

使用以下语法：

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**注意**：

- 有效的 IP 地址或地址范围值为：

  - 单个 IP：例如192.168.1.1。

  - IP 范围：例如，192.168.0.1-192.168.0.254。

  - CIDR IP：例如 192.168.0.1/25。 有效的网络掩码值为/24 到/32。

- 若要使用您指定的值 *覆盖* 任何现有条目，请使用以下语法： `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN` 。

- 若要在不影响其他现有条目的情况下 *添加或删除* IP 地址或地址范围，请使用以下语法： `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}` 。

- 若要清空 IP 允许列表或 IP 阻止列表，请使用值 `$null` 。

本示例使用指定的 IP 地址和地址范围配置 IP 允许列表和 IP 阻止列表。

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

本示例将从 IP 允许列表中添加和删除指定的 IP 地址和地址范围。

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

有关语法和参数的详细信息，请参阅 [set-hostedconnectionfilterpolicy](https://docs.microsoft.com/powershell/module/exchange/set-hostedconnectionfilterpolicy)。

## <a name="how-do-you-know-this-worked"></a>如何判断是否生效？

若要验证是否已成功修改了默认连接筛选器策略，请执行以下任一步骤：

- 在安全 & 合规性中心中，转到 " **威胁管理** \> **策略**" \> " **反垃圾邮件**" \> 单击 " **连接筛选器策略** " 旁的下拉 ("始终在) 上"，然后验证这些设置。

- 在 Exchange Online PowerShell 或独立 EOP PowerShell 中，运行以下命令并验证设置：

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- 从 IP 允许列表中的条目发送测试邮件。

## <a name="additional-considerations-for-the-ip-allow-list"></a>IP 允许列表的其他注意事项

以下各节标识了在配置 IP 允许列表时需要了解的其他项目。

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>跳过对可用范围之外的 CIDR IP 的垃圾邮件筛选

如本主题前面所述，您只能在 IP 允许列表中使用网络掩码为/24 到/32 的 CIDR IP。 若要在/1 到/23 范围内跳过来自源电子邮件服务器的邮件的垃圾邮件筛选，您需要使用 Exchange 邮件流规则 (也称为传输规则) 。 但是，我们建议您尽可能不要这样做，因为如果 Microsoft 的专用或第三方的阻止列表中显示了/1 到/23 CIDR IP 范围中的 IP 地址，则邮件将被阻止。

现在，您完全了解潜在问题，您可以创建具有以下)  (设置的邮件流规则，以确保来自这些 IP 地址的邮件将跳过垃圾邮件筛选：

- 规则条件： **如果** \> **发件人** \> **IP 地址在这些范围中的任何一个或完全匹配**，则应用此规则 \> 。请) 使用带 a/1 到/23 网络掩码的 CIDR IP (。

- 规则操作： **修改邮件属性** \> **设置垃圾邮件可信度级别 (SCL) ** \> **绕过垃圾邮件筛选**。

您可以审核规则、测试规则、在特定时间段内激活规则，以及进行其他选择。 我们建议首先在一段时间内测试规则，然后再强制应用。 有关详细信息，请参阅 [在 Exchange Online 中管理邮件流规则](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules)。

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>跳过来自相同源的选择性电子邮件域的垃圾邮件筛选

通常情况下，将 IP 地址或地址范围添加到 IP 允许列表意味着您信任来自该电子邮件源的所有传入邮件。 但如果该源发送来自多个域的电子邮件，而您想要跳过某些域的垃圾邮件筛选（而不是其他一些域），该怎么办？ 您不能仅使用 IP 允许列表来执行此操作，但可以结合使用 IP 允许列表和邮件流规则。

例如，源电子邮件服务器192.168.1.25 从域 contoso.com、fabrikam.com 和 tailspintoys.com 发送电子邮件，但您只希望跳过来自 fabrikam.com 发件人的邮件的垃圾邮件筛选。 若要执行此操作，请执行以下步骤：

1. 将192.168.1.25 添加到 IP 允许列表中。

2. 将具有下列设置的邮件流规则配置 (至少) ：

   - 规则条件： **如果** \> **发件人** \> **IP 地址位于这些范围中的任何一个或完全匹配**192.168.1.25，则应用此规则 \> 。)  (与您在上一步中添加到 IP 允许列表中的 ip 地址或地址范围相同的 ip 地址或地址范围。

   - 规则操作： **修改邮件属性** \> **设置垃圾邮件可信度级别 (SCL) ** \> **0**。

   - 规则异常： **"发件人**" \> **域为** \> fabrikam.com (仅要跳过垃圾邮件筛选) 的域。

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>来自 IP 允许列表中来源的邮件仍被筛选的情况

来自 IP 允许列表中的电子邮件服务器的邮件仍会在以下情况下受到垃圾邮件筛选：

- 您的 IP 允许列表中的 IP 地址也是在 Microsoft 365 中 *任何* 租户的本地基于 IP 的入站连接器中配置的 (让我们调用此租户 a) ， **并且** 第一次遇到邮件的租户 a 和 EOP 服务器在 Microsoft 数据中心 *的同一个* Active Directory 林中。 在这种情况下， **IPV： CAL** *将* 添加到邮件的 [反垃圾邮件邮件头](anti-spam-message-headers.md) ， (指示邮件绕过垃圾邮件筛选) ，但邮件仍受垃圾邮件筛选。

- 包含 IP 允许列表的租户以及首次遇到邮件的 EOP 服务器在 Microsoft 数据中心的 *不同* Active Directory 林中的情况。 在这种情况下， **IPV： CAL** *不会* 添加到邮件头中，因此邮件仍受垃圾邮件筛选。

如果遇到上述任一情况，您都可以创建具有以下设置的邮件流规则 (至少) ，以确保来自有问题的 IP 地址的邮件将跳过垃圾邮件筛选：

- 规则条件： **如果** \> **发件人** \> **IP 地址在任何这些范围中，或者完全匹配** \> (IP 地址或地址) ，则应用此规则。

- 规则操作： **修改邮件属性** \> **设置垃圾邮件可信度级别 (SCL) ** \> **绕过垃圾邮件筛选**。

## <a name="new-to-microsoft-365"></a>Microsoft 365 的新增功能？

****

![LinkedIn 学习 ](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **新增版到 Microsoft 365**的简短图标？ 探索通过 LinkedIn 学习获取的适用于 **Microsoft 365 管理员和 IT 专业人员**的免费视频课程。
