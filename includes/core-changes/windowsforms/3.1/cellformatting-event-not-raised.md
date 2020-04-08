---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888095"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="3a362-101">Evento de formatação de células não levantada se a dica de ferramenta for mostrada</span><span class="sxs-lookup"><span data-stu-id="3a362-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="3a362-102">Um <xref:System.Windows.Forms.DataGridView> agora mostra as dicas de texto e erro de uma célula quando pairado por um mouse e quando selecionado através do teclado.</span><span class="sxs-lookup"><span data-stu-id="3a362-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="3a362-103">Se uma dica de <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> ferramenta for mostrada, o evento não será levantado.</span><span class="sxs-lookup"><span data-stu-id="3a362-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a362-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="3a362-104">Change description</span></span>

<span data-ttu-id="3a362-105">Antes do .NET Core 3.1, um <xref:System.Windows.Forms.DataGridView> que tinha a <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriedade definida para `true` mostrar uma dica de ferramenta para o texto de uma célula e erros quando a célula era pairada por um mouse.</span><span class="sxs-lookup"><span data-stu-id="3a362-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="3a362-106">As dicas de ferramentas não foram mostradas quando uma célula foi selecionada através do teclado (por exemplo, usando a tecla Tab, teclas de atalho ou navegação de seta).</span><span class="sxs-lookup"><span data-stu-id="3a362-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="3a362-107">Se o usuário editou uma célula <xref:System.Windows.Forms.DataGridView> e, em seguida, enquanto o ainda estava <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> no modo <xref:System.Windows.Forms.DataGridView.CellFormatting> de edição, pairava sobre uma célula que não tinha o conjunto de propriedades, um evento foi levantado para formatar o texto da célula para exibição na célula.</span><span class="sxs-lookup"><span data-stu-id="3a362-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="3a362-108">Para atender aos padrões de acessibilidade, a <xref:System.Windows.Forms.DataGridView> partir do <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> .NET `true` Core 3.1, um que tem a propriedade definida para mostrar dicas de ferramentas para o texto de uma célula e erros não apenas quando a célula é pairada, mas também quando é selecionada através do teclado.</span><span class="sxs-lookup"><span data-stu-id="3a362-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="3a362-109">Como conseqüência dessa <xref:System.Windows.Forms.DataGridView.CellFormatting> mudança, o evento *não* é levantado quando <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> as células que <xref:System.Windows.Forms.DataGridView> não têm o conjunto de propriedades são pairadas enquanto o está no modo de edição.</span><span class="sxs-lookup"><span data-stu-id="3a362-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="3a362-110">O evento não é levantado porque o conteúdo da célula pairada é mostrado como uma dica de ferramenta em vez de ser exibido na célula.</span><span class="sxs-lookup"><span data-stu-id="3a362-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a362-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="3a362-111">Version introduced</span></span>

<span data-ttu-id="3a362-112">3.1</span><span class="sxs-lookup"><span data-stu-id="3a362-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a362-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="3a362-113">Recommended action</span></span>

<span data-ttu-id="3a362-114">Refatorar qualquer código que <xref:System.Windows.Forms.DataGridView.CellFormatting> dependa <xref:System.Windows.Forms.DataGridView> do evento enquanto estiver no modo de edição.</span><span class="sxs-lookup"><span data-stu-id="3a362-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="3a362-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="3a362-115">Category</span></span>

<span data-ttu-id="3a362-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a362-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a362-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3a362-117">Affected APIs</span></span>

<span data-ttu-id="3a362-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3a362-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
