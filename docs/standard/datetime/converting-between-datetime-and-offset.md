---
title: Convertendo entre DateTime e DateTimeOffset
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
ms.openlocfilehash: 428553f75db2cca6705ac72873e86e120e94d134
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132587"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Convertendo entre DateTime e DateTimeOffset

Embora a estrutura de <xref:System.DateTimeOffset> forneça um grau maior de reconhecimento de fuso horário que a estrutura de <xref:System.DateTime>, os parâmetros de <xref:System.DateTime> são usados com mais frequência em chamadas de método. Por isso, a capacidade de converter valores de <xref:System.DateTimeOffset> para <xref:System.DateTime> valores e vice-versa é particularmente importante. Este tópico mostra como executar essas conversões de uma maneira que preserva o máximo possível de informações de fuso horário.

> [!NOTE]
> Os tipos <xref:System.DateTime> e <xref:System.DateTimeOffset> têm algumas limitações ao representar os horários em fusos horários. Com sua propriedade <xref:System.DateTime.Kind%2A>, <xref:System.DateTime> é capaz de refletir apenas o UTC (tempo Universal Coordenado) e o fuso horário local do sistema. <xref:System.DateTimeOffset> reflete o deslocamento de um tempo do UTC, mas não reflete o fuso horário real ao qual o deslocamento pertence. Para obter detalhes sobre valores de tempo e suporte para fusos horários, consulte [escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversões de DateTime para DateTimeOffset

A estrutura de <xref:System.DateTimeOffset> fornece duas maneiras equivalentes de executar <xref:System.DateTime> para <xref:System.DateTimeOffset> conversão que são adequadas para a maioria das conversões:

- O Construtor <xref:System.DateTimeOffset.%23ctor%2A>, que cria um novo objeto <xref:System.DateTimeOffset> com base em um valor <xref:System.DateTime>.

- O operador de conversão implícita, que permite atribuir um valor de <xref:System.DateTime> a um objeto <xref:System.DateTimeOffset>.

Para valores de <xref:System.DateTime> UTC e local, a propriedade <xref:System.DateTimeOffset.Offset%2A> do valor de <xref:System.DateTimeOffset> resultante reflete precisamente o deslocamento UTC ou fuso horário local. Por exemplo, o código a seguir converte uma hora UTC em seu valor de <xref:System.DateTimeOffset> equivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Nesse caso, o deslocamento da variável `utcTime2` é 00:00. Da mesma forma, o código a seguir converte uma hora local em seu valor de <xref:System.DateTimeOffset> equivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

No entanto, para <xref:System.DateTime> valores cuja propriedade <xref:System.DateTime.Kind%2A> é <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, esses dois métodos de conversão produzem um valor de <xref:System.DateTimeOffset> cujo deslocamento é o do fuso horário local. Isso é mostrado no exemplo a seguir, que é executado no fuso horário padrão do Pacífico americano.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Se o valor de <xref:System.DateTime> refletir a data e a hora em algo diferente do fuso horário local ou UTC, você poderá convertê-lo em um valor de <xref:System.DateTimeOffset> e preservar suas informações de fuso horário chamando o construtor de <xref:System.DateTimeOffset.%23ctor%2A> sobrecarregado. Por exemplo, o exemplo a seguir instancia um objeto <xref:System.DateTimeOffset> que reflete a hora padrão central.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

O segundo parâmetro para essa sobrecarga de construtor, um objeto <xref:System.TimeSpan> que representa o deslocamento do tempo do UTC, deve ser recuperado chamando o método <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> do fuso horário correspondente do tempo. O parâmetro único do método é o valor <xref:System.DateTime> que representa a data e hora a serem convertidas. Se o fuso horário der suporte ao horário de verão, este parâmetro permite que o método determine o deslocamento apropriado para aquela data e hora determinada.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversões de DateTimeOffset em DateTime

A propriedade <xref:System.DateTimeOffset.DateTime%2A> é mais comumente usada para executar <xref:System.DateTimeOffset> para <xref:System.DateTime> conversão. No entanto, ele retorna um valor <xref:System.DateTime> cuja propriedade <xref:System.DateTime.Kind%2A> é <xref:System.DateTimeKind.Unspecified>, como ilustra o exemplo a seguir.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Isso significa que todas as informações sobre a relação do valor de <xref:System.DateTimeOffset> com o UTC são perdidas pela conversão quando a propriedade <xref:System.DateTimeOffset.DateTime%2A> é usada. Isso afeta <xref:System.DateTimeOffset> valores que correspondem à hora UTC ou à hora local do sistema porque a estrutura de <xref:System.DateTimeOffset.DateTime%2A> reflete apenas esses dois fusos horários em sua propriedade <xref:System.DateTime.Kind%2A>.

Para preservar o máximo possível de informações de fuso horário ao converter um <xref:System.DateTimeOffset> para um valor de <xref:System.DateTime>, você pode usar as propriedades <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> e <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>.

### <a name="converting-a-utc-time"></a>Convertendo uma hora UTC

Para indicar que um valor de <xref:System.DateTimeOffset.DateTime%2A> convertido é a hora UTC, você pode recuperar o valor da propriedade <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>. Ele difere da propriedade <xref:System.DateTimeOffset.DateTime%2A> de duas maneiras:

- Ele retorna um valor <xref:System.DateTime> cuja propriedade <xref:System.DateTime.Kind%2A> é <xref:System.DateTimeKind.Utc>.

- Se o valor da propriedade <xref:System.DateTimeOffset.Offset%2A> não for igual a <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, ele converterá a hora em UTC.

> [!NOTE]
> Se seu aplicativo exigir que valores de <xref:System.DateTime> convertidos identifiquem inequivocamente um único ponto no tempo, considere usar a propriedade <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> para lidar com todas as <xref:System.DateTimeOffset> para <xref:System.DateTime> conversões.

O código a seguir usa a propriedade <xref:System.DateTimeOffset.UtcDateTime%2A> para converter um valor de <xref:System.DateTimeOffset> cujo deslocamento é igual a <xref:System.TimeSpan.Zero?displayProperty=nameWithType> a um valor de <xref:System.DateTime>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

O código a seguir usa a propriedade <xref:System.DateTimeOffset.UtcDateTime%2A> para executar uma conversão de fuso horário e uma conversão de tipo em um valor de <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Convertendo uma hora local

Para indicar que um valor de <xref:System.DateTimeOffset> representa a hora local, você pode passar o valor de <xref:System.DateTime> retornado pela propriedade <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> para o método `static` (`Shared` no Visual Basic) <xref:System.DateTime.SpecifyKind%2A>. O método retorna a data e a hora passados para ele como seu primeiro parâmetro, mas define a propriedade <xref:System.DateTime.Kind%2A> para o valor especificado pelo segundo parâmetro. O código a seguir usa o método <xref:System.DateTime.SpecifyKind%2A> ao converter um valor de <xref:System.DateTimeOffset> cujo deslocamento corresponde ao do fuso horário local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Você também pode usar a propriedade <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> para converter um valor de <xref:System.DateTimeOffset> em um valor de <xref:System.DateTime> local. A propriedade <xref:System.DateTime.Kind%2A> do valor de <xref:System.DateTime> retornado é <xref:System.DateTimeKind.Local>. O código a seguir usa a propriedade <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> ao converter um valor de <xref:System.DateTimeOffset> cujo deslocamento corresponde ao do fuso horário local. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Quando você recupera um valor de <xref:System.DateTime> usando a propriedade <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>, o acessador de `get` da propriedade primeiro converte o valor de <xref:System.DateTimeOffset> para UTC e, em seguida, converte-o na hora local chamando o método <xref:System.DateTimeOffset.ToLocalTime%2A>. Isso significa que você pode recuperar um valor da propriedade <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> para executar uma conversão de fuso horário ao mesmo tempo em que executa uma conversão de tipo. Isso também significa que as regras de ajuste do fuso horário local são aplicadas na execução da conversão. O código a seguir ilustra o uso da propriedade <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> para executar um tipo e uma conversão de fuso horário.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Um método de conversão de uso geral

O exemplo a seguir define um método chamado `ConvertFromDateTimeOffset` que converte <xref:System.DateTimeOffset> valores para <xref:System.DateTime> valores. Com base em seu deslocamento, ele determina se o valor de <xref:System.DateTimeOffset> é uma hora UTC, uma hora local ou algum outro momento e define a propriedade de <xref:System.DateTime.Kind%2A> do valor de data e hora retornado de forma adequada.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

O exemplo a seguir chama o método `ConvertFromDateTimeOffset` para converter <xref:System.DateTimeOffset> valores que representam uma hora UTC, uma hora local e uma hora no fuso horário padrão central dos EUA.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Observe que esse código faz duas suposições que, dependendo do aplicativo e da fonte de seus valores de data e hora, podem não ser sempre válidas:

- Ele assume que um valor de data e hora cujo deslocamento é <xref:System.TimeSpan.Zero?displayProperty=nameWithType> representa o UTC. Na verdade, UTC não é uma hora em um determinado fuso horário, mas a hora em relação à qual as horas nos fusos horários do mundo são padronizadas. Os fusos horários também podem ter um deslocamento de <xref:System.TimeSpan.Zero>.

- Ele supõe que uma data e hora cujo deslocamento é igual ao do fuso horário local representa o fuso horário local. Como os valores de data e hora são dissociados do seu fuso horário original, este pode não ser o caso. A data e hora podem ter sido originadas em outro fuso horário com o mesmo deslocamento.

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
