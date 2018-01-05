---
title: "Trabalhando com calendários"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET Framework], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3a54d5222edca0b42f30c33584f0f62aa96f9e2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-calendars"></a>Trabalhando com calendários

Embora um valor de data e hora representem um momento, sua representação de cadeia de caracteres depende da cultura e também das convenções usadas para exibir valores de data e hora por uma cultura específica e do calendário usado por essa cultura. Este tópico explora o suporte para calendários no .NET e aborda o uso das classes de calendário ao trabalhar com valores de data.

## <a name="calendars-in-net"></a>Calendários no .NET

Todos os calendários no .NET derivam de <xref:System.Globalization.Calendar?displayProperty=nameWithType> classe, que fornece a implementação de calendário base. Uma das classes que herda da classe <xref:System.Globalization.Calendar> é a classe <xref:System.Globalization.EastAsianLunisolarCalendar>, a qual é a classe base para todos os calendários lunissolares. .NET inclui as seguintes implementações de calendário:

* <xref:System.Globalization.ChineseLunisolarCalendar>, que representa o calendário lunissolar chinês.

* <xref:System.Globalization.GregorianCalendar>, que representa o calendário gregoriano. Esse calendário é particionado em subtipos adicionais (como árabe e francês do Oriente Médio) que são definidos pela enumeração <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType>. A propriedade <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> especifica o subtipo do calendário gregoriano.

* <xref:System.Globalization.HebrewCalendar>, que representa o calendário hebraico.

* <xref:System.Globalization.HijriCalendar>, que representa o calendário islâmico.

* <xref:System.Globalization.JapaneseCalendar>, que representa o calendário japonês.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, que representa o calendário lunissolar japonês.

* <xref:System.Globalization.JulianCalendar>, que representa o calendário juliano.

* <xref:System.Globalization.KoreanCalendar>, que representa o calendário coreano.

* <xref:System.Globalization.KoreanLunisolarCalendar>, que representa o calendário lunissolar coreano.

* <xref:System.Globalization.PersianCalendar>, que representa o calendário persa.

* <xref:System.Globalization.TaiwanCalendar>, que representa o calendário de Taiwan.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, que representa o calendário lunissolar de Taiwan.

* <xref:System.Globalization.ThaiBuddhistCalendar>, que representa o calendário tailandês budista.

* <xref:System.Globalization.UmAlQuraCalendar>, que representa o calendário Um Al Qura.

Um calendário pode ser usado em uma de duas formas:

* Como o calendário usado por uma cultura específica. Cada objeto <xref:System.Globalization.CultureInfo> contém um calendário atual, que é o calendário que o objeto está usando no momento. As representações de cadeia de caracteres de todos os valores de data e hora refletem automaticamente a cultura e seu calendário atual. Normalmente, o calendário atual é o calendário padrão da cultura. Os objetos <xref:System.Globalization.CultureInfo> também possuem calendários opcionais, que incluem os calendários adicionais que aquela cultura pode usar.

* Como calendário autônomo independente de uma cultura específica. Nesse caso, os métodos <xref:System.Globalization.Calendar> são usados para expressar datas como os valores que refletem o calendário.

Observe que seis classes de calendário – <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar> e <xref:System.Globalization.TaiwanLunisolarCalendar> – podem ser usadas apenas como calendários autônomos. Elas não são usadas por nenhuma cultura, seja como o calendário padrão ou como um calendário opcional.

## <a name="calendars-and-cultures"></a>Calendários e culturas

Cada cultura tem um calendário padrão, o qual é definido pela propriedade <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>. A propriedade <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> retorna uma matriz de objetos <xref:System.Globalization.Calendar> que especifica todos os calendários suportados por uma cultura específica, inclusive o calendário padrão da cultura.

O exemplo a seguir ilustra as propriedades <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> e <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. Ele cria objetos `CultureInfo` para as culturas Tailandês (Tailândia) e Japonês (Japão) e exibe seus calendários padrão e opcionais. Observe que, em ambos os casos, o calendário padrão da cultura também é incluído na coleção <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

O calendário em uso no momento por um objeto <xref:System.Globalization.CultureInfo> específico é definido pela propriedade <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> da cultura. O objeto <xref:System.Globalization.DateTimeFormatInfo> de uma cultura é retornado pela propriedade <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. Quando uma cultura é criada, o valor padrão é o mesmo valor da propriedade <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>. No entanto, você pode mudar o calendário atual da cultura para qualquer calendário contido na matriz retornada pela propriedade <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. Se você tentar definir o calendário atual como um calendário que não está incluído no valor da propriedade <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>, uma <xref:System.ArgumentException> será gerada.

O exemplo a seguir altera o calendário usado pela cultura Árabe (Arábia Saudita). Ele primeiro cria uma instância de um valor <xref:System.DateTime> e o exibe usando a cultura atual – que, nesse caso, é Inglês (Estados Unidos) – e o calendário atual da cultura (que, nesse caso, é o calendário gregoriano). Em seguida, ele muda a cultura atual para Árabe (Arábia Saudita) e exibe a data usando seu calendário padrão Um Al Qura. Finalmente, ele chama o método `CalendarExists` para determinar se o calendário islâmico é suportado pela cultura Árabe (Arábia Saudita). Como o calendário é suportado, ele muda o calendário atual para Hijri e, novamente, exibe a data. Observe que, em cada caso, a data é exibida usando o calendário atual da cultura atual.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Calendários e datas

Com exceção dos construtores que incluem um parâmetro de tipo <xref:System.Globalization.Calendar> e permitem que os elementos de uma data (ou seja, mês, dia e ano), reflitam valores em um calendário designado, os valores de <xref:System.DateTime> e <xref:System.DateTimeOffset> sempre são baseados no calendário gregoriano. Isso significa, por exemplo, que a propriedade <xref:System.DateTime.Year%2A?displayProperty=nameWithType> retorna o ano no calendário gregoriano e que a propriedade <xref:System.DateTime.Day%2A?displayProperty=nameWithType> retorna o dia do mês no calendário gregoriano.

> [!IMPORTANT]
> É importante lembrar que há uma diferença entre um valor de data e sua representação de cadeia de caracteres. O primeiro baseia-se no calendário gregoriano; o último baseia-se no calendário atual de uma determinada cultura.

O exemplo a seguir ilustra a diferença entre as propriedades <xref:System.DateTime> e seus métodos <xref:System.Globalization.Calendar> correspondentes. No exemplo, a cultura atual é Árabe (Egito), e o calendário atual é Um Al Qura. Um valor de <xref:System.DateTime> é definido como o décimo quinto dia do sétimo mês de 2011. Está claro que esse é interpretado como uma data gregoriana, pois esses mesmos valores são retornados pelo método <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> quando as convenções da cultura invariável são usadas. A representação de cadeia de caracteres da data que é formatada usando as convenções de cultura atual é 14/08/32, que é a data equivalente no calendário Um Al Qura. Em seguida, membros de `DateTime` e `Calendar` são usados para retornar o dia, mês e o ano do valor de <xref:System.DateTime>. Em cada caso, os valores retornados pelos membros de <xref:System.DateTime> refletem os valores do calendário gregoriano, enquanto que os valores retornados pelos membros de <xref:System.Globalization.UmAlQuraCalendar> refletem os valores do calendário Um Al Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Criando datas com base em um calendário

Como os valores <xref:System.DateTime> e <xref:System.DateTimeOffset> baseiam-se no calendário gregoriano, você deve chamar um construtor sobrecarregado que inclua um parâmetro do tipo <xref:System.Globalization.Calendar> para criar uma instância de um valor de data se você quiser usar os valores de dia, mês ou ano em um calendário diferente. Você também pode chamar uma das sobrecargas do método <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> de um calendário específico para criar uma instância de um objeto <xref:System.DateTime> com base nos valores de um calendário específico.

O exemplo a seguir cria uma instância de um valor de <xref:System.DateTime> ao passar um objeto <xref:System.Globalization.HebrewCalendar> para um construtor de <xref:System.DateTime> e cria uma instância de um segundo valor <xref:System.DateTime> ao chamar o método <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>. Como os dois valores são criados com valores idênticos do calendário hebraico, a chamada ao método <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> mostra que os dois valores de <xref:System.DateTime> são iguais.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Que representa as datas do calendário atual

Os métodos de formatação de data e hora sempre usam o calendário atual ao converter datas em cadeias de caracteres. Isso significa que a representação de cadeia de caracteres do ano, mês e dia do mês reflete o calendário atual, e não necessariamente o calendário gregoriano.

O exemplo a seguir mostra como o calendário atual afeta a representação de cadeia de caracteres de uma data. Ele muda a cultura atual de Chinês (Tradicional, Taiwan) e cria uma instância de um valor de data. Ele então exibe o calendário e a data atuais, altera o calendário atual para <xref:System.Globalization.TaiwanCalendar> e exibe o calendário e a data atuais mais uma vez. Na primeira vez que a data é exibida, ela é representada como uma data no calendário gregoriano. Na segunda vez que a data é exibida, ela é representada como uma data no calendário de Taiwan.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Que representam datas em um calendário não atual

Para representar uma data usando um calendário que não é o calendário atual de uma cultura específica, você deve chamar métodos do objeto <xref:System.Globalization.Calendar>. Por exemplo, os métodos <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> e <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> convertem o ano, o mês e o dia para valores que refletem um calendário específico.

> [!WARNING]
> Como alguns calendários são calendários não opcionais de qualquer cultura, representar datas nesses calendários sempre exige que você chame métodos de calendário. Isso é verdadeiro para todos os calendários que derivam das classes <xref:System.Globalization.EastAsianLunisolarCalendar>, de <xref:System.Globalization.JulianCalendar> e <xref:System.Globalization.PersianCalendar>.

O exemplo a seguir usa um objeto <xref:System.Globalization.JulianCalendar> para criar uma instância de uma data, 9 de janeiro de 1905, no calendário juliano. Quando essa data é exibida no calendário gregoriano (padrão), ela é representada como 22 de janeiro de 1905. Chamadas para métodos <xref:System.Globalization.JulianCalendar> individuais permitem que a data seja representada no calendário juliano.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Calendários e intervalos de datas

A data mais antiga suportada por um calendário é indicada pela propriedade <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> desse calendário. Para a classe <xref:System.Globalization.GregorianCalendar>, essa data é 1º de janeiro de 0001. C.E. A maioria dos outros calendários no .NET oferecem suporte a uma data posterior. Tentar trabalhar com um valor de data e hora que antecedem a data com suporte mais antiga de um calendário gerará uma exceção <xref:System.ArgumentOutOfRangeException>.

Porém, há uma exceção importante. O valor padrão (não inicializado) de um objeto <xref:System.DateTime> e um objeto <xref:System.DateTimeOffset> é igual ao valor de <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType>. Se você tentar formatar essa data em um calendário que não oferece suporte a 1 de janeiro de 0001 C.E. e você não fornecer um especificador de formato, o método de formatação usa o especificador de formato "s" (padrão de data/hora classificável) em vez do especificador de formato "G" (padrão geral de data/hora). Como resultado, a operação de formatação não gerará uma exceção <xref:System.ArgumentOutOfRangeException>. Em vez disso, retornará uma data sem suporte. Isso é ilustrado no exemplo a seguir, que exibe o valor de <xref:System.DateTime.MinValue?displayProperty=nameWithType> quando a cultura atual é configurada para Japonês (Japão) com o calendário japonês, e para Árabe (Egito) com o calendário Um Al Qura. Ela também define a cultura atual como Inglês (Estados Unidos) e chama o método <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> com cada um desses objetos <xref:System.Globalization.CultureInfo>. Em cada caso, a data é exibida usando o padrão classificável de data/hora.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Trabalhando com eras

Os calendários normalmente dividem as datas em eras. No entanto, o <xref:System.Globalization.Calendar> classes no .NET não oferecem suporte a cada era definido por um calendário e a maioria do <xref:System.Globalization.Calendar> classes dão suporte a apenas uma única era. Somente as classes <xref:System.Globalization.JapaneseCalendar> e <xref:System.Globalization.JapaneseLunisolarCalendar> oferecem suporte a várias eras.

### <a name="eras-and-era-names"></a>Nomes de era e eras

No .NET, inteiros que representam os eras suportados por uma implementação de calendário específico são armazenados na ordem inversa na <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> matriz. A era atual está no índice zero. Para classes <xref:System.Globalization.Calendar> que oferecem suporte a várias eras, cada índice sucessivo reflete a era anterior. A propriedade estática <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> define o índice de era atual na matriz <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> ; ela é uma constante cujo valor é sempre zero. As classes <xref:System.Globalization.Calendar> individuais também incluem os campos estáticos que retornam o valor da era atual. Elas são listadas na tabela a seguir.

| Classe do calendário                                        | Campo de era atual                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

O nome que corresponde a um número de era específico não pode ser recuperado com a passagem do número da era para o método <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> ou <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType>. O exemplo a seguir chama esses métodos para recuperar informações sobre o suporte a eras na classe <xref:System.Globalization.GregorianCalendar>.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

Além disso, a cadeia de caracteres de formato de data e hora personalizado "g" inclui o nome da era na representação de cadeia de caracteres de uma data e hora. Para obter mais informações, consulte [cadeias de caracteres de formato personalizado de data e hora](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Criando uma data com uma época

Para as duas classes <xref:System.Globalization.Calendar> que oferecem suporte a várias eras, uma data que consiste em um determinado valor de ano, mês, dia e dia do mês pode ser ambígua. Por exemplo, todas as quatro eras do <xref:System.Globalization.JapaneseCalendar> têm os anos numerados de 1 a 15. Normalmente, se uma era não é especificada, os métodos de data e hora e calendário assumem que os valores pertencem à era atual. Para especificar explicitamente a era ao criar uma instância de uma data para uma classe <xref:System.Globalization.Calendar> que oferece suporte a várias eras, você pode chamar o método <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>. Esse método permite especificar explicitamente uma era junto com o ano, mês, dia, hora, minuto, segundo e milissegundo do calendário.

O exemplo a seguir usa o método <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> para criar uma instância da mesma data, o primeiro mês do primeiro dia do segundo ano em cada suportada pela classe <xref:System.Globalization.JapaneseCalendar>. Ele então exibe a data nos calendários japonês e gregoriano. Ele também chama um construtor <xref:System.DateTime> para ilustrar que os métodos que criam valores de data sem especificar uma era criam as datas na era atual.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

### <a name="representing-dates-in-calendars-with-eras"></a>Que representam datas em calendários com eras

Se um objeto <xref:System.Globalization.Calendar> oferece suporte a eras e é o calendário atual de um objeto <xref:System.Globalization.CultureInfo>, a era está incluída na representação de cadeia de caracteres de um valor de data e hora para os padrões de data e hora completa, data completa e data abreviada. O exemplo a seguir exibe esses padrões de data quando a cultura atual é Japão (japanese) e o calendário atual é o calendário japonês.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> O <xref:System.Globalization.JapaneseCalendar> classe é a única classe de calendário no .NET que ambas as datas suporta em mais de um era e que pode ser o calendário atual de um <xref:System.Globalization.CultureInfo> objeto - especificamente, de um <xref:System.Globalization.CultureInfo> objeto que representa a cultura japonês (Japão).

Para todos os calendários, o especificador de formato personalizado “g” inclui a era na cadeia de caracteres de resultado. O exemplo a seguir usa a cadeia de caracteres de formato personalizado "MM-dd-aaaa g" para incluir a era na cadeia de caracteres de resultado quando o calendário atual é o calendário gregoriano.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

Em casos em que a representação de cadeia de caracteres de uma data é expressa em um calendário que não é o calendário atual, a classe <xref:System.Globalization.Calendar> inclui um método <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> que pode ser usado junto com <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> e os métodos <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> para indicar inequivocamente uma data e a era à qual ela pertence. O exemplo a seguir usa a classe <xref:System.Globalization.JapaneseLunisolarCalendar> para fornecer uma ilustração. No entanto, observe que incluir um nome ou abreviação significativa em vez de um inteiro para a era na cadeia de caracteres de resultado exige que você crie uma instância de um objeto <xref:System.Globalization.DateTimeFormatInfo> e faça de <xref:System.Globalization.JapaneseCalendar> o calendário atual. (O calendário <xref:System.Globalization.JapaneseLunisolarCalendar> não pode ser o calendário atual de qualquer cultura, mas, nesse caso, os dois calendários compartilham as mesmas eras.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

## <a name="see-also"></a>Consulte também

[Como: exibir datas em calendários não gregorianos](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
[exemplo: utilitário de intervalo de semana de calendário](http://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
