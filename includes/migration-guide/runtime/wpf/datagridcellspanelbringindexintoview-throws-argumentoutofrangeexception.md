---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802438"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView gera ArgumentOutOfRangeException

|   |   |
|---|---|
|Detalhes|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> será executado assincronamente quando a virtualização de coluna estiver habilitada, mas as larguras das colunas ainda não estiverem determinadas.  Se as colunas forem removidas antes da operação assíncrona, um <xref:System.ArgumentOutOfRangeException?displayProperty=name> poderá ocorrer.|
|Sugestão|Siga um destes procedimentos:<ol><li>Atualize para o .NET Framework 4.7.</li><li>Instale o patch de manutenção mais recente para o .NET Framework 4.6.2.</li><li>Evitar remover colunas até que a resposta assíncrona ao método <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> seja concluída.</li></ol>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
