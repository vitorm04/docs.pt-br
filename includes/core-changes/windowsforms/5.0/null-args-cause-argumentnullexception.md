---
ms.openlocfilehash: 00f89e6ae49982917fa7591c3283adec3947eed2
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365629"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="c18f1-101">Os métodos WinForms agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="c18f1-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="c18f1-102">Alguns métodos de Windows Forms agora geram um <xref:System.ArgumentNullException> para argumentos nulos, onde anteriormente eles lançavam um <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="c18f1-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c18f1-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="c18f1-103">Change description</span></span>

<span data-ttu-id="c18f1-104">Anteriormente, determinados métodos de Windows Forms lançavam um <xref:System.NullReferenceException> se passasse um argumento que era nulo.</span><span class="sxs-lookup"><span data-stu-id="c18f1-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="c18f1-105">A partir do .NET 5,0, esses métodos agora geram um <xref:System.ArgumentNullException> para argumentos nulos, em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c18f1-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="c18f1-106">Lançar um <xref:System.ArgumentNullException> está em conformidade com o comportamento do tempo de execução do .net.</span><span class="sxs-lookup"><span data-stu-id="c18f1-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="c18f1-107">Ele também melhora a experiência de depuração, comunicando claramente que um argumento é nulo e qual é o argumento.</span><span class="sxs-lookup"><span data-stu-id="c18f1-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c18f1-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c18f1-108">Version introduced</span></span>

<span data-ttu-id="c18f1-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c18f1-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c18f1-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c18f1-110">Recommended action</span></span>

<span data-ttu-id="c18f1-111">Se você chamar qualquer um desses métodos e o seu código atualmente capturar um <xref:System.NullReferenceException> para argumentos nulos, pegue um <xref:System.ArgumentNullException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c18f1-111">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="c18f1-112">Além disso, considere atualizar o código para evitar a passagem de argumentos nulos para os métodos listados.</span><span class="sxs-lookup"><span data-stu-id="c18f1-112">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="c18f1-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="c18f1-113">Category</span></span>

<span data-ttu-id="c18f1-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c18f1-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c18f1-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c18f1-115">Affected APIs</span></span>

<span data-ttu-id="c18f1-116">A tabela a seguir lista os métodos e parâmetros afetados:</span><span class="sxs-lookup"><span data-stu-id="c18f1-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="c18f1-117">Método</span><span class="sxs-lookup"><span data-stu-id="c18f1-117">Method</span></span> | <span data-ttu-id="c18f1-118">Nome do parâmetro</span><span class="sxs-lookup"><span data-stu-id="c18f1-118">Parameter name</span></span> | <span data-ttu-id="c18f1-119">Versão adicionada</span><span class="sxs-lookup"><span data-stu-id="c18f1-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="c18f1-120">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="c18f1-120">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="c18f1-121">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="c18f1-121">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="c18f1-122">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="c18f1-122">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c18f1-123">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="c18f1-123">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c18f1-124">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="c18f1-124">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c18f1-125">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="c18f1-125">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="c18f1-126">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="c18f1-126">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="c18f1-127">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="c18f1-127">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="c18f1-128">5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="c18f1-128">5.0 Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="c18f1-129">5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="c18f1-129">5.0 Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="c18f1-130">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="c18f1-130">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="c18f1-131">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="c18f1-131">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="c18f1-132">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="c18f1-132">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="c18f1-133">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="c18f1-133">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="c18f1-134">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c18f1-134">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="c18f1-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="c18f1-135">`owner`, `value`</span></span> | <span data-ttu-id="c18f1-136">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c18f1-136">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="c18f1-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="c18f1-137">`owner`, `value`</span></span> | <span data-ttu-id="c18f1-138">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c18f1-138">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="c18f1-139">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c18f1-139">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="c18f1-140">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c18f1-140">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="c18f1-141">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c18f1-141">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="c18f1-142">`destination`perguntas</span><span class="sxs-lookup"><span data-stu-id="c18f1-142">`destination`q\`</span></span> | <span data-ttu-id="c18f1-143">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c18f1-143">5.0 Preview 6</span></span> |

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
- `M:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)`

-->
