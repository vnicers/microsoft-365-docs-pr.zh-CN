---
title: 将非 Microsoft 365 数据加载到评审集中
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 了解如何将非 Microsoft 365 数据导入到评审集，以便在高级电子数据展示事例中进行分析。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ad70207bdc015107a5aba074e2df06a42c0618b3
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285858"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>将非 Microsoft 365 数据加载到评审集中

并非所有需要在高级电子数据展示中进行分析的文档都位于 Microsoft 365 中。 使用高级电子数据展示中的非 Microsoft 365 数据导入功能，可以将不在 Microsoft 365 中的文档上传到审阅集。 本文介绍如何将非 Microsoft 365 文档转换为高级电子数据展示以进行分析。

## <a name="requirements-to-upload-non-office-365-content"></a>上载非 Office 365 内容的要求

使用本文中介绍的 "上传非 Microsoft 365" 功能，您需要具备以下条件：

- 要将非 Microsoft 365 内容与之关联的所有保管人都必须分配有相应的许可证。 有关详细信息，请参阅 [高级电子数据展示入门](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses)。

- 现有的高级电子数据展示事例。

- 必须向保管人添加保管人，然后才能将非 Microsoft 365 数据上载并关联到该事例。

- 非 Microsoft 365 数据必须是高级电子数据展示支持的文件类型。 有关详细信息，请参阅 [高级电子数据展示中支持的文件类型](supported-filetypes-ediscovery20.md)。

- 上载到审阅集的所有文件都必须位于文件夹中，其中每个文件夹都与特定的保管人相关联。 这些文件夹的名称必须使用以下命名格式： *alias@domainname*。 Alias@domainname 必须是用户的 Microsoft 365 别名和域。 您可以收集根文件夹中的所有 alias@domainname 文件夹。 根文件夹仅可包含 alias@domainname 文件夹中。 不支持根文件夹中的松散文件。

   您要上载的非 Microsoft 365 数据的文件夹结构与以下示例类似：

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   其中，abraham.mcmahon@contoso.com、jewell.gordon@contoso.com 和 staci.gonzalez@contoso.com 是在这种情况下的保管人的 SMTP 地址。

   ![非 Microsoft 365 数据上载文件夹结构](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- 分配给电子数据展示管理器角色组 (并作为电子数据展示管理员) 添加的帐户。

- 在具有对非 Microsoft 365 内容文件夹结构的访问权限的计算机上安装了 AzCopy （v 8.1）工具。 若要安装 AzCopy，请参阅 [在 Windows 上使用 AzCopy 中的传输数据](https://docs.microsoft.com/previous-versions/azure/storage/storage-use-azcopy)。 请务必将 AzCopy 安装在默认位置，即 **% ProgramFiles (x86) % \ Microsoft SDKs\Azure\AzCopy**。 必须使用 AzCopy 中的 "8.1"。 其他版本的 AzCopy 在高级电子数据展示中加载非 Microsoft 365 数据时可能不起作用。


## <a name="upload-non-microsoft-365-content-into-advanced-ediscovery"></a>将非 Microsoft 365 内容上传到高级电子数据展示

1. 作为电子数据展示管理器或电子数据展示管理员，打开高级电子数据展示，并转到将把非 Microsoft 365 数据上载到的情况。  

2. 单击 " **查看集**"，然后选择要将非 Microsoft 365 数据上传到的审阅集。  如果你没有评审集，可以创建一个。 
 
3. 在审阅集中，单击 "**管理审阅集**"，然后单击**非 Microsoft 365 数据**磁贴上的 "**查看上载**"。

4. 单击 " **上载文件** " 以启动数据导入向导。

   ![上传文件](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   向导中的第一步是准备 Microsoft 提供的安全的 Azure 存储位置，以将文件上传到。  准备完成后，" **下一步：上传文件** " 按钮将变为活动状态。

   ![非 Microsoft 365 导入：准备](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. 单击 " **下一步：上传文件**"。

6. 在 " **上载文件** " 页上，执行以下操作：

   ![非 Microsoft 365 导入：上传文件](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. 在 " **文件的位置路径** " 框中，验证或键入您要上载的非 Microsoft 365 数据所在的根文件夹的位置。 例如，对于 " **开始之前" 部分**中显示的示例文件的位置，应键入 **%USERPROFILE\Downloads\nonO365**。 提供正确的位置可确保正确更新路径中 "AzCopy" 命令中显示的框。

   b. 单击 " **复制到剪贴板** " 以复制框中显示的命令。

7. 启动 Windows 命令提示符，粘贴您在上一步中复制的命令，然后按 **enter** 以启动 AzCopy 命令。  启动该命令后，不会将非 Microsoft 365 文件上传到在步骤4中准备的 Azure 存储位置。

   ![非 Microsoft 365 导入： AzCopy](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > 如前所述，必须使用 AzCopy 中的 " **上载文件** " 页上提供的命令，才能成功使用。 如果提供的 AzCopy 命令失败，请参阅 [高级电子数据展示中的疑难解答 AzCopy](troubleshooting-azcopy.md)。

8. 返回到安全 & 合规性中心，然后单击 " **下一步：处理** 向导中的文件"。  这将启动对上载到 Azure 存储位置的非 Microsoft 365 文件的处理、文本提取和索引。  

9. 通过查看名为 "**将非 Microsoft 365 数据添加到审阅集**" 的作业来跟踪处理 "**进程文件**" 页或 "**作业**" 选项卡上的文件的进度。  作业完成后，新文件将在审阅集中可用。

   ![非 Microsoft 365 导入：处理文件](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. 处理完成后，可以关闭向导。
