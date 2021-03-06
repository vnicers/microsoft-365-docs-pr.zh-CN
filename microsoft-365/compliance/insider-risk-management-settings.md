---
title: 内幕风险管理设置
description: 了解 Microsoft 365 中的内幕风险管理设置
keywords: Microsoft 365，内幕风险管理，风险管理，合规性
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: c98c0081d95da19e79db03dc4b4fdb823a14e42c
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2020
ms.locfileid: "48377267"
---
# <a name="get-started-with-insider-risk-management-settings"></a>内幕风险管理设置入门

内幕风险管理设置适用于所有内幕风险管理策略，而不管您在创建策略时选择的模板如何。 设置是使用位于所有内幕风险管理选项卡顶部的 " **内幕风险设置** " 控件配置的。 这些设置控制以下方面的策略组件：

- 隐私
- 指示器
- 策略时间线
- 智能检测
-  (预览中导出警报) 
-  (预览的优先级用户组) 
-  (预览的优先级物理资产) 
-  (预览的功能自动执行流) 
- Microsoft 团队 (预览) 

在开始和创建内幕风险管理策略之前，请务必了解这些设置，并选择最适合您的组织的合规性需求的设置级别。

## <a name="privacy"></a>隐私

保护具有策略匹配的用户的隐私是非常重要的，有助于促进 objectivity 在数据调查和分析审查中的内幕风险警报中。 对于具有内幕风险策略匹配的用户，可以选择以下设置之一：

- **显示匿名版本的用户名**：用户的名称为匿名，以防止管理员、数据调查人员和审阅者看到与策略通知关联的人员。 例如，在内幕风险管理体验的所有方面，用户的 "宽限期" Taylor 将显示为随机 pseudonym，如 "AnonIS8-988"。 选择此设置将 anonymizes 所有具有当前策略和过去策略匹配并适用于所有策略的用户。 选择此选项后，"内幕风险警报" 和 "事例详细信息" 中的用户配置文件信息将不可用。 但是，在将新用户添加到现有策略或将用户分配到新策略时，将显示用户名。 如果您选择关闭此设置，则将为具有当前或过去策略匹配的所有用户显示用户名。
- **不显示匿名版本的用户名**：为警报和事例显示所有当前策略和过去策略匹配的用户名。 用户配置文件信息 (为用户显示所有内幕风险管理警报和事例的名称、职务、别名和组织或部门) 。

![内幕风险管理隐私设置](../media/insider-risk-settings-privacy.png)

## <a name="indicators"></a>指示器

内幕风险策略模板定义要检测和调查的风险活动的类型。 每个策略模板都基于与特定的触发器和风险活动相对应的特定指示器。 默认情况下，所有指示器都处于禁用状态，并且必须在配置内幕风险管理策略之前选择一个或多个策略指示器。

当用户执行与满足所需阈值的策略指示器相关的活动时，将按策略触发警报。 内幕风险管理使用两种类型的指示器：

- **触发事件**：确定用户是否为内部人员风险管理策略处于活动状态的事件。 如果向内幕风险管理策略中添加用户不具有触发事件，则该策略不会评估用户活动。 例如，将用户 A 添加到由 *受窃用户* 策略模板的数据失窃创建的策略中，并正确配置策略和 MICROSOFT 365 HR 连接器。 在用户 A 拥有由 HR 连接器报告的终止日期之前，此内幕风险管理策略不会评估用户 A 活动的风险。 触发事件的另一个示例是，在使用*数据泄漏*策略时，如果用户具有*高*严重性的 DLP 策略警报。
- **策略指示器**：内幕风险管理策略中包含的指标，用于确定范围内用户的风险分数。 仅当用户发生触发事件之后，才会激活这些策略指示器。 当用户将数据复制到个人云存储服务或便携式存储设备，或者如果用户与未经授权的外部方共享内部文件和文件夹时，策略指示器的一些示例。

策略指示器分成以下几个方面。 创建内幕风险策略时，可以选择标记以激活和自定义每个指示器级别的指标事件限制：

- **Office 指标**：其中包括 SharePoint 网站、团队和电子邮件消息的策略指示器。
- **设备指示器**：其中包括活动的策略指示器，例如通过网络或设备共享文件。 指标包括涉及 Microsoft Office 文件的活动。CSV 文件和。PDF 文件。 如果选择 " **设备指示器**"，则仅处理 Windows 10 内部版本1809或更高版本的设备的活动。 有关配置设备以与内幕风险集成的详细信息，请参阅 [ENDPOINT DLP 入门](endpoint-dlp-getting-started.md)。
- **安全策略冲突指示器**：其中包括 MICROSOFT Defender ATP 与未批准或恶意软件安装相关的指标或绕过安全控制的指标。 若要在 "内幕风险管理" 中接收通知，必须启用活动的 Microsoft Defender ATP 许可证和内幕风险集成。 有关为内部人员风险管理集成配置 Microsoft Defender ATP 的详细信息，请参阅 [在 Microsoft DEFENDER atp 中配置高级功能](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center)。
- **风险分数 boosters**：其中包括提高异常活动或过去策略违规的风险分数。 启用风险分数 boosters 会增加风险分数和这些类型活动的警报可能性。 只有在选择了上面的一个或多个指示器时，才能选择风险分数 boosters。

![内幕风险管理指标设置](../media/insider-risk-settings-indicators.png)

在某些情况下，您可能需要限制应用于组织中的内幕风险策略的内幕风险策略指标。 您可以通过在所有内幕风险策略中禁用特定区域的策略指示器来将其关闭。 无法修改内部人员风险策略模板的触发事件。

若要定义在所有内幕风险策略中启用的内幕风险策略指示器，请导航到 "**内幕" 风险设置**  >  **指示器**，然后选择一个或多个策略指示器。 在 "策略向导" 中创建或编辑 "内幕风险策略" 时，无法单独配置 "标记设置" 页上所选的指示器。

>[!NOTE]
>在 **用户仪表板**中显示新的手动添加的用户可能需要几个小时。 之前90天的活动显示这些用户可能需要长达24小时才能显示。 若要查看手动添加的用户的活动，请在 **用户仪表板** 上选择用户，然后在详细信息窗格中打开 " **用户活动** " 选项卡。

### <a name="indicator-level-settings-preview"></a> (预览的指示器级别设置) 

在策略向导中创建策略时，您可以配置每日风险事件数量对内幕风险警报的风险得分的影响。 这些指示器设置可帮助您控制组织中风险事件发生的次数应如何影响这些事件的风险分数，进而影响相关的警报严重性。 如果你愿意，也可以选择保留 Microsoft 建议的所有已启用指示器的默认事件阈值级别。

例如，您决定在 "内幕风险策略" 设置中启用 SharePoint 指示器，并在配置新的内幕风险 *数据泄露* 策略的指示器时为 sharepoint 事件设置自定义阈值。 在 "内幕风险策略" 向导中，为每个 SharePoint 指标配置三个不同的日常事件级别，以影响与这些事件相关联的警报的风险分数。

![内幕风险管理自定义指示器设置](../media/insider-risk-custom-indicators.png)

对于第一天的事件级别，将阈值设置为 *每日10个或更多个事件* ，以降低对事件的风险分数的影响、 *每天20个或更多* 个事件的影响，以及每天 *30 个或以上事件* 对事件风险分数的影响。 这些设置有效地表示：

- 如果在触发事件后发生了 1-9 SharePoint 事件，风险分数将受到最低影响，并且往往不会生成警报。
- 如果在触发事件之后发生了 10-19 SharePoint 事件，风险分数的优先级将变低，警报的严重性级别通常会降低。
- 如果发生触发后发生的 20-29 SharePoint 事件，风险分数就会更高，警报的严重性级别通常应为中等级别。
- 如果在触发之后发生30个或更多的 SharePoint 事件，风险分数就会变得更高，而警报严重性级别通常应为较高级别。

## <a name="policy-timeframes"></a>策略时段

通过策略时段，可以定义在策略匹配之后根据内幕风险管理策略模板的事件和活动触发的过去和将来的审查时间段。 根据您选择的策略模板，以下策略时段可用：

- **激活窗口**：适用于所有策略模板， *激活窗口* 是在触发事件 **后** 指定窗口激活的天数。 对于分配到策略的任何用户，在触发事件发生后，窗口将激活1到30天。 例如，您已配置 "内幕风险管理策略"，并将 " *激活" 窗口* 设置为30天。 自从您配置策略并在策略中包含的一个用户发生触发事件时，已超过几个月。 触发事件将激活 *激活窗口* ，并且该用户的策略在触发事件发生30天后处于活动状态。
- **过去的活动检测**：适用于所有策略模板， *过去的活动检测* 是指在触发事件 **之前** 激活的时间段（以天为单位）。 在为任何分配了策略的用户发生触发事件之前，窗口将激活0到180天。 例如，您已经配置了 "内幕风险管理策略"，并将 " *过去的活动检测* " 设置为 "90 天"。 自从您配置策略并在策略中包含的一个用户发生触发事件时，已超过几个月。 触发事件将激活 *过去的活动检测* ，策略会在触发事件之前的90天内收集该用户的历史活动。

![内幕风险管理时间范围设置](../media/insider-risk-settings-timeframes.png)

## <a name="intelligent-detections"></a>智能检测

智能检测设置有助于优化风险活动检测的处理方式，以获取通知。 在某些情况下，您可能需要定义要忽略的文件类型，或者您希望对文件实施检测级别，以帮助定义最小通知栏。 使用冒犯性语言策略时，您可能需要增加或减少检测灵敏度，以控制报告的匹配策略匹配量。 使用这些设置可以控制整个警报卷、文件类型排除、文件容量限制和冒犯性语言检测灵敏度。

![内幕风险管理智能检测设置](../media/insider-risk-settings-detections.png)

### <a name="anomaly-detections"></a>异常检测

反常检测包括文件类型排除和文件卷限制的设置。

- **文件类型排除**：若要从所有内幕风险管理策略匹配中排除特定文件类型，请输入以逗号分隔的文件类型扩展名。 例如，若要从策略匹配项中排除特定类型的音乐文件，可以在**文件类型排除**字段中输入*aac、mp3、wav 和 wma* 。 具有这些扩展名的文件将被所有内幕风险管理策略忽略。
- **文件卷切出限制**：要定义在 "内幕风险策略" 中报告活动通知前的最低文件级别，请输入文件数量。 例如，如果您不希望在用户下载10个文件或更少时生成内幕风险警报，即使策略认为此活动异常，也可以输入 "10"。

### <a name="offensive-language-detections"></a>攻击性语言检测

>[!IMPORTANT]
>从2020年10月16日起，你将无法再使用此模板创建策略。 使用此模板的任何活动策略都将起作用，直到它们在2021年1月永久删除。 我们正在弃用提供支持此模板的冒犯性语言的内置分类器，因为它生成了大量误报。 若要解决攻击性语言的风险问题，我们建议使用 Microsoft 365 [通信合规性](communication-compliance.md) 策略。 有关内置分类器的详细信息，请参阅 [trainable 分类](classifier-get-started-with.md)器入门。

若要使用 *电子邮件模板中的冒犯性语言* 调整策略的冒犯性语言分类符的灵敏度，请选择以下设置之一：

- **低**：检测到的冒犯性语言和看法的最广泛的敏感度级别。 对冒犯性语言匹配的误报概率提升。
- **中**：包含用于检测冒犯性语言和看法的平衡范围的中级敏感度级别。 对冒犯性语言匹配的误报概率是平均的。
- **高**：检测冒犯性语言和看法的最高敏感度级别和范围较窄的范围。 对于攻击性的语言匹配，误报的概率较低。

### <a name="alert-volume"></a>警报音量

由内幕风险策略检测到的用户活动被分配了特定风险分数，这反过来又决定了警报严重性 (低、中、高) 。 默认情况下，我们会生成一定数量的低、中和高严重性警报，但您可以根据需要增加或减少该卷。 若要调整所有内幕风险管理策略的警报量，请选择以下设置之一：

- **警报更少**：你将看到所有高严重性警报、低严重性警报和低严重性警报。 此设置级别表示可能会丢失一些真正的误报。
- **默认卷**：你将看到所有高严重性警报以及已平衡的中等流量和低严重性警报。
- **更多警报**：你将看到所有的 "中" 和 "高" 严重性警报和最低严重性警报。 此设置级别可能会导致更多误报。

### <a name="microsoft-defender-advanced-threat-protection-preview"></a>Microsoft Defender 高级威胁防护 (预览版) 

[Microsoft Defender 高级威胁防护](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) (ATP) 是一个企业终结点安全平台，旨在帮助企业网络阻止、检测、调查和响应高级威胁。 若要更好地了解组织中的安全冲突，可以为从内幕风险管理安全冲突策略模板创建的策略中使用的活动导入和筛选 Microsoft Defender ATP 警报。

根据您感兴趣的信号类型，您可以选择根据 Microsoft Defender ATP 警报会审状态将警报导入到内幕风险管理中。 您可以在要导入的全局设置中定义以下一个或多个警报会审状态：

- 未知
- 新式
- 进行中
- 已解决

每日导入来自 Microsoft Defender ATP 的警报。 根据您选择的会审状态，您可能会看到与 Microsoft Defender ATP 中的会审状态变化相同的警报的多个用户活动。

例如，如果为此设置选择 " *新建*"、" *正在进行*" 和 " *已解决* "，则在生成 Microsoft Defender ATP 警报且状态为 " *新*" 时，会为用户导入 "内幕风险" 中的 "初始警报" 活动。 当 Microsoft Defender ATP 会审状态更改为 " *正在进行*" 时，将为用户在内幕风险中导入此警报的第二个活动。 在设置了 *已解决* 的最终的 MICROSOFT Defender ATP 会审状态时，将为用户在内幕风险中导入此警报的第三个活动。 此功能使调查人员能够遵循 Microsoft Defender ATP 警报的进展，并选择其调查所需的可见性级别。

>[!IMPORTANT]
>您需要在组织中配置 Microsoft Defender ATP，并在 "Defender 安全中心" 中启用 Microsoft Defender ATP 以获得内部风险管理集成，以导入安全冲突警报。 有关为内部人员风险管理集成配置 Microsoft Defender ATP 的详细信息，请参阅 [在 Microsoft DEFENDER atp 中配置高级功能](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center)。

### <a name="domains-preview"></a> (预览的域) 

域设置可帮助您定义与特定域之间的通信的风险级别。 这些通信包括共享文件、电子邮件或下载内容。 通过在这些设置中指定域，可以增加或减少与这些域发生的活动的风险评分。 例如，若要将 contoso.com 和 sales.wingtiptoys.com 指定为允许的域，您将在 " **允许的域** " 字段中输入 "contoso.com sales.wingtiptoys.com"。

对于以下每个域设置，最多可以输入500个域：

- **Unallowed 域：** 通过指定 unallowed 域，与这些域发生的活动将具有 *更高* 的风险分数。
- **允许的域：** 通过在设置中指定允许的域，与这些域发生的活动将具有 *较低* 风险分数，并且与处理内部组织活动的方式类似。 例如，对这些域的电子邮件活动的分析方式类似于分析内部电子邮件活动的方式。
- **第三方域：** 第三方域是用于在组织中用于业务目的的域，敏感内容可以存储在这些位置。 通过指定第三方域，可以接收这些域上任何有风险的活动的警报。

## <a name="export-alerts-preview"></a> (预览中导出警报) 

可通过 [Office 365 管理活动 API 架构](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema)将内幕风险管理警报信息导出到安全信息和事件管理 (SIEM) 服务。 您可以使用 Office 365 管理活动 Api 将通知信息导出到组织可用于管理或聚合内幕风险信息的其他应用程序。

若要使用 Api 查看内幕风险警报信息，请执行以下操作：

1. 启用**内幕风险管理**  >  **设置**  >  **导出**中的 Office 365 管理活动 API 支持。 默认情况下，为 Microsoft 365 组织禁用此设置。
2. 按 *SecurityComplianceAlerts*筛选常见的 Office 365 审核活动。
3. 按*InsiderRiskManagement*类别筛选*SecurityComplianceAlerts* 。

![内幕风险管理导出警报设置](../media/insider-risk-settings-export.png)

警报信息包含来自安全和合规性警报架构和 Office 365 管理活动 API 常见架构的信息。

为安全 & 合规性警报架构中的 "内幕风险管理警报" 导出以下字段和值：

| **Alert 参数** | **说明** |
|:------------------|:----------------|
| AlertType | 警报的类型为 " *自定义*"。  |
| AlertId | 警报的 GUID。 内幕风险管理警报是可变的。 当警报状态更改时，将生成一个具有相同 AlertID 的新日志。 此 AlertID 可用于关联警报的更新。 |
| 类别 | 警报类别为 *InsiderRiskManagement*。 此类别可用于从其他安全 & 合规性警报中辨别这些警报。 |
| 备注 | 通知的默认注释。 值是在创建警报时记录的 *新警报* (记录) 并在更新警报) 时记录 *更新* (记录。 使用 AlertID 可关联警报的更新。 |
| 数据 | 警报的数据包括唯一的用户 ID、用户主体名称以及在将用户触发到策略中时 (UTC) 的日期和时间。 |
| 名称 | 生成警报的内幕风险管理策略的策略名称。 |
| PolicyId | 触发警报的内幕风险管理策略的 GUID。 |
| Severity | 警报的严重性。 值为 " *高*"、" *中*" 或 " *低*"。 |
| Source | 警报的来源。 值为 *Office 365 安全 & 合规性*。 |
| 状态 | 通知的状态。 值*处于活动状态* (*需要查看*内幕风险) 中*的 "* 内幕风险" 中的 " () *确认*"、"*已解决* * ("。在*内部人员风险 *) 中消除**了 (*) 。 |
| 版本 | 安全和合规性警报架构的版本。 |

为 [Office 365 管理活动 API 常见架构](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#common-schema)的内幕风险管理警报导出以下字段和值。

- UserID
- Id
- RecordType
- CreationTime
- 操作
- OrganizationId
- UserType
- UserKey

## <a name="priority-user-groups-preview"></a> (预览的优先级用户组) 

组织中的用户可能具有不同的风险级别，具体取决于其位置、敏感信息的访问级别或风险历史记录。 确定这些用户的活动的检查和评分的优先级，可帮助提醒您组织可能会产生更高后果的潜在风险。 内幕风险管理中的优先级用户组可帮助定义组织中需要更仔细检查和更敏感风险计分的用户。 结合优先级用户和*数据泄露（按优先级*用户策略模板）与*安全策略冲突*，添加到优先级用户组的用户具有更高的严重性级别的内幕风险警报和警报的可能性增加。

![内幕风险管理优先级用户组设置](../media/insider-risk-settings-priority-users.png)

例如，您需要针对高度机密项目（用户有权访问敏感信息）的数据泄露进行保护。 您可以选择为组织中使用此项目的用户创建 "*机密项目**用户*优先级" 用户组。 使用 "策略向导" 和 " *按优先级的用户数据泄露* " 策略模板，可以创建新策略并将 " *机密项目用户* 优先级用户" 组分配给策略。 由策略对 " *机密项目* 的成员" 用户组的策略检查的活动用户优先级用户组对风险和活动的敏感程度更高，这些用户将更有可能生成警报并具有更高严重性级别的警报。

### <a name="create-a-priority-user-group"></a>创建优先级用户组

若要创建新的优先级用户组，您将在 "Microsoft 365 合规性中心" 中的 " **内幕风险管理** " 解决方案中使用设置控件。 若要创建优先级用户组，您必须是 " *内幕风险管理* " 或 " *内幕风险管理" 管理员* 角色组的成员。

若要创建优先级用户组，请完成以下步骤：

1. 在 [Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 " **内幕风险管理** " 并选择 " **内幕风险设置**"。
2. 选择 " **优先级用户组** " 选项卡
3. 在 " **优先级用户组** " 选项卡上，选择 " **创建优先级用户组** " 以启动 "组创建向导"。
4. 在 " **定义组** " 页上，填写下列字段：
    - **Name (必需) **：输入优先级用户组的友好名称。 完成该向导后，不能更改优先级用户组的名称。
    - **Description (可选) **：输入优先级用户组的说明。
5. 选择 " **下一步** " 继续。
6. 在 " **选择成员** " 页上，选择 "选择要搜索的 **成员** "，然后选择组中包含哪些启用邮件的用户帐户，或选择 " **全选** " 复选框将组织中的所有用户添加到组中。 选择 " **添加** " 以继续操作或单击 " **取消** " 关闭，而不向该组添加任何用户。
7. 选择 " **下一步** " 继续。
8. 在 " **检查** " 页上，查看为 "优先级" 用户组选择的设置。 选择 " **编辑** " 以更改任何组值，或选择 " **提交** " 以创建并激活优先级用户组。
9. 在 "确认" 页上，选择 " **完成** " 退出向导。

### <a name="update-a-priority-user-group"></a>更新优先级用户组

若要更新现有的优先级用户组，您将在 "Microsoft 365 合规性中心" 中的 " **内幕风险管理** " 解决方案中使用设置控件。 若要更新优先级用户组，您必须是 " *内幕风险管理* " 或 " *内幕风险管理" 管理员* 角色组的成员。

完成以下步骤以编辑优先级用户组：

1. 在 [Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 " **内幕风险管理** " 并选择 " **内幕风险设置**"。
2. 选择 " **优先级用户组** " 选项卡
3. 选择要编辑的优先级用户组，然后选择 " **编辑组**"。
4. 在 " **定义组** " 页上，根据需要更新 "说明" 字段。 不能更新优先级用户组的名称。 选择 " **下一步** " 继续。
5. 在 " **选择成员** " 页上，使用 " **选择成员** " 控件向组添加新成员。 若要从组中删除用户，请选择要删除的用户旁边的 "X"。 选择 " **下一步** " 继续。
6. 在 " **检查** " 页上，查看为 "优先级" 用户组选择的更新设置。 选择 " **编辑** " 以更改任何组值，或选择 " **提交** " 以更新优先级用户组。
7. 在 "确认" 页上，选择 " **完成** " 退出向导。

### <a name="delete-a-priority-user-group"></a>删除优先级用户组

若要删除现有的优先级用户组，您将在 "Microsoft 365 合规性中心" 中的 " **内幕风险管理** " 解决方案中使用设置控件。 若要删除优先级用户组，您必须是 " *内幕风险管理* " 或 " *内幕风险管理" 管理员* 角色组的成员。

>[!IMPORTANT]
>删除优先级用户组会将其从其分配到的任何活动策略中删除。 如果您删除分配给活动策略的优先级用户组，则该策略将不包含任何范围内的用户，并且将有效地处于空闲状态，并且不会创建通知。

完成以下步骤以删除一个优先级用户组：

1. 在 [Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 " **内幕风险管理** " 并选择 " **内幕风险设置**"。
2. 选择 " **优先级用户组** " 选项卡
3. 选择要编辑的 "优先级" 用户组，然后从仪表板菜单中选择 " **删除** "。
4. 在 " **删除** " 对话框中，选择 **"是"** 删除 "优先级用户" 组，或选择 " **取消** " 返回仪表板。

## <a name="priority-physical-assets-preview"></a> (预览的优先级物理资产) 

确定对优先级物理资产的访问权限，并将访问活动与用户事件关联起来是合规性基础结构的重要组成部分。 这些实物资产代表组织中的优先级位置，如公司建筑物、数据中心或服务器机房。 内幕风险活动可能会与用户工作异常小时、尝试访问这些未经授权的敏感区域或安全区域相关联，并请求访问高级别区域，而无需合法的要求。

在启用了优先级的物理资产并配置了 [物理徽章数据连接器](import-physical-badging-data.md) 后，内幕风险管理将来自您的物理控制和访问系统的信号与其他用户风险活动相集成。 通过检查各个物理访问系统的行为模式并将这些活动与其他内幕风险事件相关联，内幕风险管理可帮助合规性调查人员和分析师对警报做出更明智的响应决策。 对优先级物理资产的访问权以不同方式在洞察力中进行评定和标识，而不是对非优先级资产进行访问。

例如，您的组织有一个徽章系统，用于监视和批准对正常工作和敏感项目区域的物理访问。 您有多个用户在使用敏感项目，并且这些用户将在项目完成时返回到组织的其他区域。 当敏感项目临近完成时，您希望确保项目工作保持机密并严格控制对项目区域的访问。

您可以选择在 Microsoft 365 中启用物理徽章数据连接器，以从物理徽章系统中导入访问信息，并在 "内幕风险管理" 中指定优先级物理资产。 通过从您的徽章系统中导入信息并将物理访问信息与内幕风险管理中标识的其他风险活动相关联，您会注意到项目中的一个用户在正常工作时间内访问项目办事处，同时也将大量数据从其正常工作区导出到个人云存储服务。 与在线活动相关的此物理访问活动可能会指出可能的数据失窃和合规性调查人员和分析师可以采取此用户的环境所规定的适当操作。

### <a name="configure-priority-physical-assets"></a>配置物理资产优先级

若要配置物理资产的优先级，您需要配置物理徽章连接器，并使用 Microsoft 365 合规性中心内的 **内幕风险管理** 解决方案中的设置控件。 若要配置物理资产的优先级，您必须是 " *内幕风险管理* " 或 " *内幕风险管理" 管理员角色组*的成员。

完成以下步骤以配置物理资产的优先级：

1. 在 [开始使用 "内幕风险管理](insider-risk-management-configure.md) " 文章中，按照 "内幕风险管理" 的配置步骤进行操作。 在步骤3中，请确保配置物理徽章连接器。

    >[!IMPORTANT]
    >若要使用内部风险管理策略并将与传出和终止用户相关的信号数据与您的物理控制和访问平台中的事件数据关联起来，您还必须配置 Microsoft 365 HR 连接器。 如果在不启用 Microsoft 365 HR 连接器的情况下启用物理徽章连接器，内幕风险管理策略将仅处理组织中用户的物理访问活动事件。

2. 在[Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 "**内幕风险管理**"，然后选择 "**内幕风险设置**  >  **优先级实物资产**"。
3. 在 " **优先级物理资产** " 页面上，您可以手动添加要为物理徽章连接器导入的资产事件监视的物理资产 id，也可以导入。由物理徽章连接器导入的所有物理资产 Id 的 CSV 文件： a) 手动添加实物资产 Id，选择 " **添加优先级实物资产**"，输入实物资产 id，然后选择 " **添加**"。 输入其他实物资产 Id，然后选择 " **添加优先级实物资产** " 以保存所有输入的资产。
    b) 添加来自的实物资产 Id 的列表。CSV 文件中，选择 " **导入优先级实物资产**"。 从 "文件资源管理器" 对话框中，选择。CSV 文件，然后选择 " **打开**"。 中的实际资产 Id。将 CSV 文件添加到列表中。
4. 导航到 "设置" 中的 " **策略指示器** " 选项卡。
5. 在 " **策略指示器** " 页上，导航到 " **物理访问指示器** " 部分，然后选中 "在 **终止或访问敏感资产失败后物理访问**的" 复选框。
6. 选择 " **保存** " 以配置和退出。

### <a name="delete-a-priority-physical-asset"></a>删除优先级的实际资产

若要删除现有的优先级物理资产，您将使用 Microsoft 365 合规性中心中的内幕风险管理解决方案中的设置控件。 若要删除优先级的物理资产，您必须是 "内幕风险管理" 或 "内幕风险管理" 管理员角色组的成员。

>[!IMPORTANT]
>删除优先级的实际资产会将其以前包含的任何活动策略从考试中删除。 不删除与优先级实际资产相关联的活动生成的警报。

完成以下步骤以删除优先级物理资产：

1. 在[Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 "**内幕风险管理**"，然后选择 "**内幕风险设置**  >  **优先级实物资产**"。
2. 在 " **优先级物理资产** " 页面上，选择要删除的资产。
3. 在 "操作" 菜单上选择 " **删除** " 以删除资产。

## <a name="power-automate-flows-preview"></a> (预览的功能自动执行流) 

[Microsoft Power 自动化](https://docs.microsoft.com/power-automate/getting-started) 是一种工作流服务，可跨应用程序和服务自动执行操作。 通过使用来自模板或手动创建的流，可以自动执行与这些应用程序和服务相关联的常见任务。 为内幕风险管理启用 Power 自动执行流时，可以自动执行案例和用户的重要任务。 您可以配置电源自动化流，以检索用户、警报和事例信息，并与风险承担者和其他应用程序共享此信息，以及自动化内幕风险管理中的操作，如发布到案例记录。 电力自动化流适用于事例和策略范围内的任何用户。

包含内幕风险管理的 Microsoft 365 订阅的客户无需额外的电力自动许可证即可使用建议的内幕风险管理电源自动完成模板。 可以自定义这些模板以支持您的组织，并涵盖核心内幕风险管理方案。 如果选择使用这些模板中的 "高级 Power premium 功能"，请使用 Microsoft 365 合规性连接器创建自定义模板，或在 Microsoft 365 中对其他合规性区域使用 Power premium 模板，则可能需要额外的电源自动许可证。

以下电源自动化模板为客户提供，以支持内幕风险管理用户和案例的流程自动化：

- 将**用户添加到 "内幕风险策略" 时通知用户**：此模板适用于具有内部策略、隐私或法规要求的组织，用户必须在受内幕风险管理策略时收到通知。 当为用户页面中的用户配置并选择此流时，当用户添加到内幕风险管理策略时，会向用户及其经理发送一封电子邮件。 此模板还支持更新 SharePoint 网站上托管的 SharePoint 列表，以帮助跟踪通知消息详细信息，如日期/时间和邮件收件人。 如果已选择 "在 **隐私设置**中匿名用户"，则从该模板创建的流将无法按预期工作，以便维护用户隐私。 使用此模板的电源自动化流在 **用户仪表板**上可用。
- **在内幕风险案例中，从 HR 或公司请求有关用户的信息**：当您在某个情况下操作时，内幕风险分析员和调查人员可能需要咨询 HR 或其他利益干系人，以了解案例活动的上下文。 当为事例配置和选择此流时，分析师和调查人员会向为此流配置的 HR 和业务利益干系人发送一封电子邮件。 每个收件人都使用预配置或可自定义的响应选项发送一封邮件。 收件人选择响应选项时，会将响应记录为事例注释，并包括收件人和日期/时间信息。 如果已选择 "在 **隐私设置**中匿名用户"，则从该模板创建的流将无法按预期工作，以便维护用户隐私。 使用此模板的电源自动化流在 **事例仪表板**中可用。
- **当用户拥有内幕风险警报时通知管理器**：当用户拥有内幕风险管理警报时，某些组织可能需要立即进行管理通知。 当配置和选择此流时，将向事例用户的经理发送一封电子邮件，其中包含有关所有案例通知的以下信息： 
    - 适用于警报的策略
    - 警报的日期/时间
    - 警报的严重性级别

    该流将自动更新邮件发送和流已激活的事例注释。 如果已选择 "在 **隐私设置**中匿名用户"，则从该模板创建的流将无法按预期工作，以便维护用户隐私。 使用此模板的电源自动化流在 **事例仪表板**中可用。

- **在 "内幕风险" 案例上添加 "跟踪日历" 提醒**：此模板允许风险调查人员和分析师将案例的日历提醒添加到他们的 Office 365 Outlook 日历中。 此流使用户无需在处理案例和会审警报时退出或切换出内幕风险管理工作流。 在配置和选择此流时，会向运行流的用户向 Office 365 Outlook 日历中添加提醒。 使用此模板的电源自动化流在 **事例仪表板**中可用。

### <a name="create-a-power-automate-flow-from-insider-risk-management-template"></a>创建来自内幕风险管理模板的电源自动化流

若要从建议的内幕风险管理模板创建电源自动流，您将使用 Microsoft 365 合规性中心中的**内幕风险管理**解决方案中的设置控件，或在直接在**案例**或**用户仪表板**中工作时**自动**控制中的 "**管理电源自动流**" 选项。

若要在 "设置" 区域中创建电源自动流，您必须是 " *内幕风险管理* " 或 " *内幕风险管理" 管理员* 角色组的成员。 若要使用 **管理电源自动流** 选项创建电源自动流功能，您必须是至少一个 "内幕风险管理" 角色组的成员。

完成以下步骤以创建来自推荐的内幕风险管理模板的电源自动流：

1. 在[Microsoft 365 合规性中心](https://compliance.microsoft.com/)中，转到 "**内幕风险管理**" 并选择 "**内幕风险设置**"  >  **自动执行流**。 您还可以通过选择 " **Cases** **自动** **Users dashboards**  >  **管理电源自动流程**"，从 "事例" 或 "用户" 仪表板页面访问。
2. 在 " **电源自动流程** " 页面上，从页面上的 " **内幕风险管理模板** " 部分中选择一个推荐的模板。
3. 流列出了流所需的嵌入连接，并注意连接状态是否可用。 如果需要，请更新不显示为可用的任何连接。 选择 " **继续**"。
4. 默认情况下，建议的流使用建议的内幕风险管理和 Microsoft 365 服务数据字段进行预配置，以完成流所分配的任务。 如果需要，请使用 " **显示高级选项** " 控件并配置流组件的可用属性，从而自定义流组件。
5. 如果需要，通过选择 " **新建步骤** " 按钮，向流中添加任何其他步骤。 在大多数情况下，建议的默认模板不需要这样做。
6. 选择 " **保存草稿** " 以保存流以进行进一步配置，或选择 " **保存** " 完成流的配置。
7. 选择 " **关闭** " 以返回 " **电源自动流** " 页面。 新模板将作为流列出在 " **我的流** " 选项卡上，并在使用创建流的用户的内幕风险管理案例时自动 **从下拉列表** 控件中获得。

>[!IMPORTANT]
>如果组织中的其他用户需要访问流，则必须共享流。

### <a name="create-a-custom-power-automate-flow-for-insider-risk-management"></a>为内幕风险管理创建自定义电源自动化流

您的组织的某些流程和工作流可能不在建议的内幕风险管理流模板的外部，您可能需要为内部人员风险管理领域创建自定义电源自动化流。 电源自动化流是灵活且支持广泛的自定义，但需要采取一些步骤，才能与内幕风险管理功能集成。

完成以下步骤以创建用于内幕风险管理的自定义 Power 自动模板：

1. **检查电源自动化流许可证**：若要创建使用内幕风险管理触发器的自定义电源自动化流，您需要使用电源自动许可证。 建议的内幕风险管理流模板不需要额外的许可，并作为内幕风险管理许可证的一部分包括在内。
2. **创建自动流**：创建在内部人员风险管理事件触发后执行一个或多个任务的流。 有关如何创建自动流的详细信息，请参阅 [create a flow In Power 自动化](https://docs.microsoft.com/power-automate/get-started-logic-flow)。
3. **选择 microsoft 365 合规性连接器**：搜索并选择 microsoft 365 合规性连接器。 此连接器启用内幕风险管理触发器和操作。 有关连接器的详细信息，请参阅 [连接器参考概述](https://docs.microsoft.com/connectors/connector-reference/) 一文。
4. **选择流的内幕风险管理触发器**：内部人员风险管理有两个可用于自定义电源自动流的触发器：
    - **对于选定的内幕风险管理案例**：可以从 "内幕风险管理案例" 仪表板页中选择此触发器的流。
    - **对于选定的内幕风险管理用户**：可以从 "内幕风险管理用户" 仪表板页中选择此触发器的流。
5. 为您的流选择内幕风险管理操作：您可以从用于内幕风险管理的多个操作中进行选择，以包含在自定义流中：
    - 获取内幕风险管理警报
    - 获取内幕风险管理案例
    - 获取内幕风险管理用户
    - 在案例中获取内幕风险管理警报
    - 添加内幕风险管理事例说明

### <a name="share-a-power-automate-flow"></a>共享电源自动化流

默认情况下，用户创建的电源自动流程仅对该用户可用。 若要让其他内幕风险管理用户拥有访问和使用流的权限，流创建者必须共享流。 若要共享流，您将使用 Microsoft 365 合规性中心中的**内幕风险管理解决方案**中的设置控件，或直接在 "**案例**" 或 "**用户" 仪表板**页中工作时自动控制中的 "**管理电源自动流**" 选项。 共享流后，与之共享的每个用户都可以访问**事例**和**用户仪表板**中的 "**自动**控制" 下拉列表中的流。

若要在 "设置" 区域中共享电源自动流，您必须是 " *内幕风险管理* " 或 " *内幕风险管理" 管理员* 角色组的成员。 若要与 **管理电源自动流** 选项共享电源自动流，您必须是至少一个 "内幕风险管理" 角色组的成员。

完成以下步骤以共享电源自动流：

1. 在[Microsoft 365 合规性中心](htttps://compliance.microsoft.com)中，转到 "**内幕风险管理**" 并选择 "**内幕风险设置**"  >  **自动执行流**。 您还可以通过选择 " **Cases** **自动** **Users dashboards**  >  **管理电源自动流程**"，从 "事例" 或 "用户" 仪表板页面访问。
2. 在 " **电源自动流** " 页上，选择 " **我的流** " 或 " **团队流** " 选项卡。
3. 选择要共享的流，然后从 "流量选项" 菜单中选择 " **共享** "。
4. 在 "流共享" 页面上，输入要作为流的所有者添加的用户或组的名称。
5. 在 " **使用的连接** " 对话框中，选择 **"确定"** 以确认添加的用户或组将拥有对流的完全访问权限。

### <a name="edit-a-power-automate-flow"></a>编辑电源自动化流

若要编辑流，您将使用 Microsoft 365 合规性中心中的**内幕风险管理**解决方案中的设置控件，或直接在**案例**或**用户仪表板**中工作时**自动**控制中的 "**管理电源自动流**" 选项。

若要在 "设置" 区域中编辑电源自动流，您必须是 " *内幕风险管理* " 或 " *内幕风险管理" 管理员* 角色组的成员。 若要使用 **管理电源自动流** 选项编辑电源自动流功能，您必须是至少一个 "内幕风险管理" 角色组的成员。

完成以下步骤以编辑电源自动流：

1. 在[Microsoft 365 合规性中心](htttps://compliance.microsoft.com)中，转到 "**内幕风险管理**" 并选择 "**内幕风险设置**"  >  **自动执行流**。 您还可以通过选择 " **Cases** **自动** **Users dashboards**  >  **管理电源自动流程**"，从 "事例" 或 "用户" 仪表板页面访问。
2. 在 " **电源自动流** " 页上，选择要编辑的流，然后从 "流控制" 菜单中选择 " **编辑** "。
3. 选择**ellipsis**  >  **Settings**用于更改流组件设置或通过**省略号**  >  **删除**以删除流组件的省略号设置。
4. 依次选择 " **保存** " 和 " **关闭** " 以完成流的编辑。

### <a name="delete-a-power-automate-flow"></a>删除电源自动流

若要删除流，您将使用 Microsoft 365 合规性中心中的**内幕风险管理**解决方案中的设置控件，或直接在**案例**或**用户仪表板**中工作时**自动**控制中的 "**管理电源自动流**" 选项。 删除流后，会将其作为选项删除以供所有用户使用。

若要在 "设置" 区域中删除电源自动流，您必须是 " *内幕风险管理* " 或 " *内幕风险管理" 管理员* 角色组的成员。 若要使用 " **管理电源自动流** " 选项删除电源自动流功能，您必须是至少一个 "内幕风险管理" 角色组的成员。

完成以下步骤以删除电源自动流：

1. 在[Microsoft 365 合规性中心](htttps://compliance.microsoft.com)中，转到 "**内幕风险管理**" 并选择 "**内幕风险设置**"  >  **自动执行流**。 您还可以通过选择 " **Cases** **自动** **Users dashboards**  >  **管理电源自动流程**"，从 "事例" 或 "用户" 仪表板页面访问。
2. 在 " **电源自动流** " 页上，选择要删除的流，然后从 "流控制" 菜单中选择 " **删除** "。
3. 在 "删除确认" 对话框中，选择 " **删除** " 以删除流，或选择 " **取消** " 退出删除操作。

## <a name="microsoft-teams-preview"></a>Microsoft 团队 (预览) 

合规性分析师和调查人员可以轻松地将 Microsoft 团队用于内幕风险管理案例的协作。 他们可以与 Microsoft 团队中的其他利益干系人协调和通信，以：

- 在专用团队频道中协调和查看案例的响应活动
- 安全地共享和存储与单个案例相关的文件和证据
- 通过分析师和调查人员跟踪和查看响应活动

在为 "内幕风险管理" 启用 Microsoft 团队后，每次确认通知并创建事例时，都会创建一个专用的 Microsoft 团队团队。 默认情况下，团队会自动将 " *内幕风险管理*"、" *内幕风险管理分析员*" 和 " *内幕风险管理调查员* " 角色组的所有成员包括 (最高100初始用户) 。 创建其他组织参与者后，可以将其添加到团队中并相应地添加到团队中。 对于在启用 Microsoft 团队之前创建的现有案例，分析师和调查人员可以选择在需要时创建新的 Microsoft 团队团队，在案例中工作。  在 "内幕风险管理" 中解析了关联的事例后，会自动将团队存档 (移动到隐藏和只读) 。

有关如何在 Microsoft 团队中使用团队和频道的详细信息，请参阅 [Microsoft 团队中的团队和频道概述](https://docs.microsoft.com/MicrosoftTeams/teams-channels-overview)。

启用 Microsoft 团队对案例的支持快速且易于配置。 若要为内部人员风险管理启用 Microsoft 团队，请完成以下步骤：

1. 在[Microsoft 365 合规性中心](htttps://compliance.microsoft.com)中，转到 "**内幕风险管理**  >  **内幕风险设置**"。
2. 选择 " **Microsoft 团队** " 选项卡。
3. 为内部人员风险管理启用 Microsoft 团队集成。
4. 选择 " **保存** " 以配置和退出。

### <a name="create-a-microsoft-teams-team-for-existing-cases"></a>为现有案例创建 Microsoft 团队团队

如果你在现有案例后启用了 Microsoft 团队支持内幕风险管理，则需要根据需要为每个案例手动创建一个团队。 在 "内幕风险管理" 设置中启用 Microsoft 团队支持后，新案例将自动创建一个新的 Microsoft 团队团队。

用户需要在组织中创建 Microsoft 365 组的权限，才能从案例创建 Microsoft 团队团队。 有关管理 Microsoft 365 组权限的详细信息，请参阅 [管理可以创建 microsoft 365 组的用户](https://docs.microsoft.com/microsoft-365/solutions/manage-creation-of-groups)。

若要为案例创建团队，请在直接在现有事例中工作时使用 "创建 Microsoft 团队" 控件。 完成以下步骤以创建新团队：

1. 在[Microsoft 365 合规性中心](htttps://compliance.microsoft.com)中，转到 "**内幕风险管理**  >  **案例**" 并选择现有事例。
2. 在 "案例操作" 菜单上，选择 " **创建 Microsoft 团队**"。
3. 在 " **团队名称** " 字段中，输入新的 Microsoft 团队团队的名称。
4. 选择 " **创建 Microsoft 团队** "，然后选择 " **关闭**"。

根据分配给内幕风险管理角色组的用户数量，在案例中，所有调查人员和分析师可能需要15分钟才能添加到 Microsoft 团队团队。
