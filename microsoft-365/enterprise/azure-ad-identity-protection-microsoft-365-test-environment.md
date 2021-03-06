---
title: 适用于 Microsoft 365 企业版测试环境的 Azure AD 标识保护
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: 配置 Azure AD 标识保护并分析 Microsoft 365 for 企业测试环境中的当前帐户。
ms.openlocfilehash: bd1e7560e978b13d24e9e93a99a2567adca95c75
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46694986"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>适用于 Microsoft 365 企业版测试环境的 Azure AD 标识保护

*此测试实验室指南仅可用于企业测试环境的 Microsoft 365。*

Azure Active Directory (Azure AD) 标识保护允许您检测影响组织标识、配置自动响应和调查事件的潜在漏洞。 本文介绍如何使用 Azure AD Identity Protection 查看测试环境帐户的分析。

在 Microsoft 365 企业版测试环境中设置 Azure AD 标识保护有两个阶段：

1. 创建适用于企业级测试环境的 Microsoft 365。
2. 使用 Azure AD Identity Protection。

![Microsoft 云测试实验室指南](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> 单击[此处](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf)可查看 Microsoft 365 企业版测试实验室指南集合中所有文章的直观图。
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>第1阶段：构建您的 Microsoft 365 企业版测试环境

如果只想使用最低要求以轻型方式测试 Azure AD 标识保护，请按照 [轻型基本配置](lightweight-base-configuration-microsoft-365-enterprise.md)中的说明进行操作。
  
如果要在模拟的企业中测试 Azure AD 标识保护，请按照 [传递身份验证](pass-through-auth-m365-ent-test-environment.md)中的说明进行操作。
  
> [!NOTE]
> 测试 Azure AD Identity Protection 不需要模拟企业测试环境，其中包括连接到 Internet 的模拟 intranet 和 Active Directory 域服务 (AD DS) 林的目录同步。 此处提供它作为选项，以便您可以在代表典型组织的环境中测试 Azure AD 标识保护并对其进行实验。 
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>第2阶段：使用 Azure AD Identity Protection

1. 打开浏览器的私有实例，并 [https://portal.azure.com](https://portal.azure.com) 使用 Microsoft 365 for 企业版测试环境的全局管理员帐户登录 Azure 门户。
2. 在 Azure 门户中，在搜索框中键入 **标识保护** ，然后单击 " **Azure AD identity protection**"。
3. 在 " **身份保护-概述** " 刀片中，单击每个报告以查看报告的内容。
4. 在 " **通知**" 下，单击 "用户"， **查看风险检测警报**。
5. 在 " **检测到风险的用户警报** " 窗格中，选择 " **中**"。
6. 对于 **向以下用户发送电子邮件**，请单击 " **包含** "，并验证全局管理员帐户是否在所选成员列表中。
7. 单击“保存”****。

依次单击 " **保护** " 下的不同策略以查看如何配置它们。 如果您创建并激活策略，请确保它没有阻止对条件范围过宽的访问，或者您可能无法登录，即使是全局管理员也是如此。

有关进一步的测试和实验，请参阅 [模拟风险事件](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection-playbook)。

## <a name="next-step"></a>后续步骤

在测试环境中探索其他[标识](m365-enterprise-test-lab-guides.md#identity)特性和功能。

## <a name="see-also"></a>另请参阅

[标识路线图](identity-roadmap-microsoft-365.md)

[Microsoft 365 企业版测试实验室指南](m365-enterprise-test-lab-guides.md)

[Microsoft 365 企业版概述](microsoft-365-overview.md)

[适用于企业的 Microsoft 365 文档](https://docs.microsoft.com/microsoft-365-enterprise/)
