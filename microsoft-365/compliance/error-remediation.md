---
title: 处理调查数据时的错误修正
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
description: 了解如何使用错误修正来更正数据调查中的数据问题 (预览) 可能阻止对内容进行正确处理。
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: c6c62bb1a3191e369d553df5eb451d4656e704d7
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/26/2020
ms.locfileid: "48286028"
---
# <a name="error-remediation-when-processing-data-for-an-investigation"></a>处理调查数据时的错误修正

错误修正使调查人员能够修正数据问题，从而防止数据调查 (预览) 能够正确处理内容。 例如，由于文件被锁定或加密，因此无法处理受密码保护的文件。 使用错误修正，调查人员可以下载具有此类错误的文件，删除密码保护，并上传修正的文件。

使用以下工作流修正在数据调查中出现错误的文件 (预览) 案例。

## <a name="creating-an-error-remediation-session-to-remediate-files-with-processing-errors"></a>创建错误修正会话以纠正带有处理错误的文件

>[!NOTE]
>如果在以下过程中随时关闭错误修正向导，则可以通过在 "**视图**" 下拉菜单中选择 "**错误" remediations**返回到 "**处理**" 选项卡中的 "错误修正" 会话。

1. 在数据调查的 "**处理**" 选项卡上，选择 "**视图**" 下拉菜单中的 "**错误**"。

2. 通过单击 "错误类型" 或 "文件类型" 旁边的单选按钮，选择要修正的错误。  在下面的示例中，我们正在修正受密码保护的文件。

3. 单击 " **+ 新错误修正**"。

    ![单击 "新建错误修正" 按钮](../media/8c2faf1a-834b-44fc-b418-6a18aed8b81a.png)

    错误修正会话开始，从准备阶段开始，其中将包含错误的文件复制到安全 Azure 位置，以便可以下载它们。

    ![为错误修正做准备](../media/390572ec-7012-47c4-a6b6-4cbb5649e8a8.png)

4. 准备完成后，单击 " **下一步：下载文件** " 以继续下载。

    ![下载需要修正的文件](../media/6ac04b09-8e13-414a-9e24-7c75ba586363.png)

5. 若要下载文件，请指定 **下载的目标路径**。 这是您的本地计算机上应下载文件的路径。  默认路径 "%USERPROFILE%\Downloads\errors" 指向已登录用户的 "下载" 文件夹;可以根据需要对此进行更改。

    >[!NOTE]
    >建议使用本地文件路径，而不是远程网络路径，以实现最佳性能。

    > [!NOTE]
    > 如果尚未安装 AzCopy，请转到 [AzCopy](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy) 以安装它。

6. 通过单击 " **复制到剪贴板**" 复制预定义命令。 启动 windows 命令提示符，粘贴命令，然后按 **enter**。  

    将下载这些文件。

    ![有关在命令提示符中下载的文件的信息](../media/f364ab4d-31c5-4375-b69f-650f694a2f69.png)

    > [!NOTE]
    > 如果您在运行此命令时遇到问题，请参阅 [解决 AzCopy In 高级电子数据展示](troubleshooting-azcopy.md)问题。

7. 下载文件后，可以使用适当的工具对它们进行修正。 对于受密码保护的文件，可以使用几种密码破解工具。 如果您知道这些文件的密码，则可以打开它们并删除密码保护。
    
   > [!NOTE]
    > 必须保留已修正文件的目录结构和文件名，这一点非常重要。 通过下载的文件和文件夹的路径名称，可以将修正的文件与原始文件进行关联。  如果更改了目录结构或文件的名称，您将收到以下错误： `Cannot apply Error Remediation to the current Evidenceset` 。

8. 现在，返回到 "数据调查" (预览) 并单击 " **下一步：上传文件**"。  此操作将移至下一步，你现在可以在其中上传文件。

    !["上载文件" 选项卡](../media/af3d8617-1bab-4ecd-8de0-22e53acba240.png)

9. 在 " **文件的位置路径** " 文本框中指定修正的文件的位置，然后单击 " **复制到剪贴板**"。

10. 将命令粘贴到 Windows 命令提示符中，然后按 **enter** 上传文件。

    ![有关在命令提示符中上载的文件的信息](../media/ff2ff691-629f-4065-9b37-5333f937daf6.png)

11. 最后，返回到 "数据调查" (预览) 并单击 " **下一步：处理文件**"。

12. 处理完成时。  您可以返回到工作集并查看修正的文件。

## <a name="what-happens-when-files-are-remediated"></a>修正文件时会发生什么情况

当上载修正的文件时，原始元数据将保留，但以下字段除外： 

- ExtractedTextSize
- HasText
- IsErrorRemediate
- LoadId
- ProcessingErrorMessage
- ProcessingStatus
- 文本
- WordCount
- WorkingsetId

有关数据调查中所有文档元数据字段的定义 (预览) ，请参阅 [document metadata fields](document-metadata-fields.md)。
