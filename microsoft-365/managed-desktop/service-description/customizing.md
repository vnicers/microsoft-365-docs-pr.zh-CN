---
title: 服务计划的例外情况
description: ''
keywords: Microsoft 托管桌面, Microsoft 365, 服务, 文档
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 0785d7ac12c7b027322338d9949a10ea30168b3b
ms.sourcegitcommit: abf63669daf12993ad3353e4b578f41c8910b20f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "47289057"
---
# <a name="exceptions-to-the-service-plan"></a>服务计划的例外情况

Microsoft 托管桌面提供 curated 设备列表、 [标准设备设置](device-policies.md)、应用程序要求以及某些 [可配置的设置](../working-with-managed-desktop/config-setting-overview.md)，所有这些都旨在为用户提供安全、高效和愉快的体验。 最好始终与提供的服务保持联系。 但是，我们意识到服务的一些详细信息可能无法完全满足您组织的需求。 如果你认为需要以某种方式更改服务，请务必按照以下过程请求这些更改。
 
## <a name="types-of-exceptions"></a>异常类型

异常是对 Microsoft 托管桌面基本配置的任何添加或更改;示例范围从 "USB 端口配置" 到 "部署新设备驱动程序"。 我们按如下方式对各种异常进行分组：

|类型  |说明  |
|---------|---------|
|生产力软件     |  用户所需的前台软件（受[应用程序要求](mmd-app-requirements.md)的限制）       |
|& Vpn 的安全代理     |  用于保护、监视或更改设备或网络的行为的软件       |
|数字体验监控     |  用于跟踪用户设备上的数据以向其报告的软件       |
|硬件或软件驱动程序     |   由[应用程序要求](mmd-app-requirements.md)限制的设备驱动程序      |
|策略     | Windows 10 或 Microsoft 365 在托管设备上的企业版设置的应用程序        |
|设备     | 不在 Microsoft 托管桌面[设备列表](device-list.md)中的设备        |
|其他     |  其他区域未涵盖的任何内容       |
 
## <a name="request-an-exception"></a>请求异常

通过创建更改请求，通过 Microsoft 托管桌面管理门户提交请求。 请务必包含以下详细信息：

-   免除类型：哪种例外类别是什么？  (参阅上一表格) 
-   要求：异常的特定业务要求是什么？
-   建议：您的业务请求的解决方案是什么？
-   时间轴：您希望此例外持续多长时间？ 

## <a name="how-we-assess-an-exception-request"></a>如何评估异常请求

当我们查看异常请求时，我们将按此顺序评估这些因素：
 
1.  Microsoft 托管桌面部署到所有设备的一些应用程序和策略不可转让，因此您的请求不得影响这些应用程序和策略。 有关详细信息，请参阅 [设备配置](device-policies.md) 。
2.  受限制的用户执行其工作所需的软件可能被批准。 
3.  如果我们可以使用 Microsoft 技术满足你的要求，我们可能会根据项目) 的范围，在三到12个月的例外迁移周期内批准请求 (。
4.  如果使用 Microsoft 技术无法满足你的要求，我们可能会批准你的请求，除非违反以下条件之一。  

这些原则确保 Microsoft 托管桌面始终能够满足您的需求，同时跟踪我们的标准模板的偏差。 

## <a name="key-conditions"></a>关键条件

我们将查看异常以确保它们不会违反任何这些条件：

-   例外不一定会对系统安全性产生负面影响。 
-   维护例外不一定会对 Microsoft 托管桌面操作或支持产生重大成本。
-   异常不一定会影响系统稳定性，例如，通过导致内核模式故障或挂起。
-   更改不能限制我们运行服务或与核心 Microsoft 托管桌面技术发生冲突。

这些条件可能会在将来发生变化。 如果我们确实进行了此类更改，我们将在这些条件生效前30天通知。  如果 Microsoft 托管桌面提供了另一种方法来满足批准的例外，Microsoft 托管桌面将通知客户，Microsoft 托管桌面在支持异常方面进行了更改。 

## <a name="revoking-approval-for-an-exception"></a>撤销对异常的审批

在请求的例外得到批准和部署后，我们可能会发现一些问题，这些问题可能会导致在最初批准更改时遇到的关键情况不明显。 在这种情况下，我们可能必须撤销对例外的审批。
 
如果发生这种情况，我们将使用 Microsoft 托管桌面管理门户通知你。 在我们第一次通知你时，在出现例外的设备不再受 Microsoft 托管桌面服务级别协议限制之前，你有90天的时间来删除例外。 我们将根据严格的时间线向你发送几个通知-但是，严重的事件或威胁可能需要我们更改时间线或我们关于异常的决策。 如果没有你的同意，我们将不会 *删除* 异常，但具有已吊销异常的任何设备将不再受我们的服务级别协议的约束。 下面是我们将向你发送通知的时间线：

- **第一次通知：** 我们在决定撤消批准时提供了第一次通知，其中包括有关我们吊销批准的原因的信息、我们建议采取的操作、这些操作的截止时间以及要采取的措施（如果您想要采取此决定）。 在需要从所有设备中删除例外之前，这将提前90天。 
- **第二次通知 (30 天后) ：** 我们提供了另一条通知，包括在第一次通知中提供的相同信息。 
- 第**三个通知在第一个通知) 之后 (60 天：** 我们提供了第三个通知，包括在第一个通知中提供的相同信息。 
- **最终通知 (90 天截止时间之前1周) ：** 我们提供了第四个通知，包括在第一次通知中提供的相同信息。
- **第一次通知之后的90天：** Microsoft 托管桌面服务级别协议不再适用于任何具有已吊销异常的设备。 在任何时候，您都可以挑战决策，并提供其他注意事项信息，包括升级、配置更改或软件更改。 


