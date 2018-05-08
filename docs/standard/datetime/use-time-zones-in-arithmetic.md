---
title: 'Como: usar fusos horários em data e hora'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9d326750cdef96be1aa6055d46b4ac08ec7a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Como: usar fusos horários em data e hora

Normalmente, quando você executar data e hora usando aritmético <xref:System.DateTime> ou <xref:System.DateTimeOffset> valores, o resultado não reflete quaisquer regras de ajuste de fuso horário. Isso é verdadeiro mesmo quando o fuso horário do valor de data e hora é claramente identificável (por exemplo, quando o <xref:System.DateTime.Kind%2A> está definida como <xref:System.DateTimeKind.Local>). Este tópico mostra como executar operações aritméticas em valores de data e hora que pertencem a um determinado fuso horário. Os resultados das operações aritméticas refletirão as regras de ajuste do fuso horário.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Para aplicar as regras de ajuste à aritmética de data e hora

1. Implemente um método de acoplamento próximo de um valor de data e hora com o fuso horário ao qual ele pertence. Por exemplo, declare uma estrutura que inclui o valor de data e hora e seu fuso horário. O exemplo a seguir usa essa abordagem para vincular um <xref:System.DateTime> valor com seu fuso horário.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Converter uma hora para o tempo Universal Coordenado (UTC) chamando o <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> método ou o <xref:System.TimeZoneInfo.ConvertTime%2A> método.

3. Execute a operação aritmética na hora UTC.

4. Converter a hora de UTC para a zona de tempo associada a hora original chamando o <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> método.

## <a name="example"></a>Exemplo

O exemplo a seguir adiciona duas horas e trinta minutos a 9 de março de 2008, à 1h30 do Horário Padrão Central. A transição do fuso horário para o horário de verão ocorre 30 minutos depois, às 2h. em 9 de março de 2008. Como o exemplo segue as quatro etapas listadas na seção anterior, ele relata corretamente a hora resultante como 5h. em 9 de março de 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Ambos <xref:System.DateTime> e <xref:System.DateTimeOffset> valores serão desassociados de qualquer fuso horário para o qual eles podem pertencer. Para executar a aritmética de data e hora de uma maneira que aplique automaticamente as regras de ajuste de um fuso horário, o fuso horário ao qual qualquer valor de data e hora pertence deve ser imediatamente identificável. Isso significa que uma data e hora e seu fuso horário associado devem estar estritamente acoplados. Há várias maneiras de fazer isso, que incluem o seguinte:

* Supor que todas as horas usadas em um aplicativo pertencem a um fuso horário específico. Embora adequada em alguns casos, essa abordagem oferece flexibilidade limitada e possivelmente portabilidade limitada.

* Definir um tipo que acople estritamente uma data e hora e seu fuso horário associado incluindo ambas como campos do tipo. Essa abordagem é usada no exemplo de código, que define uma estrutura para armazenar a data e hora e o fuso horário em dois campos de membro.

O exemplo ilustra como executar operações aritméticas em <xref:System.DateTime> valores para que as regras de ajuste de fuso horário são aplicadas ao resultado. No entanto, <xref:System.DateTimeOffset> valores podem ser usados facilmente. O exemplo a seguir ilustra como o código de exemplo original pode ser adaptado para usar <xref:System.DateTimeOffset> em vez de <xref:System.DateTime> valores.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Observe que, se essa adição simplesmente é realizada no <xref:System.DateTimeOffset> valor sem primeiro convertê-lo ao UTC, o resultado reflete o ponto correto no tempo, mas seu deslocamento não reflete o mesmo que o fuso horário designado para esse período.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência a System.Core.dll seja adicionada ao projeto.

* Se o <xref:System> namespace importados com o `using` instrução (necessária em código c#).

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[executando operações aritméticas com datas e horas](../../../docs/standard/datetime/performing-arithmetic-operations.md)
