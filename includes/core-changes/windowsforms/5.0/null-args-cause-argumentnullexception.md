---
ms.openlocfilehash: ab8d801f3cdcfbeb6de20146754b26e3713d7dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702486"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="4e69f-101">Os métodos WinForms agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="4e69f-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="4e69f-102">Alguns métodos de Windows Forms agora geram um <xref:System.ArgumentNullException> para argumentos nulos, onde anteriormente eles lançavam um <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="4e69f-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4e69f-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="4e69f-103">Change description</span></span>

<span data-ttu-id="4e69f-104">Anteriormente, determinados métodos de Windows Forms lançavam um <xref:System.NullReferenceException> se passasse um argumento que era nulo.</span><span class="sxs-lookup"><span data-stu-id="4e69f-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="4e69f-105">A partir do .NET 5,0, esses métodos agora geram um <xref:System.ArgumentNullException> para argumentos nulos em vez disso.</span><span class="sxs-lookup"><span data-stu-id="4e69f-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="4e69f-106">Lançar um <xref:System.ArgumentNullException> está em conformidade com o comportamento do tempo de execução do .net.</span><span class="sxs-lookup"><span data-stu-id="4e69f-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="4e69f-107">Ele também melhora a experiência de depuração, comunicando claramente que um argumento é nulo e qual é o argumento.</span><span class="sxs-lookup"><span data-stu-id="4e69f-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4e69f-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="4e69f-108">Version introduced</span></span>

<span data-ttu-id="4e69f-109">.NET 5,0 Preview 1 </span><span class="sxs-lookup"><span data-stu-id="4e69f-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="4e69f-110">.NET 5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="4e69f-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4e69f-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="4e69f-111">Recommended action</span></span>

<span data-ttu-id="4e69f-112">Se você chamar qualquer um desses métodos e o seu código atualmente capturar um <xref:System.NullReferenceException> para argumentos nulos, pegue um <xref:System.ArgumentNullException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="4e69f-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="4e69f-113">Além disso, considere atualizar o código para evitar a passagem de argumentos nulos para os métodos listados.</span><span class="sxs-lookup"><span data-stu-id="4e69f-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="4e69f-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="4e69f-114">Category</span></span>

<span data-ttu-id="4e69f-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e69f-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4e69f-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4e69f-116">Affected APIs</span></span>

<span data-ttu-id="4e69f-117">A partir do .NET 5,0 Preview 1:</span><span class="sxs-lookup"><span data-stu-id="4e69f-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="4e69f-118">A partir do .NET 5,0 Preview 2:</span><span class="sxs-lookup"><span data-stu-id="4e69f-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="4e69f-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(somente para o <xref:System.IO.Stream> parâmetro)</span><span class="sxs-lookup"><span data-stu-id="4e69f-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

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

-->
