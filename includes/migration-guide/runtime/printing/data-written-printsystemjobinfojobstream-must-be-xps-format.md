---
ms.openlocfilehash: 74f00821f2304664729faa8de2f0163c6611f513
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803129"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Dados gravados em PrintSystemJobInfo.JobStream devem estar no formato XPS

|   |   |
|---|---|
|Detalhes|A propriedade <xref:System.Printing.PrintSystemJobInfo.JobStream> expõe o fluxo de um trabalho de impressão. O usuário pode enviar dados brutos para o sistema operacional subjacente que imprime os componentes gravando-os neste fluxo. A partir do .NET Framework 4.5 no Windows 8 e em versões posteriores do sistema operacional Windows, os dados gravados nesse fluxo devem estar no formato XPS como um fluxo de pacote.|
|Sugestão|Para mostrar o conteúdo impresso, você tem duas opções:<ul><li>Use a classe <xref:System.Windows.Xps.XpsDocumentWriter> para produzir conteúdo de impressão. Essa é a alternativa recomendada.</li><li>Garanta que os dados enviados ao fluxo retornado pela propriedade <xref:System.Printing.PrintSystemJobInfo.JobStream> estão no formato XPS como um fluxo de pacote.</li></ul>|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
