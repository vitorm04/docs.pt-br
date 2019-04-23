---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803165"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="03d2e-101">O texto selecionado TextBox do WPF aparece em cor diferente quando a caixa de texto está inativa</span><span class="sxs-lookup"><span data-stu-id="03d2e-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="03d2e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="03d2e-102">Details</span></span>|<span data-ttu-id="03d2e-103">No .NET Framework 4.5, quando um controle de caixa de texto do WPF estiver inativo (não tem o foco), o texto selecionado dentro da caixa terá uma cor diferente de quando o controle estiver ativo.</span><span class="sxs-lookup"><span data-stu-id="03d2e-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="03d2e-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="03d2e-104">Suggestion</span></span>|<span data-ttu-id="03d2e-105">O comportamento anterior (.NET Framework 4.0) poderá ser restaurado definindo a propriedade <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> como <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="03d2e-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="03d2e-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="03d2e-106">Scope</span></span>|<span data-ttu-id="03d2e-107">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="03d2e-107">Edge</span></span>|
|<span data-ttu-id="03d2e-108">Versão</span><span class="sxs-lookup"><span data-stu-id="03d2e-108">Version</span></span>|<span data-ttu-id="03d2e-109">4.5</span><span class="sxs-lookup"><span data-stu-id="03d2e-109">4.5</span></span>|
|<span data-ttu-id="03d2e-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="03d2e-110">Type</span></span>|<span data-ttu-id="03d2e-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="03d2e-111">Runtime</span></span>|
|<span data-ttu-id="03d2e-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="03d2e-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
