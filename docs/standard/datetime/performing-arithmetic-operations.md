---
title: Executando operações aritméticas com datas e horários
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
ms.openlocfilehash: 2e668cf3f909ed4b89f05ca63dfe69051c1d9066
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122260"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Executando operações aritméticas com datas e horários

Embora as estruturas <xref:System.DateTime> e <xref:System.DateTimeOffset> forneçam Membros que executam operações aritméticas em seus valores, os resultados de operações aritméticas são muito diferentes. Este tópico examina essas diferenças, relaciona-as a graus de reconhecimento de fuso horário em dados de data e hora e discute como executar operações de reconhecimento de fuso horário integralmente usando dados de data e hora.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparações e operações aritméticas com valores DateTime

A propriedade <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> permite que um valor de <xref:System.DateTimeKind> seja atribuído à data e hora para indicar se ela representa a hora local, UTC (tempo Universal Coordenado) ou a hora em um fuso horário não especificado. No entanto, essas informações limitadas de fuso horário são ignoradas ao comparar ou executar a aritmética de data e hora em valores <xref:System.DateTimeKind>. O exemplo a seguir, que compara o horário local atual com o horário UTC atual, ilustra isso.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

O método <xref:System.DateTime.CompareTo%28System.DateTime%29> relata que a hora local é anterior a (ou menor que) a hora UTC, e a operação de subtração indica que a diferença entre o UTC e a hora local de um sistema no fuso horário padrão do Pacífico americano é de sete horas. Porém, como esses dois valores oferecem representações diferentes de um único momento, fica claro que, nesse caso, o intervalo de tempo é completamente atribuível ao deslocamento do fuso horário local em relação ao UTC.

Em geral, a propriedade <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> não afeta os resultados retornados por <xref:System.DateTime.Kind> métodos de comparação e aritméticos (já que a comparação de dois pontos idênticos no tempo indica), embora possa afetar a interpretação desses resultados. Por exemplo:

- O resultado de qualquer operação aritmética executada em dois valores de data e hora cujas propriedades <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> igual <xref:System.DateTimeKind> reflete o intervalo de tempo real entre os dois valores. Da mesma forma, a comparação dos dois valores de data e hora reflete com precisão a relação entre horários.

- O resultado de qualquer operação aritmética ou de comparação executada em dois valores de data e hora cujos <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriedades sejam iguais <xref:System.DateTimeKind> ou em dois valores de data e hora com diferentes valores de propriedade <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> reflete a diferença no tempo de relógio entre os dois os.

- As operações aritméticas ou de comparação em valores de data e hora local não consideram se um valor específico é ambíguo ou inválido nem levam em conta o efeito de regras de ajuste que resultam da transição do fuso horário local de ou para o horário de verão.

- Qualquer operação que compara ou calcula a diferença entre o UTC e o horário local inclui um intervalo de tempo igual ao deslocamento do fuso horário local em relação ao UTC no resultado.

- Qualquer operação que compara ou calcula a diferença entre um horário não especificado e o UTC ou o horário local reflete a hora do relógio simples. As diferenças de fuso horário não são consideradas; o resultado não reflete a aplicação das regras de ajuste de fuso horário.

- Qualquer operação que compara ou calcula a diferença entre dois horários não especificados poderá incluir um intervalo desconhecido que reflete a diferença entre o horário em dois fusos horários diferentes.

Há muitos cenários em que as diferenças de fuso horário não afetam os cálculos de data e hora (para uma discussão sobre alguns deles, consulte [escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) ou no qual o contexto dos dados de data e hora define o significado de operações de comparação ou aritmética.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparações e operações aritméticas com valores de DateTimeOffset

Um valor de <xref:System.DateTimeOffset> inclui não apenas uma data e hora, mas também um deslocamento que define inequivocamente a data e a hora em relação ao UTC. Isso torna possível definir igualdade um pouco diferente do que para valores de <xref:System.DateTimeOffset>. Enquanto <xref:System.DateTime> valores são iguais se tiverem o mesmo valor de data e hora, <xref:System.DateTimeOffset> valores serão iguais se ambos fizerem referência ao mesmo ponto no tempo. Isso torna um valor <xref:System.DateTimeOffset> mais preciso e menos em necessidade de interpretação quando usado em comparações e na maioria das operações aritméticas que determinam o intervalo entre duas datas e horas. O exemplo a seguir, que é o <xref:System.DateTimeOffset> equivalente ao exemplo anterior que comparava valores de <xref:System.DateTimeOffset> local e UTC, ilustra essa diferença no comportamento.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Neste exemplo, o método <xref:System.DateTimeOffset.CompareTo%2A> indica que a hora local atual e a hora UTC atual são iguais, e a subtração de <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> valores indica que a diferença entre as duas horas é <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

A principal limitação de usar valores de <xref:System.DateTimeOffset> na aritmética de data e hora é que, embora os valores de <xref:System.DateTimeOffset> tenham algum reconhecimento de fuso horário, eles não são totalmente cientes do fuso horário. Embora o deslocamento do valor <xref:System.DateTimeOffset> reflita o deslocamento de um fuso horário do UTC quando uma variável <xref:System.DateTimeOffset> recebe um valor primeiro, ele se torna desassociado do fuso horário depois. Como não estão mais diretamente associadas a um horário identificável, a adição e a subtração dos intervalos de data e hora não consideram as regras de ajuste de um fuso horário.

Para ilustrar, a transição para o horário de verão no fuso horário padrão central dos EUA ocorre às 2:00. em 9 de março de 2008. Isso significa que adicionar um intervalo de duas horas e meia ao fuso horário padrão da região central de 1h30min em 9 de março de 2008 deve produzir uma data e hora de 5h em 9 de março de 2008. No entanto, como mostra o exemplo a seguir, o resultado da adição é 4h em 9 de março de 2008. Observe que o resultado dessa operação representa o momento correto, embora não seja o horário no fuso horário em que estamos interessados (ou seja, não tem o deslocamento de fuso horário esperado).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operações aritméticas com tempos em fusos horários

A classe <xref:System.TimeZoneInfo> inclui vários métodos de conversão que aplicam ajustes automaticamente quando convertem horários de um fuso horário para outro. Eles incluem o seguinte:

- Os métodos <xref:System.TimeZoneInfo.ConvertTime%2A> e <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, que convertem os horários entre dois fusos horários.

- Os métodos <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> e <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, que convertem a hora em um fuso horário específico em UTC ou convertem UTC para a hora em um fuso horário específico.

Para obter detalhes, consulte [conversão de horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md).

A classe <xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> não fornece nenhum método que aplique regras de ajuste automaticamente quando você executar aritmética de data e hora. No entanto, é possível fazer isso convertendo o horário em um fuso horário para UTC, executando a operação aritmética e, em seguida, convertendo do UTC novamente para o horário no fuso horário. Para obter detalhes, consulte [como usar fusos horários em aritmética de data e hora](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Por exemplo, o código a seguir é semelhante ao código anterior, que adicionou duas horas e meia às 2h em 9 de março de 2008. No entanto, como converte um horário padrão da região central em UTC antes de realizar a aritmética de data e hora e, depois, converte o resultado do UTC novamente no horário padrão da região central, o horário resultante reflete a transição do fuso horário padrão da região central para o horário de verão.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Como usar fusos horários em aritmética de data e hora](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
