---
uid: web-forms/overview/data-access/custom-formatting/using-the-formview-s-templates-vb
title: "使用在 FormView 的範本 (VB) |Microsoft 文件"
author: rick-anderson
description: "不同於在 DetailsView 中，欄位不被由 FormView。 相反地，在 FormView 呈現使用範本。 在本教學課程中，我們將檢驗使用 F..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 03/31/2010
ms.topic: article
ms.assetid: 67b25f4c-2823-42b6-b07d-1d650b3fd711
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/data-access/custom-formatting/using-the-formview-s-templates-vb
msc.type: authoredcontent
ms.openlocfilehash: 05e97ce5efeaf72192ed294b946e2249c60007d1
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2017
---
<a name="using-the-formviews-templates-vb"></a><span data-ttu-id="ef3d1-105">使用在 FormView 的範本 (VB)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-105">Using the FormView's Templates (VB)</span></span>
====================
<span data-ttu-id="ef3d1-106">由[Scott Mitchell](https://twitter.com/ScottOnWriting)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-106">by [Scott Mitchell](https://twitter.com/ScottOnWriting)</span></span>

<span data-ttu-id="ef3d1-107">[下載範例應用程式](http://download.microsoft.com/download/5/7/0/57084608-dfb3-4781-991c-407d086e2adc/ASPNET_Data_Tutorial_14_VB.exe)或[下載 PDF](using-the-formview-s-templates-vb/_static/datatutorial14vb1.pdf)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-107">[Download Sample App](http://download.microsoft.com/download/5/7/0/57084608-dfb3-4781-991c-407d086e2adc/ASPNET_Data_Tutorial_14_VB.exe) or [Download PDF](using-the-formview-s-templates-vb/_static/datatutorial14vb1.pdf)</span></span>

> <span data-ttu-id="ef3d1-108">不同於在 DetailsView 中，欄位不被由 FormView。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-108">Unlike the DetailsView, the FormView is not composed of fields.</span></span> <span data-ttu-id="ef3d1-109">相反地，在 FormView 呈現使用範本。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-109">Instead, the FormView is rendered using templates.</span></span> <span data-ttu-id="ef3d1-110">在此教學課程中我們將檢驗使用 FormView 控制項呈現資料的較不顯示。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-110">In this tutorial we'll examine using the FormView control to present a less rigid display of data.</span></span>


## <a name="introduction"></a><span data-ttu-id="ef3d1-111">簡介</span><span class="sxs-lookup"><span data-stu-id="ef3d1-111">Introduction</span></span>

<span data-ttu-id="ef3d1-112">最後兩個教學課程中我們可了解如何自訂使用 TemplateFields GridView 和 DetailsView 控制項的輸出。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-112">In the last two tutorials we saw how to customize the GridView and DetailsView controls' outputs using TemplateFields.</span></span> <span data-ttu-id="ef3d1-113">TemplateFields 允許可高度自訂的特定欄位的內容，但最後 GridView 和 DetailsView 都有而 boxy、 類似格線的外觀。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-113">TemplateFields allow for the contents for a specific field to be highly customized, but in the end both the GridView and DetailsView have a rather boxy, grid-like appearance.</span></span> <span data-ttu-id="ef3d1-114">許多情況下這類類似格線版面配置是理想的做法，但有時候需要更流暢、 較不嚴謹的顯示。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-114">For many scenarios such a grid-like layout is ideal, but at times a more fluid, less rigid display is needed.</span></span> <span data-ttu-id="ef3d1-115">顯示單一記錄，這類流暢的版面配置時，可能使用 FormView 控制項。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-115">When displaying a single record, such a fluid layout is possible using the FormView control.</span></span>

<span data-ttu-id="ef3d1-116">不同於在 DetailsView 中，欄位不被由 FormView。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-116">Unlike the DetailsView, the FormView is not composed of fields.</span></span> <span data-ttu-id="ef3d1-117">您無法加入 BoundField 或 TemplateField FormView。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-117">You can't add a BoundField or TemplateField to a FormView.</span></span> <span data-ttu-id="ef3d1-118">相反地，在 FormView 呈現使用範本。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-118">Instead, the FormView is rendered using templates.</span></span> <span data-ttu-id="ef3d1-119">在 FormView 視為包含單一 TemplateField DetailsView 控制項。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-119">Think of the FormView as a DetailsView control that contains a single TemplateField.</span></span> <span data-ttu-id="ef3d1-120">在 FormView 支援下列範本：</span><span class="sxs-lookup"><span data-stu-id="ef3d1-120">The FormView supports the following templates:</span></span>

- <span data-ttu-id="ef3d1-121">`ItemTemplate`用來呈現特定 FormView 中顯示的資料錄</span><span class="sxs-lookup"><span data-stu-id="ef3d1-121">`ItemTemplate` used to render the particular record displayed in the FormView</span></span>
- <span data-ttu-id="ef3d1-122">`HeaderTemplate`用來指定選擇性標頭資料列</span><span class="sxs-lookup"><span data-stu-id="ef3d1-122">`HeaderTemplate` used to specify an optional header row</span></span>
- <span data-ttu-id="ef3d1-123">`FooterTemplate`用來指定選擇性頁尾資料列</span><span class="sxs-lookup"><span data-stu-id="ef3d1-123">`FooterTemplate` used to specify an optional footer row</span></span>
- <span data-ttu-id="ef3d1-124">`EmptyDataTemplate`當在 FormView 的`DataSource`缺少任何記錄，`EmptyDataTemplate`用來取代`ItemTemplate`呈現控制項的標記</span><span class="sxs-lookup"><span data-stu-id="ef3d1-124">`EmptyDataTemplate` when the FormView's `DataSource` lacks any records, the `EmptyDataTemplate` is used in place of the `ItemTemplate` for rendering the control's markup</span></span>
- <span data-ttu-id="ef3d1-125">`PagerTemplate`可用來啟用分頁的 FormViews 自訂分頁介面</span><span class="sxs-lookup"><span data-stu-id="ef3d1-125">`PagerTemplate` can be used to customize the paging interface for FormViews that have paging enabled</span></span>
- <span data-ttu-id="ef3d1-126">`EditItemTemplate` / `InsertItemTemplate`用來支援這類功能的 FormViews 自訂編輯介面或插入介面</span><span class="sxs-lookup"><span data-stu-id="ef3d1-126">`EditItemTemplate` / `InsertItemTemplate` used to customize the editing interface or inserting interface for FormViews that support such functionality</span></span>

<span data-ttu-id="ef3d1-127">在此教學課程中我們將檢驗使用 FormView 控制項來顯示產品的較不顯示。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-127">In this tutorial we'll examine using the FormView control to present a less rigid display of products.</span></span> <span data-ttu-id="ef3d1-128">而不是欄位名稱、 類別、 供應商和等等，在 FormView 的`ItemTemplate`會顯示這些值使用的標頭項目組合和`<table>`（請參閱圖 1）。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-128">Rather than having fields for the name, category, supplier, and so on, the FormView's `ItemTemplate` will show these values using a combination of a header element and a `<table>` (see Figure 1).</span></span>


<span data-ttu-id="ef3d1-129">[![在 FormView 中斷的 DetailsView 中看到的類似格線版面配置](using-the-formview-s-templates-vb/_static/image2.png)](using-the-formview-s-templates-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-129">[![The FormView Breaks Out of the Grid-Like Layout Seen in the DetailsView](using-the-formview-s-templates-vb/_static/image2.png)](using-the-formview-s-templates-vb/_static/image1.png)</span></span>

<span data-ttu-id="ef3d1-130">**圖 1**: FormView 超出 Grid-Like 配置看到中斷 DetailsView 中 ([按一下以檢視完整大小的影像](using-the-formview-s-templates-vb/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="ef3d1-130">**Figure 1**: The FormView Breaks Out of the Grid-Like Layout Seen in the DetailsView ([Click to view full-size image](using-the-formview-s-templates-vb/_static/image3.png))</span></span>


## <a name="step-1-binding-the-data-to-the-formview"></a><span data-ttu-id="ef3d1-131">資料繫結至 FormView 步驟 1:</span><span class="sxs-lookup"><span data-stu-id="ef3d1-131">Step 1: Binding the Data to the FormView</span></span>

<span data-ttu-id="ef3d1-132">開啟`FormView.aspx`頁面上，並從 [工具箱] 拖曳至設計工具拖曳 FormView。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-132">Open the `FormView.aspx` page and drag a FormView from the Toolbox onto the Designer.</span></span> <span data-ttu-id="ef3d1-133">第一次加入 FormView 時它會顯示為灰色方塊，指示我們的`ItemTemplate`需要。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-133">When first adding the FormView it appears as a gray box, instructing us that an `ItemTemplate` is needed.</span></span>


<span data-ttu-id="ef3d1-134">[![在 FormView 無法轉譯設計工具中，直到提供 ItemTemplate 為止](using-the-formview-s-templates-vb/_static/image5.png)](using-the-formview-s-templates-vb/_static/image4.png)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-134">[![The FormView Cannot be Rendered in the Designer Until an ItemTemplate is Provided](using-the-formview-s-templates-vb/_static/image5.png)](using-the-formview-s-templates-vb/_static/image4.png)</span></span>

<span data-ttu-id="ef3d1-135">**圖 2**: FormView 無法轉譯設計工具之前`ItemTemplate`提供 ([按一下以檢視完整大小的影像](using-the-formview-s-templates-vb/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="ef3d1-135">**Figure 2**: The FormView Cannot be Rendered in the Designer Until an `ItemTemplate` is Provided ([Click to view full-size image](using-the-formview-s-templates-vb/_static/image6.png))</span></span>


<span data-ttu-id="ef3d1-136">`ItemTemplate`可以 （透過宣告式語法中） 以手動方式建立，或者可以透過繫結至資料來源控制項，透過設計工具的 FormView 是自動建立。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-136">The `ItemTemplate` can be created by hand (through the declarative syntax) or can be auto-created by binding the FormView to a data source control through the Designer.</span></span> <span data-ttu-id="ef3d1-137">這會自動建立`ItemTemplate`包含，列出每個欄位名稱和標籤控制項的 HTML`Text`屬性繫結至欄位的值。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-137">This auto-created `ItemTemplate` contains HTML that lists the name of each field and a Label control whose `Text` property is bound to the field's value.</span></span> <span data-ttu-id="ef3d1-138">這個方法也自動-建立`InsertItemTemplate`和`EditItemTemplate`，這兩種會針對每個資料來源控制項所傳回的資料欄位填入具有輸入控制項。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-138">This approach also auto-creates an `InsertItemTemplate` and `EditItemTemplate`, both of which are populated with input controls for each of the data fields returned by the data source control.</span></span>

<span data-ttu-id="ef3d1-139">如果您想要自動建立範本，從在 FormView 的智慧標籤新增 ObjectDataSource 控制項叫用`ProductsBLL`類別的`GetProducts()`方法。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-139">If you want to auto-create the template, from the FormView's smart tag add a new ObjectDataSource control that invokes the `ProductsBLL` class's `GetProducts()` method.</span></span> <span data-ttu-id="ef3d1-140">這會建立與 FormView `ItemTemplate`， `InsertItemTemplate`，和`EditItemTemplate`。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-140">This will create a FormView with an `ItemTemplate`, `InsertItemTemplate`, and `EditItemTemplate`.</span></span> <span data-ttu-id="ef3d1-141">從原始碼 檢視中，移除`InsertItemTemplate`和`EditItemTemplate`因為我們不感興趣建立 FormView 支援編輯，或尚未插入。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-141">From the Source view, remove the `InsertItemTemplate` and `EditItemTemplate` since we're not interested in creating a FormView that supports editing or inserting yet.</span></span> <span data-ttu-id="ef3d1-142">下一步，清除內標記`ItemTemplate`，所以我們需要從重新開始。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-142">Next, clear out the markup within the `ItemTemplate` so that we have a clean slate to work from.</span></span>

<span data-ttu-id="ef3d1-143">如果您而是會往上建置`ItemTemplate`以手動方式，您可以加入並設定從 [工具箱] 拖曳至設計工具拖曳 ObjectDataSource。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-143">If you'd rather build up the `ItemTemplate` manually, you can add and configure the ObjectDataSource by dragging it from the Toolbox onto the Designer.</span></span> <span data-ttu-id="ef3d1-144">不過，不會設定在 FormView 的資料來源從設計工具。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-144">However, don't set the FormView's data source from the Designer.</span></span> <span data-ttu-id="ef3d1-145">相反地，請移至來源檢視，並手動設定在 FormView 的`DataSourceID`屬性`ID`ObjectDataSource 的值。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-145">Instead, go to the Source view and manually set the FormView's `DataSourceID` property to the `ID` value of the ObjectDataSource.</span></span> <span data-ttu-id="ef3d1-146">接下來，以手動方式加入`ItemTemplate`。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-146">Next, manually add the `ItemTemplate`.</span></span>

<span data-ttu-id="ef3d1-147">不論哪種方法，您決定採取，此時您在 FormView 的宣告式標記應該看起來：</span><span class="sxs-lookup"><span data-stu-id="ef3d1-147">Regardless of what approach you decided to take, at this point your FormView's declarative markup should look like:</span></span>


[!code-aspx[Main](using-the-formview-s-templates-vb/samples/sample1.aspx)]

<span data-ttu-id="ef3d1-148">請花一點時間檢查啟用分頁 核取方塊在 FormView 的智慧標籤。這會新增`AllowPaging="True"`屬性設定為在 FormView 的宣告式語法。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-148">Take a moment to check the Enable Paging checkbox in the FormView's smart tag; this will add the `AllowPaging="True"` attribute to the FormView's declarative syntax.</span></span> <span data-ttu-id="ef3d1-149">此外，設定`EnableViewState`屬性設定為 False。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-149">Also, set the `EnableViewState` property to False.</span></span>

## <a name="step-2-defining-theitemtemplates-markup"></a><span data-ttu-id="ef3d1-150">步驟 2： 定義`ItemTemplate`的標記</span><span class="sxs-lookup"><span data-stu-id="ef3d1-150">Step 2: Defining the`ItemTemplate`'s Markup</span></span>

<span data-ttu-id="ef3d1-151">在 FormView ObjectDataSource 控制項繫結並設定以支援分頁我們就可以指定的內容`ItemTemplate`。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-151">With the FormView bound to the ObjectDataSource control and configured to support paging we're ready to specify the content for the `ItemTemplate`.</span></span> <span data-ttu-id="ef3d1-152">本教學課程，讓我們有產品名稱顯示在`<h3>`標題。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-152">For this tutorial, let's have the product's name displayed in an `<h3>` heading.</span></span> <span data-ttu-id="ef3d1-153">接下來，我們將使用 HTML`<table>`顯示剩餘的產品屬性中包含的第一個和第三個資料行清單的屬性名稱和第二個和第四個清單及其值的四個資料行資料表。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-153">Following that, let's use an HTML `<table>` to display the remaining product properties in a four-column table where the first and third columns list the property names and the second and fourth list their values.</span></span>

<span data-ttu-id="ef3d1-154">這個標記可以透過在設計工具在 FormView 的範本編輯介面中輸入，或手動輸入透過宣告式語法。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-154">This markup can be entered in through the FormView's template editing interface in the Designer or entered manually through the declarative syntax.</span></span> <span data-ttu-id="ef3d1-155">使用範本時通常找到它更快速地進行直接使用宣告式語法，但可以自由使用您最熟悉任何技術。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-155">When working with templates I typically find it quicker to work directly with the declarative syntax, but feel free to use whatever technique you're most comfortable with.</span></span>

<span data-ttu-id="ef3d1-156">下列標記會顯示在 FormView 宣告式標記之後`ItemTemplate`的結構已完成：</span><span class="sxs-lookup"><span data-stu-id="ef3d1-156">The following markup shows the FormView declarative markup after the `ItemTemplate`'s structure has been completed:</span></span>


[!code-aspx[Main](using-the-formview-s-templates-vb/samples/sample2.aspx)]

<span data-ttu-id="ef3d1-157">請注意，資料繫結語法- `<%# Eval("ProductName") %>`，針對範例直接插入的範本輸出。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-157">Notice that the databinding syntax - `<%# Eval("ProductName") %>`, for example can be injected directly into the template's output.</span></span> <span data-ttu-id="ef3d1-158">也就是說，它需要指派給 Label 控制項`Text`屬性。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-158">That is, it need not be assigned to a Label control's `Text` property.</span></span> <span data-ttu-id="ef3d1-159">比方說，我們有`ProductName`值顯示在`<h3>`項目使用`<h3><%# Eval("ProductName") %></h3>`，其中產品 Chai 會轉譯為`<h3>Chai</h3>`。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-159">For example, we have the `ProductName` value displayed in an `<h3>` element using `<h3><%# Eval("ProductName") %></h3>`, which for the product Chai will render as `<h3>Chai</h3>`.</span></span>

<span data-ttu-id="ef3d1-160">`ProductPropertyLabel`和`ProductPropertyValue`CSS 類別用於指定的產品屬性名稱和值中的樣式`<table>`。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-160">The `ProductPropertyLabel` and `ProductPropertyValue` CSS classes are used for specifying the style of the product property names and values in the `<table>`.</span></span> <span data-ttu-id="ef3d1-161">這些 CSS 類別定義於`Styles.css`，而且會導致粗體且靠右對齊，並加入填補的屬性值右邊的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-161">These CSS classes are defined in `Styles.css` and cause the property names to be bold and right-aligned and add a right padding to the property values.</span></span>

<span data-ttu-id="ef3d1-162">因為沒有任何 CheckBoxFields 適用於在 FormView 中，以便顯示`Discontinued`值為核取方塊中，我們必須加入自己的核取方塊控制項。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-162">Since there are no CheckBoxFields available with the FormView, in order to show the `Discontinued` value as a checkbox we must add our own CheckBox control.</span></span> <span data-ttu-id="ef3d1-163">`Enabled`屬性設為 False，因此唯讀狀態，並核取方塊的`Checked`屬性的值繫結`Discontinued`資料欄位。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-163">The `Enabled` property is set to False, making it read-only, and the CheckBox's `Checked` property is bound to the value of the `Discontinued` data field.</span></span>

<span data-ttu-id="ef3d1-164">與`ItemTemplate`完成時，會顯示產品資訊以更流暢的方式。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-164">With the `ItemTemplate` complete, the product information is displayed in a much more fluid manner.</span></span> <span data-ttu-id="ef3d1-165">比較上一個教學課程 (圖 3) 的 DetailsView 輸出產生 FormView 在本教學課程 (圖 4) 的輸出。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-165">Compare the DetailsView output from the last tutorial (Figure 3) with the output generated by the FormView in this tutorial (Figure 4).</span></span>


<span data-ttu-id="ef3d1-166">[![固定的 DetailsView 輸出](using-the-formview-s-templates-vb/_static/image8.png)](using-the-formview-s-templates-vb/_static/image7.png)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-166">[![The Rigid DetailsView Output](using-the-formview-s-templates-vb/_static/image8.png)](using-the-formview-s-templates-vb/_static/image7.png)</span></span>

<span data-ttu-id="ef3d1-167">**圖 3**： 固定 DetailsView Output ([按一下以檢視完整大小的影像](using-the-formview-s-templates-vb/_static/image9.png))</span><span class="sxs-lookup"><span data-stu-id="ef3d1-167">**Figure 3**: The Rigid DetailsView Output ([Click to view full-size image](using-the-formview-s-templates-vb/_static/image9.png))</span></span>


<span data-ttu-id="ef3d1-168">[![流暢 FormView 輸出](using-the-formview-s-templates-vb/_static/image11.png)](using-the-formview-s-templates-vb/_static/image10.png)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-168">[![The Fluid FormView Output](using-the-formview-s-templates-vb/_static/image11.png)](using-the-formview-s-templates-vb/_static/image10.png)</span></span>

<span data-ttu-id="ef3d1-169">**圖 4**： 流體 FormView Output ([按一下以檢視完整大小的影像](using-the-formview-s-templates-vb/_static/image12.png))</span><span class="sxs-lookup"><span data-stu-id="ef3d1-169">**Figure 4**: The Fluid FormView Output ([Click to view full-size image](using-the-formview-s-templates-vb/_static/image12.png))</span></span>


## <a name="summary"></a><span data-ttu-id="ef3d1-170">總結</span><span class="sxs-lookup"><span data-stu-id="ef3d1-170">Summary</span></span>

<span data-ttu-id="ef3d1-171">雖然 GridView 和 DetailsView 控制項可以有使用 TemplateFields 自訂其輸出，同時仍會其資料以類似格線 boxy 的格式。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-171">While the GridView and DetailsView controls can have their output customized using TemplateFields, both still present their data in a grid-like, boxy format.</span></span> <span data-ttu-id="ef3d1-172">為單一記錄需要顯示這些時間 FormView 使用較不嚴謹的配置時，是理想的選擇。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-172">For those times when a single record needs to be shown using a less rigid layout, the FormView is an ideal choice.</span></span> <span data-ttu-id="ef3d1-173">在 DetailsView 中，例如 FormView 呈現的單一記錄其`DataSource`，但不同於 DetailsView 方法，它可以是只組成的範本，並不支援欄位。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-173">Like the DetailsView, the FormView renders a single record from its `DataSource`, but unlike the DetailsView it is composed just of templates and does not support fields.</span></span>

<span data-ttu-id="ef3d1-174">如我們所見本教學課程中，在 FormView 允許更彈性的配置顯示單一記錄時。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-174">As we saw in this tutorial, the FormView allows for a more flexible layout when displaying a single record.</span></span> <span data-ttu-id="ef3d1-175">在未來我們將檢驗 DataList 和中繼器控制項提供相同層級的彈性不如 FormsView，但可以顯示多筆記錄 （例如 GridView) 教學課程。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-175">In future tutorials we'll examine the DataList and Repeater controls, which provide the same level of flexibility as the FormsView, but are able to display multiple records (like the GridView).</span></span>

<span data-ttu-id="ef3d1-176">祝您程式設計 ！</span><span class="sxs-lookup"><span data-stu-id="ef3d1-176">Happy Programming!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="ef3d1-177">關於作者</span><span class="sxs-lookup"><span data-stu-id="ef3d1-177">About the Author</span></span>

<span data-ttu-id="ef3d1-178">[Scott Mitchell](http://www.4guysfromrolla.com/ScottMitchell.shtml)，作者的七個 ASP/ASP.NET 書籍和的創辦[4GuysFromRolla.com](http://www.4guysfromrolla.com)，已從 1998 年使用 Microsoft Web 技術。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-178">[Scott Mitchell](http://www.4guysfromrolla.com/ScottMitchell.shtml), author of seven ASP/ASP.NET books and founder of [4GuysFromRolla.com](http://www.4guysfromrolla.com), has been working with Microsoft Web technologies since 1998.</span></span> <span data-ttu-id="ef3d1-179">Scott 可做為獨立顧問、 訓練和寫入器。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-179">Scott works as an independent consultant, trainer, and writer.</span></span> <span data-ttu-id="ef3d1-180">他最新的活頁簿[ *Sam 教導您自己 ASP.NET 2.0 24 小時內*](https://www.amazon.com/exec/obidos/ASIN/0672327384/4guysfromrollaco)。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-180">His latest book is [*Sams Teach Yourself ASP.NET 2.0 in 24 Hours*](https://www.amazon.com/exec/obidos/ASIN/0672327384/4guysfromrollaco).</span></span> <span data-ttu-id="ef3d1-181">他可以在達到[ mitchell@4GuysFromRolla.com。](mailto:mitchell@4GuysFromRolla.com)或透過他的部落格，這可以在找到[http://ScottOnWriting.NET](http://ScottOnWriting.NET)。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-181">He can be reached at [mitchell@4GuysFromRolla.com.](mailto:mitchell@4GuysFromRolla.com) or via his blog, which can be found at [http://ScottOnWriting.NET](http://ScottOnWriting.NET).</span></span>

## <a name="special-thanks-to"></a><span data-ttu-id="ef3d1-182">特別感謝</span><span class="sxs-lookup"><span data-stu-id="ef3d1-182">Special Thanks To</span></span>

<span data-ttu-id="ef3d1-183">許多有用的檢閱者已檢閱本教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-183">This tutorial series was reviewed by many helpful reviewers.</span></span> <span data-ttu-id="ef3d1-184">本教學課程是 E.R.導致檢閱者</span><span class="sxs-lookup"><span data-stu-id="ef3d1-184">Lead reviewer for this tutorial was E.R.</span></span> <span data-ttu-id="ef3d1-185">Gilmore。</span><span class="sxs-lookup"><span data-stu-id="ef3d1-185">Gilmore.</span></span> <span data-ttu-id="ef3d1-186">檢閱我即將推出的 MSDN 文件有興趣嗎？</span><span class="sxs-lookup"><span data-stu-id="ef3d1-186">Interested in reviewing my upcoming MSDN articles?</span></span> <span data-ttu-id="ef3d1-187">如果是這樣，卸除我一行[ mitchell@4GuysFromRolla.com。](mailto:mitchell@4GuysFromRolla.com)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-187">If so, drop me a line at [mitchell@4GuysFromRolla.com.](mailto:mitchell@4GuysFromRolla.com)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="ef3d1-188">[上一頁](using-templatefields-in-the-detailsview-control-vb.md)
[下一頁](displaying-summary-information-in-the-gridview-s-footer-vb.md)</span><span class="sxs-lookup"><span data-stu-id="ef3d1-188">[Previous](using-templatefields-in-the-detailsview-control-vb.md)
[Next](displaying-summary-information-in-the-gridview-s-footer-vb.md)</span></span>