---
ms.openlocfilehash: 63959c240b2fe16e086b97881a5a1792035bb3f8
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888092"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a><span data-ttu-id="0719a-101">WinForms APIs agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="0719a-101">WinForms APIs now throw ArgumentNullException</span></span>

<span data-ttu-id="0719a-102">Alguns métodos do <xref:System.ArgumentNullException> Windows Forms agora lançam um para <xref:System.NullReferenceException>argumentos nulos, onde anteriormente eles jogaram um .</span><span class="sxs-lookup"><span data-stu-id="0719a-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0719a-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="0719a-103">Change description</span></span>

<span data-ttu-id="0719a-104">Anteriormente, certos métodos do <xref:System.NullReferenceException> Windows Forms lançavam um argumento que era nulo.</span><span class="sxs-lookup"><span data-stu-id="0719a-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="0719a-105">A partir de .NET 5.0, <xref:System.ArgumentNullException> esses métodos agora lançam um para argumentos nulos.</span><span class="sxs-lookup"><span data-stu-id="0719a-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="0719a-106">Lançar <xref:System.ArgumentNullException> um conforme o comportamento do tempo de execução .NET.</span><span class="sxs-lookup"><span data-stu-id="0719a-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="0719a-107">Também melhora a experiência de depuração ao comunicar claramente que um argumento é nulo e qual argumento é.</span><span class="sxs-lookup"><span data-stu-id="0719a-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0719a-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0719a-108">Version introduced</span></span>

<span data-ttu-id="0719a-109">.NET 5.0 Visualização 1</span><span class="sxs-lookup"><span data-stu-id="0719a-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="0719a-110">.NET 5.0 Visualização 2</span><span class="sxs-lookup"><span data-stu-id="0719a-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0719a-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0719a-111">Recommended action</span></span>

<span data-ttu-id="0719a-112">Se você chamar qualquer um desses métodos <xref:System.NullReferenceException> e seu código atualmente pegar um para argumentos nulos, pegue um <xref:System.ArgumentNullException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0719a-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="0719a-113">Além disso, considere atualizar o código para evitar a aprovação de argumentos nulos para os métodos listados.</span><span class="sxs-lookup"><span data-stu-id="0719a-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="0719a-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="0719a-114">Category</span></span>

<span data-ttu-id="0719a-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0719a-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0719a-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0719a-116">Affected APIs</span></span>

<span data-ttu-id="0719a-117">A partir de .NET 5.0 Visualização 1:</span><span class="sxs-lookup"><span data-stu-id="0719a-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="0719a-118">A partir de .NET 5.0 Visualização 2:</span><span class="sxs-lookup"><span data-stu-id="0719a-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="0719a-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(apenas <xref:System.IO.Stream> para o parâmetro)</span><span class="sxs-lookup"><span data-stu-id="0719a-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

### Affected APIs

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

-->
