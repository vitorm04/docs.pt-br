---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858381"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Acessar os itens selecionados de um DataGrid do WPF em um manipulador do evento UnloadingRow do DataGrid pode gerar NullReferenceException

|   |   |
|---|---|
|Detalhes|Por causa de um bug no .NET Framework 4.5, os manipuladores de eventos <xref:System.Windows.Controls.DataGrid> que envolvem a remoção de uma linha podem gerar <xref:System.NullReferenceException?displayProperty=name> se acessarem as propriedades <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> ou <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> de <xref:System.Windows.Controls.DataGrid>.|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Secundária|
|Versão|4.5|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
