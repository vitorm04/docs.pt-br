---
ms.openlocfilehash: c78122a2fe69c78625d6cb7fa9ddf41c49c2e737
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497794"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="2c105-101">Chamar DataGrid.CommitEdit de um manipulador CellEditEnding descarta o foco</span><span class="sxs-lookup"><span data-stu-id="2c105-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="2c105-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2c105-102">Details</span></span>

<span data-ttu-id="2c105-103">Chamar <xref:System.Windows.Controls.DataGrid.CommitEdit> de um dos manipuladores de eventos <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> do <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> faz com que <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> perca o foco.</span><span class="sxs-lookup"><span data-stu-id="2c105-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2c105-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2c105-104">Suggestion</span></span>

<span data-ttu-id="2c105-105">Esse bug foi corrigido no .NET Framework 4.5.2, portanto, ele pode ser evitado com a atualização do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c105-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="2c105-106">Como alternativa, ele pode ser evitado com a nova seleção explícita de <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> após chamada de <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2c105-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="2c105-107">Nome</span><span class="sxs-lookup"><span data-stu-id="2c105-107">Name</span></span>    | <span data-ttu-id="2c105-108">Valor</span><span class="sxs-lookup"><span data-stu-id="2c105-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2c105-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="2c105-109">Scope</span></span>   |<span data-ttu-id="2c105-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2c105-110">Edge</span></span>|
|<span data-ttu-id="2c105-111">Versão</span><span class="sxs-lookup"><span data-stu-id="2c105-111">Version</span></span>|<span data-ttu-id="2c105-112">4.5</span><span class="sxs-lookup"><span data-stu-id="2c105-112">4.5</span></span>|
|<span data-ttu-id="2c105-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="2c105-113">Type</span></span>|<span data-ttu-id="2c105-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="2c105-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2c105-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2c105-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.CommitEdit`
- `M:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)`

-->
