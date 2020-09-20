---
ms.openlocfilehash: 59e7b55516d79aa5c574a8869698e1a18576ef41
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770946"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="c7d94-101">Os métodos WinForms agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="c7d94-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="c7d94-102">Alguns métodos de Windows Forms agora geram um <xref:System.ArgumentNullException> para argumentos nulos, onde anteriormente eles lançavam um <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="c7d94-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c7d94-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="c7d94-103">Change description</span></span>

<span data-ttu-id="c7d94-104">Anteriormente, determinados métodos de Windows Forms lançavam um <xref:System.NullReferenceException> se passasse um argumento que era nulo.</span><span class="sxs-lookup"><span data-stu-id="c7d94-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="c7d94-105">A partir do .NET 5,0, esses métodos agora geram um <xref:System.ArgumentNullException> para argumentos nulos, em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c7d94-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="c7d94-106">Lançar um <xref:System.ArgumentNullException> está em conformidade com o comportamento do tempo de execução do .net.</span><span class="sxs-lookup"><span data-stu-id="c7d94-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="c7d94-107">Ele também melhora a experiência de depuração, comunicando claramente que um argumento é nulo e qual é o argumento.</span><span class="sxs-lookup"><span data-stu-id="c7d94-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c7d94-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7d94-108">Version introduced</span></span>

<span data-ttu-id="c7d94-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c7d94-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c7d94-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c7d94-110">Recommended action</span></span>

<span data-ttu-id="c7d94-111">Se você chamar qualquer um desses métodos e o seu código atualmente capturar um <xref:System.NullReferenceException> para argumentos nulos, pegue um <xref:System.ArgumentNullException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c7d94-111">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="c7d94-112">Além disso, considere atualizar o código para evitar a passagem de argumentos nulos para os métodos listados.</span><span class="sxs-lookup"><span data-stu-id="c7d94-112">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="c7d94-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="c7d94-113">Category</span></span>

<span data-ttu-id="c7d94-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7d94-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c7d94-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c7d94-115">Affected APIs</span></span>

<span data-ttu-id="c7d94-116">A tabela a seguir lista os métodos e parâmetros afetados:</span><span class="sxs-lookup"><span data-stu-id="c7d94-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="c7d94-117">Método</span><span class="sxs-lookup"><span data-stu-id="c7d94-117">Method</span></span> | <span data-ttu-id="c7d94-118">Nome do parâmetro</span><span class="sxs-lookup"><span data-stu-id="c7d94-118">Parameter name</span></span> | <span data-ttu-id="c7d94-119">Versão adicionada</span><span class="sxs-lookup"><span data-stu-id="c7d94-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="c7d94-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="c7d94-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="c7d94-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="c7d94-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="c7d94-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="c7d94-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c7d94-123">Preview 1</span><span class="sxs-lookup"><span data-stu-id="c7d94-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c7d94-124">Preview 1</span><span class="sxs-lookup"><span data-stu-id="c7d94-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c7d94-125">Preview 1</span><span class="sxs-lookup"><span data-stu-id="c7d94-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c7d94-126">Preview 1</span><span class="sxs-lookup"><span data-stu-id="c7d94-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="c7d94-127">Preview 1</span><span class="sxs-lookup"><span data-stu-id="c7d94-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="c7d94-128">Preview 2</span><span class="sxs-lookup"><span data-stu-id="c7d94-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="c7d94-129">Preview 2</span><span class="sxs-lookup"><span data-stu-id="c7d94-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="c7d94-130">Versão prévia 5</span><span class="sxs-lookup"><span data-stu-id="c7d94-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="c7d94-131">Versão prévia 5</span><span class="sxs-lookup"><span data-stu-id="c7d94-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="c7d94-132">Versão prévia 5</span><span class="sxs-lookup"><span data-stu-id="c7d94-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="c7d94-133">Versão prévia 5</span><span class="sxs-lookup"><span data-stu-id="c7d94-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="c7d94-134">Versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="c7d94-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="c7d94-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="c7d94-135">`owner`, `value`</span></span> | <span data-ttu-id="c7d94-136">Versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="c7d94-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="c7d94-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="c7d94-137">`owner`, `value`</span></span> | <span data-ttu-id="c7d94-138">Versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="c7d94-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="c7d94-139">Versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="c7d94-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="c7d94-140">Versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="c7d94-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="c7d94-141">Versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="c7d94-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="c7d94-142">Versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="c7d94-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="c7d94-143">Versão prévia 7</span><span class="sxs-lookup"><span data-stu-id="c7d94-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="c7d94-144">`key` está `null` ou vazio</span><span class="sxs-lookup"><span data-stu-id="c7d94-144">`key` is `null` or empty</span></span> | <span data-ttu-id="c7d94-145">Visualização 8</span><span class="sxs-lookup"><span data-stu-id="c7d94-145">Preview 8</span></span> |
> | <xref:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="c7d94-146">`key` está `null` ou vazio</span><span class="sxs-lookup"><span data-stu-id="c7d94-146">`key` is `null` or empty</span></span> | <span data-ttu-id="c7d94-147">RC1</span><span class="sxs-lookup"><span data-stu-id="c7d94-147">RC1</span></span> |
> | <xref:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c7d94-148">RC1</span><span class="sxs-lookup"><span data-stu-id="c7d94-148">RC1</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`
- `M:System.Windows.Forms.ListViewGroup.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.#ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System#Collections#ICollection#CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)`

-->
