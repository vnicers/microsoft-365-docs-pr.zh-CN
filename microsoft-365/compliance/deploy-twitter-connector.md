---
title: 部署连接器以存档 Twitter 数据
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
ROBOTS: NOINDEX, NOFOLLOW
description: 管理员可以设置本机连接器以将 Twitter 数据导入和存档到 Microsoft 365。 将此数据导入 Microsoft 365 后，您可以使用合规性功能（如法律封存、内容搜索和保留策略）来管理组织的 Twitter 数据的管理。
ms.openlocfilehash: 01c4901544e47cd1c361a132e144440f00bd8504
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48200825"
---
# <a name="deploy-a-connector-to-archive-twitter-data"></a>部署连接器以存档 Twitter 数据

本文包含的分步过程可部署使用 Office 365 导入服务将数据从组织的 Twitter 帐户导入 Microsoft 365 的连接器。 有关此过程的高级概述以及部署 Twitter 连接器所需的先决条件列表，请参阅 [Set up a connector to Archive twitter data ](archive-twitter-data-with-sample-connector.md)。 

## <a name="step-1-create-an-app-in-azure-active-directory"></a>步骤1：在 Azure Active Directory 中创建应用程序

1. 转到 <https://portal.azure.com> 并使用全局管理员帐户的凭据登录。

   ![登录到 Azure](../media/TCimage01.png)

2. 在左侧导航窗格中，单击 " **Azure Active Directory**"。

   ![转到 Azure Active Directory](../media/TCimage02.png)

3. 在左侧导航窗格中，单击 " **应用程序注册" (预览 ") ** 然后单击" **新建注册**"。

   ![创建新的应用注册](../media/TCimage03.png)

4. 注册应用程序。 在 " **重定向 URI (可选) **中，在" 应用程序类型 "下拉列表中选择" **Web** "，然后 `https://portal.azure.com` 在" URI "框中键入。

   ![https://portal.azure.com重定向 URI 的类型 ](../media/TCimage04.png)

5. 将 **应用程序 (客户端) id** 和 **目录 (租户) ID** ，并将其保存到文本文件或其他安全位置。 可在后续步骤中使用这些 Id。

    ![复制并保存应用程序 Id 和目录 Id](../media/TCimage05.png)

6. 转到 **证书 & 新应用程序的证书** ，并在 " **客户端密码** " 下，单击 " **新建客户端密码**"。

   ![创建新的客户端密码](../media/TCimage06.png)

7. 创建新的机密。 在 "说明" 框中，键入密码，然后选择一个过期时间段。 

   ![键入密码并选择 "过期期限"](../media/TCimage08.png)

8. 复制密码的值，并将其保存到文本文件或其他存储位置。 这是您在后续步骤中使用的 AAD 应用程序密码。

   ![复制并保存密码](../media/TCimage09.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>步骤2：将来自 GitHub 的连接器 web 服务部署到你的 Azure 帐户

1. 转到 [此 GitHub 网站](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet) ，然后单击 " **部署到 Azure**"。

    ![转到 Azure 主页](../media/FBCimage11.png)

2. 单击 " **部署到 Azure**" 后，您将被重定向到具有自定义模板页面的 Azure 门户。 填写 " **基础知识** " 和 " **设置** 详细信息"，然后单击 " **购买**"。

   ![单击 "创建资源并键入存储帐户"](../media/FBCimage12.png)

    - **订阅：** 选择要将 Twitter 连接器 web 服务部署到的 Azure 订阅。
    
    - **资源组：** 选择或创建新的资源组。 资源组是保留 Azure 解决方案的相关资源的容器。

    - **位置：** 选择一个位置。

    - **Web 应用名称：** 为连接器 web 应用提供一个唯一的名称。 Th 名称的长度必须介于3到18个字符之间。 此名称用于创建 Azure 应用服务 URL;例如，如果提供 Web 应用程序名称 **twitterconnector** ，则 Azure 应用服务 URL 将为 **twitterconnector.azurewebsites.net**。
    
    - **tenantId：** 在步骤1中创建 Azure Active Directory 中的 Facebook 连接器应用之后复制的 Microsoft 365 组织的租户 ID。
    
   - **APISecretKey：** 您可以键入任何值作为密码。 这用于在步骤5中访问连接器 web 应用。

3. 部署成功后，页面外观将类似于以下屏幕截图：

    ![单击 "存储"，然后单击 "存储帐户"](../media/FBCimage13.png)

## <a name="step-3-create-the-twitter-app"></a>步骤3：创建 Twitter 应用

1. 转到 https://developer.twitter.com ，使用组织的开发人员帐户的凭据登录，然后单击 " **应用**"。

   ![转到 https://developer.twitter.com 并登录](../media/TCimage25-5.png)
2. 单击 " **创建应用程序**"。
   
   ![转到 "应用程序" 页以创建应用程序](../media/TCimage26.png)

3. 在 " **应用程序详细信息**" 下，添加有关应用程序的信息。

   ![输入有关应用程序的信息](../media/TCimage27.png)

4. 在 Twitter 开发人员仪表板中，选择您刚创建的应用程序，然后单击 " **详细信息**"。
   
   ![复制并保存应用程序 Id](../media/TCimage28.png)

5. 在 " **密钥和令牌** " 选项卡上的 " **使用者 api** 密钥" 下，复制 api 密钥和 api 密钥，并将其保存到文本文件或其他存储位置。 然后，单击 " **创建** " 以生成访问令牌并访问令牌秘密，并将它们复制到文本文件或其他存储位置。
   
   ![复制并保存到 API 密钥](../media/TCimage29.png)

   然后，单击 " **创建** " 以生成访问令牌和访问令牌机密，并将它们复制到文本文件或其他存储位置。

6. 单击 " **权限** " 选项卡并配置权限，如以下屏幕截图所示：

   ![配置权限](../media/TCimage30.png)

7. 保存权限设置后，单击 " **应用程序详细信息** " 选项卡，然后单击 "编辑" > "编辑 **详细信息**"。

   ![编辑应用程序详细信息](../media/TCimage31.png)

8. 执行以下任务：

   - 选中此复选框可允许连接器应用登录 Twitter。
   
   - 使用以下格式添加 OAuth 重定向 Uri： ** \<connectorserviceuri> /Views/TwitterOAuth**，其中*connectorserviceuri*的值是您的组织的 Azure 应用服务 URL; 例如， https://twitterconnector.azurewebsites.net/Views/TwitterOAuth 。

    ![允许连接器应用登录到 Twitter 并添加 OAuth 重定向 Uri](../media/TCimage32.png)

现在可以使用 Twitter 开发人员应用。

## <a name="step-4-configure-the-connector-web-app"></a>步骤4：配置连接器 web 应用程序 

1. 转到 https:// \<AzureAppResourceName> (其中 **AzureAppResourceName** 是您在步骤 4) 中命名的 Azure 应用程序资源的名称。 例如，如果名称为 **twitterconnector**，请转到 https://twitterconnector.azurewebsites.net 。 该应用程序的主页如以下屏幕截图所示：

   ![转到 Azure 应用资源页](../media/FBCimage41.png)

2. 单击 " **配置** " 以显示登录页。

   ![单击 "配置" 以显示登录页](../media/FBCimage42.png)

3. 在 "租户 Id" 框中，键入或粘贴您在步骤 2) 中获取的租户 Id (。 在 "密码" 框中，键入或粘贴您在步骤 2) 中获取的 APISecretKey (，然后单击 " **设置配置设置** " 以显示 "配置详细信息" 页。

   ![使用租户 Id 和 API 密钥登录](../media/TCimage35.png)

4. 输入以下配置设置 

   - **Twitter Api 密钥：** 您在步骤3中创建的 Twitter 应用程序的 API 密钥。
   
   - **Twitter Api 密钥：** 您在步骤3中创建的 Twitter 应用程序的 API 密钥。
   
   - **Twitter 访问令牌：** 您在步骤3中创建的访问令牌。
   
   - **Twitter 访问令牌机密：** 您在步骤3中创建的访问令牌密码。
   
   - **AAD 应用程序 ID：** 您在步骤1中创建的 Azure Active Directory 应用程序的应用程序 ID
   
   - **AAD 应用程序密码：** 您在步骤1中创建的 APISecretKey 密码的值。

5. 单击 " **保存** " 以保存连接器设置。

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>步骤5：在 Microsoft 365 合规性中心中设置 Twitter 连接器

1. 转到 [https://compliance.microsoft.com](https://compliance.microsoft.com) ，然后单击左侧导航中的 " **数据连接器** "。

2. 在**Twitter**下的 "**数据连接器**" 页上，单击 "**查看**"。

3. 在 **Twitter** 页面上，单击 " **添加连接器**"。

4. 在 " **服务条款** " 页上，单击 " **接受**"。

5. 在 " **为连接器应用添加凭据** " 页上，输入以下信息，然后单击 " **验证连接**"。

   ![输入连接器应用凭据](../media/TCimage38.png)

    - 在 " **名称** " 框中，键入连接器的名称，如 **Twitter 帮助句柄**。
    
    - 在 " **连接器 URL** " 框中，键入或粘贴 Azure 应用服务 URL;例如 `https://twitterconnector.azurewebsites.net` 。
    
    - 在 " **密码** " 框中，键入或粘贴您在步骤2中创建的 APISecretKey 的值。
    
    - 在 " **Azure 应用 id** " 框中，键入或粘贴 azure 应用程序应用 ID 的值 (也称为您在步骤1中获取的 " *客户端 ID* ") 。

6. 成功验证连接后，单击 " **下一步**"。

7. 在 " **授权 Microsoft 365 导入数据** " 页上，再次键入或粘贴 APISecretKey，然后单击 "  **登录 web 应用**"。

8. 单击 " **使用 Twitter 登录**"。

9. 在 Twitter 登录页面上，使用您的组织的 Twitter 帐户的凭据进行登录。

   ![登录到 Twitter 帐户](../media/TCimage42.png)

   登录后，Twitter 页面将显示以下消息： "已成功设置 Twitter 连接器作业"。

10. 单击 " **继续** " 以完成 Twitter 连接器的设置。

11. 在 " **设置筛选器** " 页上，您可以将筛选器应用于最初导入特定年龄的项目。 选择年龄，然后单击 " **下一步**"。

12. 在 " **选择存储位置** " 页上，键入要将 Twitter 项目导入到其中的 Microsoft 365 邮箱的电子邮件地址，然后单击 " **下一步**"。

13. 在 " **提供管理员同意**" 中，单击 " **提供许可** "，然后按照步骤操作。 您必须是全局管理员，才能同意 Office 365 导入服务以访问组织中的数据。

14. 单击 " **下一步** " 查看连接器设置，然后单击 " **完成** " 以完成连接器设置。

15. 在 "合规性中心" 中，转到 " **数据连接器** " 页，然后单击 " **连接器** " 选项卡以查看导入过程的进度。
