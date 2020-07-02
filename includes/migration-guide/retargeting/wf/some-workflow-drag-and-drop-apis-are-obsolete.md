---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617111"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="8fff3-101">Algumas APIs arrastar e soltar do Fluxo de Trabalho estão obsoletas</span><span class="sxs-lookup"><span data-stu-id="8fff3-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="8fff3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8fff3-102">Details</span></span>

<span data-ttu-id="8fff3-103">A API Arrastar/Soltar do Fluxo de Trabalho está obsoleta e vai gerar avisos do compilador se o aplicativo for recompilado na versão 4.5.</span><span class="sxs-lookup"><span data-stu-id="8fff3-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8fff3-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8fff3-104">Suggestion</span></span>

<span data-ttu-id="8fff3-105">No lugar, devem ser usadas as novas APIs <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> compatíveis com operações com vários objetos.</span><span class="sxs-lookup"><span data-stu-id="8fff3-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="8fff3-106">Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo.</span><span class="sxs-lookup"><span data-stu-id="8fff3-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="8fff3-107">Ainda há suporte para as APIs.</span><span class="sxs-lookup"><span data-stu-id="8fff3-107">The APIs are still supported.</span></span>

| <span data-ttu-id="8fff3-108">Name</span><span class="sxs-lookup"><span data-stu-id="8fff3-108">Name</span></span>    | <span data-ttu-id="8fff3-109">Valor</span><span class="sxs-lookup"><span data-stu-id="8fff3-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8fff3-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="8fff3-110">Scope</span></span>   | <span data-ttu-id="8fff3-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="8fff3-111">Minor</span></span>       |
| <span data-ttu-id="8fff3-112">Versão</span><span class="sxs-lookup"><span data-stu-id="8fff3-112">Version</span></span> | <span data-ttu-id="8fff3-113">4.5</span><span class="sxs-lookup"><span data-stu-id="8fff3-113">4.5</span></span>         |
| <span data-ttu-id="8fff3-114">Type</span><span class="sxs-lookup"><span data-stu-id="8fff3-114">Type</span></span>    | <span data-ttu-id="8fff3-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="8fff3-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8fff3-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8fff3-116">Affected APIs</span></span>

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
