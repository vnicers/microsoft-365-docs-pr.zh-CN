---
title: 自动调查的详细信息和结果
description: 在自动调查期间和之后，您可以查看结果和主要发现
keywords: 自动化、调查、结果、分析、详细信息、修正、autoair
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.date: 09/16/2020
ms.openlocfilehash: 96fa036d3154b15499303623efe027e4d340c98a
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "48413622"
---
# <a name="details-and-results-of-an-automated-investigation"></a>自动调查的详细信息和结果

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**适用于：**
- Microsoft 威胁防护

在 Microsoft 威胁防护中进行自动调查时，有关该调查的详细信息在自动调查过程的过程中和之后都是可用的。 如果您具有 [所需的权限](mtp-action-center.md#required-permissions-for-action-center-tasks)，则可以在调查详细信息视图中查看这些详细信息。 调查详细信息视图为您提供了最新状态，并能够批准任何挂起的操作。 

![调查详细信息](../../media/mtp-air-investdetails.png)

## <a name="open-the-investigation-details-view"></a>打开调查详细信息视图

您可以使用以下方法之一打开调查详细信息视图：
- [在操作中心中选择一个项目](#select-an-item-in-the-action-center)
- [从 "事件详细信息" 页中选择调查](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>在操作中心中选择一个项目

使用操作中心查看 " **待定** " 选项卡上的 "等待审批" (的操作) 或已在 " **历史记录** " 选项卡) 上已获得批准 (。 

1. 转到 [https://security.microsoft.com](https://security.microsoft.com) 并登录。 

2. 在“导航”窗格中，选择“操作中心”****。 

3. 在 " **挂起** " 或 " **历史记录** " 选项卡上，选择一个项目。 如果您具有 [必要的权限](mtp-action-center.md#required-permissions-for-action-center-tasks)，则可以批准 (或拒绝) 挂起的操作。

### <a name="open-an-investigation-from-an-incident-details-page"></a>从 "事件详细信息" 页打开调查

使用 "事件详细信息" 页查看有关事件的详细信息，包括触发了任何受影响的设备、用户帐户或邮箱的信息的警报。

1. 转到 [https://security.microsoft.com](https://security.microsoft.com) 并登录。 

2. 在导航窗格中，选择 " **事件**"。 

3. 在列表中选择一个项目以打开 "事件详细信息" 视图。<br/>![事件详细信息](../../media/mtp-incidentdetails-tabs.png)

4. 在 " **调查** " 选项卡上，选择列表中的调查。

## <a name="investigation-details"></a>调查详细信息

使用调查详细信息视图查看与调查相关的过去、当前和待定活动。 调查详细信息视图类似于以下图像：

![调查详细信息](../../media/mtp-air-investdetails.png)

在调查详细信息视图中，您可以查看下表中所述的有关 **调查图**、 **警报**、 **设备**、 **标识**、 **关键发现**、 **实体**、 **日志**和 **待定操作** 选项卡的信息。

|Tab    |说明 |
|--------|--------|
|调查图形    |提供调查的直观表示形式。 描述实体并列出发现的威胁以及警报以及是否有任何操作正在等待审批。<br/>您可以单击关系图上的某一项以查看更多详细信息。 例如，单击 " **发现威胁** " 图标将转到 " **关键调查结果** " 选项卡。 |
|警报 |列出与调查相关的警报。 警报可以来自用户计算机上的威胁防护功能、Office 应用程序、云应用安全和其他 Microsoft 365 威胁防护功能。|
|设备|列出调查中包含的计算机以及修正级别。|
|主要发现   |列出调查结果以及所执行或挂起的状态和操作。 您可以在此选项卡上为设备和标识批准挂起的操作。|
|实体   |列出与调查相关联的用户活动、文件、进程、服务、驱动程序、IP 地址和持久性方法，以及所执行的状态和操作。|
|Log    |提供调查过程中执行的所有步骤的详细视图以及状态。|
|挂起的操作    |列出需要审批才能继续的项目。|

## <a name="next-steps"></a>后续步骤

- [批准或拒绝与自动调查和响应相关的操作](mtp-autoir-actions.md)

