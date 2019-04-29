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
ms.openlocfilehash: d4bce84d26e8f498f065c887b583e18d8ea7c786
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61901921"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Convertendo entre DateTime e DateTimeOffset

Embora o <xref:System.DateTimeOffset> estrutura fornece um maior grau de reconhecimento de fuso horário que o <xref:System.DateTime> estrutura, <xref:System.DateTime> parâmetros são usados mais comumente em chamadas de método. Por isso, a habilidade de converter <xref:System.DateTimeOffset> valores <xref:System.DateTime> valores e vice-versa é particularmente importante. Este tópico mostra como executar essas conversões de maneira a preservar o máximo possível de informações de fuso horário.

> [!NOTE]
> Tanto a <xref:System.DateTime> e o <xref:System.DateTimeOffset> tipos têm algumas limitações para representar horas em fusos horários. Com sua <xref:System.DateTime.Kind%2A> propriedade, <xref:System.DateTime> pode refletir somente o tempo Universal Coordenado (UTC) e o fuso horário local do sistema. <xref:System.DateTimeOffset> reflete um tempo de deslocamento do UTC, mas ele não reflete o fuso horário real ao qual esse deslocamento pertence. Para obter detalhes sobre valores de hora e o suporte para fusos horários, consulte [escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversões de DateTime para DateTimeOffset

O <xref:System.DateTimeOffset> estrutura oferece duas maneiras equivalentes de executar <xref:System.DateTime> para <xref:System.DateTimeOffset> conversão que são adequadas para a maioria das conversões:

* O <xref:System.DateTimeOffset.%23ctor%2A> construtor, que cria um novo <xref:System.DateTimeOffset> objeto com base em um <xref:System.DateTime> valor.

* O operador de conversão implícita, que permite que você atribua uma <xref:System.DateTime> de valor para um <xref:System.DateTimeOffset> objeto.

Para UTC e local <xref:System.DateTime> valores, o <xref:System.DateTimeOffset.Offset%2A> propriedade resultantes <xref:System.DateTimeOffset> valor reflete com precisão o deslocamento de fuso UTC ou hora local. Por exemplo, o código a seguir converte uma hora UTC em seu equivalente <xref:System.DateTimeOffset> valor.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Nesse caso, o deslocamento da variável `utcTime2` é 00:00. Da mesma forma, o código a seguir converte um horário local para seu equivalente <xref:System.DateTimeOffset> valor.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

No entanto, para <xref:System.DateTime> valores cuja <xref:System.DateTime.Kind%2A> é de propriedade <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, esses dois métodos de conversão produzem um <xref:System.DateTimeOffset> valor cujo deslocamento é o de fuso horário local. Isso é mostrado no exemplo a seguir, que é executado no Fuso horário padrão do Pacífico.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Se o <xref:System.DateTime> valor reflete a data e hora em algo diferente do fuso horário local ou UTC, você pode convertê-lo para um <xref:System.DateTimeOffset> de valor e preservar suas informações de fuso horário chamando sobrecarregado <xref:System.DateTimeOffset.%23ctor%2A> construtor. Por exemplo, o exemplo a seguir cria uma instância de um <xref:System.DateTimeOffset> objeto que reflete a hora padrão Central.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

O segundo parâmetro para essa sobrecarga de construtor, um <xref:System.TimeSpan> objeto que representa o deslocamento de hora do UTC, deve ser recuperado chamando o <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> método do fuso horário correspondente de hora. O parâmetro do método único é a <xref:System.DateTime> valor que representa a data e hora a ser convertido. Se o fuso horário der suporte ao horário de verão, este parâmetro permite que o método determine o deslocamento apropriado para aquela data e hora determinada.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversões de DateTimeOffset em DateTime

O <xref:System.DateTimeOffset.DateTime%2A> propriedade é mais comumente usada para realizar <xref:System.DateTimeOffset> para <xref:System.DateTime> conversão. No entanto, ela retorna um <xref:System.DateTime> valor cuja <xref:System.DateTime.Kind%2A> é de propriedade <xref:System.DateTimeKind.Unspecified>, como mostra o exemplo a seguir.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Isso significa que todas as informações sobre o <xref:System.DateTimeOffset> relação do valor de UTC é perdida pela conversão quando a <xref:System.DateTimeOffset.DateTime%2A> propriedade é usada. Isso afeta <xref:System.DateTimeOffset> valores que correspondem à hora UTC ou a hora do sistema local porque o <xref:System.DateTimeOffset.DateTime%2A> estrutura reflete somente esses dois fusos horários no seu <xref:System.DateTime.Kind%2A> propriedade.

Para preservar o máximo possível de informações de fuso horário ao converter um <xref:System.DateTimeOffset> para um <xref:System.DateTime> valor, você pode usar o <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> e <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedades.

### <a name="converting-a-utc-time"></a>Convertendo uma hora UTC

Para indicar que um convertido <xref:System.DateTimeOffset.DateTime%2A> valor é a hora UTC, você pode recuperar o valor da <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> propriedade. Ele difere do <xref:System.DateTimeOffset.DateTime%2A> propriedade de duas maneiras:

* Ele retorna um <xref:System.DateTime> valor cuja <xref:System.DateTime.Kind%2A> é de propriedade <xref:System.DateTimeKind.Utc>.

* Se o <xref:System.DateTimeOffset.Offset%2A> não é igual a valor da propriedade <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, ele converte a hora em UTC.

> [!NOTE]
> Se seu aplicativo requer que convertido <xref:System.DateTime> valores identificam sem ambiguidade um único ponto no tempo, você deve considerar usar o <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> propriedade lidar com todo <xref:System.DateTimeOffset> para <xref:System.DateTime> conversões.

O código a seguir usa o <xref:System.DateTimeOffset.UtcDateTime%2A> propriedade para converter um <xref:System.DateTimeOffset> cujo deslocamento é igual ao valor de <xref:System.TimeSpan.Zero?displayProperty=nameWithType> para um <xref:System.DateTime> valor.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

O código a seguir usa o <xref:System.DateTimeOffset.UtcDateTime%2A> propriedade para executar uma conversão de fuso horário e uma conversão de tipo em um <xref:System.DateTimeOffset> valor.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Convertendo uma hora local

Para indicar que um <xref:System.DateTimeOffset> valor representa a hora local, você pode passar a <xref:System.DateTime> valor retornado pela <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> propriedade para o `static` (`Shared` no Visual Basic) <xref:System.DateTime.SpecifyKind%2A> método. O método retorna a data e hora passada para ele como seu primeiro parâmetro, mas define o <xref:System.DateTime.Kind%2A> propriedade para o valor especificado pelo seu segundo parâmetro. O código a seguir usa o <xref:System.DateTime.SpecifyKind%2A> método ao converter um <xref:System.DateTimeOffset> valor cujo deslocamento corresponde do fuso horário local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Você também pode usar o <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedade para converter um <xref:System.DateTimeOffset> valor até um local <xref:System.DateTime> valor. O <xref:System.DateTime.Kind%2A> propriedade retornada <xref:System.DateTime> valor é <xref:System.DateTimeKind.Local>. O código a seguir usa o <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedade ao converter um <xref:System.DateTimeOffset> valor cujo deslocamento corresponde do fuso horário local. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Quando você recuperar um <xref:System.DateTime> valor usando o <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedade, a propriedade `get` acessador primeiro converte o <xref:System.DateTimeOffset> valor para UTC, em seguida, converte a hora local chamando o <xref:System.DateTimeOffset.ToLocalTime%2A> método. Isso significa que você pode recuperar o valor de <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedade para executar uma conversão de fuso horário ao mesmo tempo que você executa uma conversão de tipo. Isso também significa que as regras de ajuste do fuso horário local são aplicadas na execução da conversão. O código a seguir ilustra o uso do <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriedade para executar um tipo e uma conversão de fuso horário.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Um método de conversão de finalidade geral

O exemplo a seguir define um método chamado `ConvertFromDateTimeOffset` que converte <xref:System.DateTimeOffset> valores <xref:System.DateTime> valores. Com base no seu deslocamento, ele determina se o <xref:System.DateTimeOffset> valor é uma hora UTC, uma hora local ou outro momento e define o valor de hora e data retornada <xref:System.DateTime.Kind%2A> propriedade adequadamente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

A exemplo a seguir chama o `ConvertFromDateTimeOffset` método para converter <xref:System.DateTimeOffset> valores que representam uma hora UTC, uma hora local e uma hora nos EUA Fuso horário padrão central.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Observe que esse código faz duas suposições que, dependendo do aplicativo e da fonte de seus valores de data e hora, podem não ser sempre válidas:

* Ele pressupõe que uma data e hora valor cujo deslocamento é <xref:System.TimeSpan.Zero?displayProperty=nameWithType> representa o UTC. Na verdade, UTC não é uma hora em um determinado fuso horário, mas a hora em relação à qual as horas nos fusos horários do mundo são padronizadas. Fusos horários também podem ter um deslocamento de <xref:System.TimeSpan.Zero>.

* Ele supõe que uma data e hora cujo deslocamento é igual ao do fuso horário local representa o fuso horário local. Como os valores de data e hora são dissociados do seu fuso horário original, este pode não ser o caso. A data e hora podem ter sido originadas em outro fuso horário com o mesmo deslocamento.

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
