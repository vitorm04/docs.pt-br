---
title: Convertendo horários entre fusos horários
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
ms.openlocfilehash: d0b38523f054598ba6fb1f05a0183bc4ccff2120
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132561"
---
# <a name="converting-times-between-time-zones"></a>Convertendo horários entre fusos horários

Está se tornando cada vez mais importante para qualquer aplicativo que trabalha com datas e horas lidar com diferenças entre fusos horários. Um aplicativo não pode mais supor que todos os horários possam ser expressos na hora local, que é o tempo disponível na estrutura de <xref:System.DateTime>. Por exemplo, uma página da Web que exibe a hora atual no leste dos Estados Unidos não terá credibilidade para um cliente no leste da Ásia. Este tópico explica como converter horários de um fuso horário para outro, bem como converter <xref:System.DateTimeOffset> valores com reconhecimento de fuso horário limitado.

## <a name="converting-to-coordinated-universal-time"></a>Convertendo para o Tempo Universal Coordenado

O UTC (Tempo Universal Coordenado) é um padrão de tempo atômico de alta precisão. Os fusos horários do mundo são expressos como deslocamentos positivos ou negativos com relação ao UTC. Sendo assim, o UTC fornece uma espécie de hora livre de fuso horário ou com fuso horário neutro. O uso da hora em UTC é recomendado quando a portabilidade da data e hora entre computadores é importante. (Para obter detalhes e outras práticas recomendadas usando datas e horas, confira [codificando práticas recomendadas usando DateTime no .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10)).) Converter fusos horários individuais em UTC facilita as comparações de tempo.

> [!NOTE]
> Você também pode serializar uma estrutura de <xref:System.DateTimeOffset> para representar de forma não ambígua um único ponto no tempo. Como <xref:System.DateTimeOffset> objetos armazenam um valor de data e hora junto com seu deslocamento do UTC, eles sempre representam um determinado ponto no tempo em relação ao UTC.

A maneira mais fácil de converter uma hora em UTC é chamar o método de <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> de `static` (`Shared` no Visual Basic). A conversão exata executada pelo método depende do valor da propriedade <xref:System.DateTime.Kind%2A> do parâmetro de `dateTime`, como mostra a tabela a seguir.

| `DateTime.Kind`            | Conversão                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Converte a hora local para UTC.                                                    |
| `DateTimeKind.Unspecified` | Presume que o parâmetro `dateTime` é a hora local e converte a hora local para UTC. |
| `DateTimeKind.Utc`         | Retorna o parâmetro `dateTime` inalterado.                                    |

O código a seguir converte a hora local atual para UTC e exibe o resultado no console.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Se o valor de data e hora não representar a hora local ou UTC, o método <xref:System.DateTime.ToUniversalTime%2A> provavelmente retornará um resultado errado. No entanto, você pode usar o método <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> para converter a data e a hora de um fuso horário especificado. (Para obter detalhes sobre como recuperar um objeto de <xref:System.TimeZoneInfo> que representa o fuso horário de destino, consulte [localizando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) O código a seguir usa o método <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> para converter o horário padrão do leste em UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Observe que esse método gera uma <xref:System.ArgumentException> se a propriedade <xref:System.DateTime.Kind%2A> do objeto <xref:System.DateTime> e o fuso horário não forem correspondentes. Uma incompatibilidade ocorrerá se a propriedade <xref:System.DateTime.Kind%2A> for <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, mas o objeto <xref:System.TimeZoneInfo> não representar o fuso horário local ou se a propriedade <xref:System.DateTime.Kind%2A> for <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, mas o objeto <xref:System.TimeZoneInfo> não for igual a <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>.

Todos esses métodos levam <xref:System.DateTime> valores como parâmetros e retornam um valor de <xref:System.DateTime>. Para <xref:System.DateTimeOffset> valores, a estrutura de <xref:System.DateTimeOffset> tem um método de instância de <xref:System.DateTimeOffset.ToUniversalTime%2A> que converte a data e a hora da instância atual em UTC. O exemplo a seguir chama o método <xref:System.DateTimeOffset.ToUniversalTime%2A> para converter uma hora local e várias outras vezes em UTC (tempo Universal Coordenado).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Convertendo UTC em um fuso horário designado

Para converter UTC em hora local, consulte a seção "convertendo UTC para a hora local" a seguir. Para converter o UTC para a hora em qualquer fuso horário que você designar, chame o método <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>. O método utiliza dois parâmetros:

- O UTC a ser convertido. Deve ser um valor <xref:System.DateTime> cuja propriedade <xref:System.DateTime.Kind%2A> está definida como `Unspecified` ou `Utc`.

- O fuso horário no qual o UTC deve ser convertido.

O código a seguir converte o UTC para o Horário Padrão Central.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Convertendo UTC em hora local

Para converter UTC em hora local, chame o método <xref:System.DateTime.ToLocalTime%2A> do objeto <xref:System.DateTime> cujo tempo você deseja converter. O comportamento exato do método depende do valor da propriedade <xref:System.DateTime.Kind%2A> do objeto, como mostra a tabela a seguir.

| `DateTime.Kind`            | Conversão                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Retorna o valor de <xref:System.DateTime> inalterado.                                      |
| `DateTimeKind.Unspecified` | Pressupõe que o valor de <xref:System.DateTime> é UTC e converte o UTC para a hora local. |
| `DateTimeKind.Utc`         | Converte o valor de <xref:System.DateTime> para a hora local.                                 |

> [!NOTE]
> O método <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> se comporta de forma idêntica ao método `DateTime.ToLocalTime`. Ele usa um único parâmetro, que é o valor de data e hora a ser convertido.

Você também pode converter a hora em qualquer fuso horário designado para a hora local usando o método `static` (`Shared` no Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType>. Essa técnica é discutida na próxima seção.

## <a name="converting-between-any-two-time-zones"></a>Convertendo entre dois fusos horários

Você pode converter entre dois fusos horários usando um dos seguintes dois `static` (`Shared` em Visual Basic) métodos da classe <xref:System.TimeZoneInfo>:

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Os parâmetros desse método são o valor de data e hora a ser convertido, um objeto `TimeZoneInfo` que representa o fuso horário do valor de data e hora e um objeto `TimeZoneInfo` que representa o fuso horário para o qual converter o valor de data e hora.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Os parâmetros do método são o valor de data e hora a ser convertido, o identificador do fuso horário do valor de data e hora e o identificador do fuso horário para o qual converter o valor de data e hora.

Os dois métodos exigem que a propriedade <xref:System.DateTime.Kind%2A> do valor de data e hora para converter e o objeto <xref:System.TimeZoneInfo> ou o identificador de fuso horário que representa seu fuso horário correspondam uns aos outros. Caso contrário, um <xref:System.ArgumentException> será gerado. Por exemplo, se a propriedade `Kind` do valor de data e hora for `DateTimeKind.Local`, uma exceção será gerada se o objeto de `TimeZoneInfo` passado como um parâmetro para o método não for igual a `TimeZoneInfo.Local`. Uma exceção também será gerada se o identificador passado como um parâmetro para o método não for igual a `TimeZoneInfo.Local.Id`.

O exemplo a seguir usa o método <xref:System.TimeZoneInfo.ConvertTime%2A> para converter do horário padrão do Havaí para a hora local.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Convertendo valores de DateTimeOffset

Os valores de data e hora representados por <xref:System.DateTimeOffset> objetos não têm reconhecimento total de fuso horário porque o objeto é desassociado de seu fuso horário no momento em que é instanciado. No entanto, em muitos casos o aplicativo precisa apenas converter uma data e hora com base em dois deslocamentos diferentes do UTC, em vez da hora em fusos horários específicos. Para executar essa conversão, você pode chamar o método de <xref:System.DateTimeOffset.ToOffset%2A> da instância atual. O parâmetro único do método é o deslocamento do novo valor de data e hora que o método deve retornar.

Por exemplo, se a data e hora da solicitação de um usuário de uma página da Web for conhecida e for serializada como uma cadeia de caracteres no formato MM/dd/aaaa hh:mm:ss zzzz, o seguinte método `ReturnTimeOnServer` converte esse valor de data e hora para a data e hora no servidor Web.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Se o método for passado para a cadeia de caracteres "9/1/2007 5:32:07 -05:00", que representa a data e a hora em um fuso horário cinco horas anteriores à UTC, ele retornará 9/1/2007 3:32:07 AM-07:00 para um servidor localizado no fuso horário padrão do Pacífico americano.

A classe <xref:System.TimeZoneInfo> também inclui uma sobrecarga do método <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> que executa conversões de fuso horário com valores <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)>. Os parâmetros do método são um valor <xref:System.DateTimeOffset> e uma referência ao fuso horário no qual o tempo deve ser convertido. A chamada do método retorna um valor <xref:System.DateTimeOffset>. Por exemplo, o método `ReturnTimeOnServer` no exemplo anterior poderia ser reescrito da seguinte maneira para chamar o método <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29>.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Consulte também

- <xref:System.TimeZoneInfo>
- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
