---
title: 规划你的试点 Microsoft 威胁防护项目
description: 使用利益干系人规划试点 Microsoft 威胁防护项目，以管理预期并确保成功的结果。
keywords: Microsoft 威胁防护试点，规划试点 Microsoft 威胁防护项目，评估 Microsoft 威胁防护在生产中，Microsoft 威胁防护试点项目，网络安全，高级持久威胁，企业安全性，设备，设备，标识，用户，数据，应用程序，事件，自动化调查和修正，高级搜寻
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: conceptual
ms.openlocfilehash: 7d1870d1b8972009bed657f476810ca011dc2621
ms.sourcegitcommit: 9d8d071659e662c266b101377e24549963e43fef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2020
ms.locfileid: "48367973"
---
# <a name="planning-your-pilot-microsoft-threat-protection-project"></a>规划你的试点 Microsoft 威胁防护项目 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**适用于：**
- Microsoft 威胁防护
<br>
<table border="0" width="100%" align="center">
  <tr style="text-align:center;">
    <td align="center" style="width:25%; border:0;" bgcolor="#d5f5e3">
      <a href= "https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-plan"> 
        <img src="../../media/mtp/plan.png" alt="Plan your pilot Microsoft Threat Protection project" title="规划你的试点 Microsoft 威胁防护项目" />
      <br/>套餐</a><br>
    </td>
    <td align="center">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/prepare-mtpeval">
        <img src="../../media/mtp/prep.png" alt="Prepare your Microsoft Threat Protection trial lab or pilot environment" title="准备你的 Microsoft 威胁防护试用实验室或试点环境" />
      <br/>准备</a><br>
    </td>
    <td align="center">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate">
        <img src="../../media/mtp/run-sim.png" alt="Run your Microsoft Threat Protection attack simulations" title="运行 Microsoft 威胁防护攻击模拟" />
     <br/>模拟攻击</a><br>
    </td>
    <td align="center">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-close">
        <img src="../../media/mtp/close.png" alt="Close and summarize your Microsoft Threat Protection pilot" title="关闭并汇总你的 Microsoft 威胁防护试点" />
     <br/>结束和汇总</a><br>
    </td>
  </tr>
  <tr>
    <td style="width:25%; border:0;">
   
    </td>
    <td valign="top" style="width:25%; border:0;">
    
</td>
    <td valign="top" style="width:25%; border:0;">

</td>    
    <td valign="top" style="width:25%; border:0;">

</td>
  </tr>
</table>

你当前正在计划阶段。

为确保您的试点项目成功，必须在开始时全面规划和获取利益干系人的批准。 规划的元素包括标识范围、用例、要求和成功条件。

本指南将指导你如何规划你的试点项目。 

>[!IMPORTANT]
>为获得最佳结果，请尽可能仔细地执行试点说明。


## <a name="scope"></a>范围

试验的范围将根据您的环境和可接受的测试方法确定测试的范围。 下面是一些需要考虑的示例范围：
- 包含终结点、服务器和域控制器的开发或测试环境。
- 使用 Microsoft 365、Azure、Active Directory 服务、终结点和服务器的生产环境

>[!NOTE]
>如果你还没有完全许可证，可以获取试用版许可证来 [评估 Microsoft 威胁防护](https://aka.ms/mtp-trial-lab) –规划、准备、设置、配置和运行你的试点项目。 你的利益干系人将在帮助促进从开始到完成的过程中发挥重要作用。

要评估的操作系统的类型还应根据组织的构成进行定义。 这可能包括以下内容： [Mac 终结点](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac#system-requirements)、 [Linux 服务器](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-linux#system-requirements)、 [windows 10 终结点](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions)、 [windows Server 2016](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions)。

## <a name="use-cases"></a>用例

用例表示要测试的工具应由其预期用户使用的声明。 可以从特定角色（如 SOC 分析师）的角度来制定用户情景。 例如：
- 作为 SOC 分析师，我需要在网络中的设备、用户和邮箱之间查看、关联、评估和管理警报和事件。 [事件管理]
- 作为 SOC 分析师，我必须具有工具和过程来自动调查网络中的恶意事件并对其做出响应。 [自动红外线]
- 作为 SOC 分析师，我必须从我的环境中搜索数据，以找出已知的和潜在的威胁以及可疑的活动。 [高级搜寻]

请记住，应在定义的作用域的参数中创建这些用例。 例如，如果测试范围不包括 Microsoft 云应用安全性等工具的评估，则不应创建依赖此数据源的用例。

## <a name="requirements"></a>要求

在用例列表中，您可以开始创建要求。 要求包含工具必须具备的功能才能满足用例。 这些要求可以分解为多个类别，如配置和维护、支持集成以及特定于功能的要求（如搜寻能力和构建自定义警报的能力）。

## <a name="test-plan"></a>测试计划

根据要求的不同，可能适合测试的不同方法。 例如，如果要求是评估自动修正的 efficacy，则测试计划需要包括生成在 Microsoft 威胁防护中将触发自动修正操作的行为 () s 的步骤。 如果要求是检测特定行为或攻击，则测试可能会涉及更多步骤。 这样一点是制定一个适当的计划，以准确地针对您的要求进行测试。

## <a name="success-criteria"></a>成功条件

成功条件最终将设置为针对要测试的内容进行度量的条形图。 无论您是要测试 Microsoft 威胁防护 (还是针对其他工具或其本身的任何其他技术) ，都必须有一些可量化的条件来确定该工具提供的值。 根据范围、要求和测试计划，成功条件将确定如何对测试进行评分。 根据你的需要，此过程应不只是通过或失败，更多的加权计分。 例如，若要成功，工具可能需要在您确定的某些关键区域中得分超过80%。

## <a name="scorecard"></a>记分卡

将计划的所有元素组合在一起的一种方法就是创建记分卡。 请参阅下面的示例记分卡：

|**用例**|**要求**|**配置要求**|**测试计划**|**预期结果**|**测试状态**|**分**|**备注**|
|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|
|事件管理|-Microsoft 威胁防护 </br></br>-Azure ATP </br></br>-Microsoft Defender ATP </br></br>-Microsoft 云应用安全 (可选) |有关详细信息，请参阅准备、设置和配置的[先决条件](https://aka.ms/mtp-trial-lab) |[模拟攻击](mtp-pilot-simulate.md) <br></br>[调查事件](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate#investigate-an-incident) |调查人员可以了解事件的范围和影响并管理事件||||
|AutoIR|-Microsoft 威胁防护 </br></br>-Azure ATP </br></br>-Microsoft Defender ATP |有关详细信息，请参阅准备、设置和配置的[先决条件](https://aka.ms/mtp-trial-lab) <br>启用 AutoIR  |[模拟攻击](mtp-pilot-simulate.md) <br></br>[自动调查](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate.md#automated-investigation-and-remediation) |Microsoft 威胁防护会自动修正警报和事件||||
|高级搜寻|-Microsoft 威胁防护 </br></br>-Microsoft Defender ATP </br></br>-Office 365 ATP   |有关详细信息，请参阅准备、设置和配置的[先决条件](https://aka.ms/mtp-trial-lab)|[高级搜寻方案](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate.md#advanced-hunting-scenario) |调查人员可以通过高级搜索、旋转受影响的实体和创建自定义检测来查找数据||||



## <a name="next-step"></a>后续步骤
|![准备阶段](../../media/mtp/prep.png) <br>[准备阶段](prepare-mtpeval.md) | 准备你的 Microsoft 威胁防护试点环境
|:-------|:-----|
