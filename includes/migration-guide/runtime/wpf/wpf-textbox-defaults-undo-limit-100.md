---
ms.openlocfilehash: de79182e326082786c1e0691f8888e30cd410f5d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235030"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="cd2b1-101">O padrão da Caixa de Texto do WPF é o limite de 100 na ação desfazer</span><span class="sxs-lookup"><span data-stu-id="cd2b1-101">WPF TextBox defaults to undo limit of 100</span></span>

|   |   |
|---|---|
|<span data-ttu-id="cd2b1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="cd2b1-102">Details</span></span>|<span data-ttu-id="cd2b1-103">No .NET Framework 4.5, o limite padrão de desfazer para uma caixa de texto do WPF é 100 (em vez de ser ilimitado como no .NET Framework 4.0)</span><span class="sxs-lookup"><span data-stu-id="cd2b1-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>|
|<span data-ttu-id="cd2b1-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="cd2b1-104">Suggestion</span></span>|<span data-ttu-id="cd2b1-105">Se um limite de 100 da ação desfazer for muito baixo, o limite poderá ser definido explicitamente com <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>.</span><span class="sxs-lookup"><span data-stu-id="cd2b1-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>|
|<span data-ttu-id="cd2b1-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="cd2b1-106">Scope</span></span>|<span data-ttu-id="cd2b1-107">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="cd2b1-107">Edge</span></span>|
|<span data-ttu-id="cd2b1-108">Versão</span><span class="sxs-lookup"><span data-stu-id="cd2b1-108">Version</span></span>|<span data-ttu-id="cd2b1-109">4.5</span><span class="sxs-lookup"><span data-stu-id="cd2b1-109">4.5</span></span>|
|<span data-ttu-id="cd2b1-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="cd2b1-110">Type</span></span>|<span data-ttu-id="cd2b1-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="cd2b1-111">Runtime</span></span>|
|<span data-ttu-id="cd2b1-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="cd2b1-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
