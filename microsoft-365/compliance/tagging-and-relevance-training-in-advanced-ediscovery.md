---
title: 高级电子数据展示中的标记和相关性培训
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
titleSuffix: Office 365
ms.date: 09/14/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 8576cc86-d51b-4285-b54b-67184714cc62
description: 了解在高级电子数据展示的相关培训阶段，要标记并使用40文件的培训示例的步骤。
ms.openlocfilehash: 56ce30754e04d4a2adcf854093e603f93be5ae36
ms.sourcegitcommit: c43ebb915fa0eb7eb720b21b62c0d1e58e7cde3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2020
ms.locfileid: "44936668"
---
# <a name="tagging-and-relevance-training-in-advanced-ediscovery-classic"></a>高级电子数据展示中的标记和相关性培训（经典）

> [!NOTE]
> 若要使用高级电子数据展示，组织必须订阅随附高级合规性加载项的 Office 365 E3，或订阅 E5。如果没有此计划，但又要试用高级电子数据展示，可以[注册 Office 365 企业版 E5 试用版](https://go.microsoft.com/fwlink/p/?LinkID=698279)。 
  
本主题介绍使用高级电子数据展示相关性培训模块的过程。 
  
在高级电子数据展示中完成评估并进入相关性培训阶段后，将在标记选项卡中添加一个40文件的培训示例。 
  
## <a name="performing-relevance-training"></a>执行关联性培训

1. 在 "**相关性 \> 标记**" 选项卡中，默认情况下将在左窗格中显示 "标记" 窗格，并显示示例文件（一次显示一个标记）。 
    
    ![相关性标签面板](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    在 "**标签**" 选项卡中，显示文件的显示名称。 这可以是路径、电子邮件主题、标题或用户定义的名称。 可以通过右键单击文件路径来复制 ID、文件路径或文本路径。 
    
    "**标记**" 选项卡标记统计信息显示文件示例编号（位于左侧窗格顶部）、示例中当前显示的文件的编号（右边窗格的底部）以及示例中的已标记文件（左侧窗格的底部）的当前总数，这些文件在您标记文件时进行了更改。 这适用于任何已完成的相关性标记，无论是在评估、培训、追赶还是测试中。 
    
    表示注释、标记和系列文件的存在的图标显示在文件视图中文件的上方。
    
2. 为事例问题确定文件的相关性，并使用 "标记" 选项图标按钮或键盘快捷方式标记文件，如下表所示：

|**标记选项**|**说明**|**键盘快捷方式**|**对于多个问题-批量标记键盘快捷方式**|
|-----|-----|-----|-----|
|R  <br/> |符合  <br/> |Z  <br/> |Shift + Z  <br/> |
|FÜHRERSCHEIN-NR  <br/> |无关  <br/> |X  <br/> |Shift + X  <br/> |
|Skip  <br/> |Skip  <br/> |C  <br/> |Shift + A  <br/> |
   
  - 如果一个文件存在多个问题，则在标记一个问题后，所选内容将移至下一个问题（如果有）。 
    
  - 在突出显示关键字（相关性设置突出显示的关键字）时，由管理员或事例管理者定义的关键字 \> 将显示（以指定的颜色为单位），以帮助标识相关文件在加标签时。 如果一个关键字有双下划线，则可单击它以显示带有关键字说明的工具提示。 
    
    （可选）在 "**标记**" 选项卡中，单击 "**标记设置**" 以设置以下选项： 
    
    ![相关性标签设置](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
  - **批量标记**：使用此选项可以为文件分配多个问题，方法是选择 "**全部**" 以为所选文件设置所有问题（重写已标记的问题）的标记，或选择 **"rest** " 将该标记应用于其余的未加标签的问题。 选定的选项在此用户的所有情况下始终有效，直到该用户发生更改（针对所有用户案例为每个用户设置）。 
    
  - **自动标记**：选中此复选框可在单个相关标记后将文件的其他问题设置为 "不相关"。
    
  - "**自动换片**：选中此复选框可在标记最后一个或仅有无标签的问题时，将显示的文件选择移动到下一个文件。 
    
    对于相关性培训和相关性评分目的，不会考虑跳过的文件。
    
3. 可以通过左窗格下拉列表中的 "**注释**" 选项查看和编辑与文件相关的自由文本注释。 （可选） 
    
4. 可以通过选择左窗格下拉列表中的 "**标记指南**" 选项来查看标记的指南。 
    
5. 完成列表中所有文件的标记并准备好计算结果后，请单击 "**计算**"。 将显示 "**跟踪**" 选项卡。 
    
## <a name="working-with-the-sample-files-list"></a>使用示例文件列表

示例文件列表允许您查看培训示例中的文件列表，并对一个或多个文件执行各种操作。 在 "**相关性** \> **标记**" 选项卡中，**示例文件**左窗格显示了用于处理评估、培训、追赶和不一致流程的示例文件的列表。 
  
1. 在 "**相关性 \> 标记**" 选项卡中，选择左窗格下拉列表中的示例文件。 示例文件在左窗格中列出。 
    
    ![相关性标记示例文件列表](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. 通过在 "**示例**" 或 "**文件**" 框中输入或选择一个特定的采样或文件编号来选择它们。 
    
  -   - 文件序列号列在 "**标记**" 选项卡上显示的文件列表的左侧列中。通过单击标题，文件的原始显示顺序将恢复为其原始顺序。 
    
  - 单击某个文件行会在右侧窗格中显示其内容。
    
  - 使用下面的菜单栏选项在当前示例中的文件之间导航。 此外，导航键盘快捷方式也可用：
    
    导航到示例中的第一个文件： Shift + Ctrl +\<
    
    导航到示例中的上一个文件： Shift +\<
    
    导航到示例中的下一个文件： Shift +\>
    
    导航到示例中的最后一个文件： Shift + Ctrl +\>
    
## <a name="see-also"></a>另请参阅

[高级电子数据展示（经典）](office-365-advanced-ediscovery.md)
  
[了解相关性方面的评估](assessment-in-relevance-in-advanced-ediscovery.md)
  
[标记和评估](tagging-and-assessment-in-advanced-ediscovery.md)
  
[跟踪相关性分析](track-relevance-analysis-in-advanced-ediscovery.md)
  
[根据结果做出决定](decision-based-on-the-results-in-advanced-ediscovery.md)
  
[测试相关性分析](test-relevance-analysis-in-advanced-ediscovery.md)

