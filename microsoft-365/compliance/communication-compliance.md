---
title: Microsoft 365 中的通信合规性（预览）
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
description: 了解 Microsoft 365 中的通信合规性
ms.openlocfilehash: 3765e8236b319eaadc543782f2254aefaa8914a2
ms.sourcegitcommit: 33242c260439de0d8db41247e9414913f24adc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "38685070"
---
# <a name="communication-compliance-in-microsoft-365-preview"></a>Microsoft 365 中的通信合规性（预览）

通信合规性是 Microsoft 365 中新的内幕风险解决方案集的一部分，可帮助您对组织中不适当的邮件进行检测、捕获和采取补救措施，从而帮助最大限度地减少通信风险。 通过预定义和自定义策略，可以扫描策略匹配的内部和外部通信，以便指定的审阅者可以对其进行检查。 审阅者可以调查组织中扫描的电子邮件、Microsoft 团队或第三方通信，并采取适当的补救措施以确保它们符合组织的邮件标准。

Microsoft 365 中的通信合规性策略可帮助您解决与合规性、内部和外部通信相关的许多新式难题，包括：

- 扫描日益增长的通信信道类型
- 邮件数据量的增加
- 法规实施 & 受到罚款的风险

在某些组织中，IT 支持与合规性管理组之间可能存在的职责分离。 Microsoft 365 支持通信合规性配置和扫描通信策略配置的分离。 例如，组织的 IT 组可能负责设置角色权限和组，以支持由组织的合规性团队配置和管理的通信合规性策略。

## <a name="scenarios-for-communication-compliance"></a>通信合规性方案

通信合规性策略可协助在几个重要的合规性领域中查看组织中的邮件：

- **公司策略**

    员工必须遵守其所有与业务相关的通信中的可接受使用、道德标准和其他公司政策。 通信合规性策略可以检测策略匹配，并帮助您采取纠正措施来帮助缓解这些类型的事件。 例如，您可以扫描组织中的员工通信，以查找潜在的人为资源问题，如骚扰或使用不当或攻击性的语言。

- **风险管理**

    组织负责在其基础结构和公司网络系统中分布的所有通信。 使用通信监督策略来帮助确定和管理潜在的法律暴露和风险，可帮助最大限度地减少风险，然后才会损坏公司运营。 例如，您可以扫描组织中的邮件，以获取有关机密项目的未经授权的通信，例如即将进行的收购、合并、收益披露、reorganizations 或领导团队更改。

- **合规性**

    大多数组织必须符合其正常操作过程中的某些类型的法规遵从性标准。 这些法规通常要求组织为适合其行业的邮件服务实施某种类型的监督或监督过程。 金融行业规章颁发机构（FINRA）规则3110是一个很好的示例，它是组织实施监督过程以扫描员工通信以及它所参与的企业类型的一个很好的示例。 另一个示例可能是查看组织中的经纪人通信以防止潜在的 laundering、内幕交易、collusion 或 bribery 活动的需要。 通过提供扫描和报告公司通信的过程，通信合规性策略可以帮助您的组织满足这些要求。

## <a name="new-enhancements"></a>新的增强功能

Microsoft 365 中的通信合规性建立在[Office 365 中的监督策略](supervision-policies.md)功能之上，具有以下几项新的增强功能：

- 智能可自定义模板
- 灵活的补救工作流
- 可操作的见解

![通信合规性主页](media/communication-compliance-home.png)

### <a name="intelligent-customizable-templates"></a>智能可自定义模板

通过通信合规性的智能可自定义模板，您可以应用机器学习，以智能化检测组织中的通信冲突。

- **可自定义的预先配置的模板**：新的策略模板可帮助解决最常见的通信风险。 使用预定义的反骚扰和攻击性语言、敏感信息和法规遵从性模板，现在可以更快地创建初始策略和后续更新。
- **新机器学习支持**：内置威胁、骚扰和猥亵语言[分类](classifier-getting-started-with.md)程序有助于减少扫描邮件中的误报，并在调查和修正过程中保存审阅者时间。
- **改进了条件生成器**：配置策略条件现已简化为策略向导中的单个集成体验，减少了如何对策略应用条件的混淆。

### <a name="flexible-remediation-workflows"></a>灵活的补救工作流

利用内置的补救工作流，可以快速识别组织中具有策略匹配项的邮件并对其执行操作。 以下新功能提高了调查和补救活动的效率：

- **灵活修正工作流**：新的修正工作流可帮助您快速对策略匹配采取措施，包括将邮件升级到其他审阅者的新选项以及向具有策略匹配的用户发送电子邮件通知。
- **对话线程**：邮件现在以直观方式按原始邮件和所有关联的答复邮件进行分组，从而在调查和修正操作过程中获得更好的上下文。
- **关键字突出显示**：术语匹配策略条件在邮件文本视图中突出显示，以帮助审阅者快速查找和修正策略通知。
- **确切的和接近的重复检测**：除了扫描匹配通信合规性策略的确切术语，临近的重复检测也会对以文字为依据的术语和消息进行分组，以帮助加快审阅过程。
- **新筛选器**：使用多个字段（包括发件人、收件人、日期、域等）的邮件筛选器更快地调查和修正策略警报。
- **改进的邮件视图**：现在，使用新的邮件源、文本和批注视图，调查和修正操作的速度更快。 现在可以查看邮件附件，以便在采取补救措施时提供完整的上下文。
- **用户历史记录视图**：所有用户邮件修正活动的历史视图（如过去的策略匹配通知和升级）现在，在修正工作流程过程中为审阅者提供更多上下文。 对用户的策略匹配的首次或重复实例现已存档，可轻松查看。

### <a name="actionable-insights"></a>可操作的见解

新的用于通知、策略匹配、操作和趋势的交互仪表板可帮助您快速查看组织中的挂起和已解决通知的状态。

- **主动预防性智能警报**：需要立即关注的策略匹配警报包括按严重性排序的新仪表板和发送给指定审阅者的新自动电子邮件通知。
- **交互仪表板**：新仪表板显示策略匹配、挂起和解决的操作，以及用户和策略的趋势。
- **审核支持**：可以轻松地从 Microsoft 365 合规性中心导出策略和审阅活动的完整日志，以帮助支持审核审阅请求。

## <a name="integration-with-microsoft-365-services"></a>与 Microsoft 365 服务集成

通信合规性策略跨多个通信通道扫描和捕获邮件，以帮助您快速查看和修正合规性问题：

- **Microsoft 团队**：针对公共和私有[microsoft 团队](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)频道和个人聊天的聊天通信和相关附件在通信合规性中支持作为独立频道源或其他 Microsoft 365 服务。 现在，策略将自动扫描策略中定义的特定用户的所有 Microsoft 团队频道和团队，从而无需为 Microsoft 工作组工作分配保留单独的映射列表。
- **Exchange online**：在 Microsoft 365 组织中的[exchange online](https://docs.microsoft.com/Exchange/exchange-online)上托管的所有邮箱都符合扫描条件。 与通信合规性策略条件匹配的电子邮件和附件可立即用于监视和监控报告。 Exchange Online 现在是一个可选的源通道，并且在通信合规性策略中不再需要。
- **Skype For Business online**：通信合规性策略支持在[Skype for business Online](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)中扫描聊天通信和关联的附件。
- **第三方来源**：您可以从[第三方来源](archiving-third-party-data.md)扫描邮件，以获取在 Microsoft 365 组织中导入到邮箱中的数据。 通信合规性支持与几个流行平台（包括即时 Bloomberg、Facebook、Twitter 和其他平台）的连接。

若要了解有关通信合规性策略中的邮件传递通道支持的详细信息，请参阅[支持的通信类型](communication-compliance-feature-reference.md#supported-communication-types)。

## <a name="workflow"></a>工作流

通信合规性帮助您解决与遵守内部策略和法规遵从性要求相关的常见痛点。 使用集中式策略模板和灵活的工作流，您可以使用可操作的见解快速解决检测到的合规性问题。

通过 Microsoft 365 中的通信合规性确定和解决合规性问题，请使用以下工作流：

![通信合规性工作流](media/communication-compliance-workflow.png)

### <a name="configure"></a>配置

在此工作流步骤中，您可以确定合规性要求并配置适用的通信合规性策略。 策略模板是一种很好的方法，不仅可以快速配置新的符合性策略，还可以在要求发生变化时快速修改和更新策略。 例如，在为组织中的所有用户配置策略之前，您可能需要为一小部分用户在通信中快速测试针对冒犯性语言和反骚扰的策略。

您可以从 Microsoft 365 合规性中心的以下策略模板中进行选择：

- **冒犯性语言和反骚扰**：使用此模板可以快速创建使用内置分类器的策略，以自动检测可能被视为滥用或攻击性的内容。
- **敏感信息**：使用此模板创建用于扫描包含定义的敏感信息类型或关键字的通信的策略，以帮助确保重要数据不与不应访问的用户共享。
- **法规遵从性**：使用此模板创建策略以扫描通信，以查找与法规标准相关联的标准财务术语的参考。
- **自定义策略**：使用此模板可配置特定通信通道、各个检测条件以及在组织中要查看的内容量。

### <a name="investigate"></a>调查

在此步骤中，您将更深入地了解检测到与通信合规性策略相匹配的问题。 此步骤包括 Microsoft 365 合规性中心中提供的以下操作：

- **警报**：当邮件符合监督策略时，将自动生成警报。 对于每个警报，您都可以看到状态、严重性、检测到的时间，以及是否分配了事例以及其状态。 新警报显示在通信合规性主页和 "**警报**" 页面上，并按严重性顺序列出。
- **问题管理**：对于每个通知，您都可以采取调查操作来帮助修正邮件中检测到的问题
- **文档审阅**：在调查问题期间，您可以使用邮件的多个视图来帮助正确评估检测到的问题。 这些视图包括对话摘要、仅文本、已批注和通信对话的详细信息视图。
- 查看**用户活动历史记录**：查看用户消息活动和更正操作的历史记录，如策略匹配的过去通知和升级。
- **筛选器**：使用筛选器（如发件人、收件人、日期和主题）快速缩小要审阅的邮件通知。

### <a name="remediate"></a>修正

下一步是使用以下选项修正已调查的通信合规性问题：

- **解决**方法：查看问题后，可以通过解析警报进行修正。 解析警报会将其从待处理的警报队列中删除，并将操作保留为匹配策略的已解析队列中的条目。 在将警报标记为误报、向员工发送有关通知的通知或打开警报的新事例之后，将自动解决通知。
- **标记邮件**：作为问题解决的一部分，您可以将检测到的邮件标记为兼容性、不符合条件或可疑之处，因为它与组织的策略和标准相关。 标记可帮助您微筛选策略警报以进行升级或作为其他内部审核流程的一部分。
- **通知用户**：通常，用户意外或无意地违反通信合规性策略。 您可以使用通知功能向用户提供警告通知并解决问题。
- **升级到另一个审阅者**：有时，问题的最初审阅者需要从其他审阅者处进行输入，以帮助解决事件。 您可以轻松地将邮件问题提升到组织其他区域中的审阅者，作为解决过程的一部分。
- **标记为误报**：在符合性策略的匹配项中，错误地检测到邮件将偶尔遍历到审阅过程。 您可以将这些类型的警报标记为误报并自动解决问题。

### <a name="monitor"></a>监视

跟踪和管理由通信合规性策略标识的合规性问题跨整个工作流过程。 在生成警报并实施调查和修正操作后，现有策略可能需要审阅和更新，并且可能需要创建新策略。

- **监视和报告**：使用在统一 Office 365 审核日志中记录的通信合规性仪表板、报告、导出日志和事件，以不断评估和改进您的合规性状况。

## <a name="ready-to-get-started"></a>准备好开始了吗？

若要为 Microsoft 365 组织配置通信合规性，请参阅[configure communication 合规性 For microsoft 365 （预览）](communication-compliance-configure.md)。