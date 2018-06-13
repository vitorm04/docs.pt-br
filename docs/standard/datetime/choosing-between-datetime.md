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
ms.openlocfilehash: 368884e7f61f4504c8ca714165c543b19b3a1171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578255"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo

Os aplicativos .NET que usam informações de data e hora são muito diferentes e podem usar essas informações de várias maneiras. Os usos de informações de data e hora mais comuns incluem uma ou mais das seguintes opções:

* Para refletir somente uma data, uma vez que a informação de tempo não é importante.

* Para refletir somente um tempo, uma vez que a informação de data não é importante.

* Para refletir uma data abstrata e um tempo que não está vinculado a uma hora e local específicos (por exemplo, a maioria das lojas em um uma cadeia internacional abre em dias da semana às 9h).

* Para recuperar informações de data e hora de fontes de fora do .NET, normalmente onde informações de data e hora são armazenadas em um simples tipo de dados.

* Para identificar um único ponto no tempo de maneira única e não ambígua. Alguns aplicativos exigem que uma data e hora não seja ambígua somente no sistema host; outros exigem que ela não seja ambígua entre sistemas (ou seja, uma data serializada em um sistema pode ser significativamente desserializada e usada em outro sistema em qualquer lugar do mundo).

* Para preservar vários horários relacionados (como o horário local do solicitante e o horário de recebimento de uma solicitação Web pelo servidor).

* Para realizar a aritmética de data e hora, possivelmente com um resultado que identifica de maneira única e não ambígua um único ponto no tempo.

.NET inclui o <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, e <xref:System.TimeZoneInfo> tipos, que pode ser usado para criar aplicativos que funcionam com datas e horas.

> [!NOTE]
> Este tópico não aborda um quarto tipo, <xref:System.TimeZone>, porque sua funcionalidade é quase inteiramente incorporada a <xref:System.TimeZoneInfo> classe. Sempre que possível, os desenvolvedores devem usar o <xref:System.TimeZoneInfo> classe o <xref:System.TimeZone> classe.

## <a name="the-datetime-structure"></a>A estrutura DateTime

Um <xref:System.DateTime> valor define uma determinada data e hora. Ele inclui um <xref:System.DateTime.Kind%2A> propriedade que fornece informações limitadas sobre o fuso horário para o qual essa data e hora pertencem. O <xref:System.DateTimeKind> valor retornado pelo <xref:System.DateTime.Kind%2A> propriedade indica se o <xref:System.DateTime> valor representa a hora local (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), Tempo Universal Coordenado (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), ou um tempo não especificado (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

O <xref:System.DateTime> estrutura é adequada para aplicativos que fazem o seguinte:

* Trabalhar apenas com datas.

* Trabalhar apenas com horas.

* Trabalhar com datas e horas abstratas.

* Trabalhar com datas e horas para as quais as informações de fuso horário estão ausentes.

* Trabalhar apenas com datas e horas UTC.

* Recupere informações de data e hora de fontes fora do .NET, como bancos de dados SQL. Normalmente, essas fontes armazenam informações de data e hora em um formato simple que é compatível com o <xref:System.DateTime> estrutura.

* Realizar aritmética de data e hora, mas que há preocupação com resultados gerais. Por exemplo, em uma operação de adição que soma seis meses a uma data e hora determinada, geralmente não é importante se o resultado é ajustado para horário de verão.

A menos que um determinado <xref:System.DateTime> valor representa o UTC, data e valor de tempo é geralmente ambíguos ou limitados na sua portabilidade. Por exemplo, se um <xref:System.DateTime> valor representa a hora local, ele é portátil dentro desse fuso horário local (ou seja, se o valor é desserializado em outro sistema no mesmo fuso horário, que o valor ainda especificamente identifica um único ponto no tempo). Fora da zona de hora local, que <xref:System.DateTime> value pode ter vários interpretações. Se o valor <xref:System.DateTime.Kind%2A> é de propriedade <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, é ainda menos portátil: é agora ambíguo dentro da mesma zona de tempo e, possivelmente, até mesmo no mesmo sistema no qual ele foi serializado pela primeira vez. Somente se um <xref:System.DateTime> valor representa o UTC valor inequivocamente identifique um único ponto no tempo, independentemente do sistema ou o fuso horário em que o valor é usado.

> [!IMPORTANT]
> Ao salvar ou compartilhar <xref:System.DateTime> dados, UTC devem ser usados e o <xref:System.DateTime> do valor <xref:System.DateTime.Kind%2A> propriedade deve ser definida como <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>A estrutura DateTimeOffset

O <xref:System.DateTimeOffset> estrutura representa um valor de data e hora, junto com um deslocamento que indica quanto aquele valor diferencia o UTC. Portanto, o valor sempre identifica sem ambiguidade um único ponto no tempo.

O <xref:System.DateTimeOffset> tipo inclui toda a funcionalidade do <xref:System.DateTime> tipo junto com reconhecimento de fuso horário. Isso torna adequada para aplicativos que fazem o seguinte:

* Identifique de maneira única e não ambígua um único ponto no tempo. O <xref:System.DateTimeOffset> tipo pode ser usado para definir sem ambiguidade o significado de "agora", para tempos de transação de log para os horários de eventos do sistema ou aplicativo e tempos de criação e modificação do arquivo de registro.

* Realizar aritmética geral de data e hora.

* Preserve vários tempos relacionados contanto que esses tempos sejam armazenados como dois valores separados ou como dois membros de uma estrutura.

> [!NOTE]
> Esses usos para <xref:System.DateTimeOffset> os valores são muito mais comuns do que os <xref:System.DateTime> valores. Como resultado, <xref:System.DateTimeOffset> deve ser considerado o tipo padrão de data e hora para o desenvolvimento de aplicativos.

Um <xref:System.DateTimeOffset> valor não estiver associado a um determinado fuso horário, mas pode ser originado de qualquer dos fusos horários. Para ilustrar isso, o exemplo a seguir lista os fusos horários aos quais um número de <xref:System.DateTimeOffset> valores (incluindo um local da hora oficial do Pacífico) podem pertencer.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

A saída mostra que cada valor de data e hora nesse exemplo pode pertencer a pelo menos três fusos horários diferentes. O <xref:System.DateTimeOffset> valor de 6/10/2007 mostra que se um valor de data e hora representa um horário de verão, seu deslocamento do UTC não corresponde necessariamente deslocamento UTC base de origem do fuso horário ou o deslocamento do UTC encontrado no seu nome de exibição. Isso significa que, como um único <xref:System.DateTimeOffset> valor não está acoplado ao seu fuso horário, não é possível refletir a transição de uma zona de tempo para e a partir do horário de verão. Isso pode ser problemático principalmente quando a data e hora é usada para manipular um <xref:System.DateTimeOffset> valor. (Para uma discussão sobre como executar a data e hora de uma maneira que usa a conta de regras de ajuste de uma zona de tempo, consulte [executando operações aritméticas com datas e horas](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>A estrutura TimeSpan

O <xref:System.TimeSpan> estrutura representa um intervalo de tempo. Seus dois usos típicos são:

* Refletir o intervalo de tempo entre dois valores de data e hora. Por exemplo, subtrair um <xref:System.DateTime> valor de outro retorna um <xref:System.TimeSpan> valor.

* Calcular o tempo decorrido. Por exemplo, o <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> propriedade retorna um <xref:System.TimeSpan> valor que reflete o intervalo de tempo decorrido desde a chamada para uma da <xref:System.Diagnostics.Stopwatch> métodos que começa a medir o tempo decorrido.

Um <xref:System.TimeSpan> valor também pode ser usado como uma substituição para um <xref:System.DateTime> valor quando esse valor reflete um tempo sem referência para um determinado período do dia. Esse uso é semelhante do <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> e <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> propriedades que retornam um <xref:System.TimeSpan> valor que representa o tempo sem referência a uma data. Por exemplo, o <xref:System.TimeSpan> estrutura pode ser usada para refletir um armazenamento diária abertura ou fechamento tempo, ou ele pode ser usado para representar a hora em que ocorre algum evento regular.

O exemplo a seguir define uma `StoreInfo` estrutura inclui <xref:System.TimeSpan> objetos para armazenam de abertura e fechamento vezes, bem como um <xref:System.TimeZoneInfo> objeto que representa o fuso horário da loja. A estrutura também inclui dois métodos, `IsOpenNow` e `IsOpenAt`, que indica se o repositório está aberto em um momento especificado pelo usuário, que se considera estar no fuso horário local.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

A estrutura `StoreInfo` pode ser usada pelo código do cliente como o exposto a seguir.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>A classe TimeZoneInfo

O <xref:System.TimeZoneInfo> classe representa qualquer um dos fusos horários da Terra e permite a conversão de qualquer data e hora em um fuso horário para seu equivalente em outro fuso horário. O <xref:System.TimeZoneInfo> classe torna possível trabalhar com datas e horas de modo que qualquer valor de data e hora especificamente identifica um único ponto no tempo. O <xref:System.TimeZoneInfo> classe também é extensível. Embora ele depende de informações de fuso horário fornecido para os sistemas Windows e definidas no registro, ele oferece suporte à criação de fusos horários personalizados. Ele também dá suporte a serialização e desserialização de informações de fuso horário.

Em alguns casos, aproveitando ao máximo o <xref:System.TimeZoneInfo> classe pode exigir mais trabalho de desenvolvimento. Se os valores de data e hora não estão estritamente ligados aos fusos horários à qual eles pertencem, trabalho posterior é necessários. A menos que seu aplicativo fornece um mecanismo para vincular uma data e hora com seu fuso horário associado, é fácil para uma determinada data e o valor de tempo para se tornar desassociado do seu fuso horário. Um método de vinculação dessas informações é definir uma classe ou estrutura que contenha o valor de data e hora e seu objeto de fuso horário associado.

É possível obter suporte de fuso horário no .NET apenas se o fuso horário ao qual um valor de data e hora pertence for conhecido quando a instância desse objeto de data e hora for criada. Geralmente isso não acontece, especialmente em aplicativos Web ou de rede.

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
