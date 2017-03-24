---
title: Cadeias de caracteres de formato de data e hora personalizado
description: Cadeias de caracteres de formato de data e hora personalizado
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 45f286f5-92c9-4150-957c-fa6d394bc29b
translationtype: Human Translation
ms.sourcegitcommit: 28625def4199a660fe0ea04ab75f4f65d2e0c9c4
ms.openlocfilehash: 285e4bfd6a53d576ce4538b09a2561065c93e399
ms.lasthandoff: 02/23/2017

---

# <a name="custom-date-and-time-format-strings"></a>Cadeias de caracteres de formato de data e hora personalizado

Uma cadeia de caracteres de formato de data e hora define a representação de texto de um valor [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) que é resultante de uma operação de formatação. Ela também pode definir a representação de um valor de data e hora necessário em uma operação de análise para converter com êxito a cadeia de caracteres para uma data e hora. Uma cadeia de caracteres de formato personalizado consiste em um ou mais especificadores de formato de data e hora personalizado. Qualquer cadeia de caracteres que não é uma [cadeia de caracteres de formato de data e hora padrão](standard-datetime.md) é interpretada como uma cadeia de caracteres de formato de data e hora personalizado. 

Cadeias de caracteres de formato de data e hora personalizado podem ser usadas com valores [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset).

Nas operações de formatação, as cadeias de caracteres de formato de data e hora personalizado podem ser usadas com o método `ToString` de uma instância de data e hora ou com um método que ofereça suporte a formatação de composição. O exemplo a seguir ilustra ambos os usos. 

```csharp
DateTime thisDate1 = new DateTime(2011, 6, 10);
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".");

DateTimeOffset thisDate2 = new DateTimeOffset(2011, 6, 10, 15, 24, 16, 
                                              TimeSpan.Zero);
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}", 
                   thisDate2); 
// The example displays the following output:
//    Today is June 10, 2011.
//    The current date and time: 06/10/11 15:24:16 +00:00
```

```vb
Dim thisDate1 As Date = #6/10/2011#
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".")

Dim thisDate2 As New DateTimeOffset(2011, 6, 10, 15, 24, 16, TimeSpan.Zero)
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}", 
                   thisDate2) 
' The example displays the following output:
'    Today is June 10, 2011.
'    The current date and time: 06/10/11 15:24:16 +00:00
```

Em operações de análise, cadeias de caracteres de formato de data e hora personalizadas podem ser usadas com os métodos [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)), [DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)), [DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) e [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)). Esses métodos exigem que uma cadeia de caracteres de entrada esteja exatamente em conformidade com um padrão específico para que a operação de análise obtenha êxito. O exemplo a seguir ilustra uma chamada ao método [DateTimeOffset.ParseExact(String, String, IFormatProvider)](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) para analisar uma data que deve incluir um dia, um mês e um ano com dois dígitos.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] dateValues = { "30-12-2011", "12-30-2011", 
                              "30-12-11", "12-30-11" };
      string pattern = "MM-dd-yy";
      DateTime parsedDate;

      foreach (var dateValue in dateValues) {
         if (DateTime.TryParseExact(dateValue, pattern, null, 
                                   DateTimeStyles.None, out parsedDate))
            Console.WriteLine("Converted '{0}' to {1:d}.", 
                              dateValue, parsedDate);
         else
            Console.WriteLine("Unable to convert '{0}' to a date and time.", 
                              dateValue);
      }
   }
}
// The example displays the following output:
//    Unable to convert '30-12-2011' to a date and time.
//    Unable to convert '12-30-2011' to a date and time.
//    Unable to convert '30-12-11' to a date and time.
//    Converted '12-30-11' to 12/30/2011.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateValues() As String = { "30-12-2011", "12-30-2011", 
                                      "30-12-11", "12-30-11" }
      Dim pattern As String = "MM-dd-yy"
      Dim parsedDate As Date

      For Each dateValue As String In dateValues
         If DateTime.TryParseExact(dateValue, pattern, Nothing, 
                                   DateTimeStyles.None, parsedDate) Then
            Console.WriteLine("Converted '{0}' to {1:d}.", 
                              dateValue, parsedDate)
         Else
            Console.WriteLine("Unable to convert '{0}' to a date and time.", 
                              dateValue)
         End If                                                         
      Next
   End Sub
End Module
' The example displays the following output:
'    Unable to convert '30-12-2011' to a date and time.
'    Unable to convert '12-30-2011' to a date and time.
'    Unable to convert '30-12-11' to a date and time.
'    Converted '12-30-11' to 12/30/2011.
```

A tabela a seguir descreve os especificadores de formato de data e hora personalizados e exibe uma cadeia de caracteres de resultado produzida por cada especificador de formato. Por padrão, as cadeias de caracteres de resultado refletem as convenções de formatação da cultura en-US. Se um determinado especificador de formato produz uma cadeia de caracteres de resultado localizada, o exemplo também observa a cultura à qual a cadeia de caracteres de resultado se aplica. Consulte a seção Observações para obter informações adicionais sobre como usar cadeias de caracteres de formato data e hora personalizado.

Especificador de formato | Descrição | Exemplos
---------------- | ----------- | --------
"d" | O dia do mês, de 1 a 31. | `2019-06-01T13:45:30 -> 1`; `2019-06-15T13:45:30 -> 15`
"dd" | O dia do mês, de 01 a 31. | `2019-06-01T13:45:30 -> 1`; `2019-06-15T13:45:30 -> 15`
"ddd" | O nome abreviado do dia da semana. | `2019-06-15T13:45:30 -> Mon (en-US)`; `2019-06-15T13:45:30 -> Пн (ru-RU)`; `2019-06-15T13:45:30 -> lun. (fr-FR)`
"dddd" | O nome completo do dia da semana. | `2019-06-15T13:45:30 -> Monday (en-US)`; `2019-06-15T13:45:30 -> понедельник (ru-RU)`; `2019-06-15T13:45:30 -> lundi (fr-FR)`
"f" | Os décimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6170000 -> 6`; `2019-06-15T13:45:30.05 -> 0` 
"ff" | Os centésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6170000 -> 61`; `2019-06-15T13:45:30.0050000 -> 00`
"fff" | Os milissegundos em um valor de data e hora. | `6/15/2019 13:45:30.617 -> 617`; `6/15/2019 13:45:30.0005 -> 000`
"ffff" | Os décimos de milésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6175000 -> 6175`; `2019-06-15T13:45:30.0000500 -> 0000`
"fffff" | Os centésimos de milésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6175400 -> 61754`; `6/15/2019 13:45:30.000005 -> 00000`
"ffffff" | Os milionésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6175420 -> 617542`; `2019-06-15T13:45:30.0000005 -> 000000`
"fffffff" | Os décimos de milionésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6175425 -> 6175425`;`2019-06-15T13:45:30.0001150 -> 0001150`
"F" | Se diferente de zero, os décimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6170000 -> 6`; `2019-06-15T13:45:30.0500000 -> (no output)`
"FF" | Se diferente de zero, os centésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6170000 -> 61`; `2019-06-15T13:45:30.0050000 -> (no output)`
"FFF" | Se diferente de zero, os milissegundos em um valor de data e hora. | `2019-06-15T13:45:30.6170000 -> 617`; `2019-06-15T13:45:30.0005000 -> (no output)`
"FFFF" | Se diferente de zero, os décimos de milésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.5275000 -> 5275`; `2019-06-15T13:45:30.0000500 -> (no output)`
"FFFFF" | Se diferente de zero, os centésimos de milésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6175400 -> 61754`; `2019-06-15T13:45:30.0000050 -> (no output)`
"FFFFFF" | Se diferente de zero, os milionésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6175420 -> 617542`; `2019-06-15T13:45:30.0000005 -> (no output)`
"FFFFFFF" | Se diferente de zero, os décimos de milionésimos de segundo em um valor de data e hora. | `2019-06-15T13:45:30.6175425 -> 6175425`; `2019-06-15T13:45:30.0001150 -> 000115`
"g", "gg" | O período ou a era. | `2019-06-15T13:45:30.6170000 -> A.D.`
"h" | A hora, usando um relógio de 12 horas de 1 a 12. | `2019-06-15T01:45:30 -> 1`; `2019-06-15T13:45:30 -> 1`
"hh" | A hora, usando um relógio de 12 horas de 01 a 12. | `2019-06-15T01:45:30 -> 01`; `2019-06-15T13:45:30 -> 01`
"H" | A hora, usando um relógio de 24 horas de 0 a 23. | `2019-06-15T01:45:30 -> 1`; `2019-06-15T13:45:30 -> 13`
"HH" | A hora, usando um relógio de 24 horas de 00 a 23. | `2019-06-15T01:45:30 -> 01`; `2019-06-15T13:45:30 -> 13`
"K" | Informações de fuso horário. | Com valores de [DateTime](xref:System.DateTime): `2019-06-15T13:45:30, Kind Unspecified ->`; `2019-06-15T13:45:30, Kind Utc -> Z`; `2019-06-15T13:45:30, Kind Local -> -07:00 (depends on local computer settings)`; Com valores de [DateTimeOffset](xref:System.DateTimeOffset): `2019-06-15T01:45:30-07:00 --> -07:00`; `2019-06-15T08:45:30+00:00 --> +00:00`
"m" | O minuto, de 0 a 59. | `2019-06-15T01:09:30 -> 9`; `2019-06-15T13:29:30 -> 29`
"mm" | O minuto, de 00 a 59. | `2019-06-15T01:09:30 -> 09`; `2019-06-15T01:45:30 -> 45`
“M” | O mês, de 1 a 12. | `2019-06-15T13:45:30 -> 6`
"MM" | O mês, de 01 a 12. | `2019-06-15T13:45:30 -> 06`
"MMM" | O nome do mês abreviado. | `2019-06-15T13:45:30 -> Jun (en-US)`; `2019-06-15T13:45:30 -> juin (fr-FR)`; `2019-06-15T13:45:30 -> Jun (zu-ZA)`
"MMMM" | O nome completo do mês. | `2019-06-15T13:45:30 -> June (en-US)`; `2019-06-15T13:45:30 -> juni (da-DK)`; `2019-06-15T13:45:30 -> uJuni (zu-ZA)`
"s" | O segundo, de 0 a 59. | `2019-06-15T13:45:09 -> 9`
"ss" | O segundo, de 00 a 59. | `2019-06-15T13:45:09 -> 09`
"t" | O primeiro caractere do designador AM/PM. | `2019-06-15T13:45:30 -> P (en-US)`; `2019-06-15T13:45:30 -> 午 (ja-JP)`; `2019-06-15T13:45:30 -> (fr-FR)`
"tt" | O designador AM/PM. | `2019-06-15T13:45:30 -> PM (en-US)`; `2019-06-15T13:45:30 -> 午後 (ja-JP)`; `2019-06-15T13:45:30 -> (fr-FR)`
"y" | O ano, de 0 a 99. | `0001-01-01T00:00:00 -> 1`; `0900-01-01T00:00:00 -> 0`; `1900-01-01T00:00:00 -> 0`; `2019-06-15T13:45:30 -> 9`; `2019-06-15T13:45:30 -> 19`
"yy" | O ano, de 00 a 99. | `0001-01-01T00:00:00 -> 01`; `0900-01-01T00:00:00 -> 00`; `1900-01-01T00:00:00 -> 00`; `2019-06-15T13:45:30 -> 19`
"yyy" | O ano, com um mínimo de três dígitos. | `0001-01-01T00:00:00 -> 001`; `0900-01-01T00:00:00 -> 900`; `1900-01-01T00:00:00 -> 1900`; `2019-06-15T13:45:30 -> 2019`
"yyyy" | O ano como um número de quatro dígitos. | `0001-01-01T00:00:00 -> 0001`; `0900-01-01T00:00:00 -> 0900`; `1900-01-01T00:00:00 -> 1900`; `2019-06-15T13:45:30 -> 2019`
"yyyyy" | O ano como um número de cinco dígitos. | `0001-01-01T00:00:00 -> 00001`; `2019-06-15T13:45:30 -> 02019`
"z" | Diferença de horas em relação ao UTC, sem zeros à esquerda. | `2019-06-15T13:45:30-07:00 -> -7`
"zz" | Diferença de horas em relação ao UTC, com um zero à esquerda para um valor de dígito único. | `2019-06-15T13:45:30-07:00 -> -07`
"zzz" | Diferença de horas e minutos em relação ao UTC. | `2019-06-15T13:45:30-07:00 -> -07:00`
":" | O separador de hora. | `2019-06-15T13:45:30 -> : (en-US)`; `2019-06-15T13:45:30 -> . (it-IT)`; `2019-06-15T13:45:30 -> : (ja-JP)`
"/" | O separador de data. | `2019-06-15T13:45:30 -> / (en-US)`; `2019-06-15T13:45:30 -> - (ar-DZ)`; `2019-06-15T13:45:30 -> . (tr-TR)`
"string", 'string' | Delimitador de cadeia de caracteres literal. | `2019-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P`; `2019-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P`
% | Define o caractere seguinte como um especificador de formato personalizado. | `2019-06-15T13:45:30 (%h) -> 1`
\ | O caractere de escape. | `2019-06-15T13:45:30 (h \h) -> 1 h`
Qualquer outro caractere | O caractere é copiado, inalterado, para a cadeia de caracteres de resultado. | `2019-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A`

As seções a seguir oferecem informações adicionais sobre cada especificador de formato de data e hora personalizado. A menos que observado do contrário, cada especificador produz uma representação de cadeia de caracteres idêntica independente de ela ser usada com um valor [DateTime](xref:System.DateTime) ou um valor [DateTimeOffset](xref:System.DateTimeOffset). 

## <a name="the-d-custom-format-specifier"></a>Especificador de formato personalizado "d"

O especificador de formato personalizado "d" representa o dia do mês como um número de 1 a 31. Dias de dígito único são formatados sem um zero à esquerda. 

Se o especificador de formato "d" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão "d". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

O exemplo a seguir inclui o especificador de formato personalizado "d" em várias cadeias de caracteres de formato. 

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15); 

Console.WriteLine(date1.ToString("d, M", 
                  CultureInfo.InvariantCulture)); 
// Displays 29, 8

Console.WriteLine(date1.ToString("d MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays 29 August
Console.WriteLine(date1.ToString("d MMMM", 
                  CultureInfo.CreateSpecificCulture("es-MX")));
// Displays 29 agosto  
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("d, M", _
                  CultureInfo.InvariantCulture)) 
' Displays 29, 8

Console.WriteLine(date1.ToString("d MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays 29 August
Console.WriteLine(date1.ToString("d MMMM", _
                  CultureInfo.CreateSpecificCulture("es-MX")))
' Displays 29 agosto 
```

## <a name="the-dd-custom-format-specifier"></a>Especificador de formato personalizado "dd"

A cadeia de caracteres de formato personalizado "dd" representa o dia do mês como um número de 01 a 31. Dias de dígito único são formatados com um zero à esquerda. 

O exemplo a seguir inclui o especificador de formato personalizado "dd" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 1, 2, 6, 30, 15);

Console.WriteLine(date1.ToString("dd, MM", 
                  CultureInfo.InvariantCulture)); 
// 02, 01
```

```vb
Dim date1 As Date = #1/2/2008 6:30:15AM#

Console.WriteLine(date1.ToString("dd, MM", _
                  CultureInfo.InvariantCulture)) 
' 02, 01
```

## <a name="the-ddd-custom-format-specifier"></a>Especificador de formato personalizado "ddd"

O especificador de formato personalizado "ddd" representa o nome do dia da semana abreviado. O nome do dia da semana localizado abreviado é recuperado da propriedade [DateTimeFormatInfo.AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) da cultura atual ou especificada. 

O exemplo a seguir inclui o especificador de formato personalizado "ddd" em uma cadeia de caracteres de formato personalizado. 

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays ven. 29 août    
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays ven. 29 août
```

## <a name="the-dddd-custom-format-specifier"></a>Especificador de formato personalizado "dddd"

O especificador de formato personalizado "dddd" (mais um número qualquer de especificadores "d" adicionais) representa o nome completo do dia da semana. O nome do dia da semana localizado é recuperado da propriedade [DateTimeFormatInfo.DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) da cultura atual ou especificada. 

O exemplo a seguir inclui o especificador de formato personalizado "dddd" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("it-IT")));
// Displays venerdì 29 agosto    
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("it-IT")))
' Displays venerdì 29 agosto                                          
```

## <a name="the-f-custom-format-specifier"></a>Especificador de formato personalizado "f"

O especificador de formato personalizado "f" representa o dígito mais significativo da fração de segundos, ou seja, representa os décimos de segundo em um valor de data e hora.

Se o especificador de formato "f" for usado sem outros especificadores de formato, ele será interpretado como o especificador padrão de formato de data e hora "f". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

Quando você usa especificadores de formato "f" como parte de uma cadeia de caracteres de formato fornecida para o método [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)), [DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)), [DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) ou [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)), o número de especificadores de formato "f" indica o número de dígitos mais significativos da fração de segundos que deve estar presente para analisar a cadeia de caracteres com sucesso.

O exemplo a seguir inclui o especificador de formato personalizado "f" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ff-custom-format-specifier"></a>Especificador de formato personalizado "ff"

O especificador de formato personalizado "ff" representa os dois dígitos mais significativos da fração de segundos, ou seja, ele representa os centésimos de segundo em um valor de data e hora. 

O exemplo a seguir inclui o especificador de formato personalizado "ff" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-fff-custom-format-specifier"></a>Especificador de formato personalizado "fff"

O especificador de formato personalizado "fff" representa os três dígitos mais significativos da fração de segundos, ou seja, ele representa os milissegundos em um valor de data e hora. 

O exemplo a seguir inclui o especificador de formato personalizado "fff" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ffff-custom-format-specifier"></a>Especificador de formato personalizado "ffff"

O especificador de formato personalizado "ffff" representa os quatro dígitos mais significativos da fração de segundos, ou seja, ele representa os décimos de milésimos de um segundo em um valor de data e hora.

Embora seja possível exibir os décimos de milésimos de um componente de segundos de um valor temporal, esse valor pode não ser significativo. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema.

## <a name="the-fffff-custom-format-specifier"></a>Especificador de formato personalizado "fffff"

O especificador de formato personalizado "fffff" representa os cinco dígitos mais significativos da fração de segundos, ou seja, ele representa os centésimos de milésimos de um segundo em um valor de data e hora.

Embora seja possível exibir os centésimos de milésimos de um componente de segundos de um valor temporal, esse valor pode não ser significativo. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema. 

## <a name="the-ffffff-custom-format-specifier"></a>Especificador de formato personalizado "ffffff"

O especificador de formato personalizado "ffffff" representa os seis dígitos mais significativos da fração de segundos, ou seja, ele representa os milionésimos de um segundo em um valor de data e hora.

Embora seja possível exibir os milionésimos de um componente de segundos de um valor temporal, esse valor pode não ser significativo. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema. 

## <a name="the-fffffff-custom-format-specifier"></a>Especificador de formato personalizado "fffffff"

O especificador de formato personalizado "fffffff" representa os sete dígitos mais significativos da fração de segundos; ou seja, representa os décimos de milionésimos de segundo em um valor de data e hora.

Embora seja possível exibir os décimos de milionésimos de um componente de segundos de um valor temporal, esse valor pode não ser significativo. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema. 

## <a name="the-f-custom-format-specifier"></a>Especificador de formato personalizado "F"

O especificador de formato personalizado "F" representa o dígito mais significativo da fração de segundos, ou seja, representa os décimos de segundo em um valor de data e hora. Nada será exibido se o dígito for zero. 

Se o especificador de formato "F" for usado sem outros especificadores de formato, ele será interpretado como o especificador padrão de formato de data e hora "F". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

O número de especificadores de formato "F" usados com o método [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)), [DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)), [DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) ou [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) indica o número máximo de dígitos mais significativos da fração de segundos que podem estar presentes para que a análise da cadeia de caracteres seja feita com êxito.

O exemplo a seguir inclui o especificador de formato personalizado "F" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ff-custom-format-specifier"></a>Especificador de formato personalizado "FF"

O especificador de formato personalizado "FF" representa os dois dígitos mais significativos da fração de segundos, ou seja, ele representa os centésimos de segundo em um valor de data e hora. No entanto, zeros à direita ou dois dígitos zero não são exibidos. 

O exemplo a seguir inclui o especificador de formato personalizado "FF" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-fff-custom-format-specifier"></a>Especificador de formato personalizado "FFF"

O especificador de formato personalizado "FFF" representa os três dígitos mais significativos da fração de segundos, ou seja, ele representa os milissegundos em um valor de data e hora. No entanto, zeros à direita ou três dígitos zero não são exibidos. 

O exemplo a seguir inclui o especificador de formato personalizado "FFF" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
````

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ffff-custom-format-specifier"></a>Especificador de formato personalizado "FFFF"

O especificador de formato personalizado "FFFF" representa os quatro dígitos mais significativos da fração de segundos, ou seja, ele representa os décimos de milésimos de um segundo em um valor de data e hora. No entanto, zeros à direita ou quatro dígitos zero não são exibidos.

Embora seja possível exibir os décimos de milésimos de um componente de segundos de um valor temporal, esse valor pode não ser significativo. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema.

## <a name="the-fffff-custom-format-specifier"></a>Especificador de formato personalizado "FFFFF"

O especificador de formato personalizado "FFFFF" representa os cinco dígitos mais significativos da fração de segundos, ou seja, ele representa os centésimos de milésimos de um segundo em um valor de data e hora. No entanto, zeros à direita ou cinco dígitos zero não são exibidos.

Embora seja possível exibir os centésimos de milésimos de um componente de segundos de um valor temporal, esse valor pode não ser significativo. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema.

## <a name="the-ffffff-custom-format-specifier"></a>Especificador de formato personalizado "FFFFFF"

O especificador de formato personalizado "FFFFFF" representa os seis dígitos mais significativos da fração de segundos, ou seja, ele representa os milionésimos de um segundo em um valor de data e hora. No entanto, zeros à direita ou seis dígitos zero não são exibidos.

Embora seja possível exibir os milionésimos de um componente de segundos de um valor temporal, esse valor pode não ser significativo. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema.

## <a name="the-fffffff-custom-format-specifier"></a>Especificador de formato personalizado "FFFFFFF"

O especificador de formato personalizado "FFFFFFF" representa os sete dígitos mais significativos da fração de segundos; ou seja, representa os décimos de milionésimos de segundo em um valor de data e hora. No entanto, zeros à direita ou sete dígitos zero não são exibidos.

Embora seja possível exibir os décimos de milionésimos de um componente de segundos de um valor temporal, esse valor pode não ser significativo. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema.

## <a name="the-g-or-gg-custom-format-specifier"></a>Especificador de formato personalizado "g" ou "gg"

Os especificadores de formato personalizado "g" ou "gg" (mais qualquer número de especificadores "g" adicionais) representam o período ou a era, como A.D. A operação de formatação ignora esse especificador quando a data a ser formatada não tem uma cadeia de caracteres de era ou período associada. 

Se o especificador de formato "g" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão "g". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

O exemplo a seguir inclui o especificador de formato personalizado "g" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(70, 08, 04);

Console.WriteLine(date1.ToString("MM/dd/yyyy g", 
                  CultureInfo.InvariantCulture));
// Displays 08/04/0070 A.D.                        
Console.WriteLine(date1.ToString("MM/dd/yyyy g", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));                         
// Displays 08/04/0070 ap. J.-C.
```

```vb
Dim date1 As Date = #08/04/0070#

Console.WriteLine(date1.ToString("MM/dd/yyyy g", _
                  CultureInfo.InvariantCulture))
' Displays 08/04/0070 A.D.                        
Console.WriteLine(date1.ToString("MM/dd/yyyy g", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))                         
' Displays 08/04/0070 ap. J.-C.
```

## <a name="the-h-custom-format-specifier"></a>Especificador de formato personalizado "h"

O especificador de formato personalizado "h" representa a hora como um número de 1 a 12, ou seja, a hora é representada por um relógio de 12 horas que conta todas as horas desde a meia-noite. Uma hora específica após a meia-noite é indistinguível da mesma hora depois do meio-dia. A hora não é arredondada e uma hora de dígito único é formatada sem um zero à esquerda. Por exemplo, considerando a hora 5:43 da manhã ou da tarde, este especificador de formato personalizado exibe “5". 

Se o especificador de formato "h" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão e gerará uma [FormatException](xref:System.FormatException). Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

O exemplo a seguir inclui o especificador de formato personalizado "h" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-hh-custom-format-specifier"></a>Especificador de formato personalizado "hh"

O especificador de formato personalizado "hh" (mais qualquer número de especificadores "h" adicionais) representa a hora como um número de 01 a 12, ou seja, a hora é representada por um relógio de 12 horas que conta todas as horas desde a meia-noite ou o meio-dia. Uma hora específica após a meia-noite é indistinguível da mesma hora depois do meio-dia. A hora não é arredondada e uma hora de dígito único é formatada com um zero à esquerda. Por exemplo, considerando a hora 5:43 da manhã ou da tarde, este especificador de formato exibe “05".

O exemplo a seguir inclui o especificador de formato personalizado "hh" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-h-custom-format-specifier"></a>Especificador de formato personalizado "H"

O especificador de formato personalizado "H" representa a hora como um número de 0 a 23; ou seja, a hora é representada por um relógio de 24 horas baseado em zero que conta todas as horas desde a meia-noite. Uma hora de dígito único é formatada sem um zero à esquerda. 

Se o especificador de formato "H" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão e gerará uma [FormatException](xref:System.FormatException). Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

O exemplo a seguir inclui o especificador de formato personalizado "H" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 1, 1, 6, 9, 1);
Console.WriteLine(date1.ToString("H:mm:ss", 
                  CultureInfo.InvariantCulture));
// Displays 6:09:01 
```

```vb
Dim date1 As Date = #6:09:01AM#
Console.WriteLine(date1.ToString("H:mm:ss", _
                  CultureInfo.InvariantCulture))
' Displays 6:09:01 
```

## <a name="the-hh-custom-format-specifier"></a>Especificador de formato personalizado "HH"

O especificador de formato personalizado "HH" (mais qualquer número de especificadores "H" adicionais) representa a hora como um número de 00 a 23; ou seja, a hora é representada por um relógio de 24 horas baseado em zero que conta todas as horas desde a meia-noite. Uma hora de dígito único é formatada com um zero à esquerda. 

O exemplo a seguir inclui o especificador de formato personalizado "HH" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 1, 1, 6, 9, 1);
Console.WriteLine(date1.ToString("HH:mm:ss", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01                        
```

```vb
Dim date1 As Date = #6:09:01AM#
Console.WriteLine(date1.ToString("HH:mm:ss", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01
```

## <a name="the-k-custom-format-specifier"></a>Especificador de formato personalizado "K"

O especificador de formato personalizado "K" representa as informações de fuso horário de um valor temporal. Quando esse especificador de formato é usado com valores [DateTime](xref:System.DateTime), a cadeia de caracteres de resultado é definida pelo valor da propriedade [DateTime.Kind](xref:System.DateTime.Kind): 
 
* Para o fuso horário local (um valor da propriedade [DateTime.Kind](xref:System.DateTime.Kind) de [DateTimeKind.Local](xref:System.DateTimeKind.Local)), esse especificador é equivalente ao especificador "zzz" e produz uma cadeia de caracteres resultante que contém a diferença local em relação ao Horário Universal Coordenado (UTC). Por exemplo, "-07h00". 

* Para uma hora UTC (um valor da propriedade [DateTime.Kind](xref:System.DateTime.Kind) de [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)), a cadeia de caracteres de resultado inclui um caractere "Z" para representar uma data UTC. 

* Para uma hora de fuso horário não especificado (uma hora cuja propriedade [DateTime.Kind](xref:System.DateTime.Kind) é igual à propriedade [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified)), o resultado é equivalente a [String.Empty](xref:System.String#System_String_Empty). 

Para valores [DateTimeOffset](xref:System.DateTimeOffset), o especificador de formato "K" é equivalente ao especificador de formato "zz" e produz uma cadeia de caracteres resultante que contém a diferença em relação ao valor de [DateTimeOffset](xref:System.DateTimeOffset) do UTC. 

Se o especificador de formato "K" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão e gerará uma [FormatException](xref:System.FormatException). Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

O exemplo a seguir exibe a cadeia de caracteres resultante do uso do especificador de formato personalizado "K" com vários valores [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset) em um sistema no Fuso horário do Pacífico.

```csharp
Console.WriteLine(DateTime.Now.ToString("%K"));
// Displays -07:00
Console.WriteLine(DateTime.UtcNow.ToString("%K"));
// Displays Z      
Console.WriteLine("'{0}'", 
                  DateTime.SpecifyKind(DateTime.Now, 
                       DateTimeKind.Unspecified).ToString("%K"));
// Displays ''      
Console.WriteLine(DateTimeOffset.Now.ToString("%K"));
// Displays -07:00
Console.WriteLine(DateTimeOffset.UtcNow.ToString("%K"));
// Displays +00:00
Console.WriteLine(new DateTimeOffset(2008, 5, 1, 6, 30, 0, 
                      new TimeSpan(5, 0, 0)).ToString("%K"));
// Displays +05:00  
```

```vb
Console.WriteLine(Date.Now.ToString("%K"))
' Displays -07:00
Console.WriteLine(Date.UtcNow.ToString("%K"))
' Displays Z      
Console.WriteLine("'{0}'", _
                  Date.SpecifyKind(Date.Now, _
                                   DateTimeKind.Unspecified). _
                  ToString("%K"))
' Displays ''      
Console.WriteLine(DateTimeOffset.Now.ToString("%K"))
' Displays -07:00
Console.WriteLine(DateTimeOffset.UtcNow.ToString("%K"))
' Displays +00:00
Console.WriteLine(New DateTimeOffset(2008, 5, 1, 6, 30, 0, _
                                     New TimeSpan(5, 0, 0)). _
                  ToString("%K"))
' Displays +05:00 
```

## <a name="the-m-custom-format-specifier"></a>Especificador de formato personalizado "m"

O especificador de formato personalizado "m" representa o minuto como um número de 0 a 59. O minuto representa os minutos inteiros decorridos desde a última hora. Um minuto de dígito único é formatado sem um zero à esquerda. 

Se o especificador de formato "m" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão "m". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers). 

O exemplo a seguir inclui o especificador de formato personalizado "m" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-mm-custom-format-specifier"></a>Especificador de formato personalizado "mm"

O especificador de formato personalizado "mm" (mais qualquer número de especificadores "m" adicionais) representam o minuto como um número de 00 a 59. O minuto representa os minutos inteiros decorridos desde a última hora. Um minuto de dígito único é formatado com um zero à esquerda. 

O exemplo a seguir inclui o especificador de formato personalizado "mm" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-m-custom-format-specifier"></a>Especificador de formato personalizado "M"

O especificador de formato personalizado "M" representa o mês como um número de 1 a 12 (ou de 1 a 13 para os calendários com 13 meses). Um mês de dígito único é formatado sem um zero à esquerda. 

Se o especificador de formato "M" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão "M". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

O exemplo a seguir inclui o especificador de formato personalizado "M" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 18);
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays (8) Aug, August
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("nl-NL")));                       
// Displays (8) aug, augustus
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("lv-LV")));                        
// Displays (8) Aug, augusts
```

```vb
Dim date1 As Date = #8/18/2008#
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays (8) Aug, August
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("nl-NL")))                        
' Displays (8) aug, augustus
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("lv-LV")))                        
' Displays (8) Aug, augusts 
```

## <a name="the-mm-custom-format-specifier"></a>Especificador de formato personalizado "MM"

O especificador de formato personalizado "MM" representa o mês como um número de 01 a 12 (ou de 1 a 13 para os calendários com 13 meses). Um mês de dígito único é formatado com um zero à esquerda. 

O exemplo a seguir inclui o especificador de formato personalizado "MM" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 1, 2, 6, 30, 15);

Console.WriteLine(date1.ToString("dd, MM", 
                  CultureInfo.InvariantCulture)); 
// 02, 01
```

```vb
Dim date1 As Date = #1/2/2008 6:30:15AM#

Console.WriteLine(date1.ToString("dd, MM", _
                  CultureInfo.InvariantCulture)) 
' 02, 01
```

## <a name="the-mmm-custom-format-specifier"></a>Especificador de formato personalizado "MMM"

O especificador de formato personalizado "MMM" representa o nome do mês abreviado. O nome do mês localizado abreviado é recuperado da propriedade [DateTimeFormatInfo.AbbreviatedMonthNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames) da cultura atual ou especificada.

O exemplo a seguir inclui o especificador de formato personalizado "MMM" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays ven. 29 août
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays ven. 29 août
```

## <a name="the-mmmm-custom-format-specifier"></a>Especificador de formato personalizado "MMMM"

O especificador de formato personalizado "MMMM" representa o nome do mês completo. O nome do mês localizado é recuperado da propriedade [DateTimeFormatInfo.MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) da cultura atual ou especificada. 

O exemplo a seguir inclui o especificador de formato personalizado "MMMM" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("it-IT")));
// Displays venerdì 29 agosto 
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("it-IT")))
' Displays venerdì 29 agosto  
```

## <a name="the-s-custom-format-specifier"></a>Especificador de formato personalizado "s"

O especificador de formato personalizado "s" representa os segundos como um número de 0 a 59. O resultado representa os segundos inteiros decorridos desde o último minuto. Um segundo de dígito único é formatado sem um zero à esquerda. 

Se o especificador de formato "s" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão "s". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers). 

O exemplo a seguir inclui o especificador de formato personalizado "s" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-ss-custom-format-specifier"></a>Especificador de formato personalizado "ss"

O especificador de formato personalizado "ss" (mais qualquer número de especificadores "s" adicionais) representa os segundos como um número de 00 a 59. O resultado representa os segundos inteiros decorridos desde o último minuto. Um segundo de dígito único é formatado com um zero à esquerda. 

O exemplo a seguir inclui o especificador de formato personalizado "ss" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-t-custom-format-specifier"></a>Especificador de formato personalizado "t"

O especificador de formato personalizado "t" representa o primeiro caractere do designador AM/PM. O designador localizado apropriado é recuperado da propriedade [DateTimeFormatInfo.AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) ou [DateTimeFormatInfo.PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) da cultura atual ou específica. O designador AM é usado para todas as horas de 0:00:00 (meia-noite) até 11:59:59,999. O designador PM é usado para todas as horas de 12:00:00 (meio-dia) até 23:59:59,999. 

Se o especificador de formato "t" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão "t". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

O exemplo a seguir inclui o especificador de formato personalizado "t" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-tt-custom-format-specifier"></a>Especificador de formato personalizado "tt"

O especificador de formato personalizado "tt" (mais qualquer número de especificadores "t" adicionais) representa o designador AM/PM inteiro. O designador localizado apropriado é recuperado da propriedade [DateTimeFormatInfo.AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) ou [DateTimeFormatInfo.PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) da cultura atual ou específica. O designador AM é usado para todas as horas de 0:00:00 (meia-noite) até 11:59:59,999. O designador PM é usado para todas as horas de 12:00:00 (meio-dia) até 23:59:59,999.

Certifique-se de usar o especificador "tt" para linguagens para as quais é necessário manter a distinção entre AM e PM. Um exemplo é o idioma japonês, no qual os designadores AM e PM diferem no segundo caractere e não no primeiro.

O exemplo a seguir inclui o especificador de formato personalizado "tt" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-y-custom-format-specifier"></a>Especificador de formato personalizado "y"

O especificador de formato personalizado "y" representa o ano como um número de um dígito ou de dois dígitos. Se o ano tiver mais que dois dígitos, somente os dois dígitos de ordem baixa aparecerão no resultado. Se o primeiro dígito de um ano de dois dígitos começa com zero (por exemplo, 2008), o número é formatado sem um zero à esquerda. 

Se o especificador de formato "y" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão "y". Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizado](#using-single-custom-format-specifiers).

O exemplo a seguir inclui o especificador de formato personalizado "y" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yy-custom-format-specifier"></a>Especificador de formato personalizado "yy"

O especificador de formato personalizado "yy" representa o ano como um número de dois dígitos. Se o ano tiver mais que dois dígitos, somente os dois dígitos de ordem baixa aparecerão no resultado. Se o ano de dois dígitos tiver menos de dois dígitos significativos, o número será preenchido com zeros à esquerda para produzir dois dígitos.

Em uma operação de análise, um ano de dois dígitos é analisado usando o especificador de formato personalizado “yy” interpretado com base na propriedade [Calendar.TwoDigitYearMax](xref:System.Globalization.Calendar.TwoDigitYearMax) do calendário atual do provedor de formato. O exemplo a seguir analisa a representação de cadeia de caracteres de uma data com um ano de dois dígitos usando o calendário gregoriano padrão da cultura en-US que, neste caso, é a cultura atual. Ele então altera o objeto [CultureInfo](xref:System.Globalization.CultureInfo) da cultura atual para usar um objeto [GregorianCalendar](xref:System.Globalization.GregorianCalendar) cuja propriedade [TwoDigitYearMax](xref:System.Globalization.GregorianCalendar.TwoDigitYearMax) foi modificada.

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fmt = "dd-MMM-yy";
      string value = "24-Jan-49";

      Calendar cal = (Calendar) CultureInfo.CurrentCulture.Calendar.Clone();
      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax);

      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, null));
      Console.WriteLine();

      cal.TwoDigitYearMax = 2099;
      CultureInfo culture = (CultureInfo) CultureInfo.CurrentCulture.Clone();
      culture.DateTimeFormat.Calendar = cal;
      Thread.CurrentThread.CurrentCulture = culture;

      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax);
      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, null));
   }
}
// The example displays the following output:
//       Two Digit Year Range: 1930 - 2029
//       1/24/1949
//       
//       Two Digit Year Range: 2000 - 2099
//       1/24/2049
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fmt As String = "dd-MMM-yy"
      Dim value As String = "24-Jan-49"

      Dim cal As Calendar = CType(CultureInfo.CurrentCulture.Calendar.Clone(), Calendar)
      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax)

      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, Nothing))
      Console.WriteLine()

      cal.TwoDigitYearMax = 2099
      Dim culture As CultureInfo = CType(CultureInfo.CurrentCulture.Clone(), CultureInfo)
      culture.DateTimeFormat.Calendar = cal
      Thread.CurrentThread.CurrentCulture = culture

      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax)
      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Two Digit Year Range: 1930 - 2029
'       1/24/1949
'       
'       Two Digit Year Range: 2000 - 2099
'       1/24/2049
```

O exemplo a seguir inclui o especificador de formato personalizado "yy" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yyy-custom-format-specifier"></a>Especificador de formato personalizado "yyy"

O especificador de formato personalizado "yyy" representa o ano com, no mínimo, três dígitos. Se o ano tem mais de três dígitos significativos, eles são incluídos na cadeia de caracteres de resultado. Se o ano tem menos de três dígitos, o número é preenchido com zeros à esquerda para produzir três dígitos.

> [!NOTE]
> Para o calendário budista tailandês, que pode ter anos com cinco dígitos, este especificador de formato exibe todos os dígitos significativos.

O exemplo a seguir inclui o especificador de formato personalizado "yyy" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010      
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010 
```

## <a name="the-yyyy-custom-format-specifier"></a>Especificador de formato personalizado "yyyy"

O especificador de formato personalizado "yyyy" representa o ano com, no mínimo, quatro dígitos. Se o ano tem mais de quatro dígitos significativos, eles são incluídos na cadeia de caracteres de resultado. Se o ano tem menos de quatro dígitos, o número é preenchido com zeros à esquerda para produzir quatro dígitos.

> [!NOTE]
> Para o calendário budista tailandês, que pode ter anos com cinco dígitos, este especificador de formato exibe todos os dígitos significativos.

O exemplo a seguir inclui o especificador de formato personalizado "yyyy" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010 
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yyyyy-custom-format-specifier"></a>Especificador de formato personalizado "yyyyy"

O especificador de formato personalizado "yyyyy" (mais qualquer número de especificadores "y" adicionais) representa o ano com, no mínimo, cinco dígitos. Se o ano tem mais de cinco dígitos significativos, eles são incluídos na cadeia de caracteres de resultado. Se o ano tem menos de cinco dígitos, o número é preenchido com zeros à esquerda para produzir cinco dígitos.

Se houver especificadores "y" adicionais, o número será preenchido com tantos zeros à esquerda quantos forem necessários para produzir o número de especificadores "y". 

O exemplo a seguir inclui o especificador de formato personalizado "yyyyy" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010 
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010 
```

## <a name="the-z-custom-format-specifier"></a>Especificador de formato personalizado "z"

Com valores [DateTime](xref:System.DateTime), o especificador de formato personalizado "z" representa a diferença com sinal do fuso horário do sistema operacional local em relação ao UTC, medido em horas. Ele não reflete o valor de uma instância da propriedade [DateTime.Kind](xref:System.DateTime.Kind). Por esse motivo, o especificador de formato "z" não é recomendado para uso com valores [DateTime](xref:System.DateTime).

Com valores [DateTimeOffset](xref:System.DateTimeOffset), esse especificador de formato representa a diferença do valor de [DateTimeOffset](xref:System.DateTimeOffset) em relação ao UTC em horas e minutos. 

A diferença é sempre exibida com um sinal à esquerda. Um sinal de adição (+) indica horas depois do UTC, enquanto que um sinal de subtração (-) indica horas antes do UTC. Uma diferença com um único dígito único é formatada sem um zero à esquerda. 

Se o especificador de formato "z" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão e gerará uma [FormatException](xref:System.FormatException). Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers). 

O exemplo a seguir inclui o especificador de formato personalizado "z" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the-zz-custom-format-specifier"></a>Especificador de formato personalizado "zz"

Com valores [DateTime](xref:System.DateTime), o especificador de formato personalizado "zz" representa a diferença com sinal do fuso horário do sistema operacional local em relação ao UTC, medido em horas. Ele não reflete o valor de uma instância da propriedade [DateTime.Kind](xref:System.DateTime.Kind). Por esse motivo, o especificador de formato "zz" não é recomendado para uso com valores [DateTime](xref:System.DateTime).

Com valores [DateTimeOffset](xref:System.DateTimeOffset), esse especificador de formato representa a diferença do valor de [DateTimeOffset](xref:System.DateTimeOffset) em relação ao UTC em horas e minutos.

A diferença é sempre exibida com um sinal à esquerda. Um sinal de adição (+) indica horas depois do UTC, enquanto que um sinal de subtração (-) indica horas antes do UTC. Uma diferença com um único dígito único é formatada com um zero à esquerda. 

O exemplo a seguir inclui o especificador de formato personalizado "zz" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the-zzz-custom-format-specifier"></a>Especificador de formato personalizado "zzz"

Com valores [DateTime](xref:System.DateTime), o especificador de formato personalizado "zzz" representa a diferença com sinal do fuso horário do sistema operacional local em relação ao UTC, medido em horas. Ele não reflete o valor de uma instância da propriedade [DateTime.Kind](xref:System.DateTime.Kind). Por esse motivo, o especificador de formato "zzz" não é recomendado para uso com valores [DateTime](xref:System.DateTime).

Com valores [DateTimeOffset](xref:System.DateTimeOffset), esse especificador de formato representa a diferença do valor de [DateTimeOffset](xref:System.DateTimeOffset) em relação ao UTC em horas e minutos.

A diferença é sempre exibida com um sinal à esquerda. Um sinal de adição (+) indica horas depois do UTC, enquanto que um sinal de subtração (-) indica horas antes do UTC. Uma diferença com um único dígito único é formatada com um zero à esquerda. 

O exemplo a seguir inclui o especificador de formato personalizado "zzz" em uma cadeia de caracteres de formato personalizado.

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the--custom-format-specifier"></a>Especificador de formato personalizado ":"

O especificador de formato personalizado ":" representa o separador de hora, o qual é usado para diferenciar horas, minutos e segundos. 

Se o especificador de formato ":" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão e gerará uma [FormatException](xref:System.FormatException). Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

## <a name="the--custom-format-specifier"></a>Especificador de formato personalizado "/"

O especificador de formato personalizado "/" representa o separador de data, o qual é usado para diferenciar anos, meses e dias. 

Se o especificador de formato "/" for usado sem outros especificadores de formato personalizado, ele será interpretado como um especificador de formato de data e hora padrão e gerará uma [FormatException](xref:System.FormatException). Para saber mais sobre como usar um especificador de formato simples, veja [Como usar especificadores simples de formato personalizados](#using-single-custom-format-specifiers).

## <a name="character-literals"></a>Literais de caracteres

Os seguintes caracteres de uma cadeia de caracteres de formato de data e hora personalizado são reservados e sempre são interpretados como caracteres formatação ou, no caso de ", ', / e \,, como caracteres especiais. 

  |   |   |   |      
- | - | - | - | -
F | H | M | M | d
f | g | h | m | s
y | y | z | % | :
/ | " | ' | \ |
  |   |   |   |
  
Todos os outros caracteres sempre são interpretados como literais de caracteres e, em uma operação de formatação, são incluídos na cadeia de caracteres de resultado inalterada. Em uma operação de análise, eles devem corresponder exatamente aos caracteres na cadeia de entrada; a comparação diferencia maiúsculas de minúsculas. 

O exemplo a seguir inclui os caracteres literais "PST" (que indicam a Hora Padrão do Pacífico) e “PDT” (que indicam a Hora de Verão do Pacífico) para representar o fuso horário local em uma cadeia de caracteres de formato. Observe que a cadeia de caracteres está incluída na cadeia de caracteres de resultado e que uma cadeia de caracteres que inclui a cadeia de caracteres de fuso horário local também é analisada com êxito. 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      String[] formats = { "dd MMM yyyy hh:mm tt PST", 
                           "dd MMM yyyy hh:mm tt PDT" };
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(formats[1]));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm PST";
      DateTime newDate;
      if (DateTime.TryParseExact(value, formats, null, 
                                 DateTimeStyles.None, out newDate)) 
         Console.WriteLine(newDate);
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim formats() As String = { "dd MMM yyyy hh:mm tt PST", 
                                  "dd MMM yyyy hh:mm tt PDT" }
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(formats(1)))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm PST"
      Dim newDate As Date
      If Date.TryParseExact(value, formats, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM PDT
'       12/25/2016 12:00:00 PM
```

Há duas maneiras de indicar que os caracteres devem ser interpretados como caracteres literais e não como caracteres reservados, para que possam ser incluídos em uma cadeia de caracteres de resultado ou analisados com êxito em uma cadeia de caracteres de entrada:

* Com o escape de cada caractere reservado. Para saber mais, veja [Como usar o caractere de escape](#using-the-escape-character). 
  
  O exemplo a seguir inclui os caracteres literais "pst" (que indicam a Hora Padrão do Pacífico) para representar o fuso horário local em uma cadeia de caracteres de formato. Como "s" e "t" são cadeias de caracteres de formato personalizado, ambos os caracteres devem ter um escape para serem interpretados como caracteres literais. 
  
```csharp
using System;
using System.Globalization;

public class Example
{
  public static void Main()
  {
      String format = "dd MMM yyyy hh:mm tt p\\s\\t";
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(format));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm pst";
      DateTime newDate;
      if (DateTime.TryParseExact(value, format, null, 
                                  DateTimeStyles.None, out newDate)) 
          Console.WriteLine(newDate);
      else
          Console.WriteLine("Unable to parse '{0}'", value);
  }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim fmt As String = "dd MMM yyyy hh:mm tt p\s\t" 
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(fmt))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm pst"
      Dim newDate As Date
      If Date.TryParseExact(value, fmt, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM pst
'       12/25/2016 12:00:00 PM
```
  
* Colocando toda a cadeia de caracteres literal entre aspas ou apóstrofos. O exemplo a seguir é semelhante ao anterior, mas "pst" é colocado entre aspas para indicar que toda a cadeia de caracteres delimitada deve ser interpretada como literais de caracteres. 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      String format = "dd MMM yyyy hh:mm tt \"pst\"";
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(format));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm pst";
      DateTime newDate;
      if (DateTime.TryParseExact(value, format, null, 
                                 DateTimeStyles.None, out newDate)) 
         Console.WriteLine(newDate);
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim fmt As String = "dd MMM yyyy hh:mm tt ""pst"""  
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(fmt))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm pst"
      Dim newDate As Date
      If Date.TryParseExact(value, fmt, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM pst
'       12/25/2016 12:00:00 PM
```

## <a name="notes"></a>Observações


### <a name="using-single-custom-format-specifiers"></a>Usando especificadores de formato personalizado simples

Uma cadeia de caracteres de formato de data e hora personalizado consiste em dois ou mais caracteres. Os métodos de formatação de data e hora interpretam qualquer cadeia de um único caractere como uma cadeia de caracteres de formato de data e hora padrão. Quando não reconhecem o caractere como um especificador de formato válido, eles geram uma [FormatException](xref:System.FormatException). Por exemplo, uma cadeia de caracteres de formato que consiste somente no especificador "h" é interpretada como uma cadeia de caracteres de formato padrão de data e hora. No entanto, nesse caso específico, uma exceção é gerada porque não há nenhum especificador "h" de formato padrão de data e hora. 

Para usar qualquer um dos especificadores de formato de data e hora personalizado como sendo o único especificador em uma cadeia de caracteres de formato (ou seja, para usar o especificador de formato personalizado "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" ou “/” por si só), inclua um espaço antes ou após o especificador ou inclua um especificador de formato de porcentagem "%" antes do especificador de data e hora personalizado simples.

Por exemplo, "`%h`” é interpretada como uma cadeia de caracteres de formato de data e hora personalizado que exibe a hora representada pelo valor atual de data e hora. Você também pode usar a cadeia de caracteres de formato " h" ou "H ", embora isso inclua um espaço na cadeia de caracteres resultante em conjunto com a hora. O exemplo a seguir ilustra essas três cadeias de caracteres de formatos.


```csharp
DateTime dat1 = new DateTime(2009, 6, 15, 13, 45, 0);

Console.WriteLine("'{0:%h}'", dat1);
Console.WriteLine("'{0: h}'", dat1);
Console.WriteLine("'{0:h }'", dat1);
// The example displays the following output:
//       '1'
//       ' 1'
//       '1 '
```

```vb
Dim dat1 As Date = #6/15/2009 1:45PM#

Console.WriteLine("'{0:%h}'", dat1)
Console.WriteLine("'{0: h}'", dat1)
Console.WriteLine("'{0:h }'", dat1)
' The example displays the following output:
'       '1'
'       ' 1'
'       '1 '
```

### <a name="using-the-escape-character"></a>Como usar o caractere de Escape

Os caracteres "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" ou "/" em uma cadeia de caracteres de formato são interpretados como especificadores de formato personalizados em vez de caracteres literais. Para impedir que um caractere seja interpretado como um especificador de formato, você pode precedê-lo com uma barra invertida (\)), que é o caractere de escape. O caractere de escape significa que o próximo caractere é um literal de caractere que deve ser incluído inalterado na cadeia de caracteres de resultado.

Para incluir uma barra invertida em uma cadeia de caracteres de resultado, você deve escapá-la com outra barra invertida (`\\`).

> [!NOTE]
> Alguns compiladores, como o compilador C#, também podem interpretar um único caractere de barra invertida como um caractere de escape. Para garantir que uma cadeia de caracteres seja interpretada corretamente quando formatada, você poderá usar o caractere literal de cadeia de caracteres textual (o caractere @) antes da cadeia de caracteres ou adicionar outro caractere de barra invertida antes de cada barra invertida. O exemplo de C# a seguir ilustra ambas as abordagens.

O exemplo a seguir usa o caractere de escape para impedir que a operação de formatação interprete os caracteres de "h" e "m" como especificadores de formato. 

```csharp
DateTime date = new DateTime(2009, 06, 15, 13, 45, 30, 90);
string fmt1 = "h \\h m \\m";
string fmt2 = @"h \h m \m";

Console.WriteLine("{0} ({1}) -> {2}", date, fmt1, date.ToString(fmt1));
Console.WriteLine("{0} ({1}) -> {2}", date, fmt2, date.ToString(fmt2));
// The example displays the following output:
//       6/15/2009 1:45:30 PM (h \h m \m) -> 1 h 45 m
//       6/15/2009 1:45:30 PM (h \h m \m) -> 1 h 45 m
```

```vb
Dim date1 As Date = #6/15/2009 13:45#
Dim fmt As String = "h \h m \m"

Console.WriteLine("{0} ({1}) -> {2}", date1, fmt, date1.ToString(fmt))
' The example displays the following output:
'       6/15/2009 1:45:00 PM (h \h m \m) -> 1 h 45 m 
```

### <a name="datetimeformatinfo-properties"></a>Propriedades DateTimeFormatInfo

A formatação é influenciada pelas propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) atual, que é fornecido implicitamente pela cultura de thread atual ou explicitamente pelo parâmetro [IFormatProvider](xref:System.IFormatProvider) do método que invoca a formatação. Para o parâmetro [IFormatProvider](xref:System.IFormatProvider), especifique um objeto [CultureInfo](xref:System.Globalization.CultureInfo), que representa uma cultura ou um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo). 

A cadeia de caracteres de resultado produzida por muitos dos especificadores de formato de data e hora personalizado também depende das propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) atual. Seu aplicativo pode alterar o resultado produzido por alguns especificadores de formato personalizado de data e hora ao alterar a propriedade [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) correspondente. Por exemplo, o especificador de formato "ddd" adiciona um nome de dia da semana abreviado encontrado na matriz de cadeia de caracteres [AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) à cadeia de caracteres de resultado. Da mesma forma, o especificador de formato "MMMM" adiciona um nome de mês completo encontrado na matriz de cadeias de caracteres [MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) à cadeia de caracteres de resultado.

## <a name="see-also"></a>Consulte também

[System.DateTime](xref:System.DateTime)

[System.IFormatProvider](xref:System.IFormatProvider)

[Formatação de tipos](formatting-types.md)

[Cadeias de caracteres de formato de data e hora padrão](standard-datetime.md)


