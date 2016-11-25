---
title: "Criando uma instância de um objeto DateTimeOffset"
description: "Criando uma instância de um objeto DateTimeOffset"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 476fe67b-6be4-4435-88ab-ced37304f1d1
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 3b6e2cc973b9587cc9950ecd6898b8a321a01036

---

# <a name="instantiating-a-datetimeoffset-object"></a>Criando uma instância de um objeto DateTimeOffset

A estrutura [System.DateTimeOffset](xref:System.DateTimeOffset) oferece uma série de maneiras para criar novos valores [DateTimeOffset](xref:System.DateTimeOffset). Muitas delas correspondem diretamente aos métodos disponíveis para instanciar novos valores [System.DateTime](xref:System.DateTime), com aprimoramentos que permitem que você especifique o valor de deslocamento de data e hora do UTC (Tempo Universal Coordenado). Em particular, você pode instanciar um valor [DateTimeOffset](xref:System.DateTimeOffset) das seguintes maneiras:

* Chamando um construtor [DateTimeOffset](xref:System.DateTimeOffset).

* Convertendo implicitamente um valor em um valor [DateTimeOffset](xref:System.DateTimeOffset).

* Analisando a representação de cadeia de caracteres de data e hora.

## <a name="date-and-time-literals"></a>Literais de data e hora

Para linguagens que dão suporte a literais, uma das maneiras mais comuns de instanciar um valor [DateTime](xref:System.DateTime) é fornecer a data e hora como um valor literal embutido em código. Por exemplo, o seguinte código de Visual Basic cria um objeto [DateTime](xref:System.DateTime) cujo valor é 1 de janeiro de 2008, às 10h.

```vb
Dim literalDate1 As Date = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate1.ToString())
' Displays:
'              5/1/2008 8:06:32 AM
```

Os valores [DateTimeOffset](xref:System.DateTimeOffset) também podem ser inicializados usando literais de data e hora ao usar linguagens que dão suporte a literais [DateTime](xref:System.DateTime). Por exemplo, o seguinte código de Visual Basic cria um objeto [DateTimeOffset](xref:System.DateTimeOffset).

```vb
Dim literalDate As DateTimeOffset = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate.ToString())
' Displays:
'              5/1/2008 8:06:32 AM -07:00
```

Como mostra a saída do console, ao valor [DateTimeOffset](xref:System.DateTimeOffset) criado dessa maneira é atribuído o deslocamento do fuso horário local. Isso significa que um valor [DateTimeOffset](xref:System.DateTimeOffset) atribuído usando um literal de caractere não identificará um único ponto de tempo se o código for executado em computadores diferentes.

## <a name="datetimeoffset-constructors"></a>Construtores DateTimeOffset

O tipo [System.DateTimeOffset](xref:System.DateTimeOffset) define cinco construtores. Três deles correspondem diretamente aos construtores [DateTime](xref:System.DateTime), com um parâmetro adicional do tipo [System.TimeSpan](xref:System.TimeSpan) que define o deslocamento de data e hora do UTC. Eles permitem que você defina um valor de [DateTimeOffset](xref:System.DateTimeOffset) valor com base no valor de sua data individual e componentes de tempo. Por exemplo, o código a seguir usa estes três construtores para instanciar objetos [DateTimeOffset](xref:System.DateTimeOffset) com valores idênticos de 1/7/2008 0h5 + 1h.

```csharp
DateTimeOffset dateAndTime;

// Instantiate date and time using years, months, days, 
// hours, minutes, and seconds
dateAndTime = new DateTimeOffset(2008, 5, 1, 8, 6, 32, 
                                 new TimeSpan(1, 0, 0));
Console.WriteLine(dateAndTime);
// Instantiate date and time using years, months, days,
// hours, minutes, seconds, and milliseconds
dateAndTime = new DateTimeOffset(2008, 5, 1, 8, 6, 32, 545, 
                                 new TimeSpan(1, 0, 0));
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), 
                             dateAndTime.ToString("zzz"));

// Instantiate date and time using number of ticks
// 05/01/2008 8:06:32 AM is 633,452,259,920,000,000 ticks
dateAndTime = new DateTimeOffset(633452259920000000, new TimeSpan(1, 0, 0));  
Console.WriteLine(dateAndTime);
// The example displays the following output to the console:
//       5/1/2008 8:06:32 AM +01:00
//       5/1/2008 8:06:32 AM +01:00
//       5/1/2008 8:06:32 AM +01:00
```

```vb
Dim dateAndTime As DateTimeOffset

' Instantiate date and time using years, months, days, 
' hours, minutes, and seconds
dateAndTime = New DateTimeOffset(2008, 5, 1, 8, 6, 32, _
                                 New TimeSpan(1, 0, 0))
Console.WriteLine(dateAndTime)
' Instantiate date and time using years, months, days,
' hours, minutes, seconds, and milliseconds
dateAndTime = New DateTimeOffset(2008, 5, 1, 8, 6, 32, 545, _
                                 New TimeSpan(1, 0, 0))
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), _
                             dateAndTime.ToString("zzz"))

' Instantiate date and time using Persian calendar with years,
' months, days, hours, minutes, seconds, and milliseconds
dateAndTime = New DateTimeOffset(1387, 2, 12, 8, 6, 32, 545, New PersianCalendar, New TimeSpan(1, 0, 0))
' Note that the console output displays the date in the Gregorian
' calendar, not the Persian calendar. 
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), _
                             dateAndTime.ToString("zzz"))

' Instantiate date and time using number of ticks
' 05/01/2008 8:06:32 AM is 633,452,259,920,000,000 ticks
dateAndTime = New DateTimeOffset(633452259920000000, New TimeSpan(1, 0, 0))  
Console.WriteLine(dateAndTime)
' The example displays the following output to the console:
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
```

Observe que, quando o valor do objeto [DateTimeOffset](xref:System.DateTimeOffset) instanciado usando um objeto [PersianCalendar](xref:System.Globalization.PersianCalendar) como um dos argumentos do construtor é exibido no console, ele é expresso como uma data no calendário gregoriano em vez do calendário persa. 

Os outros dois construtores criam um objeto [DateTimeOffset](xref:System.DateTimeOffset) de um valor DateTime. O primeiro desses tem um parâmetro único, o valor [DateTime](xref:System.DateTime) a ser convertido em um valor [DateTimeOffset](xref:System.DateTimeOffset). O deslocamento do valor [DateTimeOffset](xref:System.DateTimeOffset) resultante depende da propriedade [Kind](xref:System.DateTime.Kind) do parâmetro [DateTime](xref:System.DateTime) único do construtor. Se o valor for [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), o deslocamento será definido como igual ao [TimeSpan.Zero](xref:System.TimeSpan.Zero). Caso contrário, o deslocamento será definido como igual ao fuso horário local. O exemplo a seguir ilustra o uso desse construtor para instanciar objetos [DateTimeOffset](xref:System.DateTimeOffset) que representam o UTC e o fuso horário local:

```csharp
// Declare date; Kind property is DateTimeKind.Unspecified
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
DateTimeOffset targetTime;

// Instantiate a DateTimeOffset value from a UTC time 
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = new DateTimeOffset(utcTime);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc, 
// the offset is TimeSpan.Zero.

// Instantiate a DateTimeOffset value from a UTC time with a zero offset
targetTime = new DateTimeOffset(utcTime, TimeSpan.Zero);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc, 
// the call to the constructor succeeds

// Instantiate a DateTimeOffset value from a UTC time with a negative offset
try
{
   targetTime = new DateTimeOffset(utcTime, new TimeSpan(-2, 0, 0));
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      targetTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM +00:00 failed.

// Instantiate a DateTimeOffset value from a local time
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = new DateTimeOffset(localTime);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Local, 
// the offset is that of the local time zone.

// Instantiate a DateTimeOffset value from an unspecified time
targetTime = new DateTimeOffset(sourceDate);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Unspecified, 
// the offset is that of the local time zone.
```

```vb
' Declare date; Kind property is DateTimeKind.Unspecified
Dim sourceDate As Date = #5/1/2008 8:30 AM#
Dim targetTime As DateTimeOffset

' Instantiate a DateTimeOffset value from a UTC time 
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = New DateTimeOffset(utcTime)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM +00:00
' Because the Kind property is DateTimeKind.Utc, 
' the offset is TimeSpan.Zero.


' Instantiate a DateTimeOffset value from a local time
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = New DateTimeOffset(localTime)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -07:00
' Because the Kind property is DateTimeKind.Local, 
' the offset is that of the local time zone.

' Instantiate a DateTimeOffset value from an unspecified time
targetTime = New DateTimeOffset(sourceDate)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -07:00
' Because the Kind property is DateTimeKind.Unspecified, 
' the offset is that of the local time zone.
```

> [!NOTE]
> Chamar a sobrecarga do construtor [DateTimeOffset](xref:System.DateTimeOffset) que tem um único parâmetro [DateTime](xref:System.DateTime) é equivalente a executar uma conversão implícita de um valor [DateTime](xref:System.DateTime) em um valor [DateTimeOffset](xref:System.DateTimeOffset).

O segundo construtor que cria um objeto [DateTimeOffset](xref:System.DateTimeOffset) de um valor [DateTime](xref:System.DateTime) tem dois parâmetros: o valor [DateTime](xref:System.DateTime) a ser convertido e um valor [TimeSpan](xref:System.TimeSpan) que representa o deslocamento de data e hora do UTC. Esse valor de deslocamento deverá corresponder à propriedade [Kind](xref:System.DateTime.Kind) do primeiro parâmetro do construtor ou uma [System. ArgumentException](xref:System.ArgumentException) será lançada. Se a propriedade [Kind](xref:System.DateTime.Kind) do primeiro parâmetro for [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), o valor do segundo parâmetro deverá ser [TimeSpan.Zero](xref:System.TimeSpan.Zero). Se a propriedade [Kind](xref:System.DateTime.Kind) do primeiro parâmetro for [DateTimeKind.Local](xref:System.DateTimeKind.Local), o valor do segundo parâmetro deverá ser o deslocamento de fuso horário do sistema local. Se a propriedade [Kind](xref:System.DateTime.Kind) do primeiro parâmetro for [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), o deslocamento poderá ser qualquer valor válido. O código a seguir ilustra chamadas ao construtor para converter o valor [DateTime](xref:System.DateTime) em [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
DateTimeOffset targetTime;

// Instantiate a DateTimeOffset value from a UTC time with a zero offset.
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = new DateTimeOffset(utcTime, TimeSpan.Zero);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc,  
// the call to the constructor succeeds

// Instantiate a DateTimeOffset value from a UTC time with a non-zero offset.
try
{
   targetTime = new DateTimeOffset(utcTime, new TimeSpan(-2, 0, 0));
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      utcTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

// Instantiate a DateTimeOffset value from a local time with 
// the offset of the local time zone
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = new DateTimeOffset(localTime, 
                                TimeZoneInfo.Local.GetUtcOffset(localTime));
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Local and the offset matches
// that of the local time zone, the call to the constructor succeeds.

// Instantiate a DateTimeOffset value from a local time with a zero offset.
try
{
   targetTime = new DateTimeOffset(localTime, TimeSpan.Zero);
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      localTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

// Instantiate a DateTimeOffset value with an arbitary time zone. 
string timeZoneName = "Central Standard Time";
TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName). 
                         GetUtcOffset(sourceDate); 
targetTime = new DateTimeOffset(sourceDate, offset);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -05:00
```

```vb
Dim sourceDate As Date = #5/1/2008 8:30 AM#
Dim targetTime As DateTimeOffset

' Instantiate a DateTimeOffset value from a UTC time with a zero offset.
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = New DateTimeOffset(utcTime, TimeSpan.Zero)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM +00:00
' Because the Kind property is DateTimeKind.Utc,  
' the call to the constructor succeeds.

' Instantiate a DateTimeOffset value from a UTC time with a non-zero offset.
Try
   targetTime = New DateTimeOffset(utcTime, New TimeSpan(-2, 0, 0))
   Console.WriteLine(targetTime)
Catch e As ArgumentException
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", _
                      utcTime)
End Try   
' Throws exception and displays the following to the console:
'   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

' Instantiate a DateTimeOffset value from a local time with 
' the offset of the local time zone.
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = New DateTimeOffset(localTime, _
                                TimeZoneInfo.Local.GetUtcOffset(localTime))
Console.WriteLine(targetTime)
' Because the Kind property is DateTimeKind.Local and the offset matches
' that of the local time zone, the call to the constructor succeeds.

' Instantiate a DateTimeOffset value from a local time with a zero offset.
Try
   targetTime = New DateTimeOffset(localTime, TimeSpan.Zero)
   Console.WriteLine(targetTime)
Catch e As ArgumentException
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", _
                      localTime)
End Try   
' Throws exception and displays the following to the console:
'   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

' Instantiate a DateTimeOffset value with an arbitary time zone. 
Dim timeZoneName As String = "Central Standard Time"
Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName). _
                         GetUtcOffset(sourceDate) 
targetTime = New DateTimeOffset(sourceDate, offset)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -05:00
```

## <a name="implicit-type-conversion"></a>Conversão implícita de tipo
 
O tipo [System.DateTimeOffset](xref:System.DateTimeOffset) dá suporte a uma conversão implícita de tipos de um valor [System.DateTime](xref:System.DateTime) em um valor [DateTimeOffset](xref:System.DateTimeOffset). (Uma conversão implícita de tipo é uma conversão de um tipo para outro que não requer uma conversão explícita (em C#) ou conversão (no Visual Basic) e não perde informações). Isso torna o código, como o seguinte, possível.

```csharp
DateTimeOffset targetTime;

// The Kind property of sourceDate is DateTimeKind.Unspecified
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
targetTime = sourceDate;
Console.WriteLine(targetTime);   
// Displays 5/1/2008 8:30:00 AM -07:00

// define a UTC time (Kind property is DateTimeKind.Utc)
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = utcTime;
Console.WriteLine(targetTime);   
// Displays 5/1/2008 8:30:00 AM +00:00

// Define a local time (Kind property is DateTimeKind.Local)
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = localTime;
Console.WriteLine(targetTime);      
// Displays 5/1/2008 8:30:00 AM -07:00
```

```vb
Dim targetTime As DateTimeOffset

' The Kind property of sourceDate is DateTimeKind.Unspecified
Dim sourceDate As Date = #5/1/2008 8:30 AM#
targetTime = sourceDate
Console.WriteLine(targetTime)   
' Displays 5/1/2008 8:30:00 AM -07:00

' define a UTC time (Kind property is DateTimeKind.Utc)
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = utcTime
Console.WriteLine(targetTime)   
' Displays 5/1/2008 8:30:00 AM +00:00

' Define a local time (Kind property is DateTimeKind.Local)
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = localTime
Console.WriteLine(targetTime)      
' Displays 5/1/2008 8:30:00 AM -07:00
```

O deslocamento do valor [DateTimeOffset](xref:System.DateTimeOffset) resultante depende do valor de propriedade DateTime.Kind](xref:System.DateTime.Kind). Se o valor for [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), o deslocamento será definido como igual ao [TimeSpan.Zero](xref:System.TimeSpan.Zero). Se o valor for [DateTimeKind.Local](xref:System.DateTimeKind.Local) ou [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), o deslocamento será definido como igual ao do fuso horário local.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analisando a representação de cadeia de caracteres de data e hora

O tipo [System.DateTimeOffse](xref:System.DateTimeOffset) dá suporte a quatro métodos que permitem que você converta a representação de cadeia de caracteres de uma data e hora em um valor [DateTimeOffset](xref:System.DateTimeOffset):

* [Parse](xref:System.DateTimeOffset.Parse(System.String)), que tenta converter a representação da cadeia de caracteres de uma data e hora em um valor [DateTimeOffset](xref:System.DateTimeOffset) e lança uma exceção se a conversão falhar.

* [TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@)), que tenta converter a representação de cadeia de caracteres de uma data e hora em um valor [DateTimeOffset](xref:System.DateTimeOffset) e retorna `false` se a conversão falhar.

* [ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)), que tenta converter a representação de cadeia de caracteres de data e hora em um formato especificado em um valor [DateTimeOffset](xref:System.DateTimeOffset). Na ocorrência de erros, o método lança uma exceção.

* [TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)), que tenta converter a representação de cadeia de caracteres de data e hora em um formato especificado em um valor [DateTimeOffset](xref:System.DateTimeOffset). O método retornará `false` se a conversão falhar.

O exemplo a seguir ilustra chamadas para cada um desses quatro métodos de conversão de cadeia de caracteres para instanciar um [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
string timeString; 
DateTimeOffset targetTime;

timeString = "05/01/2008 8:30 AM +01:00";
try
{
   targetTime = DateTimeOffset.Parse(timeString);
   Console.WriteLine(targetTime);
}
catch (FormatException)
{
   Console.WriteLine("Unable to parse {0}.", timeString);   
}   

timeString = "05/01/2008 8:30 AM";
if (DateTimeOffset.TryParse(timeString, out targetTime))
   Console.WriteLine(targetTime);
else
   Console.WriteLine("Unable to parse {0}.", timeString);   

timeString = "Thursday, 01 May 2008 08:30";
try
{
   targetTime = DateTimeOffset.ParseExact(timeString, "f", 
                CultureInfo.InvariantCulture);
   Console.WriteLine(targetTime);
}
catch (FormatException)
{
   Console.WriteLine("Unable to parse {0}.", timeString);   
}   

timeString = "Thursday, 01 May 2008 08:30 +02:00";
string formatString; 
formatString = CultureInfo.InvariantCulture.DateTimeFormat.LongDatePattern +
                " " +
                CultureInfo.InvariantCulture.DateTimeFormat.ShortTimePattern +
                " zzz"; 
if (DateTimeOffset.TryParseExact(timeString, 
                                formatString, 
                                CultureInfo.InvariantCulture, 
                                DateTimeStyles.AllowLeadingWhite, 
                                out targetTime))
   Console.WriteLine(targetTime);
else
   Console.WriteLine("Unable to parse {0}.", timeString);
// The example displays the following output to the console:
//    5/1/2008 8:30:00 AM +01:00
//    5/1/2008 8:30:00 AM -07:00
//    5/1/2008 8:30:00 AM -07:00
//    5/1/2008 8:30:00 AM +02:00
```

```vb
Dim timeString As String 
Dim targetTime As DateTimeOffset

timeString = "05/01/2008 8:30 AM +01:00"
Try
   targetTime = DateTimeOffset.Parse(timeString)
   Console.WriteLine(targetTime)
Catch e As FormatException
   Console.WriteLine("Unable to parse {0}.", timeString)   
End Try   

timeString = "05/01/2008 8:30 AM"
If DateTimeOffset.TryParse(timeString, targetTime) Then
   Console.WriteLine(targetTime)
Else
   Console.WriteLine("Unable to parse {0}.", timeString)   
End If

timeString = "Thursday, 01 May 2008 08:30"
Try
   targetTime = DateTimeOffset.ParseExact(timeString, "f", _
                CultureInfo.InvariantCulture)
   Console.WriteLine(targetTime)
Catch e As FormatException
   Console.WriteLine("Unable to parse {0}.", timeString)   
End Try   

timeString = "Thursday, 01 May 2008 08:30 +02:00"
Dim formatString As String 
formatString = CultureInfo.InvariantCulture.DateTimeFormat.LongDatePattern & _
                " " & _
                CultureInfo.InvariantCulture.DateTimeFormat.ShortTimePattern & _
                " zzz" 
If DateTimeOffset.TryParseExact(timeString, _
                                formatString, _
                                CultureInfo.InvariantCulture, _
                                DateTimeStyles.AllowLeadingWhite, _
                                targetTime) Then
   Console.WriteLine(targetTime)
Else
   Console.WriteLine("Unable to parse {0}.", timeString)
End If      
' The example displays the following output to the console:
'    5/1/2008 8:30:00 AM +01:00
'    5/1/2008 8:30:00 AM -07:00
'    5/1/2008 8:30:00 AM -07:00
'    5/1/2008 8:30:00 AM +02:00
```

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)




<!--HONumber=Nov16_HO3-->


