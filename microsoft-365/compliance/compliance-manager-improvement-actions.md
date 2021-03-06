---
title: 在 Microsoft 合规性管理器中分配和完成改进操作
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 了解如何在 Microsoft 合规性管理器中对控件执行实现和测试。 分配工作、存储文档和导出报告。
ms.openlocfilehash: 99b08ca1336c3f347764230896af47fe1486d4b2
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48204302"
---
# <a name="assign-and-complete-improvement-actions-in-compliance-manager"></a>在合规性管理器中分配和完成改进操作

**本文内容：** 本文介绍如何使用改进操作 **管理合规性工作流** 。 了解如何为实现和测试 **分配改进操作** 、 **管理更新**和导出 **报告**。

## <a name="manage-compliance-workflows-with-improvement-actions"></a>使用改进操作管理合规性工作流

改进的操作将对合规性活动进行集中。 每个改进操作都提供了详细的实施指导，可帮助您与数据保护法规和标准保持一致。 可将操作分配给组织中的用户，以执行实施和测试工作。 您还可以在操作中存储文档、注释和记录状态更新。

"改进操作" 页面上列出了所有改进操作。 了解有关 [查看改进操作](compliance-manager-setup.md#improvement-actions-page)的详细信息。

## <a name="improvement-actions-details-page"></a>改进操作详细信息页

每个改进操作都有详细信息页面，显示其当前状态、相关的标准和法规要求以及建议的实现指南。 [技术操作](compliance-score-calculation.md#technical-and-non-technical-actions) 包括 **立即启动** 链接，该链接将带您转到合适的实施解决方案。 您可以将实现和测试文档直接附加到改进操作的详细信息页中。

若要查看改进操作的详细信息页面，请执行以下操作：

1. 转到 "改进操作" 页面。
2. 选择所需的 "改进" 操作的行，这将打开其详细信息页面。

通过选择屏幕右上角的向上或向下箭头，可以轻松查看列表中的下一个或上一个 "改进" 操作。 如果您在 "改进操作" 页面上筛选了列表，则向上或向下移动将转到该筛选列表中的下一项。

## <a name="assign-improvement-actions"></a>分配提高操作

若要开始实施改进操作，您可以自己执行工作，也可以将其分配给其他用户。 分配的人员可以是：

- 业务策略所有者
- IT 实现者
- 另一个负责执行任务的员工

一旦确定了相应的受理人，请确保他们拥有足够的 [合规性管理器角色](compliance-manager-setup.md#set-user-permissions-and-assign-roles) 来执行此工作。 然后按照以下步骤分配 "改进" 操作：

1. 从 "改进操作详细信息" 页中，选择屏幕左上角旁边的 " **编辑状态** "。

2. 在 "编辑状态" 浮出控件窗格中，选择 " **分配对象** " 框以显示 **建议的人员** 列表中的用户列表。 您可以从列表中选择用户，也可以键入要将其分配到的人员的电子邮件地址。

3. 选择 " **保存并关闭**"。 分配的用户将收到一封电子邮件，说明已向其分配了改进操作，并有一个指向改进操作的直接链接。

然后，分配的用户可以执行建议的操作。

## <a name="perform-work-and-store-documentation"></a>执行工作和存储文档

您可以将与实现和测试相关的文件和注释直接上载到 " **备注和文档** " 部分。 此环境是一个安全、集中的存储库，可帮助您演示控制的满意度，以满足合规性标准和法规要求。 任何具有只读访问权限的用户都可以读取此部分中的内容。 只有具有编辑权限的用户才能上载和下载文件，并可输入或编辑备注。

" **备注和文档** " 部分包含了上载的文档、实现说明、测试说明和其他注释的字段。

#### <a name="uploaded-documents"></a>上载的文档

- 选择 " **管理文档** " 以上传任何相关文件。
- 当 "管理文档" 浮出控件窗格打开时，选择 " **添加文档**"，然后从系统中选择文件。 接受的文件类型：
    - 文档 ( .doc、.xls、.ppt、.pdf) 
    -  ( .jpg、.png) 的图像
    - 视频 ( mkv) 
    - 压缩的文件 ( .zip 或 rar) 
- 文件在窗格中解析后，选择 " **关闭**"，这将自动保存文件附件。 然后，你将看到 "已 **上载文档**" 下方列出的文件。
- 若要下载或删除文档，请从文档列表下选择 " **管理文档** "。 在浮出控件窗格中，选择文档行以将其突出显示，然后选择 " **下载** " 或 " **删除**"。

#### <a name="implementation-notes-test-notes-and-additional-notes"></a>实现说明、测试说明和附加说明

- 若要添加这三个字段中任一字段的注释，请选择以下任一字段下的 " **编辑实现说明** "。
- 当浮出控件窗格打开时，在文本字段中输入备注，然后选择 " **保存并关闭**"。
- 若要编辑便笺，请选择 " **编辑实现说明**"，进行编辑，然后选择 " **保存并关闭**"。

"备注" 字段中没有字符限制。 建议保留备注摘要，以便可以从 "改进操作详细信息" 页轻松查看和编辑它们。

## <a name="change-improvement-action-status"></a>更改改进操作状态

您可以为每个改进操作记录实现状态和日期以及测试状态和日期。 使用编辑权限的任何用户都可以编辑 " **实施** " 和 " **测试状态** " 字段，而不是仅由指定人员编辑。

若要编辑改进操作的状态，请在 "详细信息" 页的左上部分选择 " **编辑状态** "。 以下是可用的字段和状态选项：

- **实现状态**
    - **未实现** -操作尚未实现
    - 已**实现**-操作已实现
    - **替代实现** -如果你使用其他第三方工具或执行 Microsoft 建议中未包含的其他操作，请选择此选项
    - **计划** 的操作计划实施
    - **超出范围** –操作与你的组织不相关，不会影响你的成绩
- **实施日期**：在实施状态为 "已实现" 或 "备选实现" 时可供选择
- **测试状态**：在实施状态为 "已实现" 或 "备选实现" 时可供选择：
    - **未评估** –操作尚未测试
    - 已通过评估员验证了已**通过的实现**。
    - **失败的低风险** -测试失败，低风险
    - **失败中等风险** -测试失败，中等风险
    - **失败的高风险** –测试失败，高风险
    - **超出范围** -此操作超出评估范围，不会影响你的成绩
- **测试日期**：在 "日历" 弹出窗口中切换以选择日期

各个组之间的常见操作同步。 当同一个组中的两个不同评估共享由您管理的改进操作时，您对操作的实现详细信息或状态所做的任何更新将自动同步到组中任何其他评估中的相同操作。 此同步使您能够实现一个改进操作，并在多个管理法规方面满足几个要求。

## <a name="assign-improvement-action-to-assessor-for-completion"></a>将 "改进" 操作分配给评估员以完成

完成工作、执行测试和上传证据后，下一步是将 "改进" 操作分配给评估员进行验证。 评估员验证工作并检查文档，并选择相应的测试状态。

**如果将 "测试状态" 设置为 "已传递"**：操作已完成，并且已实现的点显示达到的最大分数。 然后将这些点计为您的总体合规性分数。

**如果 "测试状态" 设置为 "失败"**：该操作不符合要求，并且评估员可以将其分配给适当的用户进行其他工作。

## <a name="accepting-updates-to-improvement-actions"></a>接受对改进操作的更新

如果有可用于改进操作的更新，则会在其名称旁边看到一个通知。 您可以接受更新，也可以将其推迟一段时间。

#### <a name="what-causes-an-update"></a>什么导致更新

如果有与计分、自动化或范围相关的更改，则会发生更新。 更改可能涉及基于法规变化的改进措施的新指导，或者可能因产品更改而异。 仅由贵组织管理的改进操作接收更新通知。

#### <a name="where-youll-see-assessment-update-notifications"></a>您将在其中看到评估更新通知

更新改进操作后，您将在 "改进操作" 页上的名称旁显示一个 **挂起的更新** 标签，并在其相关评估的 "详细信息" 页上看到该标签。

转到 "改进操作的详细信息" 页，并选择顶部横幅中的 " **查看更新** " 按钮，以查看有关更改的详细信息并接受或推迟更新。

#### <a name="review-update-to-accept-or-defer"></a>查看更新以接受或推迟

从 "改进操作详细信息" 页中选择 " **查看更新** " 后，屏幕右侧将显示一个弹出窗口。 浮出控件窗格提供有关更新的关键详细信息，例如评估受影响和分数和范围更改。

选择 " **接受更新** " 以接受对改进操作的所有更改。 **接受的更改是永久性**的。

> [!NOTE]
> 当您接受某一操作的更新时，您还将接受对此操作的任何其他版本或实例的更新。 更新将在租户范围内传播技术操作，并将传播非技术操作的组范围。

如果选择 " **取消**"，则更新不会应用于 "改进" 操作。 但是，在接受更新之前，你将继续查看 **待处理的更新** 通知。

**为什么我们建议接受更新**

接受更新有助于确保你具有使用解决方案的最新指南，并采取适当的改进措施以帮助你满足现有证书的要求。

**您可能需要推迟更新的原因**

如果你正在完成包括 "改进" 操作的评估，你可能需要确保在接受更新之前已完成工作。 您可以稍后推迟更新，方法是在 "审阅更新" 浮出控件窗格中选择 " **取消** "。

## <a name="export-a-report"></a>导出报告

选择屏幕左上角的 " **导出** "，下载包含所有改进操作的 Excel 工作表和 "改进操作" 页上显示的筛选器类别。