---
ms.openlocfilehash: 1487e32ffca7b4bbebb5edac7efc8961ac05723b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497682"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="81208-101">Acessar os itens selecionados de um DataGrid do WPF em um manipulador do evento UnloadingRow do DataGrid pode gerar NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="81208-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="81208-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="81208-102">Details</span></span>

<span data-ttu-id="81208-103">Por causa de um bug no .NET Framework 4.5, os manipuladores de eventos <xref:System.Windows.Controls.DataGrid> que envolvem a remoção de uma linha podem gerar <xref:System.NullReferenceException?displayProperty=fullName> se acessarem as propriedades <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> ou <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> de <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="81208-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=fullName> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> properties.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="81208-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="81208-104">Suggestion</span></span>

<span data-ttu-id="81208-105">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81208-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="81208-106">Nome</span><span class="sxs-lookup"><span data-stu-id="81208-106">Name</span></span>    | <span data-ttu-id="81208-107">Valor</span><span class="sxs-lookup"><span data-stu-id="81208-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="81208-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="81208-108">Scope</span></span>   |<span data-ttu-id="81208-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="81208-109">Minor</span></span>|
|<span data-ttu-id="81208-110">Versão</span><span class="sxs-lookup"><span data-stu-id="81208-110">Version</span></span>|<span data-ttu-id="81208-111">4.5</span><span class="sxs-lookup"><span data-stu-id="81208-111">4.5</span></span>|
|<span data-ttu-id="81208-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="81208-112">Type</span></span>|<span data-ttu-id="81208-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="81208-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="81208-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="81208-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.Controls.DataGrid.UnloadingRow`
- `E:System.Windows.Controls.DataGrid.UnloadingRowDetails`

-->
