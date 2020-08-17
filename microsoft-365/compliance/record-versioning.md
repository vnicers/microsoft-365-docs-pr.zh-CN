---
title: 使用记录版本控制来更新存储在 SharePoint 或 OneDrive 中的记录
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: 了解有关记录的信息，以便在 Microsoft 365 中实现记录管理解决方案。
ms.openlocfilehash: 943bf3949ab57eb4603695495d7a8ca0c4b90db7
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46695231"
---
# <a name="use-record-versioning-to-update-records-stored-in-sharepoint-or-onedrive"></a><span data-ttu-id="572db-103">使用记录版本控制来更新存储在 SharePoint 或 OneDrive 中的记录</span><span class="sxs-lookup"><span data-stu-id="572db-103">Use record versioning to update records stored in SharePoint or OneDrive</span></span>

><span data-ttu-id="572db-104">*[Microsoft 365 安全性与合规性许可指南](https://aka.ms/ComplianceSD)。*</span><span class="sxs-lookup"><span data-stu-id="572db-104">*[Microsoft 365 licensing guidance for security & compliance](https://aka.ms/ComplianceSD).*</span></span>

<span data-ttu-id="572db-105">能够将文档标记为[记录](records.md)并限制可对该记录执行的操作是任何记录管理解决方案的重要目标。</span><span class="sxs-lookup"><span data-stu-id="572db-105">The ability to mark a document as a [record](records.md) and restrict actions that can be performed on the record is an essential goal for any records management solution.</span></span> <span data-ttu-id="572db-106">但是，用户创建后续版本时也可能需要开展协作。</span><span class="sxs-lookup"><span data-stu-id="572db-106">However, collaboration might also be needed for people to create subsequent versions.</span></span>

<span data-ttu-id="572db-107">例如，你可以将销售合同标记为记录，但需要使用新条款更新合同，并将最新版本标记为新记录，同时保留先前的记录版本。</span><span class="sxs-lookup"><span data-stu-id="572db-107">For example, you might mark a sales contract as a record, but then need to update the contract with new terms and mark the latest version as a new record while still retaining the previous record version.</span></span> <span data-ttu-id="572db-108">对于这些类型的方案，SharePoint 和 OneDrive 现在支持*记录版本控制*。</span><span class="sxs-lookup"><span data-stu-id="572db-108">For these types of scenarios, SharePoint and OneDrive support *record versioning*.</span></span> <span data-ttu-id="572db-109">OneNote 笔记本文件夹不支持记录版本控制。</span><span class="sxs-lookup"><span data-stu-id="572db-109">OneNote notebook folders don't support record versioning.</span></span>

<span data-ttu-id="572db-110">若要使用记录版本控制，首先[标记文档并将其标记为记录](declare-records.md)。</span><span class="sxs-lookup"><span data-stu-id="572db-110">To use record versioning, you first [label the document and mark it as a record](declare-records.md).</span></span> <span data-ttu-id="572db-111">完成此操作后，名为“*记录状态*”的文档属性将显示在保留标签旁边，初始记录状态为“**已锁定**”。</span><span class="sxs-lookup"><span data-stu-id="572db-111">At this point, a document property, called *Record status* is displayed next to the retention label, and the initial record status is **Locked**.</span></span> 

<span data-ttu-id="572db-112">现在，可执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="572db-112">You can now do the following things:</span></span>

  - <span data-ttu-id="572db-113">**通过解锁和锁定记录状态属性，持续编辑文档的各个版本并将其保留为记录。**</span><span class="sxs-lookup"><span data-stu-id="572db-113">**Continually edit and retain individual versions of the document as records, by unlocking and locking the Record status property.**</span></span> <span data-ttu-id="572db-114">只有当“**记录状态**”属性设置为“**已锁定**”时，才会保留新版本的记录。</span><span class="sxs-lookup"><span data-stu-id="572db-114">Only when the **Record status** property is set to **Locked** is a new version of the record retained.</span></span> <span data-ttu-id="572db-115">在已锁定和已解锁之间切换可降低保留不必要的文档版本和副本的风险。</span><span class="sxs-lookup"><span data-stu-id="572db-115">This toggle of locked and unlocked reduces the risk of retaining unnecessary versions and copies of the document.</span></span>

  - <span data-ttu-id="572db-116">**将文档自动保存在位于网站集内的本地记录存储库中。**</span><span class="sxs-lookup"><span data-stu-id="572db-116">**Have the records automatically stored in an in-place records repository located within the site collection.**</span></span> <span data-ttu-id="572db-117">SharePoint 和 OneDrive 中的每个网站集将内容保存在其保留库中。</span><span class="sxs-lookup"><span data-stu-id="572db-117">Each site collection in SharePoint and OneDrive preserves content in its Preservation Hold library.</span></span> <span data-ttu-id="572db-118">记录版本保存在此库中的“记录”文件夹内。</span><span class="sxs-lookup"><span data-stu-id="572db-118">Record versions are stored in the Records folder in this library.</span></span>

  - <span data-ttu-id="572db-119">**保存包含所有版本的始终更新的文档。**</span><span class="sxs-lookup"><span data-stu-id="572db-119">**Maintain an evergreen document that contains all versions.**</span></span> <span data-ttu-id="572db-120">默认情况下，每个 SharePoint 和 OneDrive 文档的项菜单上都有可用的版本历史记录。</span><span class="sxs-lookup"><span data-stu-id="572db-120">By default, each SharePoint and OneDrive document has a version history available on the item menu.</span></span> <span data-ttu-id="572db-121">在此版本历史记录中，你可以轻松查看哪些版本是记录并查看这些文档。</span><span class="sxs-lookup"><span data-stu-id="572db-121">In this version history, you can easily see which versions are records and view those documents.</span></span>

<span data-ttu-id="572db-122">对于具有将项标记为记录的保留标签的任何文档，记录版本控制自动可用。</span><span class="sxs-lookup"><span data-stu-id="572db-122">Record versioning is automatically available for any document that has a retention label that marks the item as a record.</span></span> <span data-ttu-id="572db-123">当用户使用详细信息窗格查看文档属性时，可以将“**记录状态**”从“**已锁定**”切换为“**已解锁**”。</span><span class="sxs-lookup"><span data-stu-id="572db-123">When a user views the document properties by using the details pane, they can toggle the **Record status** from **Locked** to **Unlocked**.</span></span> <span data-ttu-id="572db-124">执行此操作即可在保留库的“记录”文件夹中创建一个记录，该记录将在其中保存剩余的保留期。</span><span class="sxs-lookup"><span data-stu-id="572db-124">This action creates a record in the Records folder in the Preservation Hold library, where it resides for the remainder of its retention period.</span></span> 

<span data-ttu-id="572db-125">当文档处于已解锁状态时，拥有标准编辑权限的任何用户均可编辑此文件。</span><span class="sxs-lookup"><span data-stu-id="572db-125">While the document is unlocked, any user with standard edit permissions can edit the file.</span></span> <span data-ttu-id="572db-126">但是，用户无法编辑此文件，因为它仍然是记录。</span><span class="sxs-lookup"><span data-stu-id="572db-126">However, users can't delete the file, because it's still a record.</span></span> <span data-ttu-id="572db-127">完成编辑后，用户可再次将“**记录状态**”从“**已解锁**”切换回“**已锁定**”，此状态下可阻止用户进一步编辑该记录。</span><span class="sxs-lookup"><span data-stu-id="572db-127">When editing is complete, a  user can then toggle the **Record status** from **Unlocked** to **Locked**, which prevents further edits while in this status.</span></span>
<br/><br/>

![标记为记录的文档上的记录状态属性](../media/recordversioning8.png)

## <a name="locking-and-unlocking-a-record"></a><span data-ttu-id="572db-129">锁定和解锁记录</span><span class="sxs-lookup"><span data-stu-id="572db-129">Locking and unlocking a record</span></span>

<span data-ttu-id="572db-130">在向文档应用将内容标记为记录的保留标签后，任何拥有参与权限或更窄权限水平的用户可解锁记录或锁定未解锁的记录。</span><span class="sxs-lookup"><span data-stu-id="572db-130">After a retention label that marks content as a record is applied to a document, any user with Contribute permissions or a narrower permission level can unlock a record or lock an unlocked record.</span></span>
<br/><br/>

![记录状态显示记录文档已解锁](../media/recordversioning9.png)

<span data-ttu-id="572db-132">当用户解锁记录时，将会发生以下操作：</span><span class="sxs-lookup"><span data-stu-id="572db-132">When a user unlocks a record, the following actions occur:</span></span>

1. <span data-ttu-id="572db-133">如果当前网站集没有保留库，将会创建一个。</span><span class="sxs-lookup"><span data-stu-id="572db-133">If the current site collection doesn't have a Preservation Hold library, one is created.</span></span>

2. <span data-ttu-id="572db-134">如果保留库没有“记录”文件夹，将会创建一个。</span><span class="sxs-lookup"><span data-stu-id="572db-134">If the Preservation Hold library doesn't have a Records folder, one is created.</span></span>

3. <span data-ttu-id="572db-135">“复制到”\*\*\*\* 操作会将文档的最新版本复制到“记录”文件夹。</span><span class="sxs-lookup"><span data-stu-id="572db-135">A **Copy to** action copies the latest version of the document to the Records folder.</span></span> <span data-ttu-id="572db-136">“复制到”\*\*\*\* 操作仅包含最新版本，不包含先前版本。</span><span class="sxs-lookup"><span data-stu-id="572db-136">The **Copy to** action includes only the latest version and no prior versions.</span></span> <span data-ttu-id="572db-137">此复制的文档现在被视为文档的记录版本，其文件名格式为：\[标题 GUID 版本\#\]</span><span class="sxs-lookup"><span data-stu-id="572db-137">This copied document is now considered a record version of the document, and its file name has the format: \[Title GUID Version\#\]</span></span>

4. <span data-ttu-id="572db-138">在“记录”文件夹中创建的副本已添加到原始文档的版本历史记录中，此版本将在注释字段中显示“**记录**”一词。</span><span class="sxs-lookup"><span data-stu-id="572db-138">The copy created in the Records folder is added to the version history of the original document, and this version shows the word **Record** in the comments field.</span></span>

5. <span data-ttu-id="572db-139">原始文档现已成为可编辑但不可删除的新版本。</span><span class="sxs-lookup"><span data-stu-id="572db-139">The original document is a new version that can be edited, but not deleted.</span></span> <span data-ttu-id="572db-140">文档库列“**项为记录**”仍显示“**是**”值，因为文档仍是记录，即使它现在可以编辑。</span><span class="sxs-lookup"><span data-stu-id="572db-140">The document library column **Item is a Record** still shows the **Yes** value because the document is still a record, even if it can now be edited.</span></span>

<span data-ttu-id="572db-141">当用户锁定记录时，原始文档同样无法编辑。</span><span class="sxs-lookup"><span data-stu-id="572db-141">When a user locks a record, the original document again can't be edited.</span></span> <span data-ttu-id="572db-142">但是，是解锁记录的操作将版本复制到保留库中的“记录”文件夹。</span><span class="sxs-lookup"><span data-stu-id="572db-142">But it is the action of unlocking a record that copies a version to the Records folder in the Preservation Hold library.</span></span>

## <a name="record-versions"></a><span data-ttu-id="572db-143">记录版本</span><span class="sxs-lookup"><span data-stu-id="572db-143">Record versions</span></span>

<span data-ttu-id="572db-144">每次用户解锁记录时，都会将最新版本复制到保留库的“记录”文件夹中，该版本在版本历史记录的“注释”\*\*\*\* 字段中的值为“记录”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="572db-144">Each time a user unlocks a record, the latest version is copied to the Records folder in the Preservation Hold library, and that version contains the value of **Record** in the **Comments** field of the version history.</span></span>
<br/><br/>

![保留库中显示的记录](../media/recordversioning10.png)

<span data-ttu-id="572db-146">要查看版本历史记录，请在文档库中选择一个文档，然后在项菜单中单击“版本历史记录”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="572db-146">To view the version history, select a document in the document library and then click **Version history** in the item menu.</span></span>

## <a name="where-records-are-stored"></a><span data-ttu-id="572db-147">存储记录的位置。</span><span class="sxs-lookup"><span data-stu-id="572db-147">Where records are stored</span></span>

<span data-ttu-id="572db-148">记录保存在网站集顶层站点的保留库内的“记录”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="572db-148">Records are stored in the Records folder in the Preservation Hold library in the top-level site in the site collection.</span></span> <span data-ttu-id="572db-149">在顶层站点的左侧导航中，选择“**网站内容**\>**”，“保留库”**。</span><span class="sxs-lookup"><span data-stu-id="572db-149">In the left navigation on the top-level site, choose **Site contents** \> **Preservation Hold Library**.</span></span>
<br/><br/>

![保留库](../media/recordversioning11.png)

<br/><br/>

![保留库中的“记录”文件夹](../media/recordversioning12.png)

<span data-ttu-id="572db-152">保留库仅对网站集管理员可见。</span><span class="sxs-lookup"><span data-stu-id="572db-152">The Preservation Hold library is visible only to site collection admins.</span></span> <span data-ttu-id="572db-153">此外，默认情况下保留库不存在。</span><span class="sxs-lookup"><span data-stu-id="572db-153">Also, the Preservation Hold library doesn't exist by default.</span></span> <span data-ttu-id="572db-154">仅当受保存标签影响的内容在网站集中第一次删除时才会创建。</span><span class="sxs-lookup"><span data-stu-id="572db-154">It's created only when content subject to a retention label or retention policy is deleted for the first time in the site collection.</span></span>

## <a name="searching-the-audit-log-for-record-versioning-events"></a><span data-ttu-id="572db-155">搜索记录版本控制事件的审核日志</span><span class="sxs-lookup"><span data-stu-id="572db-155">Searching the audit log for record versioning events</span></span>

<span data-ttu-id="572db-156">锁定和解锁记录的操作会记录在审核日志中。</span><span class="sxs-lookup"><span data-stu-id="572db-156">The actions of locking and unlocking records are logged in the audit log.</span></span> <span data-ttu-id="572db-157">你可以搜索特定活动“将记录状态更改为已锁定”\*\*\*\* 和“将记录状态更改为已解锁”\*\*\*\*，这些活动位于安全与合规性中心“审核日志搜索”\*\*\*\* 页面“活动”\*\*\*\* 下拉列表中的“文件和页面活动”\*\*\*\* 部分。</span><span class="sxs-lookup"><span data-stu-id="572db-157">You can search for the specific activities **Changed record status to locked** and **Changed record status to unlocked**, which are located in the **File and page activities** section in the **Activities** dropdown list on the **Audit log search** page in the security and compliance center.</span></span>
<br/><br/>

![在审核日志中搜索记录版本控制事件](../media/recordversioning13.png)

<span data-ttu-id="572db-159">有关搜索这些事件的详细信息，请参阅[在安全与合规性中心中搜索审核日志](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities)的“文件和页面活动”部分。</span><span class="sxs-lookup"><span data-stu-id="572db-159">For more information about searching for these events, see the "File and page activities" section in [Search the audit log in the Security & Compliance Center](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).</span></span>

## <a name="next-steps"></a><span data-ttu-id="572db-160">后续步骤</span><span class="sxs-lookup"><span data-stu-id="572db-160">Next steps</span></span>

<span data-ttu-id="572db-161">若要将内容标记为记录，请参阅[使用保留标签声明记录](declare-records.md)。</span><span class="sxs-lookup"><span data-stu-id="572db-161">To mark content as a record, see [Declare records by using retention labels](declare-records.md).</span></span>

<span data-ttu-id="572db-162">若要了解有关记录的处置，请参阅[处置内容](disposition.md)。</span><span class="sxs-lookup"><span data-stu-id="572db-162">To learn about disposition of records, see [Disposing of content](disposition.md).</span></span>