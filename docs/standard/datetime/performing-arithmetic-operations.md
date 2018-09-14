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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2a50823b812541786cf1bebfd6b1262ce2e9314
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569158"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Executando operações aritméticas com datas e horários

Embora tanto o <xref:System.DateTime> e o <xref:System.DateTimeOffset> estruturas oferecerem membros que executam operações aritméticas em seus valores, os resultados das operações aritméticas são muito diferentes. Este tópico examina essas diferenças, relaciona a graus de reconhecimento de fuso horário em dados de data e hora e discute como executar totalmente operações de reconhecimento de fuso horário usando dados de data e hora.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparações e operações aritméticas com valores de data e hora

O <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriedade permite que um <xref:System.DateTimeKind> valor a ser atribuído à data e hora para indicar se ele representa a hora local, Tempo Universal Coordenado (UTC) ou o tempo em um fuso horário não especificado. No entanto, essas informações de fuso horário limitado são ignoradas quando comparar ou executar a data e hora em <xref:System.DateTimeKind> valores. O exemplo a seguir, que compara o horário local atual com o horário UTC atual, ilustra isso.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

O <xref:System.DateTime.CompareTo%28System.DateTime%29> método relata que a hora local é anterior (ou menor que) a hora UTC e a operação de subtração indica que a diferença entre o UTC e a hora local para um sistema nos EUA Pacífico dos EUA é de sete horas. Porém, como esses dois valores oferecem representações diferentes de um único momento, fica claro que, nesse caso, o intervalo de tempo é completamente atribuível ao deslocamento do fuso horário local em relação ao UTC.

De modo geral, o <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriedade não afeta os resultados retornados por <xref:System.DateTime.Kind> métodos de comparação e de aritmética (como indica a comparação dos dois pontos idênticos no tempo), embora ele possa afetar a interpretação dos resultados. Por exemplo:

* O resultado de qualquer operação aritmética executada em dois valores de data e hora cujas <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> igual a ambas as propriedades <xref:System.DateTimeKind> reflete o intervalo de tempo real entre os dois valores. Da mesma forma, a comparação dos dois valores de data e hora reflete com precisão a relação entre horários.

* O resultado de qualquer operação aritmética ou de comparação executada em dois valores de data e hora cujas <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> igual a ambas as propriedades <xref:System.DateTimeKind> ou em dois valores de data e hora com diferentes <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> valores de propriedade reflete a diferença na hora do relógio entre os dois valores.

* As operações aritméticas ou de comparação em valores de data e hora local não consideram se um valor específico é ambíguo ou inválido nem levam em conta o efeito de regras de ajuste que resultam da transição do fuso horário local de ou para o horário de verão.

* Qualquer operação que compara ou calcula a diferença entre o UTC e o horário local inclui um intervalo de tempo igual ao deslocamento do fuso horário local em relação ao UTC no resultado.

* Qualquer operação que compara ou calcula a diferença entre um horário não especificado e o UTC ou o horário local reflete a hora do relógio simples. As diferenças de fuso horário não são consideradas; o resultado não reflete a aplicação das regras de ajuste de fuso horário.

* Qualquer operação que compara ou calcula a diferença entre dois horários não especificados poderá incluir um intervalo desconhecido que reflete a diferença entre o horário em dois fusos horários diferentes.

Há muitos cenários em qual fuso horário diferenças não afetam os cálculos de data e hora (para uma discussão sobre algumas delas, consulte [escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) ou em que o contexto a data e hora dados definem o significado das operações de comparação ou aritmética.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparações e operações aritméticas com valores de DateTimeOffset

Um <xref:System.DateTimeOffset> valor inclui não apenas uma data e hora, mas também um deslocamento que define sem ambiguidade a data e hora em relação ao UTC. Isso torna possível definir a igualdade de forma diferente do que para <xref:System.DateTimeOffset> valores. Enquanto <xref:System.DateTime> os valores são iguais se tiverem o mesma valor de data e hora, <xref:System.DateTimeOffset> os valores são iguais se os dois se referirem ao mesmo ponto no tempo. Isso faz com que um <xref:System.DateTimeOffset> valor mais preciso e com menos necessidade de interpretação quando usado em comparações e na maioria das operações aritméticas que determinam o intervalo entre duas datas e horas. O exemplo a seguir, que é o <xref:System.DateTimeOffset> equivalente ao exemplo anterior que comparou local e UTC <xref:System.DateTimeOffset> valores, ilustra essa diferença no comportamento.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Neste exemplo, o <xref:System.DateTimeOffset.CompareTo%2A> método indica que a hora local atual e a hora UTC atual são iguais e a subtração dos <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> valores indica que a diferença entre os dois horários é <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

A principal limitação da utilização <xref:System.DateTimeOffset> valores de data e hora é que, embora <xref:System.DateTimeOffset> valores têm algum reconhecimento de fuso horário, eles não são totalmente cientes de fuso horário. Embora o <xref:System.DateTimeOffset> deslocamento do valor reflete o deslocamento de um fuso horário do UTC quando um <xref:System.DateTimeOffset> variável pela primeira vez é atribuída um valor, ele se torna desassociado do fuso horário posteriormente. Como não estão mais diretamente associadas a um horário identificável, a adição e a subtração dos intervalos de data e hora não consideram as regras de ajuste de um fuso horário.

Para ilustrar, a transição para o horário de verão no fuso horário padrão da região central EUA ocorre às 2h. em 9 de março de 2008. Isso significa que adicionar um intervalo de duas horas e meia ao fuso horário padrão da região central de 1h30min em 9 de março de 2008 deve produzir uma data e hora de 5h em 9 de março de 2008. No entanto, como mostra o exemplo a seguir, o resultado da adição é 4h em 9 de março de 2008. Observe que o resultado dessa operação representa o momento correto, embora não seja o horário no fuso horário em que estamos interessados (ou seja, não tem o deslocamento de fuso horário esperado).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operações aritméticas com horários nos fusos horários

O <xref:System.TimeZoneInfo> classe inclui uma série de métodos de conversão que aplicam ajustes automaticamente quando eles convertem horas de um fuso horário para outro. Eles incluem o seguinte:

* O <xref:System.TimeZoneInfo.ConvertTime%2A> e <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> métodos que convertem horas entre quaisquer dois fusos horários.

* O <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> e <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> métodos, que converter a hora em um determinado fuso horário UTC ou converter de UTC para o horário em um determinado fuso horário.

Para obter detalhes, consulte [convertendo horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md).

O <xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> classe fornece os métodos que aplicam regras de ajuste automaticamente quando você executa a data e hora. No entanto, é possível fazer isso convertendo o horário em um fuso horário para UTC, executando a operação aritmética e, em seguida, convertendo do UTC novamente para o horário no fuso horário. Para obter detalhes, consulte [como: usar fusos horários de data e hora aritmética](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Por exemplo, o código a seguir é semelhante ao código anterior, que adicionou duas horas e meia às 2h em 9 de março de 2008. No entanto, como converte um horário padrão da região central em UTC antes de realizar a aritmética de data e hora e, depois, converte o resultado do UTC novamente no horário padrão da região central, o horário resultante reflete a transição do fuso horário padrão da região central para o horário de verão.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Consulte também

* [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
* [Como usar fusos horários em aritmética de data e hora](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
