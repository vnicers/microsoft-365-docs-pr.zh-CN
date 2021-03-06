---
title: Skype、OneDrive、SharePoint 和 Exchange 的加密
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
- SPO_Content
description: 摘要：对 Skype、OneDrive、SharePoint、Microsoft 团队和 Exchange Online 加密的说明。
ms.openlocfilehash: fc369d167d5aa35507f9509fc1b92294e16f75d9
ms.sourcegitcommit: f80c6c52e5b08290f74baec1d64c4070046c32e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "44717333"
---
# <a name="encryption-for-skype-for-business-onedrive-for-business-sharepoint-online-microsoft-teams-and-exchange-online"></a>Skype for business、OneDrive for Business、SharePoint Online、Microsoft 团队和 Exchange Online 加密

Microsoft 365 是一个高度安全的环境，可在多个层中提供广泛保护：物理数据中心安全性、网络安全性、访问安全性、应用程序安全性和数据安全性。

## <a name="skype-for-business"></a>Skype for Business

Skype for Business 客户数据可能以会议参与者上载的文件或演示文稿形式存储在 rest 上。 Web 会议服务器使用具有256位密钥的 AES 对客户数据进行加密。 加密的客户数据存储在文件共享上。 每个客户数据都使用不同的随机生成的256位密钥进行加密。 当在会议中共享一段客户数据时，Web 会议服务器会指示会议客户端通过 HTTPS 下载加密的客户数据。 它将对应的密钥发送给客户端，以便可以对客户数据进行解密。 在允许客户端访问会议客户数据之前，Web 会议服务器还会对会议客户端进行身份验证。 加入 Web 会议时，每个会议客户端将首先建立 SIP 对话框，通过 TLS 在前端服务器中运行会议焦点组件。 会议焦点将由 Web 会议服务器生成的身份验证 cookie 传递给会议客户端。 然后，会议客户端将连接到 Web 会议服务器，以呈现由服务器进行身份验证的身份验证 cookie。

## <a name="sharepoint-online-and-onedrive-for-business"></a>SharePoint Online 和 OneDrive for Business

SharePoint Online 中的所有客户文件均受唯一的、每个文件的密钥保护，这些密钥对于单个租户始终是独占的。 这些密钥是由 SharePoint Online 服务创建和管理的，或者是在使用客户密钥时，由客户创建和管理。 上载文件时，SharePoint Online 将在上载请求的上下文中执行加密，然后再将其发送到 Azure 存储。 下载文件时，SharePoint Online 将根据唯一的文档标识符从 Azure 存储中检索加密的客户数据，并在将客户数据发送给用户之前对其进行解密。 Azure 存储不能解密，甚至无法识别或理解客户数据。 所有加密和解密在强制实施租户隔离的系统中发生，即 Azure Active Directory 和 SharePoint Online。

Microsoft 365 中的几个工作负载存储在 SharePoint Online 中，其中包括 Microsoft 团队，其中存储了 SharePoint Online 中的所有文件和 OneDrive for Business，后者使用 SharePoint Online 存储其存储。 存储在 SharePoint Online 中的所有客户数据都经过加密（包含一个或多个 AES 256 位密钥），并分布在整个数据中心中，如下所示。 （此加密过程的每个步骤都是验证了 FIPS 140-2 级别2。 有关 FIPS 140-2 合规性的详细信息，请参阅[FIPS 140-2 合规性](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb326611(v=sql.105))。

- 根据文件大小，将每个文件拆分为一个或多个块。 每个区块都使用其自己唯一的 AES 256 位密钥进行加密。
- 更新文件时，将以相同的方式处理更新：将更改拆分为一个或多个块，并使用单独的唯一键对每个区块进行加密。
- 这些区块–文件、文件碎片和更新增量–存储为 Azure 存储中随机分布在多个 Azure 存储帐户中的 blob。
- 这些客户数据块的加密密钥集本身是加密的。

    - 用于加密 blob 的密钥存储在 SharePoint Online 内容数据库中。
    - 内容数据库受数据库访问控制和静态加密的保护。 使用[AZURE SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)中的[透明数据加密](https://docs.microsoft.com/sql/relational-databases/security/encryption/transparent-data-encryption-tde)（TDE）执行加密。 （Azure SQL Database 是 Microsoft Azure 中的常规用途关系数据库服务，它支持关系数据、JSON、空间和 XML 等结构。这些机密是 SharePoint Online 的服务级别，而不是租户级别。 这些机密（有时称为主密钥）存储在单独的安全存储库中，称为 "密钥存储区"。 TDE 为活动数据库和数据库备份和事务日志提供了 rest 的安全性。
    - 当客户提供可选密钥时，客户密钥存储在 Azure Key Vault 中，服务使用密钥来加密租户密钥，该密钥用于加密网站密钥，然后使用它来加密文件级密钥。 实质上，当客户提供密钥时，会引入新的密钥层次结构。
- 用于重新装配文件的映射与加密密钥一起存储在内容数据库中，并与解密时所需的主密钥分开。
- 每个 Azure 存储帐户都有其自己的每个访问类型的唯一凭据（读取、写入、枚举和删除）。 每组凭据都存放在安全的密钥存储中，并定期刷新。 如上所述，有三种不同类型的存储，每种类型都有不同的功能：
    - 在 Azure 存储中，客户数据存储为加密的 blob。 每个客户数据块的键都会被加密并单独存储在内容数据库中。 客户数据本身不包含有关如何对其进行解密的任何线索。
    - "内容数据库"是一个 SQL Server 数据库。 它包含查找和重新组装存储在 Azure 存储中的客户数据 blob 所需的映射，以及加密这些 blob 所需的密钥。 但是，键集本身是加密的（如上所述），并保存在单独的密钥存储中。
    - 密钥存储区在物理上独立于内容数据库和 Azure 存储。 它将每个 Azure 存储容器的凭据和主密钥保存到内容数据库中保留的加密密钥集。

这三个存储组件（Azure blob 存储、内容数据库和密钥存储）中的每一个都在物理上是独立的。 保留在其中任一个组件中的信息在其自身上都不可用。 如果没有访问所有三项，则无法将密钥检索到块中，对密钥进行解密以使其可用，将密钥与相应的区块相关联，对每个区块进行解密，或从其构成块中重新构造文档。

保护数据中心中的计算机上的物理磁盘卷的 BitLocker 证书存储在受服务器场密钥保护的安全存储库（SharePoint Online 密钥存储）中。

保护每个 blob 密钥的 TDE 项存储在两个位置：

- 用于承载 BitLocker 证书并受服务器场密钥保护的安全存储库;并
- 在由 Azure SQL 数据库管理的安全存储库中。

用于访问 Azure 存储容器的凭据也保留在 SharePoint Online 密钥存储中，并根据需要委派给每个 SharePoint Online 场。 这些凭据是 Azure 存储 SAS 签名，使用单独的凭据读取或写入数据，并应用策略，以便它们每60天自动过期。 使用不同的凭据来读取或写入数据（而不是同时读取或写入），并且不会向 SharePoint Online 场授予枚举权限。

> [!NOTE]
> 对于 Office 365 美国政府版客户，数据 blob 存储在 Azure 美国政府存储中。 此外，Office 365 美国政府版中对 SharePoint Online 密钥的访问权限仅限于专门筛选过的 Office 365 员工。 Azure 美国政府运营人员无法访问用于加密数据 blob 的 SharePoint Online 密钥存储。

有关 SharePoint Online 和 OneDrive for Business 中的数据加密的详细信息，请参阅[OneDrive For business 和 SharePoint Online 中的数据加密](https://technet.microsoft.com/library/dn905447.aspx)。

### <a name="list-items-in-sharepoint-online"></a>SharePoint Online 中的列表项

列表项是较小的用户数据块，可在网站中进行临时（如用户创建的列表中的行、SharePoint Online 博客中的各个帖子或 SharePoint Online wiki 页面中的条目）而创建。 列表项存储在内容数据库（Azure SQL 数据库）中，并受 TDE 保护。

## <a name="encryption-of-data-in-transit"></a>中转数据的加密

在 OneDrive for Business 和 SharePoint Online 中，有两种数据进入和退出数据中心的方案。

- **通过 Internet 与服务器通信的客户端与**SharePoint Online 和 OneDrive for business 之间的通信使用 TLS 连接。
- **数据中心之间的数据移动**-在数据中心之间移动数据的主要原因是为了实现灾难恢复。 例如，SQL Server 事务日志和 blob 存储增量沿着此管道传输。 虽然已使用专用网络传输此数据，但还将进一步使用一流加密技术来保护此数据。

## <a name="exchange-online"></a>Exchange Online

Exchange Online 对所有邮箱数据使用 BitLocker，并且 bitlocker 配置在[bitlocker 中对加密](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)进行了描述。 服务级别加密对邮箱级别的所有邮箱数据进行加密。 

除了服务加密之外，Microsoft 365 还支持客户密钥，这是基于服务加密的基础构建的。 "客户密钥" 是 Exchange Online 服务加密的 Microsoft 托管密钥选项，也在 Microsoft 的路线图中。 此加密方法提供了 BitLocker 不提供的增强保护，因为它提供了服务器管理员的分离和解密数据所需的加密密钥，并且，由于加密直接应用于数据（与 BitLocker 在逻辑磁盘卷上应用加密），因此从 Exchange 服务器复制的任何客户数据仍保持加密。

Exchange Online 服务加密的作用域是 Exchange Online 中存储在 rest 上的客户数据。 （Skype for Business 存储几乎在用户的 Exchange Online 邮箱中的所有用户生成的内容，因此继承了 Exchange Online 的服务加密功能。）


## <a name="microsoft-teams"></a>Microsoft Teams

团队使用 TLS 和 MTLS 对即时消息进行加密。 所有服务器到服务器的通信都需要 MTLS，无论流量是限制到内部网络还是跨越内部网络外围。

此表汇总了团队使用的协议。

***流量加密***

|||
|:-----|:-----|
|**通信类型**|**加密者**|
|服务器到服务器|MTLS|
|客户端到服务器（ex 即时消息和状态）|TLS|
|媒体流（ex） 媒体的音频和视频共享）|TLS|
|媒体的音频和视频共享|SRTP/TLS|
|信号|TLS|
|||

#### <a name="media-encryption"></a>媒体加密

媒体通信是使用安全 RTP (SRTP) 进行加密的，SRTP 是为 RTP 通信提供保密性、身份验证和重播攻击保护的实时传输协议 (RTP) 的配置文件。 SRTP 使用使用安全随机数生成器生成的会话密钥，并使用信号 TLS 通道进行交换。 客户端到客户端媒体流量通过客户端到服务器连接信号进行协商，但在客户端到客户端直接转时使用 SRTP 进行了加密。

团队使用基于凭据的令牌，通过转而对媒体中继进行安全访问。 媒体中继通过 TLS 安全通道交换令牌。

#### <a name="fips"></a>FIPS

团队对加密密钥交换使用 FIPS （联邦信息处理标准）兼容的算法。 有关实现 FIPS 的详细信息，请参阅[联邦信息处理标准（FIPS）发布 140-2](https://docs.microsoft.com/microsoft-365/compliance/offering-fips-140-2?view=o365-worldwide)。
