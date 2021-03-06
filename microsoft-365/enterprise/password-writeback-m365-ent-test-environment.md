---
title: Microsoft 365 测试环境的密码写回
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/22/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 摘要：配置 Microsoft 365 测试环境的密码写回。
ms.openlocfilehash: b8c89ca7ef967c423b89db4559ef04f715a5f869
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686222"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Microsoft 365 测试环境的密码写回

*此测试实验室指南仅可用于企业测试环境的 Microsoft 365。*

密码写回将允许用户通过 Azure Active Directory (Azure AD) 更新其密码，然后复制到本地 Active Directory 域服务 (AD DS)。通过密码写回，用户不需要通过本地 AD DS（原始用户帐户的存储位置）更新其密码。这非常适用于对本地网络没有远程访问连接的漫游或远程用户。

本文介绍了如何为 Microsoft 365 测试环境配置密码写回。

此设置包含两个阶段：

1.    创建采用密码哈希同步的 Microsoft 365 模拟企业测试环境。
2.    为 TESTLAB AD DS 域启用密码写回。
    
![Microsoft 云测试实验室指南](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> 单击[此处](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf)可查看 Microsoft 365 企业版测试实验室指南集合中所有文章的直观图。
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>阶段 1：为 Microsoft 365 测试环境配置密码哈希同步

首先，按照[密码哈希同步](password-hash-sync-m365-ent-test-environment.md)中的说明操作。下面是生成的配置。
  
![使用密码哈希同步测试环境的模拟企业配置](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
此配置包括： 
  
- Microsoft 365 E5 试用版或付费版订阅。
- 连接到 Internet 的简化的组织 Intranet，包含 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。 
- 在 APP1 上运行的 Azure AD Connect，用于将 TESTLAB AD DS 域同步到 Microsoft 365 订阅的 Azure AD 租户。

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>阶段 2：为 TESTLAB AD DS 域启用密码写回

首先，使用全局管理员角色配置用户 1 帐户。

1. 通过 [Microsoft 365 管理中心](https://portal.microsoft.com)使用全局管理员帐户进行登录。

2. 单击“**活动用户**”。
 
3. 在“**活跃用户**”页面上，单击 **user1** 帐户，

4. 在 **user1** 窗格中，单击“**角色**”旁边的“**编辑**”。

5. 在 user1 的“**编辑用户角色**”窗格上，单击“**全局管理员**”。单击“**保存**”，然后单击“**关闭**”。

接下来，使用允许用户 1 代表 TESTLAB AD DS 域中的其他用户更改密码的安全设置来配置用户 1 帐户。

1. 在 [Azure 门户](https://portal.azure.com)中，使用全局管理员帐户进行登录，然后使用 TESTLAB\User1 帐户连接到 APP1。

2.  在 APP1 的桌面上，单击“**开始**”，键入 **active**，然后单击“**Active Directory 用户和计算机**”。

3. 单击菜单栏中的“**视图**”。如果未启用“**高级功能**”，请单击启用该功能。

4. 在树窗格中，右键单击你的域，再单击“**属性**”，然后单击“**安全**”选项卡。

5. 单击“**高级**”。

6. 在“**权限**”选项卡上，单击“**添加**”。

7. 单击“**选择主体**”，键入 **User1**，然后单击“**确定**”。

8. 在“**适用于**”中，选择“**后代用户对象**”。

9. 在“**权限**”下，选择以下内容：

    - 更改密码
    - 重置密码

10. 在“**属性**”下，选择以下内容：
    - 写入 lockoutTime
    - 写入 pwdLastSet

11. 单击“**确定**”三次，以保存更改。

12. 关闭 **Active Directory 用户和计算机**。

接下来，在 APP1 上对 Azure AD Connect 进行密码写回配置。

1. 如果需要，使用 TESTLAB \ User1 帐户连接到 APP1。

2. 在 APP1 的桌面上，双击“**Azure AD Connect**”。

3. 在“**欢迎页**”上，单击“**配置**”。

4. 在“**其他任务**”页上，选择“**自定义同步选项**”，然后单击“**下一步**”。

5. 在“**连接到 Azure AD**”页面上，键入全局管理员帐户凭据，然后单击“**下一步**”。

6. 在“**连接目录**”和“**域/OU 筛选**”页上，单击“**下一步**”。

7. 在“**可选功能**”页上，选择“**密码写回**”，然后单击“**下一步**”。 

8. 在“**准备配置**”页上，单击“**配置**”并等待该过程完成。

9. 当看到配置完成后，单击“**退出**”。

你现在可以在未连接到模拟 Intranet 的虚拟网络的计算机上测试用户的密码写回。

下面是生成的配置：

![使用传递身份验证测试环境的模拟企业配置](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

此配置包括：

- 使用 DNS 域 TESTLAB 的 Microsoft 365 E5 试用版或付费订阅。\<your domain name> 。
- 连接到 Internet 的简化的组织 Intranet，包含 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。 
- 在 APP1 上运行的 Azure AD Connect，用于将 Azure AD 租户中的帐户和组列表从 Microsoft 365 订阅同步到 TESTLAB AD DS 域。 
- 已启用密码写回，因此用户可以通过 Azure AD 更改其密码，而无需连接到简化的 Intranet。

## <a name="next-step"></a>后续步骤

在测试环境中探索其他[标识](m365-enterprise-test-lab-guides.md#identity)特性和功能。

## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版测试实验室指南](m365-enterprise-test-lab-guides.md)

[Microsoft 365 企业版概述](microsoft-365-overview.md)

[适用于企业的 Microsoft 365 文档](https://docs.microsoft.com/microsoft-365-enterprise/)


