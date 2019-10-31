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
ms.openlocfilehash: 5425d94daf8ab023bef4a1a68f06d5c276499825
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132574"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo

Os aplicativos .NET que usam informações de data e hora são muito diferentes e podem usar essas informações de várias maneiras. Os usos de informações de data e hora mais comuns incluem uma ou mais das seguintes opções:

- Para refletir somente uma data, uma vez que a informação de tempo não é importante.

- Para refletir somente um tempo, uma vez que a informação de data não é importante.

- Para refletir uma data abstrata e um tempo que não está vinculado a uma hora e local específicos (por exemplo, a maioria das lojas em um uma cadeia internacional abre em dias da semana às 9h).

- Para recuperar informações de data e hora de fontes fora do .NET, normalmente, onde as informações de data e hora são armazenadas em um tipo de dados simples.

- Para identificar um único ponto no tempo de maneira única e não ambígua. Alguns aplicativos exigem que uma data e hora não seja ambígua somente no sistema host; outros exigem que ela não seja ambígua entre sistemas (ou seja, uma data serializada em um sistema pode ser significativamente desserializada e usada em outro sistema em qualquer lugar do mundo).

- Para preservar vários horários relacionados (como o horário local do solicitante e o horário de recebimento de uma solicitação Web pelo servidor).

- Para realizar a aritmética de data e hora, possivelmente com um resultado que identifica de maneira única e não ambígua um único ponto no tempo.

O .NET inclui os tipos <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>e <xref:System.TimeZoneInfo>, que podem ser usados para criar aplicativos que funcionam com datas e horas.

> [!NOTE]
> Este tópico não aborda <xref:System.TimeZone> porque sua funcionalidade está quase totalmente incorporada na classe <xref:System.TimeZoneInfo>. Sempre que possível, use a classe <xref:System.TimeZoneInfo> em vez da classe <xref:System.TimeZone>.

## <a name="the-datetime-structure"></a>A estrutura DateTime

Um valor <xref:System.DateTime> define uma data e hora específicas. Ele inclui uma propriedade <xref:System.DateTime.Kind%2A> que fornece informações limitadas sobre o fuso horário ao qual essa data e hora pertencem. O valor de <xref:System.DateTimeKind> retornado pela propriedade <xref:System.DateTime.Kind%2A> indica se o valor de <xref:System.DateTime> representa a hora local (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), o tempo universal coordenado (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>) ou uma hora não especificada (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

A estrutura de <xref:System.DateTime> é adequada para aplicativos que fazem o seguinte:

- Trabalhar apenas com datas.

- Trabalhar apenas com horas.

- Trabalhar com datas e horas abstratas.

- Trabalhar com datas e horas para as quais as informações de fuso horário estão ausentes.

- Trabalhar apenas com datas e horas UTC.

- Recupere informações de data e hora de fontes fora do .NET, como bancos de dados SQL. Normalmente, essas fontes armazenam informações de data e hora em um formato simples que é compatível com a estrutura de <xref:System.DateTime>.

- Realizar aritmética de data e hora, mas que há preocupação com resultados gerais. Por exemplo, em uma operação de adição que soma seis meses a uma data e hora determinada, geralmente não é importante se o resultado é ajustado para horário de verão.

A menos que um determinado valor de <xref:System.DateTime> represente o UTC, esse valor de data e hora geralmente é ambíguo ou limitado em sua portabilidade. Por exemplo, se um valor de <xref:System.DateTime> representar a hora local, ele será portátil dentro desse fuso horário local (ou seja, se o valor for desserializado em outro sistema no mesmo fuso horário, esse valor ainda identificará um único ponto no tempo). Fora do fuso horário local, esse valor <xref:System.DateTime> pode ter várias interpretações. Se a propriedade de <xref:System.DateTime.Kind%2A> do valor for <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, ela será ainda menos portátil: agora ela é ambígua dentro do mesmo fuso horário e, possivelmente, no mesmo sistema em que ele foi serializado pela primeira vez. Somente se um valor de <xref:System.DateTime> representar UTC, esse valor identificará inequivocamente um único ponto no tempo, independentemente do sistema ou fuso horário no qual o valor é usado.

> [!IMPORTANT]
> Ao salvar ou compartilhar dados de <xref:System.DateTime>, o UTC deve ser usado e a propriedade <xref:System.DateTime.Kind%2A> do valor de <xref:System.DateTime> deve ser definida como <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>A estrutura DateTimeOffset

A estrutura de <xref:System.DateTimeOffset> representa um valor de data e hora, junto com um deslocamento que indica o quanto esse valor difere do UTC. Portanto, o valor sempre identifica sem ambiguidade um único ponto no tempo.

O tipo de <xref:System.DateTimeOffset> inclui toda a funcionalidade do tipo <xref:System.DateTime> junto com o reconhecimento de fuso horário. Isso o torna adequado para aplicativos que fazem o seguinte:

- Identifique de maneira única e não ambígua um único ponto no tempo. O tipo de <xref:System.DateTimeOffset> pode ser usado para definir de forma não ambígua o significado de "Now", para registrar tempos de transação, registrar os tempos de eventos do sistema ou do aplicativo e registrar os horários de criação e modificação do arquivo.

- Realizar aritmética geral de data e hora.

- Preserve vários tempos relacionados contanto que esses tempos sejam armazenados como dois valores separados ou como dois membros de uma estrutura.

> [!NOTE]
> Esses usos para <xref:System.DateTimeOffset> valores são muito mais comuns do que os valores de <xref:System.DateTime>. Como resultado, <xref:System.DateTimeOffset> deve ser considerado o tipo de data e hora padrão para o desenvolvimento de aplicativos.

Um valor de <xref:System.DateTimeOffset> não está vinculado a um determinado fuso horário, mas pode se originar de qualquer uma variedade de fusos horários. Para ilustrar isso, o exemplo a seguir lista os fusos horários para os quais um número de valores de <xref:System.DateTimeOffset> (incluindo um horário padrão do Pacífico local) pode pertencer.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

A saída mostra que cada valor de data e hora nesse exemplo pode pertencer a pelo menos três fusos horários diferentes. O valor <xref:System.DateTimeOffset> de 6/10/2007 mostra que se um valor de data e hora representa um horário de verão, seu deslocamento do UTC não necessariamente corresponde ao deslocamento UTC base do fuso horário de origem ou ao deslocamento do UTC encontrado em seu nome de exibição. Isso significa que, como um único valor de <xref:System.DateTimeOffset> não está rigidamente acoplado ao seu fuso horário, ele não pode refletir a transição de um fuso horário para e do horário de verão. Isso pode ser particularmente problemático quando a aritmética de data e hora é usada para manipular um valor de <xref:System.DateTimeOffset>. Para ver uma discussão sobre como realizar a aritmética de data e hora de uma forma que considere as regras de ajuste de um fuso horário, consulte [Executando operações aritméticas com datas e horas](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>A estrutura TimeSpan

A estrutura de <xref:System.TimeSpan> representa um intervalo de tempo. Seus dois usos típicos são:

- Refletir o intervalo de tempo entre dois valores de data e hora. Por exemplo, subtrair um valor <xref:System.DateTime> de outro retorna um valor <xref:System.TimeSpan>.

- Calcular o tempo decorrido. Por exemplo, a propriedade <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> retorna um valor de <xref:System.TimeSpan> que reflete o intervalo de tempo decorrido desde a chamada para um dos métodos de <xref:System.Diagnostics.Stopwatch> que começa a medir o tempo decorrido.

Um valor de <xref:System.TimeSpan> também pode ser usado como uma substituição para um valor de <xref:System.DateTime> quando esse valor reflete uma hora sem referência a um dia específico. Esse uso é semelhante às propriedades <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> e <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType>, que retornam um valor <xref:System.TimeSpan> que representa a hora sem referência a uma data. Por exemplo, a estrutura de <xref:System.TimeSpan> pode ser usada para refletir o tempo diário de abertura ou de fechamento de um repositório, ou pode ser usada para representar a hora em que qualquer evento regular ocorre.

O exemplo a seguir define uma estrutura de `StoreInfo` que inclui <xref:System.TimeSpan> objetos para horas de abertura e fechamento de armazenamento, bem como um objeto <xref:System.TimeZoneInfo> que representa o fuso horário do repositório. A estrutura também inclui dois métodos, `IsOpenNow` e `IsOpenAt`, que indica se o repositório está aberto em um momento especificado pelo usuário, que se considera estar no fuso horário local.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

A estrutura `StoreInfo` pode ser usada pelo código do cliente como o exposto a seguir.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>A classe TimeZoneInfo

A classe <xref:System.TimeZoneInfo> representa qualquer um dos fusos horários da terra e permite a conversão de qualquer data e hora em um fuso horário para seu equivalente em outro fuso horário. A classe <xref:System.TimeZoneInfo> torna possível trabalhar com datas e horas para que qualquer valor de data e hora identifique inequivocamente um único ponto no tempo. A classe <xref:System.TimeZoneInfo> também é extensível. Embora isso dependa das informações de fuso horário fornecidas para sistemas Windows e definidos no registro, ele dá suporte à criação de fusos horários personalizados. Ele também dá suporte à serialização e desserialização de informações de fuso horário.

Em alguns casos, aproveitar ao máximo a <xref:System.TimeZoneInfo> classe pode exigir mais trabalho de desenvolvimento. Se os valores de data e hora não estiverem firmemente acoplados aos fusos horários aos quais eles pertencem, será necessário um trabalho adicional. A menos que seu aplicativo forneça algum mecanismo para vincular uma data e hora com seu fuso horário associado, é fácil para um valor de data e hora específico se tornar desassociado de seu fuso horário. Um método de vinculação dessas informações é definir uma classe ou estrutura que contenha o valor de data e hora e seu objeto de fuso horário associado.

É possível obter suporte de fuso horário no .NET apenas se o fuso horário ao qual um valor de data e hora pertence for conhecido quando a instância desse objeto de data e hora for criada. Geralmente isso não acontece, especialmente em aplicativos Web ou de rede.

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
