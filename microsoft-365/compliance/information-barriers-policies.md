---
title: 定义信息屏障策略
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
localization_priority: None
description: 了解如何在 Microsoft 团队中定义信息障碍策略。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f7e1fbb0f1d468f8e1b79f9cc414fdb87a224283
ms.sourcegitcommit: 5e40c760c1af2a4cc6d85cb782b17f5c979677c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2020
ms.locfileid: "48379181"
---
# <a name="define-information-barrier-policies"></a>定义信息屏障策略

通过信息障碍，您可以定义旨在防止某些用户段相互通信的策略，或允许特定的分段仅与某些其他网段进行通信。 信息屏障策略可帮助您的组织保持遵守相关的行业标准和法规，并避免潜在的利益冲突。 若要了解详细信息，请参阅 [信息障碍](information-barriers.md)。 

本文介绍如何规划、定义、实现和管理信息屏障策略。 涉及几个步骤，工作流划分为多个部分。 在开始定义 (或编辑) 信息屏障策略之前，请务必仔细阅读 [先决条件](#prerequisites) 和整个过程。

> [!TIP]
> 本文包含一个 [示例方案](#example-contosos-departments-segments-and-policies) 和一个 [可下载的 Excel 工作簿](https://github.com/MicrosoftDocs/OfficeDocs-O365SecComp/raw/public/SecurityCompliance/media/InfoBarriers-PowerShellGenerator.xlsx) ，可帮助您规划和定义信息障碍策略。

## <a name="concepts-of-information-barrier-policies"></a>信息屏障策略的概念

在定义信息障碍策略时，您将使用用户帐户属性、分段、"阻止" 和/或 "允许" 策略以及策略应用程序。

- 用户帐户属性在 Azure Active Directory (或 Exchange Online) 中定义。 这些属性可以包括部门、职务、位置、团队名称和其他作业配置文件详细信息。 

- 分段是在安全 & 合规中心中使用选定的 **用户帐户属性**定义的用户集。  (查看 [受支持属性的列表](information-barriers-attributes.md)。 )  

- 信息屏障策略决定了通信限制或限制。 在定义信息障碍策略时，可以从以下两种策略中进行选择：
    - "块" 策略防止一个分段与另一个网段通信。
    - "允许" 策略允许一段仅与某些其他段进行通信。

- 策略应用程序在定义所有信息屏障策略之后完成，并准备好在您的组织中应用它们。

## <a name="the-work-flow-at-a-glance"></a>工作流程概览

|阶段    |所涉及的内容  |
|---------|---------|
|[确保满足先决条件](#prerequisites)     |-验证您是否具有 [所需的许可证和权限](information-barriers.md#required-licenses-and-permissions)<br/>-验证您的目录是否包含分段用户的数据<br/>-为 Microsoft 团队启用范围目录搜索<br/>-请确保审核日志记录已打开<br/>-确保没有现成的 Exchange 通讯簿策略<br/>-使用 PowerShell (提供的示例) <br/>-提供 Microsoft 团队的管理员同意 (步骤包括)           |
|[第1部分：组织中的用户区段](#part-1-segment-users)     |-确定所需的策略<br/>-创建要定义的段的列表<br/>-确定要使用的属性<br/>-在策略筛选器方面定义段        |
|[第2部分：定义信息屏障策略](#part-2-define-information-barrier-policies)     |-定义您的策略 (尚不应用) <br/>-从两种类型中进行选择 (阻止或允许)  |
|[第3部分：应用信息屏障策略](#part-3-apply-information-barrier-policies)     |-将策略设置为活动状态<br/>-运行策略应用程序<br/>-查看策略状态         |
| (根据需要) [编辑分段或策略](information-barriers-edit-segments-policies.md)    |-编辑分段<br/>-编辑或删除策略<br/>-重新运行策略应用程序<br/>-查看策略状态         |
| (根据需要) [故障排除](information-barriers-troubleshooting.md)|-当事情未按预期工作时执行操作|

## <a name="prerequisites"></a>先决条件

除了 [所需的许可证和权限](information-barriers.md#required-licenses-and-permissions)之外，请确保满足以下要求： 
     
- Directory data-确保您的组织的结构反映在目录数据中。 为此，请确保在 Azure Active Directory (或 Exchange Online) 中正确填充了用户帐户属性（如组成员身份、部门名称等）。 若要了解详细信息，请参阅以下资源：
  - [信息屏障策略的属性](information-barriers-attributes.md)
  - [使用 Azure Active Directory 添加或更新用户的配置文件信息](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [使用 Office 365 PowerShell 配置用户帐户的属性](https://docs.microsoft.com/microsoft-365/enterprise/configure-user-account-properties-with-microsoft-365-powershell)

- 作用域目录搜索-在定义组织的第一个信息屏障策略之前，必须 [在 Microsoft 团队中启用范围目录搜索](https://docs.microsoft.com/MicrosoftTeams/teams-scoped-directory-search)。 在设置或定义信息屏障策略之前，请先等待至少24小时后，再启用范围目录搜索。

- 审核日志记录-为了查找策略应用程序的状态，审核日志记录必须处于打开状态。 我们建议您在开始定义段或策略之前执行此操作。 若要了解详细信息，请参阅 [打开或关闭审核日志搜索](turn-audit-log-search-on-or-off.md)。

- 无通讯簿策略-在定义和应用信息屏障策略之前，请确保没有适当的 Exchange 通讯簿策略。 信息障碍基于通讯簿策略，但这两种类型的策略不兼容。 如果您具有此类策略，请务必先 [删除您的通讯簿策略](https://docs.microsoft.com/exchange/address-books/address-book-policies/remove-an-address-book-policy) 。 在信息屏障策略启用并启用了分层通讯簿后， ***不包含*** 在信息屏障段中的所有用户都将在 Exchange online 中看到 [分层通讯簿](https://docs.microsoft.com/exchange/address-books/hierarchical-address-books/hierarchical-address-books) 。

- 目前使用 powershell cmdlet 在 Office 365 安全 & 合规中心中定义和管理信息屏障策略。 虽然本文中提供了几个示例，但您需要熟悉 PowerShell cmdlet 和参数。 你还需要 Azure PowerShell 模块。
    - [连接到安全与合规中心 PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell)
    - [安装 Azure PowerShell 模块](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-2.3.2)

- Microsoft 团队中的信息障碍的管理员同意-当你的策略准备就绪后，信息障碍可以从聊天会话中删除他们不应参与的人员。 这有助于确保您的组织遵守策略和管理法规。 使用以下过程可使信息障碍策略在 Microsoft 团队中按预期方式工作。 

   1. 运行以下 PowerShell cmdlet：

      ```powershell
      Connect-AzureAD 
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzADServicePrincipal -ServicePrincipalName $appId
      if ($sp -eq $null) { New-AzADServicePrincipal -ApplicationId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   2. 出现提示时，使用您的工作或学校帐户登录 Office 365。

   3. 在 " **请求的权限** " 对话框中，检查信息，然后选择 " **接受**"。

满足所有先决条件后，请继续执行下一节。

> [!TIP]
> 为了帮助你准备计划，本文中包含了一个示例方案。 [请参阅 Contoso 的部门、领域和策略](#example-contosos-departments-segments-and-policies)。<p>此外，还提供了一个可下载的 Excel 工作簿，可帮助您规划和定义您的分段和策略 (并创建您的 PowerShell cmdlet) 。 [获取工作簿](https://github.com/MicrosoftDocs/OfficeDocs-O365SecComp/raw/public/SecurityCompliance/media/InfoBarriers-PowerShellGenerator.xlsx)。 

## <a name="part-1-segment-users"></a>第1部分：分段用户

在此阶段中，您将确定需要哪些信息障碍策略，创建要定义的段的列表，然后定义您的段落。

### <a name="determine-what-policies-are-needed"></a>确定所需的策略

考虑法律和行业法规，谁是组织中需要信息障碍策略的组？ 创建列表。 是否有任何组应阻止其与另一个组进行通信？ 是否有任何组应允许只与一个或两个其他组进行通信？ 考虑您需要的策略是否属于两个组中的一个：
- "阻止" 策略阻止一个组与另一个组进行通信。
- "允许" 策略允许组仅与特定的其他特定组进行通信。

当您拥有组和策略的初始列表时，请继续确定所需的段。 

### <a name="identify-segments"></a>标识段

除了您的初始策略列表之外，请为您的组织创建一个段落列表。 将包括在信息屏障策略中的用户应属于某个网段。 仔细规划你的段落，因为用户只能在一段时间内使用。 每个段只能应用一个信息障碍策略。

> [!IMPORTANT]
> 一个用户只能在一段中。

确定您的组织的目录数据中将用来定义段落的属性。 您可以使用 " *部门*"、" *MemberOf*" 或任何受支持的属性。 请确保您为用户选择的属性中具有值。 [请参阅信息障碍的受支持属性的列表](information-barriers-attributes.md)。

> [!IMPORTANT]
> 在**继续下一节之前，请确保您的目录数据具有可用于定义段的属性的值**。 如果您的目录数据没有要使用的属性的值，则必须更新用户帐户以包含该信息，然后再继续进行信息屏障。 若要获取有关此方面的帮助，请参阅以下资源：<br/>- [使用 Office 365 PowerShell 配置用户帐户属性](https://docs.microsoft.com/microsoft-365/enterprise/configure-user-account-properties-with-microsoft-365-powershell)<br/>- [使用 Azure Active Directory 添加或更新用户的配置文件信息](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>使用 PowerShell 定义段

定义段不会影响用户;它只是设置要定义并应用的信息屏障策略的阶段。

1. 使用 **OrganizationSegment** Cmdlet 和 **UserGroupFilter** 参数，该参数对应于要使用的 [属性](information-barriers-attributes.md) 。

    |语法   |示例  |
    |---------|---------|
    |`New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"`     |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>在此示例中，使用*hr*（"*部门*" 属性中的值）定义名为*hr*的字段。 Cmdlet 的 **-eq** 部分引用了 "等于"。  (或者，您可以使用 **-ne** 来表示 "不等于"。 请参阅 [在段定义中使用 "等于" 和 "不等于"](#using-equals-and-not-equals-in-segment-definitions)。 )         |

    在运行每个 cmdlet 之后，您应该会看到有关新段的详细信息列表。 详细信息包括段的类型、创建者或最后修改的人，等等。 

2. 对要定义的每个段重复此过程。

    > [!IMPORTANT]
    > **请确保您的段不重叠**。 将受到信息障碍影响的每个用户应属于一个 (且只有一个) 段。 任何用户都不应属于两个或多个段。  (请参阅 [示例： Contoso 在本文中定义的部分](#contosos-defined-segments) 。 ) 


定义了分段后，请继续 [定义信息屏障策略](#part-2-define-information-barrier-policies)。

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>在段定义中使用 "等于" 和 "不等于"

在下面的示例中，我们定义了 "部门等于 HR" 的段。 

|示例  |
|---------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>请注意，在此示例中，段定义包含表示为 **-eq**的 "等于" 参数。 
  |

您还可以使用 "not 等于" 参数（表示为 **-ne**）定义段，如下表所示：

|语法  |示例  |
|---------|---------|
|`New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"`   | <p>在此示例中，我们定义了一个名为 *NotSales* 的字段，其中包括不在 *销售*中的所有人。 Cmdlet 的 **-ne** 部分引用 "不等于"。  |

除了使用 "等于" 或 "不等于" 定义段之外，您还可以使用 "等于" 和 "不等于" 参数定义一个段。 您还可以使用逻辑 *AND* 和 *OR* 运算符定义复杂的组筛选器。


|语法    |示例  |
|---------|---------|
|`New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` |<p>在此示例中，我们定义了一个名为 " *LocalFTE* " 的字段，其中包括位于本地且其位置未列为 *临时*的人员。    |
 |`New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`|  <p>在此示例中，我们定义了一个名为 *Segment1* 的字段，其中包括属于 group1@contoso.com 成员的人员，而不是 group3@contoso.com 的成员。
|`New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | 在此示例中，我们定义了一个名为 *Segment2* 的字段，其中包括属于 group2@contoso.com 成员的人员，而不是 group3@contoso.com 的成员。
|`New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`|  在此示例中，我们定义了一个名为 *Segment1and2* 的字段，其中包括 group1@contoso.com 和 group2@contoso.com 的人员成员，而不是 group3@contoso.com 的成员。


> [!TIP]
> 如果可能，请使用包含 "-eq" 或 "-ne" 的段定义。 尽量不要定义复杂的段定义。

## <a name="part-2-define-information-barrier-policies"></a>第2部分：定义信息屏障策略

确定是否需要阻止某些网段之间的通信，或将通信限制到某些段。 理想情况下，您将使用最少的策略数，以确保您的组织符合法律和行业要求。

在您的用户区段列表和要定义的信息屏障策略中，选择一个方案，然后按照步骤操作。 

- [方案1：阻止段之间的通信](#scenario-1-block-communications-between-segments)
- [方案2：允许段仅与一个其他段进行通信](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> 请**确保在定义策略时，不会向一个分段分配多个策略**。 例如，如果您为 " *sales*" 一段定义一个策略，则不要为 *sales*定义其他策略。<p>此外，在定义信息屏障策略时，请确保将这些策略设置为非活动状态，直到您准备好应用它们为止。 定义 (或编辑) 策略不会影响用户，直到这些策略设置为 "活动状态"，然后应用。

 (请参阅 [示例： Contoso 的信息屏障策略](#contosos-information-barrier-policies) 在本文中。 ) 

### <a name="scenario-1-block-communications-between-segments"></a>方案1：阻止段之间的通信

当您想要阻止多个段相互通信时，可以定义两个策略：每个方向一个。 每个策略仅阻止单向通信。

例如，假设您想要阻止段 A 和 Segment B 之间的通信。在这种情况下，您可以定义一个策略，阻止段 A 与段 B 通信，然后定义另一个策略以防止段 B 与段 A 通信。

1. 若要定义您的第一个阻止策略，请将 **InformationBarrierPolicy** Cmdlet 与 **SegmentsBlocked** 参数一起使用。 

    |语法  |示例  |
    |---------|---------|
    |`New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"`     |`New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p>    在此示例中，我们定义了名为 "*销售*" 的部门的名为 "销售 *-研究*" 的策略。 在活动和应用后，此策略将阻止 *销售* 人员与名为 " *研究*" 的部门中的人员进行通信。         |

2. 若要定义您的第二个阻塞段，请再次将 **InformationBarrierPolicy** Cmdlet 与 **SegmentsBlocked** 参数一起使用，这次将段反向。

    |示例  |
    |---------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p>    在此示例中，我们定义了一个名为 "*研究部*" 的策略，以防止与 "*销售*" 通信的*研究*。     |

2. 继续执行下列操作之一：

   - 如果需要， () [定义一个允许分段仅与一个其他网段进行通信的策略](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - 在定义所有策略之后 () [应用信息屏障策略](#part-3-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>方案2：允许段仅与一个其他段进行通信

1. 若要允许一个分段仅与一个其他网段通信，请使用 **InformationBarrierPolicy** Cmdlet 和 **SegmentsAllowed** 参数。 

    |语法  |示例  |
    |---------|---------|
    |`New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"`     |`New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p>    在此示例中，我们为 "*制造业*" 字段定义了称为 "制造业 *-HR* " 的策略。 在活动和应用后，此策略允许在 *制造业* 中的人员仅与称为 *HR*的部门中的人员进行通信。  (在这种情况下， *制造* 无法与不属于 *HR*的用户进行通信 )          |

    **如果需要，可以使用此 cmdlet 指定多个段，如下面的示例所示。**

    |语法  |示例  |
    |---------|---------|
    |`New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"`     |`New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p>在此示例中，我们定义了允许 *研究* 分段仅与 *HR* 和 *制造业*通信的策略。        |

    对于要定义的每个策略，请重复此步骤，以允许特定段仅与特定的其他特定段进行通信。

2. 继续执行下列操作之一：

   - 如果需要， () [定义用于阻止网段之间的通信的策略](#scenario-1-block-communications-between-segments) 
   - 在定义所有策略之后 () [应用信息屏障策略](#part-3-apply-information-barrier-policies)

## <a name="part-3-apply-information-barrier-policies"></a>第3部分：应用信息屏障策略

信息屏障策略在将其设置为 "活动状态" 之前不起作用，然后应用这些策略。

1. 使用 **InformationBarrierPolicy** cmdlet 可以查看已定义的策略的列表。 记下每个策略的状态和标识 (GUID) 。

    语法 `Get-InformationBarrierPolicy`

2. 若要将策略设置为活动状态，请使用带有**Identity**参数的**InformationBarrierPolicy** Cmdlet，并将**State**参数设置为 "**活动**"。 

    |语法  |示例  |
    |---------|---------|
    |`Set-InformationBarrierPolicy -Identity GUID -State Active`     |`Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p>    在此示例中，我们将 GUID 为 " *43c37853-ea10-4b90-a23d-ab8c93772471* " 的信息屏障策略设置为 "活动" 状态。   |

    根据需要对每个策略重复此步骤。

3. 完成将信息屏障策略设置为活动状态后，请使用安全 & 合规性中心中的 **InformationBarrierPoliciesApplication** cmdlet。

    语法 `Start-InformationBarrierPoliciesApplication`

    在运行 `Start-InformationBarrierPoliciesApplication` 等待30分钟后，系统开始应用策略。 系统对用户应用策略用户。 通常，系统进程每小时大约5000个用户帐户。

## <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>查看用户帐户、段、策略或策略应用程序的状态

使用 PowerShell，可以查看用户帐户、分段、策略和策略应用程序的状态，如下表所示。

|若要查看此  |具体操作  |
|---------|---------|
|用户帐户     |使用具有 Identity 参数的 **InformationBarrierRecipientStatus** cmdlet。 <p>语法 `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p>您可以使用任何唯一标识每个用户的值，如名称、别名、可分辨名称、规范域名、电子邮件地址或 GUID。 <p>示例：`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p>在此示例中，我们引用 Office 365 中的两个用户帐户： *meganb* for *Megan*和 *alexw* for *Alex*。 <p> (也可以将此 cmdlet 用于单个用户： `Get-InformationBarrierRecipientStatus -Identity <value>`)  <p>此 cmdlet 返回有关用户的信息，如属性值和应用的任何信息障碍策略。|
|段     |使用 **OrganizationSegment** cmdlet。<p>语法 `Get-OrganizationSegment` <p>这将显示为您的组织定义的所有网段的列表。         |
|信息屏障策略     |使用 **InformationBarrierPolicy** cmdlet。 <p> 语法 `Get-InformationBarrierPolicy` <p>这将显示已定义的信息障碍策略的列表及其状态。       |
|最新的信息屏障策略应用程序     | 使用 **InformationBarrierPoliciesApplicationStatus** cmdlet。 <p>语法 `Get-InformationBarrierPoliciesApplicationStatus`<p>    这将显示有关策略应用程序是已完成、失败还是正在进行的信息。       |
|所有信息屏障策略应用程序|使用 `Get-InformationBarrierPoliciesApplicationStatus -All $true`<p>这将显示有关策略应用程序是已完成、失败还是正在进行的信息。|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

## <a name="what-if-i-need-to-remove-or-change-policies"></a>如果我需要删除或更改策略，该怎么办？

资源可用于帮助您管理信息障碍策略。

- 如果信息障碍出现问题，请参阅 [故障排除信息障碍](information-barriers-troubleshooting.md)。

- 若要停止应用策略，请参阅 [停止策略应用程序](information-barriers-edit-segments-policies.md#stop-a-policy-application)。

- 若要删除信息屏障策略，请参阅 [删除策略](information-barriers-edit-segments-policies.md#remove-a-policy)。

- 若要对段落或策略进行更改，请参阅 [Edit (or remove) 信息屏障策略](information-barriers-edit-segments-policies.md)。

## <a name="example-contosos-departments-segments-and-policies"></a>示例： Contoso 的部门、分段和策略

若要了解组织如何采用定义段落和策略的方法，请考虑以下示例。

### <a name="contosos-departments-and-plan"></a>Contoso 的部门和规划

Contoso 有五个部门： HR、销售、营销、研究和制造。 为了保持与行业法规的兼容性，某些部门中的人员不应与其他部门通信，如下表所示：

|段落  |可以与  |无法对话  |
|---------|---------|---------|
|HR     |每个人         | (无限制)          |
|销售     |HR、营销、制造业         |信息检索         |
|营销     |每个人         | (无限制)          |
|信息检索     |HR、营销、制造业        |销售     |
|制造业 |HR、营销 |除 HR 或营销之外的任何人 |

考虑到这一点，Contoso 的计划包括三个信息屏障策略：

1. 旨在防止销售人员与研究 (和另一个策略进行通信以防止与销售) 进行信息检索的策略。
2. 旨在允许制造业仅与 HR 和营销进行通信的策略 

不需要为 HR 或营销定义策略。

### <a name="contosos-defined-segments"></a>Contoso 定义的段

Contoso 将使用 Azure Active Directory 中的 "部门" 属性来定义段，如下所示：

|Department  |段定义  |
|---------|---------|
|HR     | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"`        |
|销售     | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"`        |
|营销     | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"`        |
|信息检索     | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"`        |
|制造业     | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"`        |

定义段后，Contoso 将继续定义策略。 

### <a name="contosos-information-barrier-policies"></a>Contoso 的信息屏障策略

Contoso 定义了三种策略，如下表所述：

|Policy  |策略定义  |
|---------|---------|
|策略1：防止销售与信息检索通信     | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> 在此示例中，信息屏障策略称为 " *销售-研究*"。 当此策略处于活动状态且已应用时，它将有助于阻止销售部门中的用户与研究网段中的用户进行通信。 这是单向策略;它不会阻止研究与销售通信。 为此，需要策略2。      |
|策略2：防止与销售通信的研究     | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> 在此示例中，信息屏障策略称为 " *研究-销售*"。 当此策略处于活动状态且已应用时，它将有助于防止在研究网段中的用户与销售部门中的用户进行通信。       |
|策略3：允许制造业仅与 HR 和营销进行通信     | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p>在这种情况下，信息屏障策略称为 " *制造业-HRMarketing*"。 当此策略处于活动状态且已应用时，生产只能与 HR 和 Marketing 进行通信。 请注意，不限制 HR 和市场营销与其他段进行通信。 |

通过定义的段和策略，Contoso 通过运行 **InformationBarrierPoliciesApplication** cmdlet 来应用这些策略。 

完成后，Contoso 就符合法律和行业要求。

## <a name="related-articles"></a>相关文章

- [获取信息障碍概述](information-barriers.md)

- [Microsoft 团队中的信息障碍](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams)
