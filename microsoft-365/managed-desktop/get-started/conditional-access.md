---
title: 调整条件访问
description: 如何排除某些 Microsoft 帐户
keywords: Microsoft 托管桌面, Microsoft 365, 服务, 文档
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 8844c50f5faba609b3f5f53adc5ab45ba1dbaa74
ms.sourcegitcommit: 126d22d8abd190beb7101f14bd357005e4c729f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2020
ms.locfileid: "46529679"
---
# <a name="adjust-conditional-access"></a>调整条件访问

如果您在组织中使用[条件访问](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)策略，则必须将其设置为排除某些帐户，以便 Microsoft 托管桌面能够正常工作。

为此，请按照下列步骤操作：

1. 请参阅 how [to： Plan a 条件 Access deployment in The Azure Active Directory 中](https://docs.microsoft.com/azure/active-directory/conditional-access/plan-conditional-access#rollback-steps)的 "回滚步骤" 一节。
2. 按照中的步骤操作，以排除所有策略的*新式 Workplace Service 帐户*组。


如果您在条件访问方面遇到困难，请与管理员[支持](../working-with-managed-desktop/admin-support.md)联系。

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft 托管桌面入门步骤

1. [在管理门户中添加和验证管理员联系人](add-admin-contacts.md)
2. 调整条件访问（本主题）
3. [分配许可证](assign-licenses.md)
4. [部署 Intune 公司门户](company-portal.md)
5. [启用企业状态漫游](enterprise-state-roaming.md)
6. [设置设备](set-up-devices.md)
7. [让用户做好使用设备的准备](get-started-devices.md)
8. [部署应用](deploy-apps.md)
