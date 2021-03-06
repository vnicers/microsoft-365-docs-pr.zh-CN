---
title: 客户密码箱请求
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
search.appverid:
- BCS160
- MET150
- MOE150
description: 了解客户密码箱请求，使您可以控制 Microsoft 支持工程师在遇到问题时如何访问数据。
ms.openlocfilehash: d71fbaa42fba49bd0f06b26d34d2257f8a4a60ba
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2020
ms.locfileid: "47546498"
---
# <a name="customer-lockbox-in-office-365"></a>Office 365 中的客户密码箱

本文提供了客户密码箱的部署和配置指南。 客户密码箱支持访问 Exchange Online、SharePoint Online 和 OneDrive for Business 中的数据的请求。 若要推荐对其他服务的支持，请提交 [Office 365 UserVoice](https://office365.uservoice.com/)的请求。

若要查看授权你的用户从 Microsoft 365 合规性产品（包括此服务）中获益的选项（包括2020此服务），请参阅 [microsoft 365 许可指南以了解安全 & 合规性](https://aka.ms/ComplianceSD)。

客户密码箱可确保 Microsoft 无法访问你的内容以执行服务操作，而无需你的明确批准。 客户密码箱将你带到审批工作流，以获取访问内容的请求。

有时，Microsoft 工程师可帮助解决和修复支持流程中的客户报告的问题。 通常情况下，通过 Microsoft 已对其服务实施的大量遥测和调试工具来修复问题。 但是，某些情况下，需要 Microsoft 工程师才能访问客户内容，以确定根本原因并解决问题。 客户密码箱要求工程师在审批工作流的最后步骤中请求从客户进行访问。 这将为组织提供批准或拒绝这些请求的选项，并向客户提供直接访问控制。

### <a name="customer-lockbox-overview-video"></a>客户密码箱概述视频

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>客户密码箱工作流

Microsoft 工程师启动客户密码箱请求时，以下步骤概述了典型的工作流：

1. 组织中的某个人遇到 Microsoft 365 邮箱的问题。

2. 在用户对问题进行故障排除但不能修复时，他们将使用 Microsoft 支持打开支持请求。

3. Microsoft 支持工程师会检查服务请求，并确定访问组织的租户以修复 Exchange Online 中的问题的需求。

4. Microsoft 支持工程师登录到客户密码箱请求工具，并发出数据访问请求，其中包括组织的租户名称、服务请求编号以及工程师需要对数据进行访问的预计时间。

5. Microsoft 支持经理批准请求后，客户密码箱将向组织发送指定的审批者，发送来自 Microsoft 的挂起的访问请求的电子邮件通知。

    ![客户密码箱电子邮件通知示例](../media/CustomerLockbox1.png)

   在 Microsoft 365 管理中心中分配了 " [客户密码箱访问审批者](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles) " 管理员角色的任何人都可以批准客户密码箱请求。

6. 审批者登录到 Microsoft 365 管理中心并批准该请求。 此步骤将通过搜索审核日志来触发创建可供使用的审核记录。 有关详细信息，请参阅 [审核客户密码箱请求](#auditing-customer-lockbox-requests)。

   如果客户拒绝请求或不在12小时内批准请求，则请求将过期，并且不向 Microsoft 工程师授予任何访问权限。

   > [!IMPORTANT]
   > Microsoft 不包含客户密码箱中的任何链接需要登录 Office 365 的电子邮件通知。

7. 组织中的审批者批准请求后，Microsoft 工程师将收到审批邮件，登录到 Exchange Online 中的租户，并解决客户的问题。 Microsoft 工程师将请求的持续时间解决问题，在此之后，将自动吊销访问权限。

> [!NOTE]
> Microsoft 工程师执行的所有操作都记录在审核日志中。 您可以搜索并查看这些审核记录。

## <a name="turn-customer-lockbox-requests-on-or-off"></a>打开或关闭客户密码箱请求

您可以在 Microsoft 365 管理中心中打开客户密码箱控件。 当你启用客户密码箱时，Microsoft 必须先获取你的组织的审批，然后才能访问你的租户的任何内容。

1. 使用已分配全局管理员或 **客户密码箱访问审批者** 角色的工作或学校帐户，转到 [https://admin.microsoft.com](https://admin.microsoft.com) 并登录。

2. 选择 " **设置" > "组织设置**"。

3. 选择 "**服务**  >  **客户密码箱**  >  **编辑**"，然后将开关移动到 "打开" 或 **"** **关闭**" 以打开或关闭该功能。

    ![Require approval for Customer Lockbox](../media/CustomerLockbox4.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>批准或拒绝客户密码箱请求

1. 使用已分配全局管理员或 **客户密码箱访问审批者** 角色的工作或学校帐户，转到 [https://admin.microsoft.com](https://admin.microsoft.com) 并登录。

2. 选择 " **支持 > 客户密码箱请求**"。

    ![单击 "支持"，然后单击 "客户密码箱请求"](../media/CustomerLockbox5.png)

    将显示客户密码箱请求的列表。

    ![客户密码箱请求列表](../media/CustomerLockbox6.png)

3. 选择 "客户密码箱请求"，然后选择 " **批准** " 或 " **拒绝**"。

    ![批准或拒绝客户密码箱请求](../media/CustomerLockbox7.png)

    将显示有关客户密码箱请求的审批的确认消息。

    ![批准或拒绝客户密码箱请求](../media/CustomerLockbox8.png)

> [!NOTE]
> 使用 AccessToCustomerDataRequest cmdlet 可以批准、拒绝或取消 microsoft 365 客户密码箱请求，这些请求可控制 Microsoft 支持工程师对数据的访问。 有关详细信息，请参阅 [AccessToCustomerDataRequest](https://docs.microsoft.com/powershell/module/exchange/set-accesstocustomerdatarequest)。


## <a name="auditing-customer-lockbox-requests"></a>审核客户密码箱请求

审核日志中记录了与客户密码箱请求对应的审核记录。 您可以使用安全 & 合规中心中的 " [审核日志搜索" 工具](search-the-audit-log-in-security-and-compliance.md) 访问这些日志。 与接受或拒绝客户密码箱请求以及 Microsoft 工程师执行的操作相关的操作 (当访问请求被批准时，) 也会记录在审核日志中。 您可以搜索并查看这些审核记录。

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>在审核日志中搜索与客户密码箱请求相关的活动

在可以使用审核日志跟踪客户密码箱的请求之前，需要执行一些步骤来设置审核日志记录。 有关详细信息，请参阅 [在 Security & 合规性中心中搜索审核日志](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#before-you-begin)。 完成安装后，请按照以下步骤创建审核日志搜索查询，以返回与客户密码箱相关的审核记录：

1. 转到 [https://protection.office.com](https://protection.office.com)。
  
2. 使用工作或学校帐户进行登录。

3. 在安全性 & 合规性中心的左侧窗格中，选择 "**搜索 & 调查**  >  **审核日志搜索**"。

    将显示 " **审核日志搜索** " 页。

    ![审核日志搜索页](../media/auditlogsearch1.png)
  
4. 配置以下搜索条件：

    a. **活动** -将此字段保留为空，以便搜索将返回所有活动的审核记录。 若要返回与客户密码箱请求和 Microsoft 工程师所执行的相应活动相关的任何审核记录，这是必需的。

    b. "**开始日期**" 和 "**结束日期**"-选择要显示在该时间段内发生的事件的日期和时间范围。

    c. **用户** -将此字段留空。

    d. **文件、文件夹或网站** -将此字段留空。

5. 单击“**搜索**”以使用搜索条件运行搜索。

    搜索结果已加载，并在几分钟后显示在 "**审核日志搜索**" 页上的 "**结果**" 下。

6. 单击 "搜索结果" 页上的 " **筛选结果** "，然后执行下列操作之一：

   - 若要显示与组织中的审批者批准或拒绝客户密码箱请求的审核记录，请执行以下操作：在 " **活动** " 列下的框中，键入 **AccessToCustomerDataRequest**。

   - 显示与 Microsoft 工程师相关的审核记录，以响应批准的客户密码箱请求：在 " **用户** " 列下的框中，键入 " **Microsoft 接线员**"。 " **活动** " 列将显示工程师执行的操作。

      ![在 "Microsoft 接线员" 上筛选以显示审核记录](../media/CustomerLockbox10.png)

7. 在结果列表中，单击要显示的审核记录。

### <a name="audit-record-for-a-customer-lockbox-access-request"></a>客户密码箱访问请求的审核记录

当您的组织中的某个人批准或拒绝客户密码箱请求时，审核日志中会记录审核记录。 此记录包含以下信息。

| 审核记录属性| 描述|
|:---------- |:----------|
| 日期       | 批准或拒绝客户密码箱请求的日期和时间。
| IP 地址 | 审批者用于批准或拒绝请求的计算机的 IP 地址。 |
| 用户       | 服务帐户 BOXServiceAccount@ \[ customerforest。 \] prod.outlook.com。            |
| 活动   | AccessToCustomerDataRequest;这是您批准或拒绝客户密码箱请求时记录的审核活动。                                |
| Item       | 客户密码箱请求的 Guid                             |

下面的屏幕截图显示了与批准的客户密码箱请求对应的审核日志记录的示例。 如果客户密码箱请求被拒绝，则 **ApprovalDecision** 参数的值将为 **Deny**。

![批准的客户密码箱请求的审核记录](../media/CustomerLockbox9.png)

> [!TIP]
> 若要在审核记录中显示更详细的信息，请单击 " **详细信息**"。

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>由 Microsoft 工程师执行的操作的审核记录

Microsoft 工程师在客户密码箱请求批准后执行的操作 (并可能导致访问客户内容) 记录在审核日志中。 这些记录包含以下信息。

| 审核记录属性| 描述|
|:---------- |:----------|
| 日期       | 执行操作的日期时间。 请注意，执行此操作的时间将不超过客户密码箱请求批准的4个小时。              |
| IP 地址 | Microsoft 工程师使用的计算机的 IP 地址。 |
| 用户       | Microsoft 运算符;此值指示此记录与客户密码箱请求相关。                                  |
| 活动   | Microsoft 工程师执行的活动的名称。|
| Item       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>常见问题

#### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>客户密码箱适用于哪些 Microsoft 365 服务？

客户密码箱目前在 Exchange Online、SharePoint Online 和 OneDrive for Business 中受支持。

#### <a name="is-customer-lockbox-available-to-all-customers"></a>客户密码箱是否适用于所有客户？

客户密码箱包含在 Microsoft 365 或 Office 365 E5 订阅中，并且可以添加到具有信息保护和合规性或高级合规性附加订阅的其他计划中。 有关详细信息，请参阅 [计划和定价](https://products.office.com/business/office-365-enterprise-e5-business-software)   。

#### <a name="what-is-customer-content"></a>什么是客户内容？

客户内容是由 Microsoft 365 服务和应用程序的用户创建的数据。 客户内容的示例包括：

- 电子邮件正文或电子邮件附件

- SharePoint 网站内容

- SharePoint 文件正文中的信息

- Skype for Business 演示文稿文件正文

- 即时消息 (IM) 或语音对话

- 客户生成的 blob 或结构化存储数据 (例如，SQL 容器) 

- 客户拥有的安全信息 (例如，证书、加密密钥和密码) 

- 如果客户内容仍然存在，则推断和所有后续推断

有关 Office 365 中的客户内容的其他信息，请参阅 [office 365 信任中心](https://products.office.com/business/office-365-trust-center-privacy/)。

#### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>当有访问我的内容的请求时，会向谁发出通知？

系统会通知全局管理员和分配了客户密码箱访问审批者管理员角色的任何人。 这些用户也是可以批准客户密码箱请求的相同用户。

#### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>谁可以在组织中批准或拒绝这些请求？

全局管理员和分配了客户密码箱访问审批者管理员角色的任何人都可以批准客户密码箱请求。 客户在其组织中控制这些角色分配。

#### <a name="how-do-i-opt-in-to-customer-lockbox"></a>如何选择客户密码箱？

全局管理员可以在 Microsoft 365 或 Microsoft 365 管理中心中启用和配置客户密码箱。

#### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>如果我批准客户密码箱请求，工程师可以执行哪些操作，以及我如何知道 Microsoft 工程师所做的工作？

批准客户密码箱请求后，Microsoft 工程师授予这些必需的权限，以使用预先批准的 cmdlet 访问客户内容。 Microsoft 工程师在响应客户密码箱请求时所执行的操作会在安全 & 合规性中心的审核日志中记录和访问。

#### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>我如何知道 Microsoft 遵循审批过程？

您可以通过 Microsoft 365 管理中心中的客户密码箱请求历史记录，交叉引用发送给组织中的管理员和审批者的电子邮件审批通知。

最新 [SOC 1 SSAE 16 审核报告](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports)中包含客户密码箱。 有关更多详细信息，可以在 [Microsoft 服务信任门户](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports)中找到最新报告。

#### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>Microsoft 是否可以修改我的租户的审批者列表？ 如果不是，如何避免？

只有组织中的全局管理员才能指定可以批准客户密码箱请求的用户。 这意味着，只有 Azure Active Directory 中全局管理员组的成员才能指定可以批准请求的人员。 Azure Active Directory 中全局管理员组的成员身份仅由您的组织管理。

#### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>如果我需要有关内容访问请求的详细信息来批准它，该怎么办？

每个客户密码箱请求都包含一个 Microsoft 365 服务请求号码。 您可以联系 Microsoft 支持部门并参考此服务号码，以获取有关请求的详细信息。

#### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>在批准客户密码箱请求时，权限的有效期是多长时间？

目前，授予 Microsoft 工程师访问权限的最长期限为4小时。 Microsoft 工程师还可以请求较短的时间段。

#### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>如何获取所有客户密码箱请求的历史记录？

在 Microsoft 365 管理中心中查看所有客户密码箱请求。

#### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>如何将内容访问请求与相关审核日志关联？

合规中心活动源包含客户密码箱的日志活动。 客户可以根据其收到的电子邮件请求，从活动源中交叉引用客户密码箱日志活动。

#### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>当客户没有响应客户密码箱请求时，会发生什么？

客户密码箱请求的默认持续时间为12小时。 如果在12小时内不响应请求，则请求将过期。

#### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>当客户拒绝客户密码箱请求时，Microsoft 会做什么？

如果客户拒绝客户密码箱请求，则不会发生对客户内容的访问。 如果组织中的用户继续遇到要求 Microsoft 访问客户内容以解决问题的服务问题，则服务问题可能会持续存在，Microsoft 将向用户通知此问题。

#### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>客户密码箱是否防止来自法律强制机构或其他第三方的数据请求？

否。 Microsoft 会认真为客户数据提供第三方请求。 作为云服务提供商，Microsoft 始终支持客户数据的隐私。 在我们收到传唤的情况下，Microsoft 将始终尝试将第三方重定向到客户以获取信息。  (阅读 Brad Smith 的博客： [保护客户数据免受政府窥探](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)) 。 我们将定期发布有关 Microsoft 收到的法律强制请求的 [详细信息](https://www.microsoft.com/corporate-responsibility/lerr) 。

有关详细信息，请参阅有关第三方数据请求的 [Microsoft 信任中心](https://www.microsoft.com/trustcenter/default.aspx) 和 [在线服务条款](https://www.microsoft.com/Licensing/product-licensing/products.aspx) 中的 "客户数据泄露" 部分。

#### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>Microsoft 如何确保其员工的成员在 Office 365 应用程序中不具有对客户内容的访问权限？

Microsoft 通过访问控制系统实施广泛的防护措施，使用侦探措施来识别和解决绕过这些访问控制系统的尝试。 Microsoft 365 以最小特权和实时访问原则运行。 因此，任何 Microsoft 人员都不具有定期访问客户内容的权限。 如果授予了权限，将在有限的持续时间内进行。 

Microsoft 365 使用称为 " *密码箱* " 的访问控制系统处理权限的请求，该权限允许在服务中执行操作和管理功能。 操作员必须使用密码箱请求对客户内容的访问权限，这就要求第二个人对请求执行操作 (例如，在授予访问权限前批准) 。 第二个人不能是请求者，必须指定它以批准对客户内容的访问。 仅当请求得到批准时，操作员才能获取对客户内容的临时访问权限。 提升期过期后，密码箱将撤销访问权限。

有关 Microsoft 常规安全实践的更多详细信息，请参阅 [联机服务条款](https://www.microsoft.com/licensing/product-licensing/products) 。

#### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>在什么情况下，Microsoft 工程师需要访问我的内容？

最常见的情况是，Microsoft 工程师需要访问客户内容的情况是，客户提出支持访问请求以进行故障排除的情况。 Microsoft 365 的基础原则是，该服务在没有 Microsoft 访问客户内容的情况下运行。 Microsoft 执行的几乎所有服务操作都是完全自动化的，人工干预是高度控制的，并从客户内容中提取出来。 Microsoft 365 的目标是，在客户批准特定的 Microsoft access 请求之前，不需要访问客户内容以支持服务。

#### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>我已经认为我的数据是 Microsoft 云的安全性，所以我为什么需要客户密码箱？

客户密码箱通过让客户能够为服务操作提供显式访问授权，从而提供了额外的控制层。 通过演示如何将过程用于显式数据访问授权，客户密码箱还可帮助客户满足某些合规性义务，如 HIPAA 和 FEDRAMP。
