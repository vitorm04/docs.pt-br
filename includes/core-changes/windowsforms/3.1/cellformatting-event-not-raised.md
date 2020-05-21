---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721375"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="10db5-101">Evento CellFormatting não gerado se ToolTip for mostrado</span><span class="sxs-lookup"><span data-stu-id="10db5-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="10db5-102"><xref:System.Windows.Forms.DataGridView>Agora mostra as dicas de ferramenta de texto e erro de uma célula quando ele é focalizado por um mouse e quando selecionado por meio do teclado.</span><span class="sxs-lookup"><span data-stu-id="10db5-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="10db5-103">Se uma dica de ferramenta for mostrada, o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> evento não será gerado.</span><span class="sxs-lookup"><span data-stu-id="10db5-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="10db5-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="10db5-104">Change description</span></span>

<span data-ttu-id="10db5-105">Antes do .NET Core 3,1, um <xref:System.Windows.Forms.DataGridView> que tinha a <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriedade definida para `true` mostrar uma dica de ferramenta para o texto de uma célula e erros quando a célula foi focalizada por um mouse.</span><span class="sxs-lookup"><span data-stu-id="10db5-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="10db5-106">Dicas de ferramentas não são mostradas quando uma célula foi selecionada por meio do teclado (por exemplo, usando a tecla Tab, teclas de atalho ou navegação de seta).</span><span class="sxs-lookup"><span data-stu-id="10db5-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="10db5-107">Se o usuário editou uma célula e, em seguida, enquanto o <xref:System.Windows.Forms.DataGridView> ainda estava no modo de edição, focalizado em uma célula que não tinha a <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> propriedade definida, um <xref:System.Windows.Forms.DataGridView.CellFormatting> evento foi gerado para formatar o texto da célula para exibição na célula.</span><span class="sxs-lookup"><span data-stu-id="10db5-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="10db5-108">Para atender aos padrões de acessibilidade, a partir do .NET Core 3,1, um <xref:System.Windows.Forms.DataGridView> que tem a <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriedade definida para `true` Mostrar as dicas de ferramenta para o texto de uma célula e erros não apenas quando a célula é focalizada, mas também quando ela é selecionada por meio do teclado.</span><span class="sxs-lookup"><span data-stu-id="10db5-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="10db5-109">Como consequência dessa alteração, o <xref:System.Windows.Forms.DataGridView.CellFormatting> evento *não* é gerado quando células que não têm o conjunto de <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> Propriedades são focalizadas enquanto o <xref:System.Windows.Forms.DataGridView> estiver no modo de edição.</span><span class="sxs-lookup"><span data-stu-id="10db5-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="10db5-110">O evento não é gerado porque o conteúdo da célula focalizada é mostrado como uma dica de ferramenta em vez de ser exibido na célula.</span><span class="sxs-lookup"><span data-stu-id="10db5-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="10db5-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="10db5-111">Version introduced</span></span>

<span data-ttu-id="10db5-112">3.1</span><span class="sxs-lookup"><span data-stu-id="10db5-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="10db5-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="10db5-113">Recommended action</span></span>

<span data-ttu-id="10db5-114">Refatore qualquer código que dependa do <xref:System.Windows.Forms.DataGridView.CellFormatting> evento enquanto o <xref:System.Windows.Forms.DataGridView> estiver no modo de edição.</span><span class="sxs-lookup"><span data-stu-id="10db5-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="10db5-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="10db5-115">Category</span></span>

<span data-ttu-id="10db5-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="10db5-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10db5-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="10db5-117">Affected APIs</span></span>

<span data-ttu-id="10db5-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="10db5-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
