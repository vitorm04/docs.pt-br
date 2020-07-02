---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621919"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="4b76e-101">Chamar DataGrid.CommitEdit de um manipulador CellEditEnding descarta o foco</span><span class="sxs-lookup"><span data-stu-id="4b76e-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="4b76e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4b76e-102">Details</span></span>

<span data-ttu-id="4b76e-103">Chamar <xref:System.Windows.Controls.DataGrid.CommitEdit> de um dos manipuladores de eventos <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> do <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> faz com que <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> perca o foco.</span><span class="sxs-lookup"><span data-stu-id="4b76e-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4b76e-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4b76e-104">Suggestion</span></span>

<span data-ttu-id="4b76e-105">Esse bug foi corrigido no .NET Framework 4.5.2, portanto, ele pode ser evitado com a atualização do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b76e-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="4b76e-106">Como alternativa, ele pode ser evitado com a nova seleção explícita de <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> após chamada de <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="4b76e-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="4b76e-107">Name</span><span class="sxs-lookup"><span data-stu-id="4b76e-107">Name</span></span>    | <span data-ttu-id="4b76e-108">Valor</span><span class="sxs-lookup"><span data-stu-id="4b76e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4b76e-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="4b76e-109">Scope</span></span>   |<span data-ttu-id="4b76e-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4b76e-110">Edge</span></span>|
|<span data-ttu-id="4b76e-111">Versão</span><span class="sxs-lookup"><span data-stu-id="4b76e-111">Version</span></span>|<span data-ttu-id="4b76e-112">4.5</span><span class="sxs-lookup"><span data-stu-id="4b76e-112">4.5</span></span>|
|<span data-ttu-id="4b76e-113">Type</span><span class="sxs-lookup"><span data-stu-id="4b76e-113">Type</span></span>|<span data-ttu-id="4b76e-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="4b76e-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4b76e-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4b76e-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
