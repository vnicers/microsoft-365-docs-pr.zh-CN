---
title: Microsoft 365 中的高级电子数据展示解决方案概述
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
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: 本文概述了 Microsoft 365 中的高级电子数据展示，这是用于内部和外部调查的工具。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d8a43d8a7f0b1803b374839d8ed0d7d82c6adace
ms.sourcegitcommit: cd17328baa58448214487e3e68c37590ab9fd08d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "48399051"
---
# <a name="overview-of-the-advanced-ediscovery-solution-in-microsoft-365"></a>Microsoft 365 中的高级电子数据展示解决方案概述

Microsoft 365 中的高级电子数据展示解决方案构建在 Office 365 中现有的电子数据展示和分析功能之上。 这一新的解决方案称为 *高级电子数据展示*，它提供了一个端到端工作流，用于保留、收集、查看、分析和导出对组织的内部和外部调查做出响应的内容。 它还允许法律团队管理整个法律封存通知工作流，以便与案例中所涉及的保管人进行通信。 

> [!NOTE]
> 高级电子数据展示需要 Office 365 或 Microsoft 365 E5 企业版订阅。 有关高级电子数据展示许可的详细信息，请参阅 [适用于安全 & 合规性的 Microsoft 365 许可指南](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-ediscovery)。

## <a name="alignment-with-edrm"></a>与 EDRM 的对齐方式

高级电子数据展示的内置工作流与电子发现参考模型 (EDRM) 概述的电子数据展示过程相一致。 

![ (EDRM) 的电子发现参考模型](../media/EDRMv1.png)

 (图像来源 edrm.net。 源映像在 "创造性 Commons 归属 3.0 Unported License" 下可用。 ) 

在较高的层次上，以下是高级电子数据展示支持 EDRM 工作流的方式：

- **Id.** 在调查中找出潜在的感兴趣的人员之后，您可以将他们添加为保管人 (也称为 *数据保管人*，因为它们可能会拥有与调查) 相关的信息，以向高级电子数据展示事例。 将用户添加为保管人后，可以轻松地保留、收集和查看保管人文档。

- **保持.** 为了保留和保护与调查相关的数据，高级电子数据展示使您能够对与保管人相关联的数据源施加合法保留。 您还可以将非 custodial 数据置于保留状态。 高级电子数据展示还具有内置通信工作流，以便您可以向保管人发送法律保留通知并跟踪其确认。

- **组.** 确定 (并保留) 与调查相关的数据源后，您可以使用内置搜索工具在高级电子数据源中搜索，并从 custodial 数据源中收集实时数据 (和非 custodial 数据源（如果适用的) 可能与事例相关）。

- **处理.** 收集了与该事例相关的所有数据后，下一步是处理它以供进一步查看和分析。 在高级电子数据展示中，在集合阶段中标识的就地数据被复制到名为 " *审阅集*) " 的 Azure 存储位置 (，它为您提供事例数据的静态视图。 
 
- **概述.** 将数据添加到审阅集后，您可以查看特定文档并运行其他查询，以将数据缩减为与事例最相关的内容。 此外，还可以为特定文档添加批注和标记。
 
- **结果.** 高级电子数据展示提供集成分析工具，可帮助您从确定的审查集中进一步挑选数据，从而不与调查相关。 除了减少相关数据量之外，高级电子数据展示还可以通过让您组织内容以使审查过程更加轻松和高效，从而帮助您节省法律考评成本。

- **生产** 和 **演示。** 准备就绪后，您可以从审阅集导出文档以进行法律审查。 您可以按其本机格式或 EDRM 格式导出文档，以便可以将其导入第三方审阅应用程序中。

## <a name="advanced-ediscovery-workflow"></a>高级电子数据展示工作流

以下各节介绍高级电子数据展示中的内置工作流中的每个步骤。 以下屏幕截图显示了名为 "*产品责任 2019002*" 的事例的 "**主页**" 选项卡。 注释将对页面顶部的工作流选项卡进行排序，使其与 EDRM 进程一致。 

有关高级电子数据展示中的端到端工作流的详细信息，请参阅此 [Microsoft 机械视频](https://go.microsoft.com/fwlink/?linkid=2066133)。

![高级电子数据展示中的选项卡遵循 EDRM 工作流](../media/aedisco-homepage-1.png)

## <a name="managing-custodians-and-non-custodial-data-sources"></a>管理保管人和非 custodial 数据源

使用 " **源** " 选项卡可以在案例中添加和管理已标识为 "感兴趣" 的人员，以及可能不与保管人关联的其他数据源。 在添加保管人或非 custodial 数据源时，可以快速执行操作，例如，在保管人和非 custodial 数据源上放置合法保留、与保管人进行通信以及搜索保管人和非 custodial 数据源，以收集与事例相关的内容。 在这种情况下，可以轻松地添加新的保管人或非 custodial 的日期源，也可以从案例中释放它们。 有关详细信息，请参阅 [高级电子数据展示中的与保管人合作](managing-custodians.md)。

## <a name="managing-legal-hold-notifications"></a>管理法律保留通知

在这种情况下，使用 " **通信** " 选项卡来管理与保管人进行通信的过程。 合法保留通知指示保管人保留与该事例相关的任何内容。 法律团队必须能够跟踪由保管人接收、阅读和确认的通知。 高级电子数据展示中的通信工作流使你能够在保管人无法确认保留通知的情况下创建和发送初始通知、提醒、发布通知和升级。 有关详细信息，请参阅 [在高级电子数据展示中使用通信](managing-custodian-communications.md)。

## <a name="managing-content-preservation"></a>管理内容保留

向事例添加保管人时，可以对 custodial 数据进行保留。 使用 **保留** 选项卡可管理在添加保管人时创建的保留，并管理与此案例相关的其他法律封存;例如，您可以识别并在非 custodial 数据源上放置保留。 您还可以编辑该案例中的任何保留，并将其设置为基于查询的保留，以便仅保留与查询匹配的内容。 例如，可以将日期范围添加到保留，以便保留在特定日期范围内创建的内容。 您还可以获取处于保留状态的内容的统计信息，删除不再与案例相关的保留，或将其删除。 有关详细信息，请参阅 [在高级电子数据展示中管理保留](managing-holds.md)。

## <a name="indexing-custodian-data"></a>索引保管人数据

将保管人和相应的 custodial 数据源添加到某个情况时，来自保管人数据源的任何部分索引项都会由名为 " *高级索引*" 的进程重新编制索引。 这样，在运行搜索以收集数据时，可以完全搜索 custodial 内容（如图像、不受支持的文件类型和其他可能未编制索引的内容）。 使用 " **处理** " 选项卡监视高级索引的状态，并使用称为 " *错误修正*" 的过程修复处理错误。 有关详细信息，请参阅 [修复高级电子数据展示中的处理错误](processing-data-for-case.md)。

## <a name="collecting-case-data"></a>收集事例数据

使用 " **搜索** " 选项卡创建搜索，以搜索与案例相关的内容就地 custodial 和非 custodial 数据源。 您可以使用关键字和条件) 创建和运行基于查询的搜索 (，以标识一组与案例相关的电子邮件和文档，以及您希望在电子数据展示工作流中的后续步骤中进行进一步审阅和分析。 您可以创建一个或多个与事例关联的搜索。 您还可以使用搜索工具预览示例文档并查看搜索统计信息，以帮助您优化和改进搜索结果。 在您认为搜索结果包含与案例相关的所有数据后，将搜索结果添加到审阅集，以供进一步审阅、分析和剔除。 有关详细信息，请参阅 [在高级电子数据展示中收集数据的大小写](collecting-data-for-ediscovery.md)。

## <a name="reviewing-and-analyzing-case-data"></a>查看和分析事例数据

使用 " **查看设置** " 选项卡可查看和分析从 live 系统中收集的内容并将其添加到审阅集。 *审阅集*是该 (数据的静态集合，custodial 数据的脱机副本 (以及在您在电子数据展示工作流的前一阶段收集的、非 custodial 数据) （如果适用）的数据) 。 将搜索结果添加到审阅集时，将触发一个过程，该过程会从容器中提取文件、提取元数据并提取文本。 完成此过程后，系统将为从保管人中收集的所有数据生成新索引，并将其添加到审阅集。 将数据添加到评审集后，可以运行更多查询来缩小事例数据、以文本形式或以本机文件格式查看数据，以及在审阅集中对文档添加批注、标记密文和标记文档。 您还可以执行高级分析，例如确定文档复制、电子邮件线程和主题。 将数据 culled 到与事例相关的内容后，可以直接下载文档，也可以将它们连同文件元数据、批注和任何标记一起导出。 有关更多信息，请参阅：

- [查看审阅集中的文档](view-documents-in-review-set.md)

- [查询审阅集中的数据](review-set-search.md)

- [标记审阅集中的文档](tagging-documents.md)

- [分析评审集中的数据](analyzing-data-in-review-set.md)

## <a name="exporting-data-for-review-and-presentation"></a>导出数据以供审阅和演示

从审阅集中导出数据之后，使用 " **导出** " 选项卡管理导出作业并从审阅集下载数据。 导出审阅集时，会将数据上载到 Microsoft 提供的 Azure 存储位置 (或由组织) 管理的 Azure 存储位置。 将其上载到 Azure 后，即可将其下载到本地计算机。 您可以获取下载 " **导出** " 选项卡上的导出数据所需的存储评估密钥。有关详细信息，请参阅 [在高级电子数据展示中导出事例数据](exporting-data-ediscover20.md)。

## <a name="managing-jobs"></a>管理作业

使用 " **作业** " 选项卡监视已启动的、与案例相关的任务的进程长时间运行。 作业的示例包括与索引编制、搜索和导出事例数据相关的作业。 例如，如果在包含许多数据源的 " **搜索** " 选项卡上创建搜索，则此搜索过程的状态将显示在 " **作业** " 选项卡上。有关详细信息，请参阅 [在高级电子数据展示中管理作业](managing-jobs-ediscovery20.md)。

## <a name="configuring-case-settings"></a>配置事例设置

使用 " **设置** " 选项卡配置大小写设置。 这包括向事例添加成员、关闭或删除事例以及配置搜索和分析设置。
