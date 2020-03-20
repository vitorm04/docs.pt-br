---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803173"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Chamar DataGrid.CommitEdit de um manipulador CellEditEnding descarta o foco

|   |   |
|---|---|
|Detalhes|Chamar <xref:System.Windows.Controls.DataGrid.CommitEdit> de um dos manipuladores de eventos <xref:System.Windows.Controls.DataGrid?displayProperty=name> do <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> faz com que <xref:System.Windows.Controls.DataGrid?displayProperty=name> perca o foco.|
|Sugestão|Esse bug foi corrigido no .NET Framework 4.5.2, portanto, ele pode ser evitado com a atualização do .NET Framework. Como alternativa, ele pode ser evitado com a nova seleção explícita de <xref:System.Windows.Controls.DataGrid?displayProperty=name> após chamada de <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
