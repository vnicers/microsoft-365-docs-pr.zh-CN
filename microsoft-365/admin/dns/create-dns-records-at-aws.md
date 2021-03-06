---
title: 在 Amazon Web Services (AWS) for Microsoft 中创建 DNS 记录
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7a2efd75-0771-4897-ba7b-082fe5bfa9da
description: 了解如何验证您的域并为电子邮件、Skype for Business Online 和其他服务设置 (AWS) Microsoft 的 Web 服务的 DNS 记录。
ms.openlocfilehash: dbbf82c9c776108c4d5e34e2eb639f9c36e9f28b
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2020
ms.locfileid: "47307063"
---
# <a name="create-dns-records-at-amazon-web-services-aws-for-microsoft"></a>在 Amazon Web Services (AWS) for Microsoft 中创建 DNS 记录

 如果找不到要查找的内容，请**[查看域常见问题解答](../setup/domains-faq.md)**。 
  
如果 AWS 是您的 DNS 托管提供商，请按照本文中的步骤验证您的域并为电子邮件、Skype Online for Business 等设置 DNS 记录。
  
在 AWS 中添加这些记录后，您的域将设置为与 Microsoft 服务一起使用。
  

  
> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果在添加 DNS 记录后遇到邮件流问题或其他问题，请参阅[查找在添加域或 DNS 记录后遇到的问题并进行修复](../get-help-with-domains/find-and-fix-issues.md)。 
  
## <a name="add-a-txt-record-for-verification"></a>添加 TXT 记录进行验证
<a name="BKMK_verify"> </a>

在将域用于 Microsoft 之前，必须确保你拥有该域。如果你能够在域注册机构处登录到你的帐户并创建 DNS 记录，便可向 Microsoft 证明你是域所有者。
  
> [!NOTE]
> 此记录仅用于验证您是否拥有自己的域；它不会影响其他任何内容。 如果需要，您可以以后将其删除。 
  
1. 要开始，请使用[此链接](https://console.aws.amazon.com/route53/home)转到你在 AWS 上的域页面。 系统将会提示您先登录。
    
2. 在 " **资源** " 页上，选择 " **托管区域**"。
    
3. 在 " **托管区域** " 页上的 " **域名** " 列中，选择要编辑的域的名称。 
    
4. 选择 " **创建记录集**"。
    
5. In the **Create Record Set** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** and **Routing Policy** values from the drop-down lists.) 
    
    > [!TIP]
    > The quotation marks required by the onscreen instructions are supplied automatically. You don't need to type them manually. 
  
    |||||||
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |**名称** <br/> |**类型** <br/> |**别名** <br/> |**TTL（秒）** <br/> |**值** <br/> |**路由策略** <br/> |
    |(Leave this field empty.)  <br/> |TXT - Text  <br/> |否  <br/> |300  <br/> |MS=ms *XXXXXXXX*  <br/>**注意：** 这是一个示例。 在这里使用来自 Microsoft 365 中的表的具体“**目标地址或指向的地址**”值。 [如何查找此项？](../get-help-with-domains/information-for-dns-records.md)          |简单  <br/> |
   
6. 选择“创建”****。
    
7. 请在继续之前等待数分钟，以便您刚刚创建的记录可以通过 Internet 完成更新。
    
现在您已在域注册机构的网站上添加了记录，您将返回到 Microsoft 并请求搜索该记录。
  
Microsof 找到正确的 TXT 记录表明域已通过验证。
  
1. 在 Microsoft 管理中心，转到“**设置**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">域</a>”页面。

    
2. 在“**域**”页面上，选择要验证的域。 
    
3. 在“**设置**”页面上，选择“**开始设置**”。
    
4. 在“**验证域**”页面上，选择“**验证**”。
    
> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果在添加 DNS 记录后遇到邮件流问题或其他问题，请参阅[查找在添加域或 DNS 记录后遇到的问题并进行修复](../get-help-with-domains/find-and-fix-issues.md)。 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>添加 MX 记录，以便你的域的电子邮件将发送到 Microsoft 365
<a name="BKMK_add_MX"> </a>

1. 要开始，请使用[此链接](https://console.aws.amazon.com/route53/home)转到你在 AWS 上的域页面。 系统将会提示您先登录。
    
2. 在 " **资源** " 页上，选择 " **托管区域**"。
    
3. 在 " **托管区域** " 页上的 " **域名** " 列中，选择要编辑的域的名称。 
    
4. 选择 " **创建记录集**"。
    
5. In the **Create Record Set** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** and **Routing Policy** values from the drop-down lists.) 
    
    |**名称**|**类型**|**别名**|**TTL（秒）**|**值**|**路由策略**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |（将此字段留空。）  <br/> |MX - 邮件交换  <br/> |否  <br/> |300  <br/> |0  *\<domain-key\>*  .mail.protection.outlook.com.  <br/> 0 是 MX 优先级值。 将其添加到 MX 值的开头，使用一个空格将其与其余部分隔开。  <br/> **此值必须以句点 (.) 结尾。** <br/> **注意：**\<*domain-key*\>从 Microsoft 365 帐户获取。 [如何查找此内容？](../get-help-with-domains/information-for-dns-records.md)          |简单  <br/> |
       
    ![AWS-配置-2-1](../../media/94a71ce7-1b3b-4b1a-9ad3-9592db133075.png)
  
6. 选择“创建”****。
    
    ![AWS-BP-Configure-2-2](../../media/1c050c72-c04f-48d5-a8e9-44cd83ddd33e.png)
  
7. 如果有任何其他 MX 记录，请删除它们。
    
    > [!IMPORTANT]
    > AWS 将 MX 记录存储为可能包含多个记录的集合。 **请勿** 选择 " **删除记录集**"，因为这将删除所有 MX 记录，包括刚刚添加的记录。 请使用下面的说明。 
  
    首先，选择 MX 记录集。
    
    ![AWS-BP-Configure-2-3](../../media/9d9388cb-e2d0-43b7-928c-e1d07e519c6f.png)
  
    接下来，在" **编辑记录集**"区域中，通过选择" **值**"框中的条目并按键盘上的 **Delete** 键来删除每个已过时 MX 记录。 
    
    ![AWS-BP-Configure-2-4](../../media/c3b0c1bc-21ab-44cc-84b7-f504725c5540.png)
  
8. 选择 " **保存记录集**"。
    
    ![AWS-BP-Configure-2-5](../../media/86f0998d-f5d4-4750-a93d-ac13b318c40b.png)
  
## <a name="add-the-five-cname-records-that-are-required-for-microsoft-365"></a>添加 Microsoft 365 所需的五个 CNAME 记录
<a name="BKMK_add_CNAME"> </a>

1. 要开始，请使用[此链接](https://console.aws.amazon.com/route53/home)转到你在 AWS 上的域页面。 系统将会提示您先登录。
    
2. 在 " **资源** " 页上，选择 " **托管区域**"。
    
3. 在 " **托管区域** " 页上的 " **域名** " 列中，选择要编辑的域的名称。 
    
4. 选择 " **创建记录集**"。
    
5. 添加第一条 CNAME 记录。
    
    在" **创建记录集**"区域中新记录的框内，键入或复制并粘贴下表第一行中的值。 
    
    （从下拉列表中选择" **类型**"和" **路由策略**"值。） 
    
    |**名称**|**类型**|**别名**|**TTL（秒）**|**值**|**路由策略**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME - 规范名称  <br/> |否  <br/> |300  <br/> |autodiscover.outlook.com.  <br/> **此值必须以句点 (.) 结尾。** <br/> |简单  <br/> |
    |sip  <br/> |CNAME - 规范名称  <br/> |否  <br/> |300  <br/> |sipdir.online.lync.com.  <br/> **此值必须以句点 (.) 结尾。** <br/> |简单  <br/> |
    |lyncdiscover  <br/> |CNAME - 规范名称  <br/> |否  <br/> |300  <br/> |webdir.online.lync.com.  <br/> **此值必须以句点 (.) 结尾。** <br/> |简单  <br/> |
    |enterpriseregistration  <br/> |CNAME - 规范名称  <br/> |否  <br/> |300  <br/> |enterpriseregistration.windows.net.  <br/> **此值必须以句点 (.) 结尾。** <br/> |简单  <br/> |
    |EnterpriseEnrollment  <br/> |CNAME - 规范名称  <br/> |否  <br/> |300  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **此值必须以句点 (.) 结尾。** <br/> |简单  <br/> |
   
    ![AWS-配置-3-1](../../media/895c71bd-0e3a-425e-9681-98c1c67e714b.png)
  
6. 选择“创建”****。
    
    ![AWS-BP-Configure-3-2](../../media/33964846-5282-44a4-b241-62ce02b96735.png)
  
7. 添加其他 4 条 CNAME 记录。
    
    在 " **托管区域** " 页上，选择 " **创建记录集**"，使用表中下一行的值创建记录，然后再次选择 " **创建** " 以完成该记录。 
    
    重复此过程，直到创建完所有五个 CNAME 记录。
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>为 SPF 添加 TXT 记录以帮助防止垃圾邮件
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> 一个域所拥有的 SPF 的 TXT 记录不能超过一个。 如果域具有多个 SPF 记录，你将收到电子邮件错误，其中随附发送和垃圾邮件分类问题。 如果你的域已有 SPF 记录，请不要为 Microsoft 创建新记录。 改为将所需的 Microsoft 值添加到当前记录，以便您具有包含两组值的  *单个*  SPF 记录。 需要示例吗？ 请查看 [Microsoft 的外部域名系统记录](https://docs.microsoft.com/microsoft-365/enterprise/external-domain-name-system-records)。 若要验证您的 SPF 记录，您可以使用其中一种[SPF 验证工具](../setup/domains-faq.md)。 
  
1. 要开始，请使用[此链接](https://console.aws.amazon.com/route53/home)转到你在 AWS 上的域页面。 系统将会提示您先登录。
    
2. 在 " **资源** " 页上，选择 " **托管区域**"。
    
3. 在 " **托管区域** " 页上的 " **域名** " 列中，选择要编辑的域的名称。 
    
4. 选择 **TXT** 记录集。 
    
    ![AWS-BP-Configure-4-1](../../media/0310fa66-c016-4987-80df-930f1c8f3c39.png)
  
5. 在" **编辑记录集**"区域中，找到现有记录的" **值:**"框，在当前条目的末尾按 Enter 键（键盘上）创建新行；然后在该新行（现有值下方）上，键入或复制粘贴下表中的值。（可查看该表下方说明中的示例。） 
    
    |**值:**|
    |:-----|
    |v=spf1 include:outlook.com -all  <br/> （系统会自动提供屏幕说明所需的引号。无需手动键入。）  <br/> **注意：** 建议复制粘贴此条目，以保证正确保留所有空格。           |
   
    ![AWS-配置-4-2](../../media/beb3c086-eaf8-4245-9860-18512a3ff72e.png)
  
6. 选择 " **保存记录集**"。
    
    ![AWS-BP-Configure-4-3](../../media/94b9306c-bdc9-4f84-ad6f-6d12edbfde90.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft-365"></a>添加 Microsoft 365 所需的两条 SRV 记录
<a name="BKMK_add_SRV"> </a>

1. 要开始，请使用[此链接](https://console.aws.amazon.com/route53/home)转到你在 AWS 上的域页面。 系统将会提示您先登录。
    
2. 在 " **资源** " 页上，选择 " **托管区域**"。
    
3. 在 " **托管区域** " 页上的 " **域名** " 列中，选择要编辑的域的名称。 
    
4. 选择 " **创建记录集**"。
    
5. 添加第一条 SRV 记录：
    
    在" **创建记录集**"区域中新记录的框内，键入或复制并粘贴下表第一行中的值。 
    
    （从下拉列表中选择" **类型**"和" **路由策略**"值。） 
    
    |**名称**|**类型**|**别名**|**TTL（秒）**|**值**|**路由策略**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV - 服务定位器|否|300|100 1 443 sipdir.online.lync.com. **此值必须以句点 ( 结束。 ) **><br> **注意：** 建议复制粘贴此条目，以保证正确保留所有空格。           |简单|
    |_sipfederationtls._tcp|SRV - 服务定位器|否|300|100 1 5061 sipfed.online.lync.com. **此值必须以句点 (.) 结尾。**<br> **注意：** 建议复制粘贴此条目，以保证正确保留所有空格。           |简单|
   
    ![AWS-配置-5-1](../../media/c3f841d3-6076-428f-bb04-e71cc5f392fa.png)
  
6. 选择“创建”****。
    
    ![AWS-BP-Configure-5-2](../../media/1bf5dc58-a46b-47a5-bd69-7c2147dd4e50.png)
  
7. 添加其他 SRV 记录：
    
    在 " **托管区域** " 页上，选择 " **创建记录集**"，使用表中下一行的值创建记录，然后再次选择 " **创建** " 以完成该记录。 
    
> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果在添加 DNS 记录后遇到邮件流问题或其他问题，请参阅[查找在添加域或 DNS 记录后遇到的问题并进行修复](../get-help-with-domains/find-and-fix-issues.md)。 
  
