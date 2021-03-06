---
title: 批量编辑内容搜索
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/29/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 39e4654a-9588-41f6-892b-c33ab57bfbe2
ms.custom:
- seo-marvel-apr2020
description: 使用 "安全与合规中心" 中的 "批量搜索编辑器" 快速更改用于一个或多个内容搜索的查询和内容位置。
ms.openlocfilehash: 2bbe8248a82356a217557469b6639e28607be13e
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "44035520"
---
# <a name="bulk-edit-content-searches"></a>批量编辑内容搜索

您可以使用内容搜索工具中的批量搜索编辑器同时编辑多个搜索。 使用此工具可以快速更改一个或多个搜索的查询和内容位置。 然后，您可以重新运行搜索并为修订后的搜索获取新的估计搜索结果。 编辑器还允许您从 Microsoft Excel 文件或文本文件中复制并粘贴查询和内容位置。 这意味着您可以使用搜索统计信息工具查看一个或多个搜索的统计信息，将统计信息导出到 CSV 文件，在其中可以编辑 Excel 中的查询和内容位置。 然后，使用批量搜索编辑器将修订后的查询和内容位置添加到搜索中。 在您修订了一个或多个搜索之后，您可以重新启动它们并获取新的估计搜索结果。
  
有关使用搜索统计信息工具的详细信息，请参阅[查看内容搜索结果的关键字统计](view-keyword-statistics-for-content-search.md)信息。
  
## <a name="use-the-bulk-search-editor-to-change-queries"></a>使用批量搜索编辑器更改查询

1. 转到[https://protection.office.com](https://protection.office.com)，然后选择 "**搜索** \> **内容搜索**"。
    
2. 在搜索列表中，选择一个或多个搜索，然后选择 "**批量搜索编辑器** ![批量搜索编辑器"](../media/1ddb3d18-2f00-4a7b-98a6-817ca5ec7014.png)按钮。
    
    ![选择一个或多个搜索，然后选择 "批量搜索编辑器"](../media/600c9716-89a2-4451-b111-fa7cfaad2006.png)
  
    以下信息显示在批量搜索编辑器的 "**查询**" 页上。 
    
    !["批量搜索编辑器" 页将显示所选搜索的查询](../media/189659af-cc78-4479-b0bc-a93decad2f6c.png)
  
    a. "**搜索**" 列显示内容搜索的名称。 如前面所述，您可以编辑查询以查找多个搜索。 
    
    b. "**查询**" 列显示**搜索**列中列出的内容搜索的查询。 如果使用关键字列表功能创建了查询，关键字将由文本 * * `(c:s)`分隔 **。这表示关键字是通过**OR**运算符连接的。此外，如果查询包含条件，关键字和条件由文本 * * `(c:c)`分隔**。 这表示关键字（或关键字阶段）通过**and**运算符连接到条件。 例如，在前面的屏幕截图中，对于搜索 ContosoSearch1，KQL 查询等效`customer (c:s) pricing(c:c)(date=2000-01-01..2016-09-30)`于。 `(customer OR pricing) AND (date=2002-01-01..2016-09-30)`
    
3. 若要编辑查询，请在要更改的查询的单元格中选择，并执行下列操作之一。 当您选择单元格时，该单元格由一个蓝色框加上边框。
    
   - 在单元格中键入新的查询。 不能编辑查询的一部分。 您必须键入整个查询。
    
      或
    
    - 将新查询粘贴到单元格中。 这假设您已从文件（如文本文件或 Excel 文件）复制查询文本。
    
4. 在 "**查询**" 页上编辑了一个或多个查询之后，请选择 "**保存**"。
    
    修订后的查询显示在所选搜索的 "**查询**" 列中。 
    
5. 选择 "**关闭**" 以关闭批量搜索编辑器。 
    
6. 在 "**内容搜索**" 页上，选择您编辑的搜索，然后选择 "**启动**搜索" 以使用修订后的查询重新启动搜索。 
    
下面是使用批量搜索编辑器编辑查询的一些提示：
  
- 将现有查询（通过使用**Ctrl C** ）复制到文本文件中。 在文本文件中编辑查询，然后复制修订后的查询并将其粘贴（使用**Ctrl + V** ）回到 "**查询**" 页上的单元格。 
    
- 您还可以从其他应用程序（如 Microsoft Word 或 Microsoft Excel）复制查询。 但是，您可能无意中使用批量搜索编辑器将不受支持的字符添加到查询中。 阻止不受支持的字符的最佳方式是只在 "**查询**" 页上的单元格中键入查询。 或者，您可以复制 Word 或 Excel 中的查询，然后将其粘贴到纯文本编辑器（如 Microsoft 记事本）中的文件中。 接下来，保存文本文件，并在" **编码**"下拉列表中选择" **ANSI**"。 这将删除任何格式和不受支持的字符。 然后，可以将文本文件中的查询复制并粘贴到**查询**页面。 
    
  
## <a name="use-the-bulk-search-editor-to-change-content-locations"></a>使用批量搜索编辑器更改内容位置

1. 在一个或多个所选搜索的批量搜索编辑器中，选择 "**启用批量位置编辑器**"，然后选择页面上显示的 "**位置**" 链接。 
    
    在批量搜索编辑器的 "**位置**" 页上显示以下信息。 
    
    ![选择 "启用批量位置编辑器"，然后选择 "位置" 以添加或删除内容位置](../media/a5a468ce-bd63-4c53-bc37-ff64cf769e59.png)
  
    a. **要搜索的邮箱**此部分显示每个选定的内容搜索的列以及搜索中包含的每个邮箱的行。 复选标记表示该邮箱包含在搜索中。 您可以通过在空白行中键入邮箱的电子邮件地址，然后选中要将其添加到的内容搜索的复选框，将邮箱添加到搜索中。 或者，您可以通过清除复选框从搜索中删除邮箱。
    
    b. **要搜索的 SharePoint 网站**此部分为每个所选内容搜索中包含的每个 SharePoint 和 OneDrive 网站显示一行。 复选标记表示该网站包含在搜索中。 您可以通过在空白行中键入网站的 URL，然后选中要将其添加到的内容搜索的复选框，将网站添加到搜索中。 或者，您可以通过清除复选框从搜索中删除网站。
    
    c. **其他搜索选项**此部分指示搜索中是否包含未编制索引的项目和公用文件夹。 若要包含它们，请确保选中 "" 复选框。 若要删除它们，请清除该复选框。
    
2. 在编辑完 "**位置**" 页上的一个或多个分区之后，请选择 "**保存**"。
    
    修订后的内容位置将显示在所选搜索的相应部分中。
    
3. 选择 "**关闭**" 以关闭批量搜索编辑器。 
    
4. 在 "**内容搜索**" 页上，选择您编辑的搜索，然后选择 "**启动**搜索" 以使用修订后的内容位置重新启动搜索。 
    
下面是使用批量搜索编辑器编辑内容位置的一些提示：
  
- 您可以编辑内容搜索以搜索组织中的所有邮箱或网站，方法是在 "**要搜索的邮箱**" 或 "要搜索的**SharePoint 网站**" 部分中键入**所有**邮箱或网站，然后选中该复选框。 
    
- 可以通过从文本文件或 Excel 文件中复制多个行并将它们粘贴到 "**位置**" 页上的节中，将多个内容位置添加到一个或多个搜索中。 在添加新位置之后，请务必选中要向其添加位置的每个搜索的复选框。 
    
    > [!TIP]
    > 若要为组织中的所有用户生成电子邮件地址列表，请在 "[步骤2：生成用户列表](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md#step-2-generate-a-list-of-users)" 中的步骤2中运行 PowerShell 命令。 或者按照[获取组织中所有用户 Onedrive url 的列表](https://docs.microsoft.com/onedrive/list-onedrive-urls)中的步骤生成组织中所有 onedrive for business 网站的列表。 请注意，您必须将组织的 "我的网站" 域的 URL （例如， https://contoso-my.sharepoint.com)添加到由脚本创建的 OneDrive for business 网站）。 在拥有电子邮件地址或 OneDrive for Business 网站的列表后，可以将其复制并粘贴到批量搜索编辑器中的 "**位置**" 页。 
  
- 选择 "**保存**" 以在批量搜索编辑器中保存更改之后，将对添加到搜索中的邮箱的电子邮件地址进行验证。 如果电子邮件地址不存在，则会显示一条错误消息，指出邮箱无法定位。 不验证网站的 Url。 
  

