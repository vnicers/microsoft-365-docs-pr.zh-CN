---
title: 使用通信编辑器
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: 在设置内容格式时使用通信编辑器更改文本和合并字段变量。
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 0cb415da9aa09452176bd8aa9be4575cfc827582
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "44034474"
---
# <a name="use-the-communications-editor"></a>使用通信编辑器

在定义门户内容、法律保留通知和相关提醒/上报的内容时，可以利用通信编辑器格式化和动态自定义内容。

## <a name="rich-text-editor"></a>富文本编辑器 

通过通信编辑器，用户可以使用编辑器选项自定义文本。 例如，用户可以更改字体类型、创建项目符号列表、突出显示内容等。 

## <a name="merge-field-variables"></a>合并字段变量

您可以利用通信编辑器中的电子邮件合并变量将自定义的保管人属性嵌入到通信的正文文本中。 当发送给管理员时，将使用对应的字段填充合并域。 例如，当发送给保管人 John Smith 时，合并域 [保管人 Name] 将转换为相应的名称。 

您可以通过选择 "rtf" 文本编辑器控件顶部的 "**合并域**" 图标来使用电子邮件合并域。 将根据用户光标的位置添加占位符。 

### <a name="list-of-merge-field-variables"></a>合并域变量的列表

| 字段名                  | 字段详细信息 | 
| :------------------- | :------------------- |
| 显示名称  | 保管人的名字和姓氏。 | 
| 确认链接 | 记录每个保管人的确认的自定义链接。|                 |
| 门户链接     | 用于保管人合规性门户的自定义链接。|                |
| 签发专员                   | 指定的颁发专员的电子邮件地址。|                   |
| 签发日期                   | 通知发布的日期（UTC）。              |
