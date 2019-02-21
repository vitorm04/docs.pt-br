---
title: Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ed41d7739822d531986d65faa820ab7100c6651
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600109"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo

Os aplicativos .NET que usam informações de data e hora são muito diferentes e podem usar essas informações de várias maneiras. As formas de utilização mais comuns de data e hora incluem uma ou mais das seguintes opções:

* Para refletir somente uma data, uma vez que a informação de tempo não é importante.

* Para refletir somente um tempo, uma vez que a informação de data não é importante.

* Para refletir uma data abstrata e um tempo que não está vinculado a uma hora e local específicos (por exemplo, a maioria das lojas em um uma cadeia internacional abre em dias da semana às 9h).

* Para recuperar informações de data e hora de fontes fora do .NET, normalmente em que as informações de data e hora são armazenadas em um tipo simples de dados.

* Para identificar um único ponto no tempo de maneira única e não ambígua. Alguns aplicativos exigem que uma data e hora não seja ambígua somente no sistema host; outros exigem que ela não seja ambígua entre sistemas (ou seja, uma data serializada em um sistema pode ser significativamente desserializada e usada em outro sistema em qualquer lugar do mundo).

* Para preservar vários horários relacionados (como o horário local do solicitante e o horário de recebimento de uma solicitação Web pelo servidor).

* Para realizar a aritmética de data e hora, possivelmente com um resultado que identifica de maneira única e não ambígua um único ponto no tempo.

O .NET inclui os tipos <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, e <xref:System.TimeZoneInfo>, que podem ser usados para criar aplicativos que funcionam com datas e horas.

> [!NOTE]
> Este tópico não aborda um quarto tipo, <xref:System.TimeZone>, porque sua funcionalidade é quase inteiramente incorporada a classe <xref:System.TimeZoneInfo>. Sempre que possível, os desenvolvedores devem usar a classe <xref:System.TimeZoneInfo>, em vez da classe <xref:System.TimeZone>.

## <a name="the-datetime-structure"></a>A estrutura DateTime

Um valor <xref:System.DateTime> define uma determinada data e hora. Ele inclui uma propriedade <xref:System.DateTime.Kind%2A> que fornece informações limitadas sobre o fuso horário ao qual essa data e hora pertencem. O valor <xref:System.DateTimeKind> retornado pela propriedade <xref:System.DateTime.Kind%2A> indica se o valor <xref:System.DateTime> representa a hora local (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), Tempo Universal Coordenado (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), ou uma hora não especificada (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

A estrutura <xref:System.DateTime> é adequada para aplicativos que fazem o seguinte:

* Trabalhar apenas com datas.

* Trabalhar apenas com horas.

* Trabalhar com datas e horas abstratas.

* Trabalhar com datas e horas para as quais as informações de fuso horário estão ausentes.

* Trabalhar apenas com datas e horas UTC.

* Recuperar informações de data e hora de fontes fora do .NET, como bancos de dados SQL. Normalmente, essas fontes armazenam informações de data e hora em um formato simples que é compatível com a estrutura <xref:System.DateTime>.

* Realizar aritmética de data e hora, mas que há preocupações com resultados gerais. Por exemplo, em uma operação de adição que soma seis meses a uma data e hora determinada, geralmente não é importante se o resultado é ajustado para horário de verão.

A menos que um determinado valor <xref:System.DateTime> represente o UTC, esse valor de data e hora geralmente é ambíguo ou limitado na sua portabilidade. Por exemplo, se um valor <xref:System.DateTime> representa a hora local, ele é portável dentro desse fuso horário local (ou seja, se o valor for desserializado em outro sistema no mesmo fuso horário, esse valor ainda identifica um único ponto no tempo). Fora do fuso horário local, o valor <xref:System.DateTime> pode ter várias interpretações. Se a propriedade <xref:System.DateTime.Kind%2A> do valor é <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, ela será ainda menos portável: agora é ambígua dentro do mesmo fuso horário e, possivelmente, até mesmo no mesmo sistema no qual ele foi serializado pela primeira vez. Somente se um valor <xref:System.DateTime> representar um UTC, esse valor identificará um único ponto no tempo, independentemente do sistema ou do fuso horário no qual o valor é usado.

> [!IMPORTANT]
> Ao salvar ou compartilhar dados <xref:System.DateTime>, o UTC deve ser usados e o valor da propriedade <xref:System.DateTime.Kind%2A> do valor <xref:System.DateTime> deve ser definida como <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>A estrutura DateTimeOffset

A estrutura <xref:System.DateTimeOffset> representa um valor de data e hora, junto com um deslocamento que indica quanto o valor difere do UTC. Portanto, o valor sempre identifica um único ponto no tempo.

O tipo <xref:System.DateTimeOffset> inclui toda a funcionalidade do tipo <xref:System.DateTime> junto com reconhecimento de fuso horário. Isso torna adequado para aplicativos que fazem o seguinte:

* Identifique de maneira única e não ambígua um único ponto no tempo. O tipo <xref:System.DateTimeOffset> pode ser usado para definir sem ambiguidade o significado de "agora", para tempos de transação do log, para registrar os tempos de eventos do sistema ou aplicativo e tempos de criação e modificação do arquivo de registro.

* Realizar aritmética geral de data e hora.

* Preserve vários tempos relacionados contanto que esses tempos sejam armazenados como dois valores separados ou como dois membros de uma estrutura.

> [!NOTE]
> Esses usos para os valores <xref:System.DateTimeOffset> são muito mais comuns do que aqueles para valores <xref:System.DateTime>. Como resultado, <xref:System.DateTimeOffset> deve ser considerado o tipo de data e hora padrão para o desenvolvimento de aplicativo.

Um valor <xref:System.DateTimeOffset> não está vinculado a um determinado fuso horário, mas podem se originar de qualquer dos vários fusos horários. Para ilustrar isso, o exemplo a seguir lista os fusos horários aos quais um número de valores <xref:System.DateTimeOffset> (incluindo um local da hora oficial do Pacífico) podem pertencer.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

A saída mostra que cada valor de data e hora nesse exemplo pode pertencer a pelo menos três fusos horários diferentes. O <xref:System.DateTimeOffset> valor de 6/10/2007 mostra que se um valor de data e hora representa um horário de verão, seu deslocamento do UTC não corresponde necessariamente ao deslocamento base do UTC do fuso horário originário ou ao deslocamento do UTC encontrado no seu nome de exibição. Isso significa que, como um único valor <xref:System.DateTimeOffset> não está acoplado ao seu fuso horário, não é possível refletir a transição de um fuso horário para e do horário de verão. Isso pode ser particularmente problemático quando a data e hora é usada para manipular um valor <xref:System.DateTimeOffset>. (Para uma discussão sobre como realizar aritmética com data e hora de uma maneira que leva em conta as regras de ajuste de um fuso horário, consulte [executando operações aritméticas com datas e horas](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>A estrutura TimeSpan

A estrutura <xref:System.TimeSpan> representa um intervalo de tempo. Seus dois usos típicos são:

* Refletir o intervalo de tempo entre dois valores de data e hora. Por exemplo, subtrair um valor <xref:System.DateTime> de outro  e retornae um valor <xref:System.TimeSpan>.

* Calcular o tempo decorrido. Por exemplo, a propriedade <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> retorna um valor <xref:System.TimeSpan> que reflete o intervalo de tempo decorrido desde a chamada de um método <xref:System.Diagnostics.Stopwatch> que começa a medir o tempo decorrido.

Um valor <xref:System.TimeSpan> também pode ser usado como uma substituição para um valor <xref:System.DateTime> quando esse valor reflete um tempo sem referência a uma determinada hora do dia. Esse uso é semelhante para as propriedades <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> e <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType>, que retornam um valor <xref:System.TimeSpan> que representa o tempo sem referência a uma data. Por exemplo, a estrutura <xref:System.TimeSpan> pode ser usada para refletir a abertura diária ou a hora de fechamento de uma loja, ou ele pode ser usado para representar a hora em que qualquer evento regular ocorre.

O exemplo a seguir define uma estrutura `StoreInfo` que inclui objetos <xref:System.TimeSpan> para armazenar a hora de abertura e fechamento, bem como um objeto <xref:System.TimeZoneInfo> que representa o fuso horário da loja. A estrutura também inclui dois métodos, `IsOpenNow` e `IsOpenAt`, que indica se o repositório está aberto em um momento especificado pelo usuário, que se considera estar no fuso horário local.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

A estrutura `StoreInfo` pode ser usada pelo código do cliente como o exposto a seguir.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>A classe TimeZoneInfo

A classe <xref:System.TimeZoneInfo> representa qualquer um dos fusos horários da Terra e permite a conversão de qualquer data e hora em um fuso horário equivalente ao seu em outro fuso horário. A classe <xref:System.TimeZoneInfo> possibilita trabalhar com datas e horas de modo que qualquer valor de data e hora identifica distintamente um único ponto no tempo. A classe <xref:System.TimeZoneInfo> também é extensível. Embora ela dependa de informações de fuso horário fornecido para sistemas Windows e definidos no registro, ela oferece suporte à criação de fusos horários personalizados. Ele também oferece suporte a serialização e desserialização de informações de fuso horário.

Em alguns casos, aproveitar o máximo da classe <xref:System.TimeZoneInfo> pode exigir trabalho de desenvolvimento adicional. Se os valores de data e hora não são estritamente acoplados aos fusos horários aos quais eles pertencem,ainda mais trabalho será necessário. A menos que seu aplicativo forneça algum mecanismo para vincular uma data e hora com seu fuso horário associado, é mais fácil para um determinado valor de data e hora se desassociar do seu fuso horário. Um método de vinculação dessas informações é definir uma classe ou estrutura que contenha o valor de data e hora e seu objeto de fuso horário associado.

É possível obter suporte de fuso horário no .NET apenas se o fuso horário ao qual um valor de data e hora pertence for conhecido quando a instância desse objeto de data e hora for criada. Geralmente isso não acontece, especialmente em aplicativos Web ou de rede.

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
