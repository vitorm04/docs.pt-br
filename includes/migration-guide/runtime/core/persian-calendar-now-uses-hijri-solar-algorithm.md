---
ms.openlocfilehash: bfe406161ac754124a2cc38c68a80c3b9fb2c7f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234091"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>O calendário persa agora usa o algoritmo solar islâmico

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.6, a classe <xref:System.Globalization.PersianCalendar?displayProperty=name> usa o algoritmo solar islâmico. Converter datas entre o <xref:System.Globalization.PersianCalendar?displayProperty=name> e outros calendários pode produzir um resultado um pouco diferente começando com o .NET Framework 4.6 para datas anteriores a 1800 ou posteriores a 2023 (gregoriano). Além disso, agora <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> é <code>March 22, 0622</code> em vez de <code>March 21, 0622</code>.|
|Sugestão|Lembre-se de que algumas datas anteriores ou posteriores podem ser um pouco diferentes quando se usa o PersianCalendar no .NET Framework 4.6. Além disso, ao serializar datas entre processos que podem ser executados em diferentes versões do .NET Framework, não armazene-as como cadeias de caracteres de data PersianCalendar (uma vez que esses valores podem ser diferentes).|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
