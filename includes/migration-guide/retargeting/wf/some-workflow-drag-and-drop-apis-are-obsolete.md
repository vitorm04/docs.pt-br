---
ms.openlocfilehash: 297af393e86c65e84ea7271d98eab36dbc6dbb0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774293"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="a7475-101">Algumas APIs arrastar e soltar do Fluxo de Trabalho estão obsoletas</span><span class="sxs-lookup"><span data-stu-id="a7475-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a7475-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a7475-102">Details</span></span>|<span data-ttu-id="a7475-103">A API Arrastar/Soltar do Fluxo de Trabalho está obsoleta e vai gerar avisos do compilador se o aplicativo for recompilado na versão 4.5.</span><span class="sxs-lookup"><span data-stu-id="a7475-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>|
|<span data-ttu-id="a7475-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a7475-104">Suggestion</span></span>|<span data-ttu-id="a7475-105">No lugar, devem ser usadas as novas APIs <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> compatíveis com operações com vários objetos.</span><span class="sxs-lookup"><span data-stu-id="a7475-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="a7475-106">Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo.</span><span class="sxs-lookup"><span data-stu-id="a7475-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="a7475-107">Ainda há suporte para as APIs.</span><span class="sxs-lookup"><span data-stu-id="a7475-107">The APIs are still supported.</span></span>|
|<span data-ttu-id="a7475-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="a7475-108">Scope</span></span>|<span data-ttu-id="a7475-109">Secundário</span><span class="sxs-lookup"><span data-stu-id="a7475-109">Minor</span></span>|
|<span data-ttu-id="a7475-110">Versão</span><span class="sxs-lookup"><span data-stu-id="a7475-110">Version</span></span>|<span data-ttu-id="a7475-111">4.5</span><span class="sxs-lookup"><span data-stu-id="a7475-111">4.5</span></span>|
|<span data-ttu-id="a7475-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="a7475-112">Type</span></span>|<span data-ttu-id="a7475-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="a7475-113">Retargeting</span></span>|
|<span data-ttu-id="a7475-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a7475-114">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|
