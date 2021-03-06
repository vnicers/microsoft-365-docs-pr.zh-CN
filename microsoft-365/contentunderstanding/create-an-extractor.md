---
title: 创建提取程序
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: Priority
description: 了解如何在 Microsoft SharePoint Syntex 中创建提取程序。
ms.openlocfilehash: 260486c128ce76c31fe5f4a0994b4e103687b829
ms.sourcegitcommit: 0f48beaca3afa4df12d41847014975d50a4ebe7d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "48338645"
---
# <a name="create-an-extractor-in-microsoft-sharepoint-syntex"></a>在 Microsoft SharePoint Syntex 中创建提取程序


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL2G]

</br> 

在创建分类器模型以自动识别和分类特定文档类型之前或之后，可选择性地选择将提取程序添加到模型中以从这些文档中提取特定信息。 例如，你可能希望模型不仅可以标识所有添加到文档库中的“*合同续订*”文档，还可将每个文档的“*服务开始日期*”显示为文档库中的列值。

需要为要所提取的文档中的每个实体创建一个提取程序。 在本示例中，从模型识别的每个“ **合同续订**” 文档中，我们要从中提取“ **服务开始日期** ”。 我们希望能够在文档库中看到所有“ **合同续订**” 文档的视图，其中一列显示每个文档的“**服务开始**日期值”。 

> [!NOTE]
> 为创建提取程序，请使用之前所上载的训练分类器的相同文件。 

## <a name="name-your-extractor"></a>命名提取程序

1. 在模型主页的“**创建和培训提取程序**”磁贴中，单击“**培训提取器**”。
2. 在“**新实体提取程序**”屏幕上，在“**新提取程序名称**”字段中键入提取程序的名称。 例如，如果想要从每个”合同续订文档”中提取服务开始日期，请将其命名为“**服务开始日期**”。 也可以选择重复使用以前创建的列（例如，托管元数据列）。
3. 单击“**创建**”。

## <a name="add-a-label"></a>添加标签

下一步是在示例培训文件中标记想要提取的实体。

创建提取程序会打开提程序 页面。 此时，将看到示例文件的列表，并在查看器中显示列表中的第一个文件。

1. 从查看器中，选择要从文件中提取的数据。 例如，如果想要提取“*开始服务日期*”，请突出显示第一个文件中的日期值（*星期一，2019 年 10 月 14 日*）。 然后单击“**保存**”。  在“**标签**”列下，你应该会在“已标记示例”列表中看到从文件显示的值。
2. 选择“**下一个文件**”可自动保存并打开查看器列表中的下一个文件。 或选择“**保存**”，然后从“**已标记的示例**”列表中中选择另一个文件。
3. 在查看器中，重复第 1 步和第 2 步，然后重复执行，直到将标签保存到所有五个文件中。

    ![高级设置](../media/content-understanding/select-service-start-date.png) 

 
标记了五个文件后，将显示一条通知横幅，告知你移动到培训。 你可以选择更多标签，更多文档或前进到培训。 

## <a name="add-an-explanation"></a>添加说明

在我们的示例中，我们将创建一个说明来提供关于实体格式本身的提示以及其在示例文档中可能存在的差异。 例如，日期值可以采用多种不同的格式，例如：
- 10/14/2019
- 2019 年 10 月 14 日
- 星期一，2019 年 10 月 14 日
 

为帮助标识“*服务开始日期*”，可创建模式说明。

1. 在“说明”部分中，选择“**新建**”，然后键入名称（例如，“*日期*”）。
2. 对于“类型”，请选择“**模式列表**”。
3. 对于“数值”，请提供示例文件中显示的日期变体。 例如，如果你的日期格式显示为 0/00/0000，则可在文档中输入显示的任何变体，如：
    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000
4. 选择“**保存**”。

> [!NOTE]
> 有关更多关于说明类型的详细信息，请参阅“[说明类型](https://docs.microsoft.com/microsoft-365/contentunderstanding/explanation-types-overview)”。  


### <a name="use-the-explanation-library"></a>使用“说明库”

若要创建日期等项目的说明，[使用说明库](https://docs.microsoft.com/microsoft-365/contentunderstanding/explanation-types-overview#use-the-explanation-library)比手动输入所有变体来得更加简单。 说明库是一组预建短语和模式说明。 库会尝试为常见短语或模式列表提供所有格式，如日期、电话号码、邮政编码和其他许多格式。 

对于“*服务开始日期*”示例，在说明库中使用“*日期”* 的预建说明会更高效 ：

1. 在“**说明**”部分中，选择“**新建**”，然后选择“**从说明库中**”。
2. 从说明库中，选择“**日期**”。 可查看所识别的日期的所有变体。
3. 选择“**添加**”。</br>

    ![说明库](../media/content-understanding/explanation-library.png) 

4. 在“**创建说明**”页面上，说明库中的“*日期*”信息将自动填充字段。 选择“**保存**”。</br>

    ![日期](../media/content-understanding/date-explanation-library.png) 

## <a name="train-the-model"></a>培训模型 

保存说明开始培训。 如果你的模型具有足够的信息，可以从已标记的示例文件中提取数据，你将看到每个文件都标记了“**匹配**”。  

![匹配](../media/content-understanding/match2.png) 

如果说明没有足够的信息来查找你想要提取的数据，则每个文件都将标记 “**不匹配**”。 可单击“**不匹配**”的文件，查看有关为何不匹配的详细信息。


## <a name="add-another-explanation"></a>添加另一个说明

通常不匹配是指我们提供的说明未提供足够的信息来提取服务开始日期值以匹配标记的文件。 可能需要对其进行编辑，或添加其他说明。

在我们的示例中，请注意，文本字符串“*开始服务日期*”始终在实际值之前。 若要帮助标识“服务开始日期”，需要创建短语说明。

1. 在“说明”部分中，选择“**新建**”，然后键入名称（例如，*前缀字符串*）。
2. 对于“类型”，选择“**短语列表**”。
3. 使用“*服务开始日期*”作为值。
4. 选择“**保存**”。

    ![前缀字符串](../media/content-understanding/prefix-string.png) 

## <a name="train-the-model-again"></a>再次培训模型

保存说明会再次启动培训，这次将在示例中使用两个说明。 如果你的模型拥有足够的信息来提取已标记示例文件中的数据，你将看到每个文件都标记了“**匹配**”。 

如果你在已标记的文件上再次收到“**不匹配**”，则可能需要创建其他说明，以便为模型提供更多用来标识文档类型的信息，或考虑对现有的说明进行更改。

## <a name="test-your-model"></a>测试模型

如果你在标记的示例文件上收到匹配，则现在可以在其余未标记的示例文件中测试模型。 这是一个可选但很有用的步骤，可在使用模型之前评估其的“适用性”和“准备度”，方法是在该模型之前未见过的文件上对其进行测试。

1. 在模型主页中，单击“**测试**”选项卡。 这将在未标记的示例文件上运行模型。
2. 在“**测试文件**”列表中，如果模型能够提取所需的信息，将显示出陈列的示例文件。 使用此信息以帮助确定分类器在文档识别中的有效性。

    ![对文件进行测试](../media/content-understanding/test-filies-extractor.png) 

## <a name="see-also"></a>另请参阅
[创建分类器](create-a-classifier.md)

[说明类型](explanation-types-overview.md)

[创建提取程序时利用术语库分类](leverage-term-store-taxonomy.md)

[文档理解概述](document-understanding-overview.md)

[应用模型](apply-a-model.md) 
