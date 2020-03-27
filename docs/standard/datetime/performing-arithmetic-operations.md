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
ms.openlocfilehash: 0db0331620da8337930bfacf5d1bbd9913647afa
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344178"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Executando operações aritméticas com datas e horários

Embora tanto <xref:System.DateTime> as <xref:System.DateTimeOffset> estruturas forneçam aos membros que realizam operações aritméticas em seus valores, os resultados das operações aritméticas são muito diferentes. Este tópico examina essas diferenças, relaciona-as a graus de consciência do fuso horário em dados de data e hora e discute como executar operações totalmente conscientes do fuso horário usando dados de data e hora.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparações e operações aritméticas com valores dateTime

A <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriedade <xref:System.DateTimeKind> permite que um valor seja atribuído à data e hora para indicar se ele representa o horário local, o Tempo Universal Coordenado (UTC) ou a hora em um fuso horário não especificado. No entanto, essas informações de fuso horário limitado são ignoradas <xref:System.DateTimeKind> ao comparar ou realizar aritmética de data e hora sobre valores. O exemplo a seguir, que compara o horário local atual com o horário UTC atual, ilustra isso.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

O <xref:System.DateTime.CompareTo%28System.DateTime%29> método relata que a hora local é mais antiga (ou menor que) a hora UTC, e a operação de subtração indica que a diferença entre UTC e o horário local para um sistema no fuso horário padrão do Pacífico dos EUA é de sete horas. Mas como esses dois valores fornecem representações diferentes de um único ponto no tempo, é claro neste caso que o intervalo de tempo é completamente atribuível ao deslocamento do fuso horário local da UTC.

De forma mais <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> geral, a propriedade não <xref:System.DateTime.Kind> afeta os resultados retornados por comparação e métodos aritméticos (como indica a comparação de dois pontos idênticos no tempo), embora possa afetar a interpretação desses resultados. Por exemplo: 

- O resultado de qualquer operação aritmética realizada <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> em dois <xref:System.DateTimeKind> valores de data e hora cujas propriedades ambas iguais reflete o intervalo de tempo real entre os dois valores. Da mesma forma, a comparação dos dois valores de data e hora reflete com precisão a relação entre horários.

- O resultado de qualquer operação aritmética ou de <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> comparação realizada <xref:System.DateTimeKind> em dois valores de <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> data e hora cujas propriedades são iguais ou em dois valores de data e hora com valores de propriedade diferentes reflete a diferença no tempo de relógio entre os dois valores.

- As operações aritméticas ou de comparação em valores de data e hora local não consideram se um valor específico é ambíguo ou inválido nem levam em conta o efeito de regras de ajuste que resultam da transição do fuso horário local de ou para o horário de verão.

- Qualquer operação que compara ou calcula a diferença entre o UTC e o horário local inclui um intervalo de tempo igual ao deslocamento do fuso horário local em relação ao UTC no resultado.

- Qualquer operação que compara ou calcula a diferença entre um horário não especificado e o UTC ou o horário local reflete a hora do relógio simples. As diferenças de fuso horário não são consideradas; o resultado não reflete a aplicação das regras de ajuste de fuso horário.

- Qualquer operação que compara ou calcula a diferença entre dois horários não especificados poderá incluir um intervalo desconhecido que reflete a diferença entre o horário em dois fusos horários diferentes.

Existem muitos cenários em que as diferenças de fuso horário não afetam os cálculos de data e hora (para uma discussão de alguns deles, consulte [Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) ou em que o contexto dos dados de data e hora define o significado de comparação ou operações aritméticas.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparações e operações aritméticas com valores DateTimeOffset

Um <xref:System.DateTimeOffset> valor inclui não apenas uma data e hora, mas também um deslocamento que define inequivocamente essa data e hora em relação à UTC. Isso torna possível definir a igualdade de <xref:System.DateTimeOffset> forma um pouco diferente dos valores. Considerando <xref:System.DateTime> que os valores são iguais se <xref:System.DateTimeOffset> tiverem a mesma data e valor de hora, os valores são iguais se ambos se referem ao mesmo ponto no tempo. Isso torna <xref:System.DateTimeOffset> um valor mais preciso e menos necessário de interpretação quando usado em comparações e na maioria das operações aritméticas que determinam o intervalo entre duas datas e tempos. O exemplo a seguir, que é o <xref:System.DateTimeOffset> equivalente ao <xref:System.DateTimeOffset> exemplo anterior que comparou os valores locais e UTC, ilustra essa diferença de comportamento.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Neste exemplo, <xref:System.DateTimeOffset.CompareTo%2A> o método indica que a hora local atual e o <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> horário UTC atual são iguais, e a subtração dos valores indica que a diferença entre os dois tempos é <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

A principal limitação do uso <xref:System.DateTimeOffset> de valores na <xref:System.DateTimeOffset> aritmética de data e hora é que, embora os valores tenham alguma consciência de fuso horário, eles não estão totalmente cientes do fuso horário. Embora <xref:System.DateTimeOffset> a compensação do valor reflita a compensação <xref:System.DateTimeOffset> de um fuso horário da UTC quando uma variável é atribuída pela primeira vez a um valor, ela se torna desassociada do fuso horário posteriormente. Como não estão mais diretamente associadas a um horário identificável, a adição e a subtração dos intervalos de data e hora não consideram as regras de ajuste de um fuso horário.

Para ilustrar, a transição para o horário de verão no fuso horário padrão central dos EUA ocorre às 2:00 da manhã. em 9 de março de 2008. Isso significa que adicionar um intervalo de duas horas e meia ao fuso horário padrão da região central de 1h30min em 9 de março de 2008 deve produzir uma data e hora de 5h em 9 de março de 2008. No entanto, como mostra o exemplo a seguir, o resultado da adição é 4h em 9 de março de 2008. Observe que o resultado desta operação representa o ponto correto no tempo, embora não seja o horário no fuso horário em que estamos interessados (ou seja, não tem o deslocamento do fuso horário esperado).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operações aritméticas com tempos em fusos horários

A <xref:System.TimeZoneInfo> classe inclui uma série de métodos de conversão que aplicam automaticamente ajustes quando convertem tempos de um fuso horário para outro. Entre elas estão as seguintes:

- Os <xref:System.TimeZoneInfo.ConvertTime%2A> <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> métodos, que convertem tempos entre dois fusos horários.

- Os <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> métodos, que convertem o tempo em um fuso horário específico para UTC, ou convertem UTC para o horário em um fuso horário específico.

Para obter detalhes, consulte [Tempos de conversão entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md).

A <xref:System.TimeZoneInfo> classe não fornece nenhum método que aplique automaticamente regras de ajuste quando você executa a aritmética de data e hora. No entanto, é possível fazer isso convertendo o horário em um fuso horário para UTC, executando a operação aritmética e, em seguida, convertendo do UTC novamente para o horário no fuso horário. Para obter detalhes, [consulte Como: Usar fusos horários em data e hora aritmética](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Por exemplo, o código a seguir é semelhante ao código anterior, que adicionou duas horas e meia às 2h em 9 de março de 2008. No entanto, como converte um horário padrão da região central em UTC antes de realizar a aritmética de data e hora e, depois, converte o resultado do UTC novamente no horário padrão da região central, o horário resultante reflete a transição do fuso horário padrão da região central para o horário de verão.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Confira também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Como: Usar fusos horários em data e hora aritmética](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
