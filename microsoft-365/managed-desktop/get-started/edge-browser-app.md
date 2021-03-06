---
title: 新版 Microsoft Edge
description: 介绍如何部署和更新新的边缘浏览器
keywords: 浏览器、Microsoft 托管桌面、Microsoft 365、服务、文档
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
audience: ITpro
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 60ffdcddcd069330d3cde2f9cc6b2635cf205a90
ms.sourcegitcommit: 89b2ad0793c68415f178b8792a9757b9448345a6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "47294670"
---
# <a name="new-microsoft-edge-app"></a>新建 Microsoft Edge 应用

新的 [Microsoft Edge 浏览器](https://www.microsoft.com/edge) 在浏览过程中提供了世界一流的性能、更高的隐私、更高的工作效率和更多价值。 Microsoft 托管桌面提供了在您的环境中部署新边缘浏览器的公共预览。

## <a name="initial-deployment"></a>初始部署

若要将 Microsoft 托管桌面设备迁移到新的 Microsoft Edge 浏览器，请通过 Microsoft 托管桌面门户文件提供 IT 支持票证。 在您对票证进行存档时，我们会将边缘稳定通道部署到测试组，然后在每个后续的部署组中每隔24小时部署它。 若要暂停部署，请文件另一个票证请求操作保留。

[Beta 通道](https://docs.microsoft.com/deployedge/microsoft-edge-channels#beta-channel)也适用于组织内部的代表验证请求。 Microsoft 托管桌面将根据需要将应用程序部署到测试和第一组，以便除了稳定通道之外，所有这些用户都具有 Beta 通道。 对于需要访问 Beta 频道的任何其他用户，请将其添加到新式的 " **Workplace Edge Beta users** " 组，并让他们从公司门户安装它

## <a name="updates-to-microsoft-edge"></a>Microsoft Edge 的更新

Microsoft 托管桌面部署 Microsoft Edge 的 [稳定通道](https://docs.microsoft.com/deployedge/microsoft-edge-channels#stable-channel) ，每六周自动更新一次。 对稳定通道的更新由 Microsoft Edge 产品组 [逐步](https://docs.microsoft.com/deployedge/microsoft-edge-update-progressive-rollout) 进行，以确保为客户提供最佳体验。 

[Beta 通道](https://docs.microsoft.com/deployedge/microsoft-edge-channels#beta-channel)部署到测试和第一个组中的设备，用于组织内的代表验证。 此渠道完全受支持，并在每六周的时间内自动更新一次新功能。

若要确保 Microsoft Edge 正确更新，请不要修改 Microsoft Edge [更新策略](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies)。



## <a name="settings-managed-by-microsoft-managed-desktop"></a>Microsoft 托管桌面管理的设置

Microsoft 托管桌面已为 Microsoft Edge 创建了一组默认的策略，以保护浏览器的安全。 默认浏览器设置如下所示：

### <a name="microsoft-edge-extensions"></a>Microsoft Edge 扩展

Microsoft 托管桌面设备上 Microsoft Edge 的安全基准设置了两个策略来禁用所有 Chrome 扩展和安全用户。 若要在环境中启用和部署扩展，请参阅管理的设置。 

#### <a name="extension-installation-blocklist"></a>扩展安装阻止列表
**默认值：** 各种

Microsoft 托管桌面设置此策略，以防止在托管终结点上安装 Chrome 扩展。 存在与 Chromium 扩展模型关联的已知风险，其中包括数据丢失保护、隐私和可能危害设备的其他风险。 

#### <a name="allow-user-level-native-messaging-hosts-installed-without-admin-permissions"></a>允许没有管理员权限的情况下 (安装用户级别的本机邮件主机) 

**默认值：** 禁用

通过禁用此策略，Microsoft Edge 将仅使用安装在系统级别上的本机邮件主机。 本机邮件主机是 Chrome 扩展的一部分，它允许浏览器与用户终结点的其他部分进行交互，从而产生各种安全问题。  

### <a name="secure-sockets-layer-ssl"></a>安全套接字层 (SSL)

#### <a name="minimum-ssl-version"></a>最低 SSL 版本

**默认值：** 支持的最低 TLS 1。2

如果要使用安全性较低的 TLS 1.1，可以请求这样做。

#### <a name="allows-users-to-proceed-from-the-ssl-warning-page"></a>允许用户从 "SSL 警告" 页继续

**默认值：** 禁用

建议您不要启用此设置，因为它允许用户访问具有 SSL 错误的网站。

### <a name="microsoft-defender-smartscreen"></a>Microsoft Defender SmartScreen

#### <a name="configure-windows-defender-smartscreen"></a>配置 Windows Defender SmartScreen

**默认值：** 了

默认情况下启用以帮助保护用户。

#### <a name="windows-defender-smartscreen-prompts-for-sites"></a>Windows Defender SmartScreen 网站提示

**默认值：** 了

建议您不要禁用此设置，因为这将允许用户忽略警告，并继续执行潜在的恶意网站。

#### <a name="prevent-bypassing-of-windows-defender-smartscreen-warnings-about-downloads"></a>阻止绕过关于下载的 Windows Defender SmartScreen 警告

**默认值：** 了

建议不要禁用此设置，因为这将允许用户忽略警告和完成未验证的下载。

### <a name="adobe-flash"></a>Adobe Flash

#### <a name="default-adobe-flash-setting"></a>默认 Adobe Flash 设置

**默认值：** 禁用

由于相关的安全风险，建议不要使用 Flash。 如果仍有依赖于 Flash 的进程，请设置 **[PluginsAllowedForUrls](https://docs.microsoft.com/deployedge/microsoft-edge-policies#pluginsallowedforurls)** 策略以为需要它的网站启用 Flash。 如果不能将允许的网站列表维护为使用 Flash，请将更改请求更改为 **单击以播放**，这样用户就可以选择何时运行 flash。

### <a name="password-manager"></a>密码管理器

#### <a name="enable-saving-passwords-to-the-password-manager"></a>启用将密码保存到密码管理器

**默认值：** 禁用

建议您不要允许用户在其设备上保存密码。

### <a name="internet-explorer-mode-in-microsoft-edge"></a>Microsoft Edge 中的 Internet Explorer 模式
IE 模式在 Microsoft Edge 中，便于在单个浏览器中使用您的组织所需的所有网站。 它对与 Chromium 呈现引擎兼容的网站使用集成的 Chromium 引擎，并使用 Trident MSHTML 引擎从 Internet Explorer 11 (IE11) 获取对 IE 功能没有依赖关系的网站。 [了解详细信息] (https://docs.microsoft.com/DeployEdge/edge-ie-mode) 

默认情况下，Microsoft 托管桌面为你的设备启用 Internet Explorer 模式 

#### <a name="internet-explorer-mode-integration"></a>Internet Explorer 模式集成
**默认值：** Internet Explorer 模式

默认情况下，设备设置为使用 Internet Explorer 模式，但您可以将其设置为在独立 Internet Explorer 11 窗口中打开网站。 若要更改此文件，请提供支持请求。

#### <a name="add-sites-to-the-enterprise-mode-site-list"></a>将网站添加到企业模式网站列表
若要在 Internet Explorer 模式下打开网站，必须将其包含在 [企业网站列表](https://docs.microsoft.com/DeployEdge/edge-ie-mode-sitelist)中。 维护和部署企业网站列表是您的责任。 有关详细信息，请参阅 [使用配置企业模式站点列表策略配置](https://docs.microsoft.com/DeployEdge/edge-ie-mode-policies#configure-using-the-configure-the-enterprise-mode-site-list-policy)

### <a name="other-settings"></a>其他设置

#### <a name="enable-site-isolation-for-every-site"></a>为每个网站启用网站隔离

**默认值：** 了

如果启用此策略，则用户将无法退出每个网站在其自己的进程中运行的默认行为。

#### <a name="supported-authentication-schemes"></a>支持的身份验证方案

**默认值：** NTLM、协商

Microsoft 托管桌面不支持基本或摘要式身份验证方案。

#### <a name="automatically-import-another-browsers-data-and-settings-at-first-run"></a>首次运行时自动导入另一个浏览器的数据和设置

**默认值：** 从默认浏览器自动导入所有受支持的数据类型和设置 

应用此策略后，首次运行体验将跳过 "导入" 部分，最大限度地减少用户交互。 Microsoft Edge 早期版本中的浏览器数据将始终在首次运行时无提示地迁移，无论此设置如何。 


## <a name="settings-you-manage"></a>您管理的设置

您可以使用 Microsoft Intune 中的 "管理模板" 配置文件来部署之前未介绍的任何 Microsoft Edge 设置。 有关详细信息，请参阅 [Configure Microsoft Edge policy settings With Microsoft Intune](https://docs.microsoft.com/deployedge/configure-edge-with-intune)。 如果要评估当前未包含在 Intune 中的 Microsoft Edge 管理模板中的策略，可以在 Intune 中使用 Windows 10 设备的自定义设置。

### <a name="enabling-specific-chrome-extensions"></a>启用特定的部件版式扩展

管理模板提供了使用 Microsoft Intune 部署特定 Chrome 扩展的设置。 您可以在 " **计算机配置 > Microsoft Edge > 扩展中找到它，> 允许安装特定的扩展**。

### <a name="install-extensions-silently"></a>自动安装扩展

您还可以使用管理模板设置 Microsoft Edge 以安装分机，而不向用户发出警告。 您可以在 " **计算机配置" > Microsoft Edge > 扩展中找到它，> 控制自动安装哪些扩展**。

### <a name="microsoft-edge-update-policies"></a>Microsoft Edge 更新策略
若要确保 Microsoft Edge 正确更新，请不要修改 Microsoft Edge [更新策略](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies)。

### <a name="other-common-enterprise-policies"></a>其他常见的企业策略

Microsoft Edge 提供了很多其他策略。 以下是一些比较常见的项：
 
- [在企业网站列表和 IE 模式下配置网站](https://docs.microsoft.com/deployedge/edge-ie-mode-sitelist)
- [配置 "启动"、"主页" 和 "新建选项卡页" 设置](https://docs.microsoft.com/deployedge/microsoft-edge-policies#startup-home-page-and-new-tab-page)
- [配置 "冲浪游戏" 设置](https://docs.microsoft.com/deployedge/microsoft-edge-policies#allowsurfgame)
- [配置代理服务器设置](https://docs.microsoft.com/deployedge/microsoft-edge-policies#proxy-server)

