---
title: 评估 Microsoft 威胁防护
description: 设置你的 Microsoft 威胁防护试用实验室环境，以试用旨在保护设备、标识、数据和应用程序的联合威胁防护解决方案如何帮助贵组织
keywords: Microsoft 威胁防护试用版，试用 Microsoft 威胁防护，评估 Microsoft 威胁防护，Microsoft 威胁防护评估实验室，网络安全，高级持久威胁，企业安全性，设备，设备，标识，用户，数据，应用程序，事件，自动化调查和修正，高级搜寻
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
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: f6ee8147965a29b87d84690535116f096e4c6006
ms.sourcegitcommit: 5476c2578400894640ae74bfe8e93c3319f685bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "44049635"
---
# <a name="create-a-microsoft-threat-protection-trial-lab-environment"></a>创建 Microsoft 威胁防护试用实验室环境 

**适用于：**
- Microsoft 威胁防护

创建此试用版环境的目的是演示 Microsoft 威胁防护在您的组织中可使用的检测、预防、调查和响应的全面、集成和智能功能。 

本指南将指导你完成基于建议的部署路径启动 Microsoft 威胁防护评估的步骤。 目标是帮助您在实验室环境中设置集成 Microsoft 威胁保护服务，或在向组织中的安全解决方案决策制定者提供时作为概念证明（POC）。 当您完成攻击模拟、自动调查和响应并对结果感到满意时，您可以在您的组织中 Microsoft 技术销售专业人员或专家的帮助下，将其部署到生产环境中。 

本指南将帮助您：
- 设置实验室服务器和计算机
- 使用用户和组配置 Active Directory
- 设置和配置 Azure ATP、Office ATP、Microsoft Defender ATP 和 Microsoft 云应用安全性
- 为您的服务器和计算机设置本地策略
- 模拟威胁攻击以在 Microsoft 威胁防护中生成测试事件或警报

>[!IMPORTANT]
>为获得最佳结果，请尽可能严格地遵循实验室设置说明。


## <a name="deployment-phases"></a>部署阶段

创建 Microsoft 威胁防护试用实验室环境并部署它时有三个阶段：

|阶段 | 说明 | 
|:-------|:-----|
| ![第1阶段：准备](../../media/prepare.png)<br>[第1阶段：准备](prepare-mtpeval.md)| 了解在试用实验室环境中部署 Microsoft 威胁防护时需要考虑的事项： <br><br>-利益干系人和签署 <br> -环境注意事项 <br>-Access <br>-Azure Active Directory 安装程序 <br> -配置顺序
|  ![阶段2：安装程序](../../media/setup.png) <br>[阶段2：安装程序](setup-mtpeval.md)|  执行访问 Microsoft 365 安全中心的初始步骤，以设置 Microsoft 威胁防护试用实验室环境。 系统将指导您执行以下操作：<br><br>-注册 Microsoft 365 E5 试用版 <br>  -配置域<br>-分配 Microsoft 365 E5 许可证<br>-完成门户中的安装向导|
|  ![第3阶段： Configure & 板载](../../media/config-onboard.png) <br>[第3阶段： Configure & 板载](config-mtpeval.md) | 配置每个 Microsoft 威胁防护支柱和板载终结点。 系统将指导您执行以下操作：<br><br>-配置 Office 365 高级威胁防护<br>-配置 Microsoft 云应用安全<br>-配置 Azure 高级威胁防护<br>-配置 Microsoft Defender 高级威胁防护 


## <a name="in-scope"></a>在范围内

本试用版实验室环境指南的范围如下：
-   设置 Azure Active Directory
-   设置 Microsoft 威胁防护
    -   注册 Microsoft 365 E5 试用版
    -   配置域
    -   分配 Microsoft 365 E5 许可证
    -   完成门户中的设置向导
-   根据最佳实践配置所有 Microsoft 威胁防护支柱
    -   Office 365 高级威胁防护
    -   Azure 高级威胁防护
    -   Microsoft 云应用安全
    -   Microsoft Defender 高级威胁防护

## <a name="out-of-scope"></a>超出范围

以下内容超出了本部署指南的范围：

-   可能与 Microsoft Defender ATP 集成的第三方解决方案的配置
-   生产环境中的渗透测试

## <a name="next-step"></a>后续步骤
|||
|:-------|:-----|
|![第1阶段：准备](../../media/prepare.png) <br>[第1阶段：准备](prepare-mtpeval.md) | 准备 Microsoft 威胁防护评估实验室环境