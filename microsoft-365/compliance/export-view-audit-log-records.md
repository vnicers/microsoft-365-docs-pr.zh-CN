---
title: 导出、配置和查看审核日志记录
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
ms.custom: seo-marvel-apr2020
description: 在本文中，您将了解如何导出、配置和查看 Microsoft 365 审核日志记录。
ms.openlocfilehash: 688ba06fc9c5c2b26eef93fb1a68d311db9da5d8
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358490"
---
# <a name="export-configure-and-view-audit-log-records"></a>导出、配置和查看审核日志记录

在搜索审核日志并将搜索结果下载到 CSV 文件后，该文件包含一个名为 " **AuditData**" 的列，其中包含有关每个事件的其他信息。 此列中的数据的格式为 JSON 对象，该对象包含多个配置为 " *属性：值* " 对（用逗号分隔）的属性。 您可以使用 Excel 中 Power Query 编辑器中的 JSON 转换功能，将 **AuditData** 列中的 json 对象中的每个属性拆分为多个列，以便每个属性都有自己的列。 这样，您可以对一个或多个这些属性进行排序和筛选，这有助于您快速找到要查找的特定审核数据。

## <a name="step-1-export-audit-log-search-results"></a>步骤1：导出审核日志搜索结果

第一步是搜索审核日志，然后将结果以逗号分隔的 (CSV) 文件的值导出到本地计算机。
  
1. 如有必要，请运行 [审核日志搜索](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log) 并修改搜索条件，直到获得所需的结果。

2. 单击 " **导出结果** "，然后选择 " **下载所有结果**"。 

   ![单击 "下载所有结果"](../media/ExportAuditSearchResults.png)

   此选项可从您在步骤1中运行的审核日志搜索中导出所有审核记录，并将该审核日志中的原始数据下载到 CSV 文件中。 

   将在窗口底部显示一条消息，提示您打开或保存 CSV 文件。 

3. 单击 " **保存 > 另存为** "，然后将 CSV 文件保存到本地计算机。 下载多个搜索结果需要一段时间。 在搜索所有活动或广泛的日期范围时，通常会出现这种情况。 当 CSV 文件下载完成时，将在窗口底部显示一条消息。

   ![CSV 文件下载完成时显示的消息](../media/ExportAuditSearchResultsFinish.png)

> [!NOTE]
  > 你可以将最多 50,000 个条目从单个审核日志搜索中下载到 CSV 文件。 如果下载了 50,000 个条目到 CSV 文件，则可以假定可能存在超过 50,000 个符合搜索条件的事件。 若要导出超过此限制，请尝试使用日期范围来减少审核日志记录的数量。 你可能需要使用更小日期范围运行多个搜索来导出超过 50,000 个条目。

## <a name="step-2-format-the-exported-audit-log-using-the-power-query-editor"></a>步骤2：使用 Power Query 编辑器格式化导出的审核日志

下一步是在 Excel 的 Power Query 编辑器中使用 JSON 转换功能，将 **AuditData** 列中的 json 对象中的每个属性拆分为其自己的列。 然后，筛选列以根据特定属性的值查看记录。 这可以帮助您快速找到要查找的特定审核数据。

1. 在 Excel 中打开一个空白工作簿，以用于 Office 365、Excel 2019 或 Excel 2016。

2. 在 " **数据** " 选项卡上的 " **获取 & 转换数据** " 功能区组中，单击 " **发件人文本/CSV**"。

    ![在 "数据" 选项卡上，单击 "发件人文本/CSV"](../media/JSONTransformOpenCSVFile.png)

3. 打开您在步骤1中下载的 CSV 文件。

4. 在显示的窗口中，单击 " **转换数据**"。

   ![单击 "转换数据"](../media/JSONOpenPowerQuery.png)

   CSV 文件将在 **查询编辑器**中打开。 共有四列： **CreationDate**、 **UserIds**、 **Operations**和 **AuditData**。 **AuditData**列是一个包含多个属性的 JSON 对象。 下一步是为 JSON 对象中的每个属性创建一个列。

5. 右键单击 " **AuditData** " 列中的标题，单击 " **转换**"，然后单击 " **JSON**"。 

   ![右键单击 "AuditData" 列，单击 "转换"，然后选择 "JSON"。](../media/JSONTransform.png)

6. 在 " **AuditData** " 列的右上角，单击 "展开" 图标。

   ![在 "AuditData" 列中，单击展开图标](../media/JSONTransformExpandIcon.png)

   将显示 **AuditData** 列中 JSON 对象中的属性的部分列表。

7. 单击 " **加载更多** " 以在 **AuditData** 列中的 JSON 对象中显示所有属性。

   ![单击 "加载更多" 以显示 JSON 对象中的所有属性](../media/JSONTransformLoadJSONProperties.png)

   您可以取消选中任何您不想包含的属性旁边的复选框。 删除对调查不有用的列是减少审核日志中显示的数据量的好方法。 

   > [!NOTE]
   > 在上一屏幕截图中显示的 JSON 属性 (单击 " **加载更多**) 基于 CSV 文件中的前1000行中的" **AuditData** "列中的属性。 如果第一个1000行后面的记录中有不同的 JSON 属性，则在 **AuditData** 列拆分为多个列时，这些属性 (并且相应的列) 不会包括在内。 若要帮助防止这种情况，请考虑重新运行审核日志搜索并缩小搜索条件，以便返回的记录较少。 另一种解决方法是在 " **操作** " 列中筛选项目，以减少在 **AuditData** 列中转换 JSON 对象之前)  (的行数。

8. 执行下列操作之一，设置为所选的每个 JSON 属性添加的列的标题。

    - 取消选中 " **使用原始列名称作为前缀** " 复选框，以将 JSON 属性的名称用作列名称;例如， **RecordType** 或 **SourceFileName**。

    - 将 "**使用原始列名称作为前缀**" 复选框保留为选中状态，以将 AuditData 前缀添加到列名称中;例如，RecordType 或**AuditData**。 **AuditData** 。

9. 单击****“确定”。

    **AuditData**列拆分为多个列。 每个新列对应于 AuditData JSON 对象中的一个属性。 该列中的每一行都包含属性的值。 如果属性不包含值，则显示 *null* 值。 在 Excel 中，空值的单元格为空。
  
10. 在 " **开始** " 选项卡上，单击 " **关闭 & 加载** " 以关闭 Power Query 编辑器，并在 Excel 工作簿中打开转换后的 CSV 文件。

## <a name="use-powershell-to-search-and-export-audit-log-records"></a>使用 PowerShell 搜索和导出审核日志记录

您可以使用 Exchange Online PowerShell 中的 [UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) cmdlet 将审核日志搜索结果导出到 CSV 文件，而不是使用安全 & 合规中心中的审核日志搜索工具。 然后，您可以按照步骤2中描述的相同过程使用 Power Query 编辑器格式化审核日志。 使用 PowerShell cmdlet 的一个优点是，您可以使用 *RecordType* 参数从特定服务中搜索事件。 下面是使用 PowerShell 将审核记录导出到 CSV 文件的几个示例，以便您可以使用 Power Query 编辑器转换 **AuditData** 列中的 JSON 对象，如步骤2中所述。

在此示例中，运行以下命令以返回与 SharePoint 共享操作相关的所有记录。

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointSharingOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

搜索结果将导出到名为 *PowerShellAuditlog* 的 CSV 文件中，该文件包含四列： CreationDate、UserIds、RecordType、AuditData) 。

您还可以将记录类型的名称或枚举值用作 *RecordType* 参数的值。 有关记录类型名称及其相应的枚举值的列表，请参阅[Office 365 管理活动 API 架构](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#enum-auditlogrecordtype---type-edmint32)中的*AuditLogRecordType*表。

您只能包含 *RecordType* 参数的单个值。 若要搜索其他记录类型的审核记录，您必须再次运行前面的两个命令以指定不同的记录类型，并将这些结果追加到原始 CSV 文件中。 例如，您可以运行以下两个命令，将 SharePoint 文件活动从同一日期范围添加到 PowerShellAuditlog.csv 文件中。

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointFileOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Append -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

## <a name="tips-for-exporting-and-viewing-the-audit-log"></a>导出和查看审核日志的提示

下面是在使用 JSON 转换功能将 **AuditData** 列拆分为多个列之前和之后导出和查看审核日志的一些提示和示例。

- 筛选 **RecordType** 列以仅显示特定服务或功能区域中的记录。 例如，若要显示与 SharePoint 共享相关的事件，您可以选择 **14** (由 SharePoint 共享活动触发的记录) 的枚举值。 有关与 **RecordType** 列中显示的枚举值相对应的服务列表，请参阅 [audit Log 中的详细属性](detailed-properties-in-the-office-365-audit-log.md)。

- 筛选 " **操作** " 列以显示特定活动的记录。 有关与安全 & 合规中心中的审核日志搜索工具中的可搜索活动对应的大多数操作的列表，请参阅在 [安全 & 合规性中心中搜索审核日志](search-the-audit-log-in-security-and-compliance.md#audited-activities)中的 "已审核的活动" 部分。
