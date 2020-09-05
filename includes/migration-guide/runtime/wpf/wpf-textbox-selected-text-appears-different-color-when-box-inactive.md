---
ms.openlocfilehash: c01705002ad87a12389078d75ffd0f91f934d36e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497512"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="7f9d4-101">O texto selecionado TextBox do WPF aparece em cor diferente quando a caixa de texto está inativa</span><span class="sxs-lookup"><span data-stu-id="7f9d4-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="7f9d4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7f9d4-102">Details</span></span>

<span data-ttu-id="7f9d4-103">No .NET Framework 4.5, quando um controle de caixa de texto do WPF estiver inativo (não tem o foco), o texto selecionado dentro da caixa terá uma cor diferente de quando o controle estiver ativo.</span><span class="sxs-lookup"><span data-stu-id="7f9d4-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7f9d4-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7f9d4-104">Suggestion</span></span>

<span data-ttu-id="7f9d4-105">O comportamento anterior (.NET Framework 4.0) poderá ser restaurado definindo a propriedade <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> como <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="7f9d4-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="7f9d4-106">Nome</span><span class="sxs-lookup"><span data-stu-id="7f9d4-106">Name</span></span>    | <span data-ttu-id="7f9d4-107">Valor</span><span class="sxs-lookup"><span data-stu-id="7f9d4-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7f9d4-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="7f9d4-108">Scope</span></span>   |<span data-ttu-id="7f9d4-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7f9d4-109">Edge</span></span>|
|<span data-ttu-id="7f9d4-110">Versão</span><span class="sxs-lookup"><span data-stu-id="7f9d4-110">Version</span></span>|<span data-ttu-id="7f9d4-111">4.5</span><span class="sxs-lookup"><span data-stu-id="7f9d4-111">4.5</span></span>|
|<span data-ttu-id="7f9d4-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="7f9d4-112">Type</span></span>|<span data-ttu-id="7f9d4-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="7f9d4-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7f9d4-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7f9d4-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
