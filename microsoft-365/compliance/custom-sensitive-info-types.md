---
title: DLP 自定义敏感信息类型
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: 04/23/2019
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: 获取有关数据丢失防护 (DLP) 的自定义敏感信息类型的概述，如主要模式、字符接近度和可信度级别。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d21d0be23847a8fbd27b6082ca28cdca2d4eed05
ms.sourcegitcommit: 5e40c760c1af2a4cc6d85cb782b17f5c979677c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2020
ms.locfileid: "48379174"
---
# <a name="custom-sensitive-information-types"></a>自定义敏感信息类型

Microsoft 365 包括许多你可直接在组织中使用的内置敏感信息类型，包括用于[数据丢失保护](data-loss-prevention-policies.md) (DLP) 或 [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)。 内置敏感信息类型可以根据正则表达式 (regex) 或函数定义的模式，帮助标识和保护信用卡号、银行账号、护照号等。 若要了解详细信息，请参阅[敏感信息类型查找的内容](what-the-sensitive-information-types-look-for.md)。

但是，如果需要标识和保护使用组织特定格式的不同敏感信息类型，如员工 ID 或项目号，那该怎么办？ 为此，你可以创建自定义敏感信息类型。

自定义敏感信息类型的基本组成部分是：

- **主要模式**：员工 ID 号、项目编号等。这通常是由正则表达式 (RegEx) 标识，但也可以是关键字列表。

- **额外证据**：假设要查找 9 位数员工 ID 号。由于并非所有 9 位数都是员工 ID 号，因此可查找其他文本：“员工”、“徽章”、“ID”等关键字或其他基于额外正则表达式的文本模式。此支持性证据（亦称为_支持性_或_确证性_证据）提高了在内容中找到的 9 位数确实是员工 ID 号的可能性。

- **字符临近度**：主要模式和支持性证据越临近，检测到的内容就越有可能是要查找的内容。可指定主要模式和支持性证据之间的字符距离（亦称为_临近度窗口_），如下图所示：

    ![确证性证据和临近度窗口的关系图](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

- **可信度**：支持性证据越多，匹配结果就越有可能包含要查找的敏感信息。可以为使用更多证据检测到的匹配结果指定更高可信度。

  如果符合，模式会返回可用于 DLP 策略条件的计数和可信度。向 DLP 策略添加用于检测敏感信息类型的条件时，可编辑计数和可信度，如下图所示：

    ![“实例计数”和“匹配准确度”选项](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

## <a name="creating-custom-sensitive-information-types"></a>创建自定义敏感信息类型

若要在安全与合规中心内创建自定义敏感信息类型，可使用以下几种方法：

- **使用 EDM** 可以使用基于精确数据匹配 (EDM) 的分类创建自定义敏感信息类型。 通过此方法，你可以使用可定期刷新的安全数据库创建动态敏感信息类型。 请参阅[使用基于精确数据匹配的分类创建自定义敏感信息类型](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)。

- **使用 PowerShell** 可以使用 PowerShell 创建自定义敏感信息类型。 尽管此方法比使用 UI 更复杂，但你可以拥有更多的配置选项。 请参阅[使用安全与合规中心 PowerShell 创建自定义敏感信息类型](create-a-custom-sensitive-information-type-in-scc-powershell.md)。

- **使用 UI** 可以使用安全与合规中心 UI 创建自定义敏感信息类型。 通过此方法，你可以使用正则表达式、关键字和关键字字典。 若要了解详细信息，请参阅[创建自定义敏感信息类型](create-a-custom-sensitive-information-type.md)。

> [!NOTE]
> Microsoft 365 信息保护现可为以下语言提供双字节字符集语言支持（预览）：
> - 简体中文
> - 繁体中文
> - 韩语
> - 日语
> 
>此功能预览仅在商业云中提供，并且仅在以下地区推出：
> - 日本
> - 韩国
> - 中国大陆
> - 香港特别行政区
> - 澳门特别行政区
> - 中国台湾
>
>此支持适用于敏感信息类型。 有关详细信息，请参阅[双字节字符集的信息保护支持发行说明（预览版）](mip-dbcs-relnotes.md)。

