---
title: 可靠性见解
description: ''
keywords: Microsoft 托管桌面, Microsoft 365, 服务, 文档
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 06e1446ca290439c9e6689f4461c825438cf6aaf
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950338"
---
# <a name="reliability-insights"></a>可靠性见解

此视图为你提供托管设备的运行状况摘要。 若要查看可靠性数据，请选择 " **可靠性** " 选项卡。


![可靠性窗格：左上角的设备之间的可靠性、右上角的时间图表的可靠性、顶级问题表在底部。 右下方的帮助和反馈按钮。](../../media/insights_reliability.png)

" **跨设备的可靠性** " 部分通过报告被视为 "正常" 的设备的百分比以及自上次报告失败后观测到的平均时间，在最近14天中提供了部署的快速运行状况摘要。 

 
根据时间，右侧的 **可靠性** 图表将报告发生严重错误的设备数以及观测到的严重错误总数。

" **热门问题** " 部分详细介绍了影响至少5% 托管设备的特定检测到的问题。 报告的详细信息包括：

- 问题的类型
    - 应用程序崩溃，应用程序在其中停止运行或意外停止
    - 应用程序挂起，应用程序在其中停止对输入的响应
    - 严重错误，在 Windows 遇到无法恢复的问题时发生
- 受同一问题影响的设备数量
- 该数字代表的受管理设备的百分比
- 特定问题发生的总次数
- 似乎是问题源的软件组件
- 检测到的问题的类别：
    - 浏览器 (边缘、Chrome、IE) 
    -  (非 Microsoft 组件的未知) 
    - 驱动程序 (音频、图形或其他驱动程序) 
    - 工作效率 (时差、G 套件、Microsoft Office 及其加载项或扩展、团队) 
    - 媒体 (图像、音乐或视频应用程序
    -  (Windows 安全组件的安全性) 
- 当前状态为 Microsoft 托管桌面操作调查和 remediates 问题

