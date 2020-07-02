---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619895"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="268a2-101">O texto selecionado TextBox do WPF aparece em cor diferente quando a caixa de texto está inativa</span><span class="sxs-lookup"><span data-stu-id="268a2-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="268a2-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="268a2-102">Details</span></span>

<span data-ttu-id="268a2-103">No .NET Framework 4.5, quando um controle de caixa de texto do WPF estiver inativo (não tem o foco), o texto selecionado dentro da caixa terá uma cor diferente de quando o controle estiver ativo.</span><span class="sxs-lookup"><span data-stu-id="268a2-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="268a2-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="268a2-104">Suggestion</span></span>

<span data-ttu-id="268a2-105">O comportamento anterior (.NET Framework 4.0) poderá ser restaurado definindo a propriedade <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> como <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="268a2-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="268a2-106">Name</span><span class="sxs-lookup"><span data-stu-id="268a2-106">Name</span></span>    | <span data-ttu-id="268a2-107">Valor</span><span class="sxs-lookup"><span data-stu-id="268a2-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="268a2-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="268a2-108">Scope</span></span>   |<span data-ttu-id="268a2-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="268a2-109">Edge</span></span>|
|<span data-ttu-id="268a2-110">Versão</span><span class="sxs-lookup"><span data-stu-id="268a2-110">Version</span></span>|<span data-ttu-id="268a2-111">4.5</span><span class="sxs-lookup"><span data-stu-id="268a2-111">4.5</span></span>|
|<span data-ttu-id="268a2-112">Type</span><span class="sxs-lookup"><span data-stu-id="268a2-112">Type</span></span>|<span data-ttu-id="268a2-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="268a2-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="268a2-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="268a2-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
