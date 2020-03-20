---
ms.openlocfilehash: 65d9edc1e7377a86f8185ebf28bb5bee3a3f887d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803237"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open falha no Windows 7 com BSP ou LSP Winsock não IFS presente

|   |   |
|---|---|
|Detalhes|<xref:System.Data.SqlClient.SqlConnection.Open> e <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> falharão no .NET Framework 4.5 se forem executados em um computador com Windows 7 sem a presença de um BSP ou LSP não IFS Winsock. Para determinar se um BSP ou LSP não IFS está instalado, use o comando <code>netsh WinSock Show Catalog</code> e analise cada item <code>Winsock Catalog Provider Entry</code> retornado. Se o valor de Sinalizadores de Serviço tiver o bit <code>0x20000</code> definido, o provedor usará os identificadores do IFS e funcionará corretamente. Se o bit <code>0x20000</code> estiver limpo (não definido), trata-se de um BSP ou LSP não IFS.|
|Sugestão|Esse bug foi corrigido no .NET Framework 4.5.2, portanto, ele pode ser evitado com a atualização do .NET Framework. Como alternativa, ele pode ser evitado com a remoção de qualquer LSP Winsock não IFS instalado.|
|Escopo|Secundária|
|Versão|4.5|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
