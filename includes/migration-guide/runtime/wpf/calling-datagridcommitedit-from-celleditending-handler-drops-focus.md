---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803159"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="c6980-101">Chamar DataGrid.CommitEdit de um manipulador CellEditEnding descarta o foco</span><span class="sxs-lookup"><span data-stu-id="c6980-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c6980-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c6980-102">Details</span></span>|<span data-ttu-id="c6980-103">Chamar <xref:System.Windows.Controls.DataGrid.CommitEdit> de um dos manipuladores de eventos <xref:System.Windows.Controls.DataGrid?displayProperty=name> do <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> faz com que <xref:System.Windows.Controls.DataGrid?displayProperty=name> perca o foco.</span><span class="sxs-lookup"><span data-stu-id="c6980-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="c6980-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c6980-104">Suggestion</span></span>|<span data-ttu-id="c6980-105">Esse bug foi corrigido no .NET Framework 4.5.2, portanto, ele pode ser evitado com a atualização do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6980-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="c6980-106">Como alternativa, ele pode ser evitado com a nova seleção explícita de <xref:System.Windows.Controls.DataGrid?displayProperty=name> após chamada de <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="c6980-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="c6980-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="c6980-107">Scope</span></span>|<span data-ttu-id="c6980-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="c6980-108">Edge</span></span>|
|<span data-ttu-id="c6980-109">Versão</span><span class="sxs-lookup"><span data-stu-id="c6980-109">Version</span></span>|<span data-ttu-id="c6980-110">4.5</span><span class="sxs-lookup"><span data-stu-id="c6980-110">4.5</span></span>|
|<span data-ttu-id="c6980-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="c6980-111">Type</span></span>|<span data-ttu-id="c6980-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c6980-112">Runtime</span></span>|
|<span data-ttu-id="c6980-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c6980-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
