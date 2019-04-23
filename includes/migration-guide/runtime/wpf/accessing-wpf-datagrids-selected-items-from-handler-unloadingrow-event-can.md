---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803126"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="1b8f0-101">Acessar os itens selecionados de um DataGrid do WPF em um manipulador do evento UnloadingRow do DataGrid pode gerar NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="1b8f0-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1b8f0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1b8f0-102">Details</span></span>|<span data-ttu-id="1b8f0-103">Por causa de um bug no .NET Framework 4.5, os manipuladores de eventos <xref:System.Windows.Controls.DataGrid> que envolvem a remoção de uma linha podem gerar <xref:System.NullReferenceException?displayProperty=name> se acessarem as propriedades <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> ou <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> de <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="1b8f0-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="1b8f0-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1b8f0-104">Suggestion</span></span>|<span data-ttu-id="1b8f0-105">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b8f0-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="1b8f0-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="1b8f0-106">Scope</span></span>|<span data-ttu-id="1b8f0-107">Secundário</span><span class="sxs-lookup"><span data-stu-id="1b8f0-107">Minor</span></span>|
|<span data-ttu-id="1b8f0-108">Versão</span><span class="sxs-lookup"><span data-stu-id="1b8f0-108">Version</span></span>|<span data-ttu-id="1b8f0-109">4.5</span><span class="sxs-lookup"><span data-stu-id="1b8f0-109">4.5</span></span>|
|<span data-ttu-id="1b8f0-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="1b8f0-110">Type</span></span>|<span data-ttu-id="1b8f0-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1b8f0-111">Runtime</span></span>|
|<span data-ttu-id="1b8f0-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1b8f0-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
