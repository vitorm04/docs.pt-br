---
title: Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo
description: Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2dd84ee8-9f0f-4054-9537-155857a460cd
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: f8a603bab32afd0b8e7d13c9c5755e3f14a9d2bd

---

# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo

Os aplicativos .NET que usam informações de data e hora são muito diferentes e podem usar essas informações de várias maneiras. Os usos de informações de data e hora mais comuns incluem uma ou mais das seguintes opções:

* Para refletir somente uma data, uma vez que a informação de tempo não é importante.

* Para refletir somente um tempo, uma vez que a informação de data não é importante.

* Para refletir uma data abstrata e um tempo que não está vinculado a uma hora e local específicos (por exemplo, a maioria das lojas em um uma cadeia internacional abre em dias da semana às 9h).

* Para recuperar informações de data e hora de fontes fora do aplicativo .NET, normalmente na qual as informações de data e hora são armazenadas em um tipo de dados simples.

* Para identificar um único ponto no tempo de maneira única e não ambígua. Alguns aplicativos exigem que uma data e hora não seja ambígua somente no sistema host; outros exigem que ela não seja ambígua entre sistemas (ou seja, uma data serializada em um sistema pode ser significativamente desserializada e usada em outro sistema em qualquer lugar do mundo). 

* Para preservar vários horários relacionados (como o horário local do solicitante e o horário de recebimento de uma solicitação Web pelo servidor).

* Para realizar a aritmética de data e hora, possivelmente com um resultado que identifica de maneira única e não ambígua um único ponto no tempo. 

O .NET inclui os tipos [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset), [System.TimeSpan](xref:System.TimeSpan) e [System.TimeZoneInfo](xref:System.TimeZoneInfo), que podem ser usados para criar aplicativos que funcionam com datas e horas. 

> [!NOTE]
> Este tópico não discute o tipo `TimeZone` mais antigo, porque sua funcionalidade é quase inteiramente incorporada à classe [System.TimeZoneInfo](xref:System.TimeZoneInfo). Sempre que possível, os desenvolvedores devem usar a classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) em vez da classe `TimeZone`.


## <a name="the-datetime-structure"></a>A estrutura DateTime

Um valor [System.DateTime](xref:System.DateTime) define uma data e hora específica. Ele inclui uma propriedade [Kind](xref:System.DateTime.Kind) que fornece informações limitadas sobre o fuso horário ao qual essa data e hora pertencem. O valor [DateTimeKind](xref:System.DateTimeKind) retornado pela propriedade [Kind](xref:System.DateTime.Kind) indica se o valor [DateTime](xref:System.DateTime) representa a hora local [DateTimeKind.Local](xref:System.DateTimeKind.Local)), UTC (Tempo Universal Coordenado) [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) ou uma hora não específicada [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).

A estrutura [DateTime](xref:System.DateTime) é adequada para aplicativos que fazem o seguinte: 

* Trabalhar apenas com datas.

* Trabalhar apenas com horas.

* Trabalhar com datas e horas abstratas.

* Trabalhar com datas e horas para as quais as informações de fuso horário estão ausentes. 

* Trabalhar apenas com datas e horas UTC. 

* Recuperar informações de data e hora de fontes fora do .NET Framework, como bancos de dados do SQL. Normalmente, essas fontes armazenam informações de data e hora em um formato simples, compatível com a estrutura [DateTime](xref:System.DateTime).

* Realizar aritmética de data e hora, mas que há preocupação com resultados gerais. Por exemplo, em uma operação de adição que soma seis meses a uma data e hora determinada, geralmente não é importante se o resultado é ajustado para horário de verão.

A menos que um valor [DateTime](xref:System.DateTime) determinado represente o UTC, o valor de data e hora geralmente é ambíguo ou limitado na sua portabilidade. Por exemplo, se um valor [DateTime](xref:System.DateTime) representa a hora local, ele é portátil dentro desse fuso horário local (isto é, se o valor for desserializado em outro sistema no mesmo fuso horário, esse valor ainda identificará de maneira não ambígua um único ponto no tempo). Fora do fuso horário local, esse valor [DateTime](xref:System.DateTime) pode ter várias interpretações. Se a propriedade [Kind](xref:System.DateTime.Kind) do valor for [DateTimeKind](xref:System.DateTimeKind.Unspecified), ela será ainda menos portátil: ela agora é ambígua dentro do mesmo fuso horário e possivelmente até no mesmo sistema no qual ele foi serializado pela primeira vez. Somente se um valor [DateTime](xref:System.DateTime) representar o UTC, esse valor identifica sem ambiguidade um único ponto no tempo, independentemente do sistema ou do fuso horário em que o valor é usado.

> [!IMPORTANT]
> Ao salvar ou compartilhar os dados de [DateTime](xref:System.DateTime), o UTC deve ser usado e a propriedades [Kind](xref:System.DateTime) do valor [DateTime](xref:System.DateTime.Kind) deve ser definida como [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).

## <a name="the-datetimeoffset-structure"></a>A estrutura DateTimeOffset

A estrutura [System.DateTimeOffset](xref:System.DateTimeOffset) representa um valor de data e hora juntamente com um deslocamento que indica quanto o valor difere do UTC. Portanto, o valor sempre identifica sem ambiguidade um único ponto no tempo. 

O tipo [DateTimeOffset](xref:System.DateTimeOffset) inclui toda a funcionalidade do tipo [DateTime](xref:System.DateTime) juntamente com reconhecimento de fuso horário. Isso o torna adequado para aplicativos que fazem o seguinte: 

* Identifique de maneira única e não ambígua um único ponto no tempo. O tipo [DateTimeOffset](xref:System.DateTimeOffset) pode ser usado para definir sem ambiguidade o significado de "agora", para tempos de transação do log, para registrar os tempos de sistema ou eventos do aplicativo e para registrar a criação do arquivo e os tempos de modificação. 

* Realizar aritmética geral de data e hora.

* Preserve vários tempos relacionados contanto que esses tempos sejam armazenados como dois valores separados ou como dois membros de uma estrutura.

> [!NOTE]
> Esses usos para os valores [DateTimeOffset](xref:System.DateTimeOffset) são muito mais comuns do que aqueles para os valores [DateTime](xref:System.DateTime). Como resultado, [DateTimeOffset](xref:System.DateTimeOffset) deve ser considerado como o tipo de data e hora padrão para o desenvolvimento de aplicativos.

Um valor [DateTimeOffset](xref:System.DateTimeOffset) não está vinculado a um fuso horário específico, mas pode se originar de qualquer um dos vários fusos horários. Para ilustrar isso, o exemplo a seguir lista os fusos horários aos quais inúmeros valores [DateTimeOffset](xref:System.DateTimeOffset) (incluindo um Fuso Horário do Pacífico local) podem pertencer.

```csharp
using System;
using System.Collections.ObjectModel;

public class TimeOffsets
{
   public static void Main()
   {
      DateTime thisDate = new DateTime(2007, 3, 10, 0, 0, 0);
      DateTime dstDate = new DateTime(2007, 6, 10, 0, 0, 0);
      DateTimeOffset thisTime;

      thisTime = new DateTimeOffset(dstDate, new TimeSpan(-7, 0, 0));
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(-6, 0, 0));  
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(+1, 0, 0));
      ShowPossibleTimeZones(thisTime);
   }

   private static void ShowPossibleTimeZones(DateTimeOffset offsetTime)
   {
      TimeSpan offset = offsetTime.Offset;
      ReadOnlyCollection<TimeZoneInfo> timeZones;

      Console.WriteLine("{0} could belong to the following time zones:", 
                        offsetTime.ToString());
      // Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones();     
      // Iterate time zones 
      foreach (TimeZoneInfo timeZone in timeZones)
      {
         // Compare offset with offset for that date in that time zone
         if (timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset))
            Console.WriteLine("   {0}", timeZone.DisplayName);
      }
      Console.WriteLine();
   } 
}
// This example displays the following output to the console:
//       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
//          (GMT-07:00) Arizona
//          (GMT-08:00) Pacific Time (US & Canada)
//          (GMT-08:00) Tijuana, Baja California
//       
//       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
//          (GMT-06:00) Central America
//          (GMT-06:00) Central Time (US & Canada)
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
//          (GMT-06:00) Saskatchewan
//       
//       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
//          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
//          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
//          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
//          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
//          (GMT+01:00) West Central Africa
```

```vb
Imports System.Collections.ObjectModel

Module TimeOffsets
   Public Sub Main()
      Dim thisTime As DateTimeOffset 

      thisTime = New DateTimeOffset(#06/10/2007#, New TimeSpan(-7, 0, 0))
      ShowPossibleTimeZones(thisTime) 

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(-6, 0, 0))  
      ShowPossibleTimeZones(thisTime)

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(+1, 0, 0))
      ShowPossibleTimeZones(thisTime)
   End Sub

   Private Sub ShowPossibleTimeZones(offsetTime As DateTimeOffset)
      Dim offset As TimeSpan = offsetTime.Offset
      Dim timeZones As ReadOnlyCollection(Of TimeZoneInfo)

      Console.WriteLine("{0} could belong to the following time zones:", _
                        offsetTime.ToString())
      ' Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones()     
      ' Iterate time zones
      For Each timeZone As TimeZoneInfo In timeZones
         ' Compare offset with offset for that date in that time zone
         If timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset) Then
            Console.WriteLine("   {0}", timeZone.DisplayName)
         End If   
      Next
      Console.WriteLine()
   End Sub
End Module
' This example displays the following output to the console:
'       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
'          (GMT-07:00) Arizona
'          (GMT-08:00) Pacific Time (US & Canada)
'          (GMT-08:00) Tijuana, Baja California
'       
'       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
'          (GMT-06:00) Central America
'          (GMT-06:00) Central Time (US & Canada)
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
'          (GMT-06:00) Saskatchewan
'       
'       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
'          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
'          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
'          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
'          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
'          (GMT+01:00) West Central Africa
```

A saída mostra que cada valor de data e hora nesse exemplo pode pertencer a pelo menos três fusos horários diferentes. O valor [DateTimeOffset](xref:System.DateTimeOffset) de 10/06/2007 mostra que, se um valor de data e hora representa um horário de verão, seu deslocamento do UTC não corresponde necessariamente ao deslocamento base do UTC do fuso horário originário ou ao deslocamento do UTC encontrado no seu nome de exibição. Isso significa que, como um único valor [DateTimeOffset](xref:System.DateTimeOffset) não está estritamente acoplado ao seu fuso horário, não é possível refletir a transição de um fuso horário para e do horário de verão. Isso pode ser particularmente problemático quando a aritmética de data e hora é usada para manipular um valor [DateTimeOffset](xref:System.DateTimeOffset). Para ver uma discussão sobre como realizar a aritmética de data e hora de uma forma que considere as regras de ajuste de um fuso horário, consulte [Executando operações aritméticas com datas e horas](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>A estrutura TimeSpan

A estrutura [System.TimeSpan](xref:System.TimeSpan) representa um intervalo de tempo. Seus dois usos típicos são: 

* Refletir o intervalo de tempo entre dois valores de data e hora. Por exemplo, subtrair um valor [DateTime](xref:System.DateTime) de outro retorna um valor [TimeSpan](xref:System.TimeSpan). 

* Calcular o tempo decorrido. Por exemplo, a propriedade [Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) retorna um valor [TimeSpan](xref:System.TimeSpan) que reflete o intervalo de tempo decorrido desde a chamada para um dos métodos [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch) que começa a medir o tempo decorrido.

Um valor [TimeSpan](xref:System.TimeSpan) também pode ser usado como uma substituição para um valor [DateTime](xref:System.DateTime) quando esse valor reflete um tempo sem referência a uma determinada hora do dia. Esse uso é semelhante às propriedades [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) e [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay), que retornam um valor [TimeSpan](xref:System.TimeSpan) que representa o tempo sem referência a uma data. Por exemplo, a estrutura [TimeSpan](xref:System.TimeSpan) pode ser usada para refletir a hora de abertura ou de fechamento diário de um repositório ou pode ser usado para representar a hora na qual qualquer evento regular ocorre.

O exemplo a seguir define uma estrutura `StoreInfo` que inclui objetos [TimeSpan](xref:System.TimeSpan) para tempos de abertura e fechamento do repositório, bem como um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa o fuso horário do repositório. A estrutura também inclui dois métodos, `IsOpenNow` e `IsOpenAt`, que indica se o repositório está aberto em um momento especificado pelo usuário, que se considera estar no fuso horário local.  

```csharp
using System;

public struct StoreInfo
{
   public String store;
   public TimeZoneInfo tz;
   public TimeSpan open;
   public TimeSpan close;

   public bool IsOpenNow()
   {
      return IsOpenAt(DateTime.TimeOfDay);
   }

   public bool IsOpenAt(TimeSpan time)
   {
      TimeZoneInfo local = TimeZoneInfo.Local;
      TimeSpan offset = TimeZoneInfo.BaseUtcOffset;

      // Is the store in the same time zone?
      if (tz.Equals(local)) {
         return time >= open & time <= close;
      }
   }
}
```

```vb
Public Structure StoreInfo
   Dim store As String
   Dim tz As TimeZoneInfo
   Dim open As TimeSpan
   Dim close As TimeSpan

   Public Function IsOpenNow() As Boolean
      Return IsOpenAt(Date.Now.TimeOfDay)
   End Function

   Public Function IsOpenAt(time As TimeSpan) As Boolean
      Dim local As TimeZoneInfo = TimeZoneInfo.Local
      Dim offset As TimeSpan = TimeZoneInfo.Local.BaseUtcOffset

      ' Is the store in the same time zone?
      If tz.Equals(local) Then
         Return time >= open And time <= close
      Else
         Dim delta As TimeSpan = TimeSpan.Zero
         Dim storeDelta As TimeSpan = TimeSpan.Zero

         ' Is it daylight saving time in either time zone?
         If local.IsDaylightSavingTime(Date.Now.Date + time) Then
            delta = local.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         If tz.IsDaylightSavingTime(TimeZoneInfo.ConvertTime(Date.Now.Date + time, local, tz))
            storeDelta = tz.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         Dim comparisonTime As TimeSpan = time + (offset - tz.BaseUtcOffset).Negate() + (delta - storeDelta).Negate
         Return (comparisonTime >= open And comparisonTime <= close)
      End If
   End Function
End Structure
```

A estrutura `StoreInfo` pode ser usada pelo código do cliente como o exposto a seguir. 

```csharp
public class Example
{
   public static void Main()
   {
      // Instantiate a StoreInfo object.
      var store103 = new StoreInfo();
      store103.store = "Store #103";
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
      // Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0);
      // Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0);

      Console.WriteLine("Store is open now at {0}: {1}",
                        DateTime.TimeOfDay, store103.IsOpenNow());
      TimeSpan[] times = { new TimeSpan(8, 0, 0), new TimeSpan(21, 0, 0),
                           new TimeSpan(4, 59, 0), new TimeSpan(18, 31, 0) };
      foreach (var time in times)
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time));
   }
}
// The example displays the following output:
//       Store is open now at 15:29:01.6129911: True
//       Store is open at 08:00:00: True
//       Store is open at 21:00:00: False
//       Store is open at 04:59:00: False
//       Store is open at 18:31:00: False
```

```vb
Module Example
   Public Sub Main()
      ' Instantiate a StoreInfo object.
      Dim store103 As New StoreInfo()
      store103.store = "Store #103"
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
      ' Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0)
      ' Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0)

      Console.WriteLine("Store is open now at {0}: {1}",
                        Date.Now.TimeOfDay, store103.IsOpenNow())
      Dim times() As TimeSpan = { New TimeSpan(8, 0, 0),
                                  New TimeSpan(21, 0, 0),
                                  New TimeSpan(4, 59, 0),
                                  New TimeSpan(18, 31, 0) }
      For Each time In times
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time))
      Next
   End Sub
End Module
' The example displays the following output:
'       Store is open now at 15:29:01.6129911: True
'       Store is open at 08:00:00: True
'       Store is open at 21:00:00: False
'       Store is open at 04:59:00: False
'       Store is open at 18:31:00: False
```

## <a name="the-timezoneinfo-class"></a>A classe TimeZoneInfo

A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) representa qualquer um dos fusos horários da Terra e permite a conversão de qualquer data e hora em um fuso horário para seu equivalente em outro fuso horário. A classe [TimeZoneInfo](xref:System.TimeZoneInfo) possibilita trabalhar com datas e horas de modo que qualquer valor de data e hora identifica sem ambiguidade um único ponto no tempo.

Em alguns casos, usar ao máximo a classe [TimeZoneInfo](xref:System.TimeZoneInfo) pode exigir trabalho de desenvolvimento adicional. Os valores de data e hora não são estritamente acoplados aos fusos horários aos quais eles pertencem. Como resultado, a menos que seu aplicativo ofereça algum mecanismo para vincular uma data e hora com seu fuso horário associado, é fácil para um determinado valor de data e hora se desassociar do seu fuso horário. Um método de vinculação dessas informações é definir uma classe ou estrutura que contenha o valor de data e hora e seu objeto de fuso horário associado.

É possível obter suporte de fuso horário no .NET apenas se o fuso horário ao qual um valor de data e hora pertence for conhecido quando a instância desse objeto de data e hora for criada. Geralmente isso não acontece, especialmente em aplicativos Web ou de rede.

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)


<!--HONumber=Nov16_HO3-->


