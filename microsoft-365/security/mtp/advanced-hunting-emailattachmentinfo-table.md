---
title: 高级搜寻架构中的 EmailAttachmentInfo 表
description: 在高级搜寻架构的 EmailAttachmentInfo 表中，了解电子邮件附件信息
keywords: 高级搜寻, 威胁搜寻, 网络威胁搜寻, 搜索, 查询, 遥测, 架构参考, kusto, 表格, 列, 数据类型, 说明, EmailAttachmentInfo, 网络邮件 id, 发件人, 收件人, 附件 id, 附件名称, 恶意软件裁定
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 9368185fff037b8c3c2f5b70a178f2485fda3736
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "40808717"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

**适用于：**
- Microsoft 威胁防护

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[高级搜寻](advanced-hunting-overview.md)架构中的 `EmailAttachmentInfo` 表包含有关由 Office 365 ATP 处理的电子邮件附件的信息。 使用此参考来构建从此表返回信息的查询。

有关高级搜寻架构中其他表的信息，请[参阅高级搜寻参考](advanced-hunting-schema-tables.md)。

| 列名称 | 数据类型 | 说明 |
|-------------|-----------|-------------|
| `Timestamp` | datetime | 记录事件的日期和时间 |
| `AttachmentId` | string | 唯一电子邮件附件标识符 |
| `NetworkMessageId` | string | 由 Office 365 生成的电子邮件的唯一标识符 |
| `SenderFromAddress` | string | 发件人标题中的发件人电子邮件地址（电子邮件收件人在其电子邮件客户端上可以看到） |
| `RecipientEmailAddress` | string | 收件人的电子邮件地址，或通讯组列表扩展后收件人的电子邮件地址 |
| `FileName` | string | 录制操作所应用到的文件的名称 |
| `FileType` | string | 文件扩展名类型 |
| `SHA256` | string | 录制操作所应用到的文件的 SHA-256。 通常不会填充此字段 — 可用时使用 SHA1 列。 |
| `MalwareFilterVerdict` | string | 电子邮件筛选堆栈关于电子邮件是否包含恶意软件的裁定：恶意软件，非恶意软件 |
| `MalwareDetectionMethod` | string | 用于检测电子邮件中的恶意软件的方法：反恶意软件引擎、文件信誉、ATP 安全附件 |

## <a name="related-topics"></a>相关主题
- [主动搜寻威胁](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [使用共享查询](advanced-hunting-shared-queries.md)
- [跨设备和电子邮件搜寻威胁](advanced-hunting-query-emails-devices.md)
- [了解架构](advanced-hunting-schema-tables.md)
- [应用查询最佳做法](advanced-hunting-best-practices.md)