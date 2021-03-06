---
title: 导出内容搜索报告
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExportReport
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 5c8c1db6-d8ac-4dbb-8a7a-f65d452169b9
description: 您可以导出搜索结果报告，而不是在 Office 365 的安全性 & 合规性中心中导出内容搜索的实际结果。 报告包含搜索结果摘要和文档，其中包含有关要导出的每个项目的详细信息。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: de27e25945f14f6a6119b4c1776eebca5e84d8ce
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358298"
---
# <a name="export-a-content-search-report"></a>导出内容搜索报告

而不是从 Security & 合规性中心中的内容搜索中导出完整的搜索结果集，而不是从与电子数据展示事例相关联的内容搜索 (和) 中导出的搜索结果，则可以导出在导出搜索结果时生成的相同报告。
  
导出报表时，会将其下载到与内容搜索同名的文件夹中，但附加 *_ReportsOnly*。 例如，如果内容搜索名为  *ContosoCase0815*，则会将该报告下载到名为 *ContosoCase0815_ReportsOnly*的文件夹中。 有关报告中包含的文档的列表，请参阅 [报告中包含的内容](#whats-included-in-the-report)。

## <a name="assign-roles-and-check-system-requirements"></a>分配角色并检查系统要求

- 若要导出内容搜索报告，您必须在安全 & 合规性中心中分配合规性搜索管理角色。 默认情况下，此角色分配给内置的电子数据展示管理器和组织管理角色组。 有关详细信息，请参阅[分配电子数据展示权限](assign-ediscovery-permissions.md)。

- 导出报表时，数据将临时存储在 Microsoft 云中的唯一 Azure 存储区域中，然后再将其下载到本地计算机。 确保您的组织可以连接到 Azure 中的终结点，即** \* blob.core.windows.net** (通配符代表导出) 的唯一标识符。 搜索结果数据在创建后两周从 Azure 存储区域中删除。 
    
- 用于导出搜索结果的计算机必须满足以下系统要求：
    
  - 32位或64位版本的 Windows 7 及更高版本
    
  - Microsoft .NET Framework 4.7
    
- 您必须使用下列受支持的浏览器之一运行电子数据展示导出工具<sup>1</sup>：

  - Microsoft Edge <sup>2</sup>

    OR

  - Microsoft Internet Explorer 10 及更高版本

  > [!NOTE]
  > <sup>1</sup> Microsoft 不会为 ClickOnce 应用程序制造第三方扩展或加载项。 使用不受支持的浏览器导出搜索结果，但不支持第三方分机或加载项。<br/>
  > <sup>2</sup> 由于最近对 Microsoft Edge 进行了更改，因此 ClickOnce 支持在默认情况下不再启用。 有关在 Edge 中启用 ClickOnce 支持的说明，请参阅 [在 Microsoft Edge 中使用电子数据展示导出工具](configure-edge-to-export-search-results.md)。

- 如果内容搜索返回的结果的估计总大小超过了 2 TB，则将报告导出失败。 若要成功导出报告，请尝试缩小范围并重新运行搜索，以使结果的估计大小小于 2 TB。

- 导出内容搜索报告会对同时运行的最大导出数和单个用户可以运行的最大导出数进行计数。 有关导出限制的详细信息，请参阅 [导出内容搜索结果](export-search-results.md#export-limits)。

## <a name="generate-and-download-a-content-search-report"></a>生成和下载内容搜索报告

生成和下载内容搜索报告的步骤类似于实际导出搜索结果。
  
## <a name="step-1-generate-the-report-for-export"></a>步骤1：生成要导出的报告

第一步是准备要下载到计算机导出的报告。 在报告中，报告文档将上载到 Microsoft 云中的 Azure 存储区域。
  
1. 转到 [https://protection.office.com](https://protection.office.com)。
    
2. 使用工作或学校帐户进行登录。
    
3. 在安全性 & 合规性中心的左侧窗格中，单击 " **搜索** \> **内容搜索**"。
    
4. 在 " **内容搜索** " 页上，选择 "搜索"。 
    
5. 在详细信息窗格中的 " **将报告导出到计算机**" 下，单击 " **生成报告**"。
    
    > [!NOTE]
    > 如果搜索结果超过 7 天，将提示你更新搜索结果。 如果发生这种情况，请取消导出，在 "详细信息" 窗格中单击 " **更新搜索结果** " 以选择搜索，然后在结果更新后再次启动报告导出。 
  
6. 在 " **导出报告** " 页上的 " **从搜索中包含这些项目**" 下，选择下列选项之一：
    
    - 仅导出索引项
    
    - 导出索引和未编制索引项
    
    - 仅导出未编制索引项
    
    有关未编制索引的项目的详细信息，请参阅 [内容搜索中的部分索引项目](partially-indexed-items-in-content-search.md)。
    
7. 选择包括所有版本的 SharePoint 文档的搜索统计信息。 仅当搜索的内容源包括 SharePoint 或 OneDrive for Business 网站时，才会出现此选项。
    
8. 单击 " **生成报告**"。
    
    搜索结果报告已准备好下载，这意味着将报告文档上载到 Microsoft 云中的 Azure 存储区域。 当报告准备好下载时，将在详细信息窗格中的 "**将报告导出到计算机**" 下显示 "**下载报告**" 链接。 
    
> [!NOTE]
> 您还可以导出与电子数据展示事例相关联的内容搜索的报告。 若要执行此操作，请转到 **电子数据展示** \> **电子数据展示**，选择一个事例，然后单击 " **编辑** ![ 编辑图标" ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) 。 在 " **搜索** " 页上，选择 "搜索"，然后单击 " **导出** ![ 导出搜索结果" 图标 " ](../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png) \> **导出报告**"。 
  
## <a name="step-2-download-the-report"></a>步骤2：下载报告

下一步是将报告从 Azure 存储区域下载到本地计算机。
  
1. 在为其生成报告的搜索的详细信息窗格中，在 " **将报告导出到计算机**" 下，单击 " **下载报告**"。
    
    将显示 " **下载报告** " 页，其中包含有关下载到计算机的报告的以下信息。 
    
    - 将下载的项的数目。
    
    - 将下载的项的预计总大小。
    
    - 是否导出索引或未编制索引。 未编制索引的项目是具有可识别格式、已加密或因其他原因而未编制索引的项目。
    
    - 是否将下载 SharePoint 文档的版本。
    
    - 报告导出过程的状态。 即使报表准备尚未完成，也可以开始下载报告。
    
2. 在“**导出密钥**”下，单击“**复制到剪贴板**”。 您可以在步骤5中使用此项下载报告。
    
    > [!IMPORTANT]
    > 由于任何人都可以安装和启动电子数据展示导出工具，然后使用此密钥下载搜索报告，因此请务必采取预防措施来保护此项，就像保护密码或其他与安全相关的信息一样。 
  
3. 单击 " **下载报告**"。
    
4. 如果系统提示您安装 **电子数据展示导出工具**，请单击 " **安装**"。
    
5. 在“电子数据展示导出工具”**** 中，将你在步骤 2 中复制的导出密钥粘贴在相应的框中。
    
6. 单击 " **浏览** " 以指定要下载报告的位置。 
    
7. 单击****“启动”将搜索结果下载到计算机。 
    
    **电子数据展示工具**显示有关导出过程的状态信息，包括要下载的剩余项的估计数量（和大小）。 导出过程完成后，可以在文件的下载位置访问这些文件。 
    
> [!NOTE]
> 您可以下载与电子数据展示事例相关联的内容搜索的报告。 若要执行此操作，请转到 **电子数据展示** \> **电子数据展示**，选择一个事例，然后单击 " **编辑** ![ 编辑图标" ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) 。 在 " **导出** " 页上，选择报告导出，然后单击 "详细信息" 窗格中的 " **下载报告** "。 
  
## <a name="whats-included-in-the-report"></a>报告中包含的内容

生成和导出有关内容搜索结果的报告时，将下载以下文档：
  
- **导出摘要：** 包含导出摘要的 Excel 文档。 其中包括以下信息：已搜索的内容源的数量、每个内容位置的搜索结果数、估计的项目数、要导出的实际项目数以及要导出的项目的估计大小和实际大小。 
    
    > [!NOTE]
    > 如果在导出报表时包含未编制索引的项目，则在已下载的搜索结果总数中包含未编制索引的项目数，并在 "已下载的搜索结果总数" (如果要导出 "导出摘要报告" 中列出的搜索结果) 。 换言之，要下载的项目总数等于估计结果的总数和未编制索引项目总数的总数。 
  
- **清单：** 以 XML 格式)  (的清单文件，其中包含搜索结果中包含的每个项目的相关信息。 
    
- **结果：** 包含包含每个索引项的相关信息的行的 Excel 文档，这些项将随搜索结果一起导出。 对于电子邮件，结果日志包含有关每封邮件的信息，其中包括： 
    
  - 邮件在源邮箱中的位置（包括邮件位于主邮箱还是存档邮箱）。
    
  - 发送或接收邮件的日期。
    
  - 邮件的主题行。
    
  - 邮件的发件人和收件人。
    
    对于 SharePoint 和 OneDrive for business 网站中的文档，结果日志包含有关每个文档的信息，包括：
    
  - 文档的 URL。
    
  - 文档所在的网站集的 URL 。
    
  - 上次修改文档的日期。
    
  - 文档的名称（位于结果日志中的主题列）。
    
    > [!NOTE]
    > **结果**报告中的行数应等于搜索结果的总数减去 "未**编制索引的项目**" 报告中列出的总项目数。 
  
- 未**编制索引的项目：** 包含搜索结果中包含的任何未编制索引项目的相关信息的 Excel 文档。 如果在生成搜索结果报告时未包含未编制索引的项目，则仍将下载此报告，但会将其保留为空。
