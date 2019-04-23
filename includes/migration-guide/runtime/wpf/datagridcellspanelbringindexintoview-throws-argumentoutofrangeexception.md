---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235982"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView gera ArgumentOutOfRangeException

|   |   |
|---|---|
|Detalhes|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> será executado assincronamente quando a virtualização de coluna estiver habilitada, mas as larguras das colunas ainda não estiverem determinadas.  Se as colunas forem removidas antes da operação assíncrona, um <xref:System.ArgumentOutOfRangeException?displayProperty=name> poderá ocorrer.|
|Sugestão|Siga um destes procedimentos:<ol><li>Atualize para o .NET Framework 4.7.</li><li>Instale o patch de manutenção mais recente para o .NET Framework 4.6.2.</li><li>Evitar remover colunas até que a resposta assíncrona ao método <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> seja concluída.</li></ol>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
