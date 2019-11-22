---
title: Microsoft 合规性分数发行说明
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
description: Microsoft 合规性分数的发行说明和已知问题（预览版）（M365 合规性中心中的一项功能，可帮助简化和自动化风险评估）。
ms.openlocfilehash: d46e8a621b6f4daa1275a78b5cc1e6917e0a997c
ms.sourcegitcommit: 3eae8fe39cea912d29e211a1c9fd035d6b606f91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "38793636"
---
# <a name="microsoft-compliance-score-preview-release-notes"></a>Microsoft 合规性分数（预览）发行说明

Microsoft 合规性分数的公开预览为你提供了对即将推出的功能和更新的早期访问权限。

合规性分数是[Microsoft 365 合规性中心](microsoft-365-compliance-center.md)中的一项新功能，可计算基于风险的分数，从而衡量完成建议的操作以帮助降低合规性风险的进度。

## <a name="compliance-score-and-compliance-manager-relationship"></a>合规性分数和合规性管理器关系

现在，在合规性管理器中处理的许多合规性函数都可以在合规性分数中完成。 但是，某些功能仍仅驻留在合规性管理器中，并且在公共预览版期间，合规性管理器中的一些以前的功能会发生更改。 

在公共预览版过程中使用合规性分数和合规性管理器时，请牢记以下几点：

- **管理评估**：用户可以按合规性分数查看评估及其状态详细信息。 但是，用户只能在合规性管理器（[查看说明](working-with-compliance-manager.md#assessments)）和任务中执行评估管理任务，并将其限制为以下各项：
    - 上载新的评估，但不修改现有评估。 如果需要修改现有评估，将需要上传新模板。
    - 导出评估
    - 存档评估
    - 查看存档的评估
 - **创建用于评估的模板**： 
   - 用户必须转到合规性管理器以创建新模板并导出现有模板。 
   - 现有模板不能自定义。 阅读有关[管理合规性管理器中的模板](working-with-compliance-manager.md#templates)的说明。
   - 创建模板时，您必须包括**产品**和**证书**的维度，以确保您的模板在合规性分数中显示。
 - **设置权限**：合规性分数以前未授予合规性管理器中的权限的用户必须在 Microsoft 365 合规性中心中设置其权限。 以前在合规性管理器中设置了其角色的用户可以在遵守合规性分数时使用相同级别的访问权限。
- **数据传输**：具有驻留在合规性管理器中的数据的组织将看到符合性分数的数据，反之亦然。
- **根据合规性分数登录合规性管理器**：如果用户已登录合规性分数并选择链接以转到合规性管理器，则用户将不必再次登录。 单击该链接后，将在浏览器中打开一个新的选项卡，其中带有一个对话框。 在标题为 "已成为 Microsoft 云服务客户" 的顶部部分？ 登录您的帐户，选择 "**登录**" 按钮以自动登录合规性管理器。

## <a name="known-issues-in-compliance-score-preview"></a>合规性分数中的已知问题（预览）

以下各节介绍了在即将发布的合规性分数中要解决的已知问题。

### <a name="launch-now-links-in-certain-improvement-actions"></a>在某些改进操作中立即启动链接

在某些改进操作中，选择显示在实现指令下方的 "**立即启动**" 链接会产生错误。 若要访问正确的目标（即 SharePoint 管理中心），请按照以下步骤操作：

1. 转到[Microsoft 365 管理中心](https://admin.microsoft.com)。
2. 在左侧导航菜单上，选择 "**全部显示**"。
3. 在 "**管理中心" 下，** 选择 " **SharePoint**"。

以下是受影响的改进操作，它们都驻留在 "**保护信息**" 类别中：
  - 将加密应用于 SharePoint 库
  - 对 SharePoint Online 中的数据进行分类
  - 配置外部共享链接以使其过期
  - 为文档库启用版本控制

### <a name="long-load-times-for-non-admin-users"></a>非管理员用户的长时间加载时间
合规性分数在尝试登录时，保留非管理员角色角色的用户可能会遇到较长的加载时间。 刷新浏览器将解决此问题。 （了解有关[合规性分数角色](compliance-score-setup.md#set-user-permissions-and-assign-roles)的详细信息。）

### <a name="supported-browsers"></a>支持的浏览器

- Microsoft Edge、Chrome 和 Safari 的最新版本均受支持。
- 在刷新浏览器之前，可能会出现更新后的数据未出现的情况。
- Microsoft Edge 的预览版本不受支持，但没有已知问题。
- 不支持 Internet Explorer。
 
### <a name="language-support"></a>语言支持

- 合规性分数仅适用于美国英语版。