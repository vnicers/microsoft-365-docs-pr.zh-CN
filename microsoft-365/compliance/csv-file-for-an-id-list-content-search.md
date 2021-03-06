---
title: 准备用于 ID 列表内容搜索的 CSV 文件
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 82c97bb4-2b64-4edc-804d-cedbda525d22
ms.custom:
- seo-marvel-apr2020
description: 使用现有内容搜索中的 CSV 文件创建一个返回特定电子邮件的 ID 列表搜索。
ms.openlocfilehash: 7b63a78d34306cf3afcef49276e584bc816c107f
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "44817971"
---
# <a name="prepare-a-csv-file-for-an-id-list-content-search"></a>准备用于 ID 列表内容搜索的 CSV 文件

您可以使用 Exchange Id 列表搜索特定邮箱电子邮件和其他邮箱项目。 若要创建 ID 列表搜索（正式称为目标搜索），请提交一个逗号分隔值（CSV）文件，该文件标识要搜索的特定邮箱项目。 对于此 CSV 文件，您可以使用在导出内容搜索结果或从现有内容搜索中导出内容搜索报告时所包含的**Results.csv**文件或未**编制索引的 Items.csv**文件。 然后，编辑其中一个文件以指示要搜索的特定项目，然后创建一个新的 ID 列表搜索并提交 CSV 文件。

以下是创建 ID 列表搜索的过程的快速概述。

1. 在安全 & 合规中心中创建和运行新的或引导的内容搜索。

2. 导出内容搜索结果或导出内容搜索报告。 有关详细信息，请参阅：

    - [导出内容搜索结果](export-search-results.md)

    - [导出内容搜索报告](export-a-content-search-report.md)

3. 编辑**Results.csv**文件或未**索引的 Items.csv** ，并标识要包括在 ID 列表搜索中的特定邮箱项目。 有关为 ID 列表搜索准备 CSV 文件的[说明](#prepare-the-csv-file-for-an-id-list-search)，请参阅。

4. 创建新的 ID 列表搜索（请参阅[说明](#create-an-id-list-search)）并提交您准备的 CSV 文件。 创建的搜索查询将仅搜索 CSV 文件中选定的项目。

> [!NOTE]
> 仅邮箱项目支持 ID 列表搜索。 您无法在 ID 列表搜索中搜索 SharePoint 和 OneDrive 文档。

 **为什么要创建 ID 列表搜索？** 如果您无法确定某个项目是否根据**Results.csv**中的元数据或非**索引 Items.csv**文件中的元数据响应电子数据展示请求，则可以使用 ID 列表搜索来查找、预览和导出该项目，以确定它是否能响应您正在调查的案例。 ID 列表搜索通常用于搜索和返回一组特定的未编制索引的项目。

## <a name="prepare-the-csv-file-for-an-id-list-search"></a>为 ID 列表搜索准备 CSV 文件

导出内容搜索的搜索结果或报告之后，可以执行以下步骤来准备用于 ID 列表搜索的 CSV 文件。 此 CSV 文件将标识 ID 列表搜索中的每个项目。

请注意，可以从包含 SharePoint 网站和 OneDrive 帐户的搜索中使用 CSV 文件，但只能为 ID 列表*搜索选择邮箱*项目。 如果选择 SharePoint 或 OneDrive 中的文档，则创建 ID 列表搜索时，CSV 文件验证将失败。

1. 在 Excel 中打开 " **Results.csv** " 或 "未**编制索引的 Items.csv** " 文件。

2. 在 "**所选**" 列中，在与要搜索的项目相对应的单元格中键入 **"是"** 。 对要搜索的每个项目重复此步骤。

    > [!IMPORTANT]
    > 当您在 Excel 中打开 CSV 文件时，"**文档 ID** " 列的数据格式将更改为 "**常规**"。 这将导致显示科学记数法中项的文档 ID。 例如，文档 ID "481037338205" 显示为 "4.81037 E + 11"。必须执行后续步骤将**文档 id**列的数据格式更改为 "**数字**"，以还原文档 id 的正确格式。 如果不执行此操作，则使用 CSV 文件的 ID 列表搜索将失败。

3. 右键单击整个 "**文档 ID** " 列，然后选择 "**设置单元格格式**"。

4. 在 "**类别**" 框中，单击 "**数字**"。

5. 将小数位数更改为**0**，然后单击 **"确定"** 以保存所做的更改。 请注意，"文档 ID" 列中的值更改为 "数字"。

    下面的示例展示了一个为 ID 列表内容搜索准备提交的 CSV 文件。

    ![目标内容搜索的 CSV 文件的示例](../media/8371b8cb-1638-496e-9be1-fe1565757d67.png)

6. 保存 CSV 文件或使用 "**另存为**" 将文件保存为其他文件名。 在这两种情况下，请务必使用 CSV 格式保存文件。

## <a name="create-an-id-list-search"></a>创建 ID 列表搜索

下一步是创建新的 ID 列表内容搜索，并提交在上一步中准备的 CSV 文件。

> [!IMPORTANT]
> 在从内容搜索导出结果或报告之后，您应创建一个 ID 列表搜索不超过2天的时间。 如果在超过2天前导出的搜索结果或报告，应重新导出搜索结果或报告以生成更新的 CSV 文件。 然后，您可以准备一个更新的 CSV 文件，并使用它来创建一个 ID 列表搜索。

1. 在 "安全性 & 合规性中心中，转到"**搜索** \> **内容搜索**"。

2. 在 "**搜索**" 页上，单击 " ![ 添加图标新搜索" 旁边的箭头 ](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **New search**，然后单击 "**按 ID 列表搜索**"。

    ![单击 "新建搜索" 下拉列表中的 "按 ID 列表搜索"](../media/e65f9942-09b2-4127-865e-e64029a590df.png)

3. 在 "**按标识号搜索" 列表**中，命名搜索（并根据需要对其进行描述），然后单击 "**浏览**" 并选择在上一步中准备的 CSV 文件。

    Microsoft 365 尝试验证 CSV 文件。 如果验证失败，将显示一条错误消息，可能会帮助您解决验证错误。 必须成功验证 CSV 文件，才能创建 ID 列表搜索。

4. 成功验证 CSV 文件后，单击 "**搜索**" 以创建 ID 列表搜索。

    下面的示例展示了估计的搜索结果和为 ID 列表搜索生成的查询。

    ![详细信息窗格中的目标内容搜索的搜索查询](../media/dbd9e570-c04b-4056-a8a7-37e9916ec683.png)

    请注意，ID 搜索的统计信息中显示的估计项目数应与您在 CSV 文件中选择的项目数相匹配。

5. 预览或导出由 ID 列表搜索返回的项目。

> [!NOTE]
> 如果您在创建 ID 列表搜索之后移动邮箱，搜索的查询不会返回指定的项目。 这是因为在移动邮箱时，邮箱项目的**DocumentId**属性会发生更改。 在创建 ID 列表搜索之后移动邮箱时，在少数情况下，您应创建新的内容搜索（或更新现有内容搜索的搜索结果），然后导出搜索结果或报表以生成可用于创建新的 ID 列表搜索的已更新 CSV 文件。
