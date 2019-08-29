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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb91ed8edd0c5cd3cb1d051157596f311718195d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107059"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Convertendo entre DateTime e DateTimeOffset

Embora a <xref:System.DateTimeOffset> estrutura forneça um grau maior de reconhecimento de fuso horário do <xref:System.DateTime> que a <xref:System.DateTime> estrutura, os parâmetros são usados com mais frequência em chamadas de método. Por isso, a capacidade de converter <xref:System.DateTimeOffset> valores em <xref:System.DateTime> valores e vice-versa é particularmente importante. Este tópico mostra como executar essas conversões de uma maneira que preserva o máximo possível de informações de fuso horário.

> [!NOTE]
> Os <xref:System.DateTime> tipos<xref:System.DateTimeOffset> e têm algumas limitações ao representar os horários em fusos horários. Com sua <xref:System.DateTime.Kind%2A> Propriedade, <xref:System.DateTime> é capaz de refletir apenas o UTC (tempo Universal Coordenado) e o fuso horário local do sistema. <xref:System.DateTimeOffset>reflete o deslocamento de um tempo do UTC, mas não reflete o fuso horário real ao qual o deslocamento pertence. Para obter detalhes sobre valores de tempo e suporte para fusos horários, consulte [escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversões de DateTime para DateTimeOffset

A <xref:System.DateTimeOffset> estrutura fornece duas maneiras equivalentes de <xref:System.DateTime> executar <xref:System.DateTimeOffset> a conversão que são adequadas para a maioria das conversões:

- O <xref:System.DateTimeOffset.%23ctor%2A> Construtor, que cria um novo <xref:System.DateTimeOffset> objeto com base em <xref:System.DateTime> um valor.

- O operador de conversão implícita, que permite atribuir um <xref:System.DateTime> valor a um <xref:System.DateTimeOffset> objeto.

Para valores UTC e <xref:System.DateTime> local, a <xref:System.DateTimeOffset.Offset%2A> Propriedade do valor resultante <xref:System.DateTimeOffset> reflete com precisão o deslocamento de fuso horário local ou UTC. Por exemplo, o código a seguir converte uma hora UTC em seu <xref:System.DateTimeOffset> valor equivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Nesse caso, o deslocamento da variável `utcTime2` é 00:00. Da mesma forma, o código a seguir converte uma hora local <xref:System.DateTimeOffset> em seu valor equivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

No entanto <xref:System.DateTime> , para <xref:System.DateTime.Kind%2A> valores cuja <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>propriedade é, esses dois métodos de <xref:System.DateTimeOffset> conversão produzem um valor cujo deslocamento é o do fuso horário local. Isso é mostrado no exemplo a seguir, que é executado no Fuso horário padrão do Pacífico.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Se o <xref:System.DateTime> valor refletir a data e a hora em algo diferente do fuso horário local ou UTC, você poderá convertê-lo <xref:System.DateTimeOffset> em um valor e preservar suas informações de fuso horário <xref:System.DateTimeOffset.%23ctor%2A> chamando o construtor sobrecarregado. Por exemplo, o exemplo a seguir instancia um <xref:System.DateTimeOffset> objeto que reflete a hora padrão central.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

O segundo parâmetro para essa sobrecarga de construtor, <xref:System.TimeSpan> um objeto que representa o deslocamento de tempo do UTC, deve ser recuperado chamando o <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> método do fuso horário correspondente do tempo. O parâmetro único do método é o <xref:System.DateTime> valor que representa a data e a hora a serem convertidas. Se o fuso horário der suporte ao horário de verão, este parâmetro permite que o método determine o deslocamento apropriado para aquela data e hora determinada.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversões de DateTimeOffset em DateTime

A <xref:System.DateTimeOffset.DateTime%2A> propriedade é mais comumente usada para realizar <xref:System.DateTimeOffset> a <xref:System.DateTime> conversão. No entanto, ele <xref:System.DateTime> retorna um <xref:System.DateTime.Kind%2A> valor cuja <xref:System.DateTimeKind.Unspecified>propriedade é, como ilustra o exemplo a seguir.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Isso significa que todas as informações sobre <xref:System.DateTimeOffset> a relação do valor com o UTC são perdidas pela conversão quando <xref:System.DateTimeOffset.DateTime%2A> a propriedade é usada. Isso afeta <xref:System.DateTimeOffset> os valores que correspondem à hora UTC ou à hora local do sistema, pois <xref:System.DateTimeOffset.DateTime%2A> a estrutura reflete apenas esses dois fusos horários <xref:System.DateTime.Kind%2A> em sua propriedade.

Para preservar o máximo possível de informações de fuso horário ao converter <xref:System.DateTimeOffset> um para <xref:System.DateTime> um valor, você pode usar <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> as <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> Propriedades e.

### <a name="converting-a-utc-time"></a>Convertendo uma hora UTC

Para indicar que um valor <xref:System.DateTimeOffset.DateTime%2A> convertido é a hora UTC, você pode recuperar o valor <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> da propriedade. Ele difere da <xref:System.DateTimeOffset.DateTime%2A> propriedade de duas maneiras:

- Ele retorna um <xref:System.DateTime> valor cuja <xref:System.DateTime.Kind%2A> propriedade é <xref:System.DateTimeKind.Utc>.

- Se o <xref:System.DateTimeOffset.Offset%2A> valor da propriedade não for <xref:System.TimeSpan.Zero?displayProperty=nameWithType>igual, ele converterá a hora em UTC.

> [!NOTE]
> Se seu aplicativo exigir que os <xref:System.DateTime> valores convertidos identifiquem inequivocamente um único ponto no tempo, considere usar <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> a <xref:System.DateTime> propriedade para lidar <xref:System.DateTimeOffset> com todas as conversões.

O código a seguir usa <xref:System.DateTimeOffset.UtcDateTime%2A> a propriedade para converter <xref:System.DateTimeOffset> um valor cujo deslocamento <xref:System.TimeSpan.Zero?displayProperty=nameWithType> é igual <xref:System.DateTime> a um valor.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

O código a seguir usa <xref:System.DateTimeOffset.UtcDateTime%2A> a propriedade para executar uma conversão de fuso horário e uma conversão de tipo <xref:System.DateTimeOffset> em um valor.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Convertendo uma hora local

Para indicar que um <xref:System.DateTimeOffset> valor representa a hora local, você pode passar o <xref:System.DateTime> valor retornado pela <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> propriedade para o `static` método (`Shared` no Visual Basic) <xref:System.DateTime.SpecifyKind%2A> . O método retorna a data e a hora passados para ele como seu primeiro parâmetro, mas define <xref:System.DateTime.Kind%2A> a propriedade para o valor especificado pelo segundo parâmetro. O código a seguir usa <xref:System.DateTime.SpecifyKind%2A> o método ao converter <xref:System.DateTimeOffset> um valor cujo deslocamento corresponde ao do fuso horário local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Você também pode usar a <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedade para converter um <xref:System.DateTimeOffset> valor em um valor <xref:System.DateTime> local. A <xref:System.DateTime.Kind%2A> Propriedade do valor retornado <xref:System.DateTime> é <xref:System.DateTimeKind.Local>. O código a seguir usa <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> a propriedade ao converter <xref:System.DateTimeOffset> um valor cujo deslocamento corresponde ao do fuso horário local. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Quando você recupera um <xref:System.DateTime> valor usando a <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> Propriedade, o acessador da `get` Propriedade primeiro <xref:System.DateTimeOffset> converte o valor em UTC e, em seguida, converte-o <xref:System.DateTimeOffset.ToLocalTime%2A> em hora local chamando o método. Isso significa que você pode recuperar um valor da <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedade para executar uma conversão de fuso horário ao mesmo tempo em que executa uma conversão de tipo. Isso também significa que as regras de ajuste do fuso horário local são aplicadas na execução da conversão. O código a seguir ilustra o uso da <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedade para executar um tipo e uma conversão de fuso horário.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Um método de conversão de uso geral

O exemplo a seguir define um método `ConvertFromDateTimeOffset` chamado que <xref:System.DateTimeOffset> converte valores <xref:System.DateTime> em valores. Com base em seu deslocamento, ele determina se <xref:System.DateTimeOffset> o valor é uma hora UTC, uma hora local ou algum outro momento e define a <xref:System.DateTime.Kind%2A> propriedade de valor de data e hora retornada de forma adequada.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

O exemplo a seguir chama `ConvertFromDateTimeOffset` o método para <xref:System.DateTimeOffset> converter valores que representam uma hora UTC, uma hora local e uma hora nos EUA Fuso horário padrão central.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Observe que esse código faz duas suposições que, dependendo do aplicativo e da fonte de seus valores de data e hora, podem não ser sempre válidas:

- Ele assume que um valor de data e hora cujo deslocamento <xref:System.TimeSpan.Zero?displayProperty=nameWithType> é representa o UTC. Na verdade, UTC não é uma hora em um determinado fuso horário, mas a hora em relação à qual as horas nos fusos horários do mundo são padronizadas. Os fusos horários também podem ter um <xref:System.TimeSpan.Zero>deslocamento de.

- Ele supõe que uma data e hora cujo deslocamento é igual ao do fuso horário local representa o fuso horário local. Como os valores de data e hora são dissociados do seu fuso horário original, este pode não ser o caso. A data e hora podem ter sido originadas em outro fuso horário com o mesmo deslocamento.

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
