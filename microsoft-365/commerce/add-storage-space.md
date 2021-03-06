---
title: 为你的订阅添加存储空间
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- commerce
- Adm_TOC
- SPO_Content
ms.custom:
- MAX_CampaignID
- okr_SMB
- AdminSurgePortfolio
search.appverid:
- MET150
description: 了解如何在 Microsoft 365 订阅中添加和减少文件存储。 使用额外的文件存储，可以在 SharePoint Online 和 OneDrive 中存储更多内容。
ms.date: ''
ms.openlocfilehash: 7f9973054bfe97beae36e28b73a3eb2025a13e73
ms.sourcegitcommit: 25afc0c34edc7f8a5eb389d8c701175256c58ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/01/2020
ms.locfileid: "47324464"
---
# <a name="add-storage-space-for-your-subscription"></a>为你的订阅添加存储空间

::: moniker range="o365-21vianet"

> [!NOTE]
> 管理中心正在发生改变。 如果你的体验与此处提供的详细信息不匹配，请参阅[有关新版 Microsoft 365 管理中心](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet)。

::: moniker-end

如果你的 SharePoint Online 网站集存储空间即将用完，并且你的计划符合条件，则可以为你的订阅增加存储空间。 如果在可用加载项列表中看不到 **Office 365 额外文件存储空间** ，说明您的计划不符合条件。 有关详细信息，请参阅 ["我的计划是否符合条件？"](#is-my-plan-eligible-for-office-365-extra-file-storage)

> [!NOTE]
> 如果你通过批量许可或 CSP 购买了订阅，则不能直接从 Microsoft 为你的组织购买 **Office 365 额外文件存储** 。 请联系你的代表或合作伙伴寻求帮助。

## <a name="before-you-begin"></a>准备工作

若要执行本文中的任务，您必须是全局管理员或 SharePoint 管理员。 有关详细信息，请参阅[关于管理员角色](../admin/add-users/about-admin-roles.md)。

## <a name="view-available-storage"></a>查看可用存储

::: moniker range="o365-worldwide"

1. 在 SharePoint 管理中心中，转到 " <a href="https://admin.microsoft.com/sharepoint?page=siteManagement&modern=true" target="_blank">活动网站</a> " 页，并使用对组织具有 [管理员权限](https://docs.microsoft.com/sharepoint/sharepoint-admin-role) 的帐户进行登录。

2. 在页面的右上方，查看所有站点使用的存储量以及订阅的总存储空间。 如果你的组织已在 Office 365 中配置了多地理位置，则此栏还会显示在所有地理位置上使用的存储量。

   !["活动网站" 页面上的存储栏](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > 使用的存储不包括在过去的24-48 小时内所做的更改。

::: moniker-end

::: moniker range="o365-germany"

1. 以 https://portal.office.de 全局或 SharePoint 管理员的身份登录，然后选择 "管理员" 磁贴打开管理中心。 如果您看到一条消息，表明您没有访问该页面的权限，则表示您的组织中没有 Microsoft 365 管理员权限。

2. 在左窗格中的 " **管理中心**" 下，选择 " **SharePoint**"。 如果看到经典 SharePoint 管理中心，请选择页面顶部的“**立即打开**”，打开新的 SharePoint 管理中心。

3. 在新的 SharePoint 管理中心的左侧窗格中，选择“**活动网站数**”。

4. 在页面的右上方，查看所有站点使用的存储量以及订阅的总存储空间。

   !["活动网站" 页面上的存储栏](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > 使用的存储不包括在过去的24-48 小时内所做的更改。

::: moniker-end

::: moniker range="o365-21vianet"

1. 以 https://login.partner.microsoftonline.cn/ 全局或 SharePoint 管理员的身份登录，然后选择 "管理员" 磁贴打开管理中心。  (如果您看到一条消息，表明您没有访问该页面的权限，则表示您的组织中没有 Microsoft 365 管理员权限。

2. 在左窗格中的 " **管理中心**" 下，选择 " **SharePoint**"。 如果看到经典 SharePoint 管理中心，请选择页面顶部的“**立即打开**”，打开新的 SharePoint 管理中心。

3. 在新的 SharePoint 管理中心的左侧窗格中，选择“**活动网站数**”。

4. 在页面的右上方，查看所有站点使用的存储量以及订阅的总存储空间。  

   !["活动网站" 页面上的存储栏](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > 使用的存储不包括在过去的24-48 小时内所做的更改。

::: moniker-end

在确定要使用的存储空间后，可以为订阅添加或删除存储空间。 若要了解添加存储空间需要多少成本，请按照本文中的步骤操作，并在购买之前查看定价信息。
  
有关设置网站集存储限制的信息，请参阅 [管理网站集存储限制](https://docs.microsoft.com/sharepoint/manage-site-collection-storage-limits)。
  
## <a name="add-storage-to-your-subscription"></a>向订阅添加存储空间

如果还没有为订阅购买额外的存储空间，可以执行此操作。

::: moniker range="o365-worldwide"

1. 在 "管理中心" 中，转到 " **付费** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">购买服务</a> " 页。
2. 在 " **购买服务** " 页的底部，选择 " **加载项**"。
3. 选择 " **Office 365 额外文件存储**"。
4. 在 " **Office 365 额外文件存储** " 页上，如果显示，请选择基本订阅，然后输入要添加的存储的 gb 数。
5. 选择 " **立即签出**"。
6. 在 " **此外观如何？** " 页上，验证所选存储的 gb 数，查看定价信息，然后选择 " **下一步**"。
7. 在 " **完成订单** " 页上，验证总数。 如果需要进行任何更改，请选择 " **编辑订单**"。 如果订单要求进行信用检查，请选中 "" 复选框。 完成后，请选择 " **下订单**" \> **转到 "管理员主页**"。

::: moniker-end

::: moniker range="o365-germany"

1. 在管理中心中，转到 "**记帐** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">订阅</a>" 页。  

2. 在 " **订阅** " 页上，选择要向其添加存储空间的订阅，然后选择 " **加载项**"。

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > 如果你未看到 **加载项**，并且你的订阅是通过合作伙伴购买的，请选择 " **批量许可服务中心 (VLSC") **。
  
3. 选择 " **购买加载项**"。

    ![在管理中心的 "订阅" 页上购买加载项链接。](../media/f5cbc3fa-90f7-4299-976d-2482f2c69755.png)
  
4. 在 " **购买服务** " 页上，鼠标移过或点击 " **Office 365 额外文件存储**"，然后选择 " **立即购买**"。
  
5. 输入所需的用户许可证数，如果显示，请选择基本订阅。 选择 " **立即签出**"。
  
6. 在 " **此外观如何？** " 页上，验证所选存储的 gb 数，查看定价信息，然后选择 " **下一步**"。

7. 在 " **完成订单** " 页上，选择 " **下订单**"。

::: moniker-end

::: moniker range="o365-21vianet"

1. 在管理中心，转到“**计费**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">订阅</a>”页面。

2. 在 " **订阅** " 页上，选择要向其添加存储空间的订阅，然后选择 " **加载项**"。

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > 如果你未看到 **加载项**，并且你的订阅是通过合作伙伴购买的，请选择 " **批量许可服务中心 (VLSC") **。
  
3. 选择 " **购买加载项**"。

    ![在管理中心的 "订阅" 页上购买加载项链接。](../media/f5cbc3fa-90f7-4299-976d-2482f2c69755.png)
  
4. 在 " **购买服务** " 页上，鼠标移过或点击 " **Office 365 额外文件存储**"，然后选择 " **立即购买**"。
  
5. 输入所需的用户许可证数，如果显示，请选择基本订阅。 选择 " **立即签出**"。
  
6. 在 " **此外观如何？** " 页上，验证所选存储的 gb 数，查看定价信息，然后选择 " **下一步**"。

7. 在 " **完成订单** " 页上，选择 " **下订单**"。

::: moniker-end

## <a name="increase-or-decrease-storage"></a>增加或减少存储空间

如果您已通过 **Office 365 额外文件存储** 附加设备购买了额外的文件存储，则可以使用这些步骤增加或减少订阅的额外存储空间。 可以将存储减小为低达 1 gb。 若要删除所有额外的存储空间，请 [与支持人员联系](../admin/contact-support-for-business-products.md)。

::: moniker range="o365-worldwide"

1. 在管理中心中，转到“**计费**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">你的产品</a>”页面。
2. 在 " **产品** " 选项卡上，选择包含 " **Office 365 额外文件存储** " 加载项的订阅。
3. 在 "产品详细信息" 页上的 " **加载项** " 部分，选择 " **管理加载项**"。
4. 在 " **管理加载项** " 窗格中，从 **加载** 项列表中选择 " **Office 365 额外文件存储**"。
5. 在 " **数量** " 文本框中，输入所需的订阅存储空间的 gb 数。
6. 选择 **“保存”**。

::: moniker-end

::: moniker range="o365-germany"

1. 在管理中心，转到“**计费**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">订阅</a>”页面。

2. 在 " **订阅** " 页上，选择 " **加载项**"。

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > 如果你未看到 **加载项**，并且你的订阅是通过合作伙伴购买的，请选择 " **批量许可服务中心 (VLSC") **。
  
3. 在 " **Office 365 额外文件存储**" 下，选择 " **更改数量**"。

    !['更改数量'链接。](../media/96473f2b-6ff6-45ec-b1a3-d7b204ac1f6e.png)
  
4. 在右侧窗格中，输入所需的 gb 的总数，然后选择 " **提交**"。

    例如，如果你目前拥有 200 GB 的额外文件存储空间，但你只需要 100 GB，则可以在框中输入" **100**"。

5. 选择“**关闭**”。

::: moniker-end

::: moniker range="o365-21vianet"

1. 在管理中心，转到“**计费**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">订阅</a>”页面。

2. 在 " **订阅** " 页上，选择 " **加载项**"。

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > 如果你未看到 **加载项**，并且你的订阅是通过合作伙伴购买的，请选择 " **批量许可服务中心 (VLSC") **。
  
3. 在 " **Office 365 额外文件存储**" 下，选择 " **更改数量**"。

    !['更改数量'链接。](../media/96473f2b-6ff6-45ec-b1a3-d7b204ac1f6e.png)
  
4. 在右侧窗格中，输入所需的 gb 的总数，然后选择 " **提交**"。

    例如，如果你目前拥有 200 GB 的额外文件存储空间，但你只需要 100 GB，则可以在框中输入" **100**"。

5. 选择“**关闭**”。

::: moniker-end

## <a name="is-my-plan-eligible-for-office-365-extra-file-storage"></a>我的计划是否符合使用 Office 365 额外文件存储空间的条件？

Office 365 额外文件存储空间可以用于以下订阅：
  
- Office 365 企业版 E1

- Office 365 企业版 E2

- Office 365 企业版 E3

- Office 365 企业版 E4

- Office 365 企业版 E5

- Office for web 与 SharePoint 计划1

- 使用 SharePoint 计划2的网站的 Office

- SharePoint Online 计划 1

- SharePoint Online 计划 2

- Microsoft 365 商业基础版

- Microsoft 365 商业标准版

- Microsoft 365 商业高级版

- Microsoft 365 E3

- Microsoft 365 E5

- Microsoft 365 F1

> [!NOTE]
> Office 365 额外文件存储也适用于 GCC、GCC 和 DOD 计划。

## <a name="related-content"></a>相关内容

[管理网站存储限制](ttps://docs.microsoft.com/sharepoint/manage-site-collection-storage-limits) (文章) \
[将 OneDrive 用户的默认存储空间设置](https://docs.microsoft.com/onedrive/set-default-storage-space) (文章) 
