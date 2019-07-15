---
ms.openlocfilehash: 8049bf01bc10c5913fa11b25e49afd1b1317eecc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802953"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>A Verificação Ortográfica do WPF falha de formas inesperadas

|   |   |
|---|---|
|Detalhes|Isso inclui alguns problemas da Verificação Ortográfica do WPF:<ul><li>Às vezes, a Verificação Ortográfica do WPF gera <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>A Verificação Ortográfica do WPF falha com <xref:System.UnauthorizedAccessException> quando aplicativos são iniciados usando "Executar como usuário diferente"</li><li>O Verificador Ortográfico do WPF identifica incorretamente erros ortográficos em palavras compostas, como "Hausnummer" em alemão.</li></ul>|
|Sugestão|Problema nº 1 – esse problema foi corrigido no .NET Framework 4.6.2 Problema nº 2 – a Verificação Ortográfica do WPF deixou de ter suporte quando aplicativos são iniciados usando "Executar como usuário diferente". A partir do .NET Framework 4.6.2, aplicativos iniciados dessa maneira não falharão inesperadamente, em vez disso, a Verificação Ortográfica será desabilitada silenciosamente. Problema nº 3 – esse problema foi corrigido no .NET Framework 4.6.2.|
|Escopo|Microsoft Edge|
|Versão|4.6.1|
|Tipo|Tempo de execução|

