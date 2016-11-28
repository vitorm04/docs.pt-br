---
title: Convertendo entre DateTime e DateTimeOffset
description: Convertendo entre DateTime e DateTimeOffset
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: fab3af5b-5d0f-4384-a40a-1b5d99b30dd1
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 99ec9d8c433025bbc5122fe3ea364fe84f33a1f8

---

# <a name="converting-between-datetime-and-datetimeoffset"></a>Convertendo entre DateTime e DateTimeOffset

Embora a estrutura [System.DateTimeOffset](xref:System.DateTimeOffset) ofereça um maior grau de reconhecimento de fuso horário que a estrutura [System.DateTime](xref:System.DateTime), parâmetros [DateTime](xref:System.DateTime) são usados com mais frequência em chamadas de método. Por isso, a capacidade de converter valores [DateTimeOffset](xref:System.DateTimeOffset) em valores [DateTime](xref:System.DateTime) e vice-versa é muito importante. Este artigo mostra como executar essas conversões de maneira a preservar as informações de fuso horário tanto quanto possível.

> [!NOTE]
> Os tipos [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset) têm algumas limitações para representar horas em fusos horários. Com sua propriedade [Kind](xref:System.DateTime.Kind), [DateTime](xref:System.DateTime) pode refletir somente o UTC (Tempo Universal Coordenado) e o fuso horário local do sistema. [DateTimeOffset](xref:System.DateTimeOffset) reflete um deslocamento da hora com relação ao UTC, mas não reflete o fuso horário real ao qual esse deslocamento pertence. Para obter detalhes sobre os valores de hora e o suporte para fusos horários, consulte [Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversões de DateTime para DateTimeOffset

A estrutura [DateTimeOffset](xref:System.DateTimeOffset) fornece duas maneiras equivalentes de executar uma conversão de [DateTime](xref:System.DateTime) para [DateTimeOffset](xref:System.DateTimeOffset) que são adequadas para a maioria das conversões:

* O construtor [DateTimeOffset(DateTime)](xref:System.DateTimeOffset), que cria um novo objeto [DateTimeOffset](xref:System.DateTimeOffset) com base em um valor de [DateTime](xref:System.DateTime).

* O operador de conversão implícita, que permite que você atribua um valor [DateTime](xref:System.DateTime) a um objeto [DateTimeOffset](xref:System.DateTimeOffset).

Para UTC e valores locais de [DateTime](xref:System.DateTime), a propriedade [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) do valor [DateTimeOffset](xref:System.DateTimeOffset) resultante reflete com precisão o UTC ou o deslocamento do fuso horário local. Por exemplo, o código a seguir converte uma hora em UTC no valor equivalente de [DateTimeOffset](xref:System.DateTimeOffset). 

```csharp
DateTime utcTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
utcTime1 = DateTime.SpecifyKind(utcTime1, DateTimeKind.Utc);
DateTimeOffset utcTime2 = utcTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  utcTime1, 
                  utcTime1.Kind.ToString(), 
                  utcTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM +00:00
```

```vb
Dim utcTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, _
                                        DateTimeKind.Utc)
Dim utcTime2 As DateTimeOffset = utcTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  utcTime1, _
                  utcTime1.Kind.ToString(), _
                  utcTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM  +00:00
```

Nesse caso, o deslocamento da variável `utcTime2` é 00:00. De forma semelhante, o código a seguir converte uma hora local no valor equivalente de [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
DateTime localTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
localTime1 = DateTime.SpecifyKind(localTime1, DateTimeKind.Local);
DateTimeOffset localTime2 = localTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  localTime1, 
                  localTime1.Kind.ToString(), 
                  localTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim localTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, DateTimeKind.Local)
Dim localTime2 As DateTimeOffset = localTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  localTime1, _
                  localTime1.Kind.ToString(), _
                  localTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

No entanto, para valores de [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) é [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), esses dois métodos de conversão produzem um valor de [DateTimeOffset](xref:System.DateTimeOffset) cujo deslocamento é o do fuso horário local. Isso é mostrado no exemplo a seguir, que é executado no Fuso horário padrão do Pacífico.

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);  // Kind is DateTimeKind.Unspecified
DateTimeOffset time2 = time1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  time1, 
                  time1.Kind.ToString(), 
                  time2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Dim time2 As DateTimeOffset = time1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  time1, _
                  time1.Kind.ToString(), _
                  time2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

Se o valor de [DateTime](xref:System.DateTime) refletir a data e a hora em algo diferente do fuso horário local ou UTC, você poderá convertê-lo para um valor de [DateTimeOffset](xref:System.DateTimeOffset) e preservar suas informações de fuso horário chamando o construtor sobrecarregado [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset). O exemplo a seguir instancia um objeto [DateTimeOffset](xref:System.DateTimeOffset) que reflete a Hora Padrão Central.

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);     // Kind is DateTimeKind.Unspecified
try
{
   DateTimeOffset time2 = new DateTimeOffset(time1, 
                  TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)); 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", 
                     time1, 
                     time1.Kind.ToString(), 
                     time2);
}
// Handle exception if time zone is not defined in registry
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to identify target time zone for conversion.");
}
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Try
   Dim time2 As New DateTimeOffset(time1, _
                    TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)) 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", _
                     time1, _
                     time1.Kind.ToString(), _
                     time2)
' Handle exception if time zone is not defined in registry
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to identify target time zone for conversion.")
End Try
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

O segundo parâmetro para essa sobrecarga de construtor, um objeto [System.TimeSpan](xref:System.TimeSpan) que representa o deslocamento da hora com relação ao UTC, deve ser recuperado chamando o método [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) do fuso horário correspondente da hora. O único parâmetro do método é o valor de [DateTime](xref:System.DateTime) que representa a data e hora a ser convertida. Se o fuso horário der suporte ao horário de verão, este parâmetro permite que o método determine o deslocamento apropriado para aquela data e hora determinada.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversões de DateTimeOffset em DateTime

A propriedade [DateTime](xref:System.DateTime) é usada mais comumente para executar a conversão de [DateTimeOffset](xref:System.DateTimeOffset) para [DateTime](xref:System.DateTime). No entanto, ela retorna um valor de [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) é [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), como mostra o exemplo a seguir. 

```csharp
DateTime baseTime = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset sourceTime;
DateTime targetTime;

// Convert UTC to DateTime value
sourceTime = new DateTimeOffset(baseTime, TimeSpan.Zero);
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert local time to DateTime value
sourceTime = new DateTimeOffset(baseTime, 
                                TimeZoneInfo.Local.GetUtcOffset(baseTime));
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert Central Standard Time to a DateTime value
try
{
   TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime);
   sourceTime = new DateTimeOffset(baseTime, offset);
   targetTime = sourceTime.DateTime;
   Console.WriteLine("{0} converts to {1} {2}", 
                     sourceTime, 
                     targetTime, 
                     targetTime.Kind.ToString());
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.");
} 
// This example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

```vb
Const baseTime As Date = #06/19/2008 7:00AM#
Dim sourceTime As DateTimeOffset
Dim targetTime As Date

' Convert UTC to DateTime value
sourceTime = New DateTimeOffset(baseTime, TimeSpan.Zero)
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert local time to DateTime value
sourceTime = New DateTimeOffset(baseTime, _
                                TimeZoneInfo.Local.GetUtcOffset(baseTime))
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert Central Standard Time to a DateTime value
Try
   Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime)
   sourceTime = New DateTimeOffset(baseTime, offset)
   targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.")
End Try 
' This example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

Isso significa que todas as informações sobre a relação do valor de [DateTimeOffset](xref:System.DateTimeOffset) com o UTC são perdidas pela conversão quando a propriedade [DateTime](xref:System.DateTime) é usada. Isso afeta valores de [DateTimeOffset](xref:System.DateTimeOffset) que correspondem à hora em UTC ou à hora do sistema local porque a estrutura [DateTime](xref:System.DateTime) reflete somente esses dois fusos horários em sua propriedade [Kind](xref:System.DateTime.Kind).

Para preservar o máximo possível de informações do fuso horário ao converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) para [DateTime](xref:System.DateTime), você pode usar as propriedades [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) e [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime). 

## <a name="converting-a-utc-time"></a>Convertendo uma hora UTC

Para indicar que um valor de [DateTime](xref:System.DateTime) convertido é a hora em UTC, você pode recuperar o valor da propriedade [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime). Ele difere da propriedade [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) de duas maneiras:

* Ele retorna um valor de [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) é [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).

* Se o valor da propriedade [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) não for igual a [TimeSpan.Zero](xref:System.TimeSpan.Zero), ele converte a hora em UTC.

> [!NOTE]
> Se seu aplicativo exigir que os valores convertidos de [DateTime](xref:System.DateTime) identifiquem sem ambiguidade um único ponto no tempo, considere usar a propriedade [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) para lidar com todas as conversões de [DateTimeOffset](xref:System.DateTimeOffset) em [DateTime](xref:System.DateTime).

O código a seguir usa a propriedade [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) para converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) cujo deslocamento é igual a [TimeSpan.Zero](xref:System.TimeSpan.Zero) em um valor de [DateTime](xref:System.DateTime).

```csharp
DateTimeOffset utcTime1 = new DateTimeOffset(2008, 6, 19, 7, 0, 0, TimeSpan.Zero);
DateTime utcTime2 = utcTime1.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

```vb
Dim utcTime1 As New DateTimeOffset(#06/19/2008 7:00AM#, TimeSpan.Zero)
Dim utcTime2 As Date = utcTime1.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

O código a seguir usa a propriedade UtcDateTime para executar uma conversão de fuso horário e uma conversão de tipo em um valor de [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
DateTimeOffset originalTime = new DateTimeOffset(2008, 6, 19, 7, 0, 0, new TimeSpan(5, 0, 0));
DateTime utcTime = originalTime.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalTime, 
                  utcTime, 
                  utcTime.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

```vb
Dim originalTime As New DateTimeOffset(#6/19/2008 7:00AM#, _
                                       New TimeSpan(5, 0, 0))
Dim utcTime As Date = originalTime.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _ 
                  originalTime, _
                  utcTime, _
                  utcTime.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

## <a name="converting-a-local-time"></a>Convertendo uma hora Local

Para indicar que um valor de [DateTimeOffset](xref:System.DateTimeOffset) representa a hora local, você pode passar o valor de [DateTime](xref:System.DateTime) retornado pela propriedade [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) para o método estático [DateTime.SpecifyKind (DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)). O método retorna a data e hora passada para ele como o primeiro parâmetro, mas define a propriedade [Kind](xref:System.DateTime.Kind) como o valor especificado pelo seu segundo parâmetro. O código a seguir usa o método [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) ao converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) cujo deslocamento corresponde ao do fuso horário local.

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset utcTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime utcTime2 = utcTime1.DateTime;
if (utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime))) 
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local);

Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim utcTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim utcTime2 As Date = utcTime1.DateTime
If utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime)) Then
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local)
End If   
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

Você também pode usar a propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) para converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) para um valor de [DateTime](xref:System.DateTime) local. A propriedade [Kind](xref:System.DateTime.Kind) do valor [DateTime](xref:System.DateTime) retornado é [DateTimeKind.Local](xref:System.DateTimeKind.Local). O código a seguir usa a propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) ao converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) cujo deslocamento corresponde ao do fuso horário local.

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset localTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime localTime2 = localTime1.LocalDateTime;

Console.WriteLine("{0} converted to {1} {2}", 
                  localTime1, 
                  localTime2, 
                  localTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim localTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim localTime2 As Date = localTime1.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime1, _
                  localTime2, _
                  localTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local 
```

Quando você recupera um valor de [DateTime](xref:System.DateTime) usando a propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime), o acessador `get` da propriedade primeiro converte o valor de [DateTimeOffset](xref:System.DateTimeOffset) para UTC e depois o converte para a hora local chamando o método [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset). Isso significa que você pode recuperar um valor a partir a propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) para executar uma conversão de fuso horário ao mesmo tempo em que executa uma conversão de tipo. Isso também significa que as regras de ajuste do fuso horário local são aplicadas na execução da conversão. O código a seguir ilustra o uso da propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) para executar uma conversão de tipo e de fuso horário.

```csharp
DateTimeOffset originalDate;
DateTime localDate;

// Convert time originating in a different time zone
originalDate = new DateTimeOffset(2008, 6, 18, 7, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// Convert time originating in a different time zone 
// so local time zone's adjustment rules are applied
originalDate = new DateTimeOffset(2007, 11, 4, 4, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
//       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

```vb
Dim originalDate As DateTimeOffset
Dim localDate As Date

' Convert time originating in a different time zone
originalDate = New DateTimeOffset(#06/19/2008 7:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' Convert time originating in a different time zone 
' so local time zone's adjustment rules are applied
originalDate = New DateTimeOffset(#11/04/2007 4:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
'       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

## <a name="a-general-purpose-conversion-method"></a>Um método de conversão com finalidade geral

O exemplo a seguir define um método chamado `ConvertFromDateTimeOffset` que converte valores de [DateTimeOffset](xref:System.DateTimeOffset) para valores de [DateTime](xref:System.DateTime). Com base no seu deslocamento, ele determina se o valor de [DateTimeOffset](xref:System.DateTimeOffset) é uma hora no UTC, uma hora local ou outro tipo de hora e define a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora retornado de acordo com isso. 

```csharp
static DateTime ConvertFromDateTimeOffset(DateTimeOffset dateTime)
{
   if (dateTime.Offset.Equals(TimeSpan.Zero))
      return dateTime.UtcDateTime;
   else if (dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime)))
      return DateTime.SpecifyKind(dateTime.DateTime, DateTimeKind.Local);
   else
      return dateTime.DateTime;   
}
```

```vb
Function ConvertFromDateTimeOffset(dateTime As DateTimeOffset) As Date
   If dateTime.Offset.Equals(TimeSpan.Zero) Then
      Return dateTime.UtcDateTime
   ElseIf dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime))
      Return Date.SpecifyKind(dateTime.DateTime, DateTimeKind.Local)
   Else
      Return dateTime.DateTime   
   End If
```

O exemplo a seguir chama o método `ConvertFromDateTimeOffset` para converter valores de [DateTimeOffset](xref:System.DateTimeOffset) que representam uma hora em UTC, uma hora local e uma hora no Fuso horário padrão central.

```csharp
DateTime timeComponent = new DateTime(2008, 6, 19, 7, 0, 0);
DateTime returnedDate; 

// Convert UTC time
DateTimeOffset utcTime = new DateTimeOffset(timeComponent, TimeSpan.Zero);
returnedDate = ConvertFromDateTimeOffset(utcTime); 
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert local time
DateTimeOffset localTime = new DateTimeOffset(timeComponent, 
                           TimeZoneInfo.Local.GetUtcOffset(timeComponent)); 
returnedDate = ConvertFromDateTimeOffset(localTime);                                          
Console.WriteLine("{0} converted to {1} {2}", 
                  localTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert Central Standard Time
DateTimeOffset cstTime = new DateTimeOffset(timeComponent, 
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent));
returnedDate = ConvertFromDateTimeOffset(cstTime);
Console.WriteLine("{0} converted to {1} {2}", 
                  cstTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());
// The example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
//    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
//    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

```vb
Dim timeComponent As Date = #06/19/2008 7:00AM#
Dim returnedDate As Date 

' Convert UTC time
Dim utcTime As New DateTimeOffset(timeComponent, TimeSpan.Zero)
returnedDate = ConvertFromDateTimeOffset(utcTime) 
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert local time
Dim localTime As New DateTimeOffset(timeComponent, _
                                    TimeZoneInfo.Local.GetUtcOffset(timeComponent)) 
returnedDate = ConvertFromDateTimeOffset(localTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert Central Standard Time
Dim cstTime As New DateTimeOffset(timeComponent, _
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent))
returnedDate = ConvertFromDateTimeOffset(cstTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  cstTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())
' The example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
'    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
'    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

Observe que esse código faz duas suposições que, dependendo do aplicativo e da fonte de seus valores de data e hora, podem não ser sempre válidas:

* Ele supõe que um valor de data e hora cujo deslocamento é [TimeSpan.Zero](xref:System.TimeSpan.Zero) representa o UTC. Na verdade, UTC não é uma hora em um determinado fuso horário, mas a hora em relação à qual as horas nos fusos horários do mundo são padronizadas. Os fusos horários também podem ter um deslocamento de [Zero](xref:System.TimeSpan.Zero).

* Ele supõe que uma data e hora cujo deslocamento é igual ao do fuso horário local representa o fuso horário local. Como os valores de data e hora são dissociados do seu fuso horário original, este pode não ser o caso. A data e hora podem ter sido originadas em outro fuso horário com o mesmo deslocamento.

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)







<!--HONumber=Nov16_HO4-->


