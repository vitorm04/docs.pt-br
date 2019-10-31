---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857470"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Categorias do padrão Unicode versão 8.0 agora são compatíveis

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2, os dados Unicode foram atualizados do Unicode Standard versão 6.3 para a versão 8.0.  Ao solicitar a categorias de caracteres Unicode no .NET Framework 4.6.2, alguns resultados poderão não corresponder aos resultados nas versões anteriores do .NET Framework.  Essa alteração afeta principalmente as sílabas Cheroqui, bem como os símbolos vocálicos e as marcas de tom Tai Lue Novo.|
|Sugestão|Examine o código e remova ou altere a lógica que depende de categorias de caractere Unicode embutido em código.|
|Escopo|Secundário|
|Versão|4.6.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

