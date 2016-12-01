---
title: Cadeias de caracteres de formato TimeSpan personalizado
description: Cadeias de caracteres de formato TimeSpan personalizado
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e79745eb-6ebd-4e62-85c4-4f2830c27285
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 168bd497891ead884413fad4542943a24de7a7f4

---

# <a name="custom-timespan-format-strings"></a>Cadeias de caracteres de formato TimeSpan personalizado

Uma cadeia de caracteres de formato [TimeSpan](xref:System.TimeSpan) define a representação de cadeia de caracteres de um valor de [TimeSpan](xref:System.TimeSpan) que é resultante de uma operação de formatação. Uma cadeia de caracteres de formato personalizado consiste em um ou mais especificadores de formato [TimeSpan](xref:System.TimeSpan) em conjunto com qualquer número de caracteres literais. Qualquer cadeia de caracteres que não é uma cadeia de caracteres de formato [TimeSpan padrão](standard-timespan.md) é interpretada como uma cadeia de caracteres de formato [TimeSpan](xref:System.TimeSpan) personalizada.

> [!IMPORTANT]
> Os especificadores de formato [TimeSpan](xref:System.TimeSpan) personalizados não incluem símbolos de separador de espaço reservado, como os símbolos que separam dias de horas, horas de minutos ou segundos de frações de segundo. Em vez disso, esses símbolos devem ser incluídos na cadeia de caracteres de formato personalizado como literais de cadeia de caracteres. Por exemplo, `"dd\.hh\:mm"` define um ponto (.) como o separador entre dias e horas e dois-pontos (:) como o separador entre horas e minutos. 

> Especificadores de formato [TimeSpan](xref:System.TimeSpan) personalizado também não incluem um símbolo de sinal que permite diferenciar entre intervalos de tempo positivos e negativos. Para incluir um símbolo de sinal, você precisa construir uma cadeia de caracteres de formato usando lógica condicional. A seção [Outros caracteres](#other-characters) inclui um exemplo. 

As representações de cadeia de caracteres de valores [TimeSpan](xref:System.TimeSpan) são produzidas por chamadas para as sobrecargas do método [TimeSpan](xref:System.TimeSpan) `ToString`, bem como por métodos que dão suporte à formatação de composição, como [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Para saber mais, veja [Formatação de tipos](formatting-types.md) e [Formatação de composição](composite-format.md). O exemplo a seguir ilustra o uso de sequências de formato padrão em operações de formatação.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan duration = new TimeSpan(1, 12, 23, 62);

      string output = null;
      output = "Time of Travel: " + duration.ToString("%d") + " days";
      Console.WriteLine(output);
      output = "Time of Travel: " + duration.ToString(xref:"dd\.hh\:mm\:ss"); 
      Console.WriteLine(output);

      Console.WriteLine("Time of Travel: {0:%d} day(s)", duration);
      Console.WriteLine("Time of Travel: {0:dd\\.hh\\:mm\\:ss} days", duration);
   }
}
// The example displays the following output:
//       Time of Travel: 1 days
//       Time of Travel: 01.12:24:02
//       Time of Travel: 1 day(s)
//       Time of Travel: 01.12:24:02 days
```

```vb
Module Example
   Public Sub Main()
      Dim duration As New TimeSpan(1, 12, 23, 62)

      Dim output As String = Nothing
      output = "Time of Travel: " + duration.ToString("%d") + " days"
      Console.WriteLine(output)
      output = "Time of Travel: " + duration.ToString("dd\.hh\:mm\:ss") 
      Console.WriteLine(output)

      Console.WriteLine("Time of Travel: {0:%d} day(s)", duration)
      Console.WriteLine("Time of Travel: {0:dd\.hh\:mm\:ss} days", duration)
   End Sub
End Module
' The example displays the following output:
'       Time of Travel: 1 days
'       Time of Travel: 01.12:24:02
'       Time of Travel: 1 day(s)
'       Time of Travel: 01.12:24:02 days
```

As cadeias de caracteres de formato [TimeSpan](xref:System.TimeSpan) personalizado também são usadas pelos métodos [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) e [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)) para definir o formato necessário de cadeias de caracteres de entrada para operações de análise. (A análise converte a representação de sequência de um valor para esse valor). O exemplo a seguir ilustra o uso de sequências de formato padrão em operações de análise.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value = null;
      TimeSpan interval;

      value = "6";
      if (TimeSpan.TryParseExact(value, "%d", null, out interval))
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"));
      else
         Console.WriteLine("Unable to parse '{0}'", value);

      value = "16:32.05";
      if (TimeSpan.TryParseExact(value, @"mm\:ss\.ff", null, out interval))
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"));
      else
         Console.WriteLine("Unable to parse '{0}'", value);

      value= "12.035";
      if (TimeSpan.TryParseExact(value, "ss\\.fff", null, out interval))
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"));
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       6 --> 6.00:00:00
//       16:32.05 --> 00:16:32.0500000
//       12.035 --> 00:00:12.0350000
```

```vb
Module Example
   Public Sub Main()
      Dim value As String = Nothing
      Dim interval As TimeSpan

      value = "6"
      If TimeSpan.TryParseExact(value, "%d", Nothing, interval) Then
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"))
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If

      value = "16:32.05"
      If TimeSpan.TryParseExact(value, "mm\:ss\.ff", Nothing, interval) Then
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"))
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If

      value= "12.035"
      If TimeSpan.TryParseExact(value, "ss\.fff", Nothing, interval) Then
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"))
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       6 --> 6.00:00:00
'       16:32.05 --> 00:16:32.0500000
'       12.035 --> 00:00:12.0350000
```

A tabela a seguir descreve os especificadores de formato personalizado de data e hora.

Especificador de formato | Descrição | Exemplos
---------------- | ----------- | --------
"d", "%d" | O número de dias inteiros no intervalo de tempo. | `new TimeSpan(6, 14, 32, 17, 685):` `%d --> "6"`;  `d\.hh\:mm --> "6.14:32"`
"dd", "dddddddd" | O número de dias inteiros no intervalo de tempo, preenchido com zeros à esquerda, conforme necessário. | `new TimeSpan(6, 14, 32, 17, 685):` `ddd --> "006"`; `dd\.hh\:mm --> "06.14:32"`
"h", "%h" | O número de horas inteiras no intervalo de tempo que não são contadas como parte dos dias. Horas de dígito único não têm um zero à esquerda. | `new TimeSpan(6, 14, 32, 17, 685):` `%h --> "14"`; `hh\:mm --> "14:32"`
"hh" | O número de horas inteiras no intervalo de tempo que não são contadas como parte dos dias. Horas de dígito único têm um zero à esquerda. | `new TimeSpan(6, 14, 32, 17, 685):` `hh --> "14"`  `new TimeSpan(6, 8, 32, 17, 685):` `hh --> 08`
"m", "%m" | O número de minutos inteiros no intervalo de tempo que não são incluídos como parte das horas ou dias. Minutos de dígito único não têm um zero à esquerda. | `new TimeSpan(6, 14, 8, 17, 685):` `%m --> "8"`; `h\:m --> "14:8"`
"mm" | O número de minutos inteiros no intervalo de tempo que não são incluídos como parte das horas ou dias. Minutos de dígito único têm um zero à esquerda. | `new TimeSpan(6, 14, 8, 17, 685):` `mm --> "08"` `new TimeSpan(6, 8, 5, 17, 685):` `d\.hh\:mm\:ss --> 6.08:05:17`
"s", "%s" | O número de segundos inteiros no intervalo de tempo que não são incluídos como parte das horas, dias ou minutos. Segundos de dígito único não têm um zero à esquerda. | `TimeSpan.FromSeconds(12.965):` `%s --> 12`; `s\.fff --> 12.965`
"ss" | O número de segundos inteiros no intervalo de tempo que não são incluídos como parte das horas, dias ou minutos. Segundos de dígito único têm um zero à esquerda. | `TimeSpan.FromSeconds(6.965):` `ss --> 06`; `ss\.fff --> 06.965`
"f", "%f" | Os décimos de segundo em um intervalo de tempo. | `TimeSpan.FromSeconds(6.895):` `f --> 8`; `ss\.f --> 06.8`
"ff" | Os centésimos de segundo em um intervalo de tempo. | `TimeSpan.FromSeconds(6.895):` `ff --> 89`; `ss\.ff --> 06.89`
"fff" | Os milissegundos em um intervalo de tempo. | `TimeSpan.FromSeconds(6.895):` `fff --> 895`; `ss\.fff --> 06.895`
"ffff" | Os décimos de milésimos de segundo em um intervalo de tempo. | `TimeSpan.Parse("0:0:6.8954321"):` `ffff --> 8954`; `ss\.ffff --> 06.8954`
"fffff" | As centenas de milésimos de segundo em um intervalo de tempo. | `TimeSpan.Parse("0:0:6.8954321"):` `ffff --> 89543`; `ss\.ffff --> 06.89543`
"ffffff" | Os milionésimos de segundo em um intervalo de tempo. | `TimeSpan.Parse("0:0:6.8954321"):` `ffff --> 895432`; `ss\.ffff --> 06.895432`
"fffffff" | Os dez milionésimos de segundo (ou as marcas fracionárias) em um intervalo de tempo. | `TimeSpan.Parse("0:0:6.8954321"):` `ffff --> 8954321`; `ss\.ffff --> 06.8954321`
"F", "%F" | Os décimos de segundo em um intervalo de tempo. Nada será exibido se o dígito for zero. | `TimeSpan.Parse("00:00:06.32"):` `%F: 3`  `TimeSpan.Parse("0:0:3.091"):` `ss\.F: 03.`
"FF" | Os centésimos de segundo em um intervalo de tempo. Zeros à direita fracionais ou dois dígitos zero não são incluídos. |  `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 32`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFF" | Os milissegundos em um intervalo de tempo. Zeros à direita fracionais não são incluídos. |  `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 329`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFFF" | Os décimos de milésimos de segundo em um intervalo de tempo. Zeros à direita fracionais não são incluídos. |  `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 3291`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFFFF" | As centenas de milésimos de segundo em um intervalo de tempo. Zeros à direita fracionais não são incluídos. | `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 32917`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFFFFF" | Os milionésimos de segundo em um intervalo de tempo. Zeros à direita fracionais não são exibidos. | `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 329179`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFFFFFF" | Os décimos de milionésimos de segundo em um intervalo de tempo. Zeros à direita fracionais ou sete dígitos zero não são exibidos. | `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 3291791`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.19`
'string' | Delimitador de cadeia de caracteres literal | `new TimeSpan(14, 32, 17):` `hh':'mm':'ss --> "14:32:17"`
\ | O caractere de escape. | `new TimeSpan(14, 32, 17):` `hh\:mm\:ss --> "14:32:17"`
Qualquer outro caractere | Qualquer outro caractere sem escape é interpretado como um especificador de formato personalizado. | `new TimeSpan(14, 32, 17):` `hh\:mm\:ss --> "14:32:17"`

## <a name="the-d-custom-format-specifier"></a>Especificador de formato personalizado "d"

O especificador de formato personalizado "d" fornece o valor da propriedade [TimeSpan.Days](xref:System.TimeSpan.Days), que representa o número de dias inteiros no intervalo de tempo. Ele gera o número total de dias em um valor de [TimeSpan](xref:System.TimeSpan), mesmo se o valor tiver mais de um dígito. Se o valor de [TimeSpan.Days](xref:System.TimeSpan.Days) for zero, o especificador gerará "0".

Se o especificador de formato personalizado "d" for usado sozinho, especifique "%d" para que ele não seja interpretado incorretamente como uma cadeia de caracteres de formato padrão. O exemplo a seguir fornece uma ilustração.

```csharp
TimeSpan ts1 = new TimeSpan(16, 4, 3, 17, 250);
Console.WriteLine(ts1.ToString("%d"));
// Displays 16
```

```vb
Dim ts As New TimeSpan(16, 4, 3, 17, 250)
Console.WriteLine(ts.ToString("%d"))
' Displays 16 
```

O exemplo a seguir ilustra o uso do especificador de formato personalizado “d”.

```csharp
TimeSpan ts2 = new TimeSpan(4, 3, 17);
Console.WriteLine(ts2.ToString(xref:"d\.hh\:mm\:ss"));

TimeSpan ts3 = new TimeSpan(3, 4, 3, 17);
Console.WriteLine(ts3.ToString(xref:"d\.hh\:mm\:ss"));
// The example displays the following output:
//       0.04:03:17
//       3.04:03:17
```

```vb
Dim ts2 As New TimeSpan(4, 3, 17)
Console.WriteLine(ts2.ToString("d\.hh\:mm\:ss"))

Dim ts3 As New TimeSpan(3, 4, 3, 17)
Console.WriteLine(ts3.ToString("d\.hh\:mm\:ss"))
' The example displays the following output:
'       0.04:03:17
'       3.04:03:17
```

## <a name="the-dd-dddddddd-custom-format-specifiers"></a>Especificadores de formato personalizado "dd"-"dddddddd"

Os especificadores de formato personalizados "dd", "ddd", "dddd", "ddddd", "dddddd", "ddddddd" e "dddddddd" fornecem o valor da propriedade [TimeSpan.Days](xref:System.TimeSpan.Days), que representa o número de dias inteiros no intervalo de tempo. 

A cadeia de caracteres de saída inclui um número mínimo de dígitos especificado pelo número de caracteres "d" no especificador de formato e é preenchido com zeros à esquerda conforme necessário. Se os dígitos do número de dias ultrapassarem o número de caracteres "d" no especificador de formato, o número total de dias será fornecido na cadeia de caracteres de resultado.

O exemplo a seguir usa esses especificadores de formato para exibir a representação de cadeia de caracteres de dois valores de [TimeSpan](xref:System.TimeSpan). O valor do componente de dias do primeiro intervalo de tempo é zero; o valor do componente de dias do segundo é 365.

```csharp
TimeSpan ts1 = new TimeSpan(0, 23, 17, 47);
TimeSpan ts2 = new TimeSpan(365, 21, 19, 45);

for (int ctr = 2; ctr <= 8; ctr++)
{
   string fmt = new String('d', ctr) + @"\.hh\:mm\:ss";
   Console.WriteLine("{0} --> {1:" + fmt + "}", fmt, ts1);  
   Console.WriteLine("{0} --> {1:" + fmt + "}", fmt, ts2);
   Console.WriteLine();
}  
// The example displays the following output:
//       dd\.hh\:mm\:ss --> 00.23:17:47
//       dd\.hh\:mm\:ss --> 365.21:19:45
//       
//       ddd\.hh\:mm\:ss --> 000.23:17:47
//       ddd\.hh\:mm\:ss --> 365.21:19:45
//       
//       dddd\.hh\:mm\:ss --> 0000.23:17:47
//       dddd\.hh\:mm\:ss --> 0365.21:19:45
//       
//       ddddd\.hh\:mm\:ss --> 00000.23:17:47
//       ddddd\.hh\:mm\:ss --> 00365.21:19:45
//       
//       dddddd\.hh\:mm\:ss --> 000000.23:17:47
//       dddddd\.hh\:mm\:ss --> 000365.21:19:45
//       
//       ddddddd\.hh\:mm\:ss --> 0000000.23:17:47
//       ddddddd\.hh\:mm\:ss --> 0000365.21:19:45
//       
//       dddddddd\.hh\:mm\:ss --> 00000000.23:17:47
//       dddddddd\.hh\:mm\:ss --> 00000365.21:19:45
```

```vb
Dim ts1 As New TimeSpan(0, 23, 17, 47)
Dim ts2 As New TimeSpan(365, 21, 19, 45)

For ctr As Integer = 2 To 8
   Dim fmt As String = New String("d"c, ctr) + "\.hh\:mm\:ss"
   Console.WriteLine("{0} --> {1:" + fmt + "}", fmt, ts1) 
   Console.WriteLine("{0} --> {1:" + fmt + "}", fmt, ts2)
   Console.WriteLine()
Next  
' The example displays the following output:
'       dd\.hh\:mm\:ss --> 00.23:17:47
'       dd\.hh\:mm\:ss --> 365.21:19:45
'       
'       ddd\.hh\:mm\:ss --> 000.23:17:47
'       ddd\.hh\:mm\:ss --> 365.21:19:45
'       
'       dddd\.hh\:mm\:ss --> 0000.23:17:47
'       dddd\.hh\:mm\:ss --> 0365.21:19:45
'       
'       ddddd\.hh\:mm\:ss --> 00000.23:17:47
'       ddddd\.hh\:mm\:ss --> 00365.21:19:45
'       
'       dddddd\.hh\:mm\:ss --> 000000.23:17:47
'       dddddd\.hh\:mm\:ss --> 000365.21:19:45
'       
'       ddddddd\.hh\:mm\:ss --> 0000000.23:17:47
'       ddddddd\.hh\:mm\:ss --> 0000365.21:19:45
'       
'       dddddddd\.hh\:mm\:ss --> 00000000.23:17:47
'       dddddddd\.hh\:mm\:ss --> 00000365.21:19:45
```

## <a name="the-h-custom-format-specifier"></a>Especificador de formato personalizado "h"

O especificador de formato personalizado "h" fornece o valor da propriedade [TimeSpan.Hours](xref:System.TimeSpan.Hours), que representa o número de horas inteiras no intervalo de tempo que não são contadas como parte do componente de dia. Ele retorna um valor de cadeia de caracteres de um dígito se o valor da propriedade [TimeSpan.Hours](xref:System.TimeSpan.Hours) for de 0 a 9 e retorna um valor de cadeia de caracteres de dois dígitos se o valor da propriedade [TimeSpan.Hours](xref:System.TimeSpan.Hours) for de 10 a 23.

Se o especificador de formato personalizado "h" for usado sozinho, especifique "%h" para que ele não seja interpretado incorretamente como uma cadeia de caracteres de formato padrão. O exemplo a seguir fornece uma ilustração.

```csharp
TimeSpan ts = new TimeSpan(3, 42, 0);
Console.WriteLine("{0:%h} hours {0:%m} minutes", ts);
// The example displays the following output:
//       3 hours 42 minutes
```

```vb
Dim ts As New TimeSpan(3, 42, 0)
Console.WriteLine("{0:%h} hours {0:%m} minutes", ts)
' The example displays the following output:
'       3 hours 42 minutes
```

Normalmente, em uma operação de análise, uma cadeia de caracteres de entrada que inclui apenas um único número é interpretada como o número de dias. Você pode usar o especificador de formato personalizado "%h" em vez disso para interpretar a cadeia de caracteres numérica como o número de horas. O exemplo a seguir fornece uma ilustração.

```csharp
string value = "8";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "%h", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       08:00:00
```

```vb
Dim value As String = "8"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "%h", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       08:00:00
```

O exemplo a seguir ilustra o uso do especificador de formato personalizado “h”.

```csharp
TimeSpan ts1 = new TimeSpan(14, 3, 17);
Console.WriteLine(ts1.ToString(xref:"d\.h\:mm\:ss"));

TimeSpan ts2 = new TimeSpan(3, 4, 3, 17);
Console.WriteLine(ts2.ToString(xref:"d\.h\:mm\:ss"));
// The example displays the following output:
//       0.14:03:17
//       3.4:03:17
```

```vb
Dim ts1 As New TimeSpan(14, 3, 17)
Console.WriteLine(ts1.ToString("d\.h\:mm\:ss"))

Dim ts2 As New TimeSpan(3, 4, 3, 17)
Console.WriteLine(ts2.ToString("d\.h\:mm\:ss"))
' The example displays the following output:
'       0.14:03:17
'       3.4:03:17
```

## <a name="the-hh-custom-format-specifier"></a>Especificador de formato personalizado "hh"

O especificador de formato personalizado "hh" fornece o valor da propriedade [TimeSpan.Hours](xref:System.TimeSpan.Hours), que representa o número de horas inteiras no intervalo de tempo que não são contadas como parte do componente de dia. Para valores de 0 a 9, a cadeia de caracteres de saída inclui um zero à esquerda. 

Normalmente, em uma operação de análise, uma cadeia de caracteres de entrada que inclui apenas um único número é interpretada como o número de dias. Você pode usar o especificador de formato personalizado "hh" em vez disso para interpretar a cadeia de caracteres numérica como o número de horas. O exemplo a seguir fornece uma ilustração.

```csharp
string value = "08";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "hh", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       08:00:00 
```

```vb
Dim value As String = "08"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "hh", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       08:00:00
```

O exemplo a seguir ilustra o uso do especificador de formato personalizado “hh”.

```csharp
TimeSpan ts1 = new TimeSpan(14, 3, 17);
Console.WriteLine(ts1.ToString(xref:"d\.hh\:mm\:ss"));

TimeSpan ts2 = new TimeSpan(3, 4, 3, 17);
Console.WriteLine(ts2.ToString(xref:"d\.hh\:mm\:ss"));
// The example displays the following output:
//       0.14:03:17
//       3.04:03:17
```

```vb
Dim ts1 As New TimeSpan(14, 3, 17)
Console.WriteLine(ts1.ToString("d\.hh\:mm\:ss"))

Dim ts2 As New TimeSpan(3, 4, 3, 17)
Console.WriteLine(ts2.ToString("d\.hh\:mm\:ss"))
' The example displays the following output:
'       0.14:03:17
'       3.04:03:17
```

## <a name="the-m-custom-format-specifier"></a>Especificador de formato personalizado "m"

O especificador de formato personalizado "m" fornece o valor da propriedade [TimeSpan.Minutes](xref:System.TimeSpan.Minutes), que representa o número de minutos inteiros no intervalo de tempo que não são contados como parte do componente de dia. Ele retorna um valor de cadeia de caracteres de um dígito se o valor da propriedade [TimeSpan.Minutes](xref:System.TimeSpan.Minutes) for de 0 a 9 e retorna um valor de cadeia de caracteres de dois dígitos se o valor da propriedade [TimeSpan.Minutes](xref:System.TimeSpan.Minutes) for de 10 a 59.

Se o especificador de formato personalizado "m" for usado sozinho, especifique "%m" para que ele não seja interpretado incorretamente como uma cadeia de caracteres de formato padrão. O exemplo a seguir fornece uma ilustração.

```csharp
TimeSpan ts = new TimeSpan(3, 42, 0);
Console.WriteLine("{0:%h} hours {0:%m} minutes", ts);
// The example displays the following output:
//       3 hours 42 minutes
```

```vb
Dim ts As New TimeSpan(3, 42, 0)
Console.WriteLine("{0:%h} hours {0:%m} minutes", ts)
' The example displays the following output:
'       3 hours 42 minutes
```

Normalmente, em uma operação de análise, uma cadeia de caracteres de entrada que inclui apenas um único número é interpretada como o número de dias. Você pode usar o especificador de formato personalizado "%m" em vez disso para interpretar a cadeia de caracteres numérica como o número de minutos. O exemplo a seguir fornece uma ilustração.

```csharp
string value = "3";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "%m", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       00:03:00
```

```vb
Dim value As String = "3"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "%m", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       00:03:00                              
```

O exemplo a seguir ilustra o uso do especificador de formato personalizado “m”.

```csharp
TimeSpan ts1 = new TimeSpan(0, 6, 32);
Console.WriteLine("{0:m\\:ss} minutes", ts1);

TimeSpan ts2 = new TimeSpan(3, 4, 3, 17);
Console.WriteLine("Elapsed time: {0:m\\:ss}", ts2);
// The example displays the following output:
//       6:32 minutes
//       Elapsed time: 18:44
```

```vb
Dim ts1 As New TimeSpan(0, 6, 32)
Console.WriteLine("{0:m\:ss} minutes", ts1)

Dim ts2 As New TimeSpan(0, 18, 44)
Console.WriteLine("Elapsed time: {0:m\:ss}", ts2)
' The example displays the following output:
'       6:32 minutes
'       Elapsed time: 18:44
```

## <a name="the-mm-custom-format-specifier"></a>Especificador de formato personalizado "mm"

O especificador de formato personalizado "mm" fornece o valor da propriedade [TimeSpan.Minutes](xref:System.TimeSpan.Minutes), que representa o número de minutos inteiros no intervalo de tempo que não são incluídos como parte do componente de horas ou dias. Para valores de 0 a 9, a cadeia de caracteres de saída inclui um zero à esquerda. 

Normalmente, em uma operação de análise, uma cadeia de caracteres de entrada que inclui apenas um único número é interpretada como o número de dias. Você pode usar o especificador de formato personalizado "mm" em vez disso para interpretar a cadeia de caracteres numérica como o número de minutos. O exemplo a seguir fornece uma ilustração.

```csharp
string value = "07";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "mm", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       00:07:00
```

```vb
Dim value As String = "05"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "mm", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       00:05:00
```

O exemplo a seguir ilustra o uso do especificador de formato personalizado “mm”.

```csharp
TimeSpan departTime = new TimeSpan(11, 12, 00);
TimeSpan arriveTime = new TimeSpan(16, 28, 00);
Console.WriteLine("Travel time: {0:hh\\:mm}", 
                  arriveTime - departTime);
// The example displays the following output:
//       Travel time: 05:16
```

```vb
Dim departTime As New TimeSpan(11, 12, 00)
Dim arriveTime As New TimeSpan(16, 28, 00)
Console.WriteLine("Travel time: {0:hh\:mm}", 
                  arriveTime - departTime)
' The example displays the following output:
'       Travel time: 05:16
```

## <a name="the-s-custom-format-specifier"></a>Especificador de formato personalizado "s"

O especificador de formato personalizado "s" fornece o valor da propriedade [TimeSpan.Seconds](xref:System.TimeSpan.Seconds), que representa o número de segundos inteiros no intervalo de tempo que não são incluídos como parte do componente de horas, dias ou minutos. Ele retorna um valor de cadeia de caracteres de um dígito se o valor da propriedade [TimeSpan.Seconds](xref:System.TimeSpan.Seconds) for de 0 a 9 e retorna um valor de cadeia de caracteres de dois dígitos se o valor da propriedade [TimeSpan.Seconds](xref:System.TimeSpan.Seconds) for de 10 a 59. 

Se o especificador de formato personalizado "s" for usado sozinho, especifique "%s" para que ele não seja interpretado incorretamente como uma cadeia de caracteres de formato padrão. O exemplo a seguir fornece uma ilustração.

```csharp
TimeSpan ts = TimeSpan.FromSeconds(12.465);
Console.WriteLine(ts.ToString("%s"));
// The example displays the following output:
//       12
```

```vb
Dim ts As TimeSpan = TimeSpan.FromSeconds(12.465)
Console.WriteLine(ts.ToString("%s"))
' The example displays the following output:
'       12
```

Normalmente, em uma operação de análise, uma cadeia de caracteres de entrada que inclui apenas um único número é interpretada como o número de dias. Você pode usar o especificador de formato personalizado "%s" em vez disso para interpretar a cadeia de caracteres numérica como o número de segundos. O exemplo a seguir fornece uma ilustração.

```csharp
string value = "9";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "%s", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       00:00:09
```

```vb
Dim value As String = "9"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "%s", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       00:00:09
```

O exemplo a seguir ilustra o uso do especificador de formato personalizado “s”.

```csharp
TimeSpan startTime = new TimeSpan(0, 12, 30, 15, 0);
TimeSpan endTime = new TimeSpan(0, 12, 30, 21, 3);
Console.WriteLine(xref:"Elapsed Time: {0:s\:fff} seconds", 
                  endTime - startTime);
// The example displays the following output:
//       Elapsed Time: 6:003 seconds      
```

```vb
Dim startTime As New TimeSpan(0, 12, 30, 15, 0)
Dim endTime As New TimeSpan(0, 12, 30, 21, 3)
Console.WriteLine("Elapsed Time: {0:s\:fff} seconds", 
                  endTime - startTime)
' The example displays the following output:
'       Elapsed Time: 6:003 seconds
```

## <a name="the-ss-custom-format-specifier"></a>Especificador de formato personalizado "ss"

O especificador de formato personalizado "ss" fornece o valor da propriedade [TimeSpan.Seconds](xref:System.TimeSpan.Seconds), que representa o número de segundos inteiros no intervalo de tempo que não são incluídos como parte do componente de horas, dias ou minutos. Para valores de 0 a 9, a cadeia de caracteres de saída inclui um zero à esquerda. 

Normalmente, em uma operação de análise, uma cadeia de caracteres de entrada que inclui apenas um único número é interpretada como o número de dias. Você pode usar o especificador de formato personalizado "ss" em vez disso para interpretar a cadeia de caracteres numérica como o número de segundos. O exemplo a seguir fornece uma ilustração.

```csharp
string[] values = { "49", "9", "06" };
TimeSpan interval;
foreach (string value in values)
{
   if (TimeSpan.TryParseExact(value, "ss", null, out interval))
      Console.WriteLine(interval.ToString("c"));
   else
      Console.WriteLine("Unable to convert '{0}' to a time interval", 
                        value);   
}
// The example displays the following output:
//       00:00:49
//       Unable to convert '9' to a time interval
//       00:00:06
```

```vb
Dim values() As String = { "49", "9", "06" }
Dim interval As TimeSpan
For Each value As String In values
   If TimeSpan.TryParseExact(value, "ss", Nothing, interval) Then
      Console.WriteLine(interval.ToString("c"))
   Else
      Console.WriteLine("Unable to convert '{0}' to a time interval", 
                        value)   
   End If   
Next   
' The example displays the following output:
'       00:00:49
'       Unable to convert '9' to a time interval
'       00:00:06
```

O exemplo a seguir ilustra o uso do especificador de formato personalizado “ss”.

```csharp
TimeSpan interval1 = TimeSpan.FromSeconds(12.60);
Console.WriteLine(interval1.ToString(xref:"ss\.fff"));

TimeSpan interval2 = TimeSpan.FromSeconds(6.485);
Console.WriteLine(interval2.ToString(xref:"ss\.fff"));
// The example displays the following output:
//       12.600
//       06.485
```

```vb
Dim interval1 As TimeSpan = TimeSpan.FromSeconds(12.60)
Console.WriteLine(interval1.ToString("ss\.fff"))
Dim interval2 As TimeSpan = TimeSpan.FromSeconds(6.485)
Console.WriteLine(interval2.ToString("ss\.fff"))
' The example displays the following output:
'       12.600
'       06.485
```

## <a name="the-f-custom-format-specifier"></a>Especificador de formato personalizado "f"

O especificador de formato personalizado "f" gera os décimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a cadeia de caracteres de entrada deve conter exatamente um dígito fracionário. 

Se o especificador de formato personalizado "f" for usado sozinho, especifique "%f" para que ele não seja interpretado incorretamente como uma cadeia de caracteres de formato padrão.

O exemplo a seguir usa o especificador de formato personalizado "f" para exibir os décimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). "f" é usado primeiro como o especificador de formato único e, depois, combinado com o especificador "s" em uma cadeia de caracteres de formato personalizado.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-ff-custom-format-specifier"></a>Especificador de formato personalizado "ff"

O especificador de formato personalizado "ff" gera os centésimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a cadeia de caracteres de entrada deve conter exatamente dois dígitos fracionários. 

O exemplo a seguir usa o especificador de formato personalizado "ff" para exibir os centésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). "ff" é usado primeiro como o especificador de formato único e, depois, combinado com o especificador "s" em uma cadeia de caracteres de formato personalizado.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-fff-custom-format-specifier"></a>Especificador de formato personalizado "fff"

O especificador de formato personalizado "fff" (com três caracteres "f") gera os milissegundos em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a cadeia de caracteres de entrada deve conter exatamente três dígitos fracionários. 

O exemplo a seguir usa o especificador de formato personalizado "fff" para exibir os milissegundos em um valor de [TimeSpan](xref:System.TimeSpan). "fff" é usado primeiro como o especificador de formato único e, depois, combinado com o especificador "s" em uma cadeia de caracteres de formato personalizado.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-ffff-custom-format-specifier"></a>Especificador de formato personalizado "ffff"
O especificador de formato personalizado "ffff" (com quatro caracteres "f") gera os décimos de milésimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a cadeia de caracteres de entrada deve conter exatamente quatro dígitos fracionários. 

O exemplo a seguir usa o especificador de formato personalizado "ffff" para exibir os décimos de milésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). "ffff" é usado primeiro como o especificador de formato único e, depois, combinado com o especificador "s" em uma cadeia de caracteres de formato personalizado.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-fffff-custom-format-specifier"></a>Especificador de formato personalizado "fffff"
O especificador de formato personalizado "fffff" (com cinco caracteres "f") gera os centésimos de milésimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a cadeia de caracteres de entrada deve conter exatamente cinco dígitos fracionários. 

O exemplo a seguir usa o especificador de formato personalizado "fffff" para exibir os centésimos de milésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). "fffff" é usado primeiro como o especificador de formato único e, depois, combinado com o especificador "s" em uma cadeia de caracteres de formato personalizado.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432 
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-ffffff-custom-format-specifier"></a>Especificador de formato personalizado "ffffff"

O especificador de formato personalizado "ffffff" (com seis caracteres "f") gera os milionésimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a cadeia de caracteres de entrada deve conter exatamente seis dígitos fracionários. 

O exemplo a seguir usa o especificador de formato personalizado "ffffff" para exibir os milionésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). Ele é usado primeiro como o especificador de formato único e, depois, combinado com o especificador "s" em uma cadeia de caracteres de formato personalizado.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432 
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-fffffff-custom-format-specifier"></a>Especificador de formato personalizado "fffffff"

O especificador de formato personalizado "fffffff" (com sete caracteres "f") gera os décimos de milionésimos de segundo (ou o número fracionário de marcadores) em um intervalo de tempo. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a cadeia de caracteres de entrada deve conter exatamente sete dígitos fracionários. 

O exemplo a seguir usa o especificador de formato personalizado "fffffff" para exibir o número fracionário de marcadores em um valor de [TimeSpan](xref:System.TimeSpan). Ele é usado primeiro como o especificador de formato único e, depois, combinado com o especificador "s" em uma cadeia de caracteres de formato personalizado.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432 
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-f-custom-format-specifier"></a>Especificador de formato personalizado "F"

O especificador de formato personalizado "F" gera os décimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Se o valor dos décimos de segundo do intervalo de tempo for zero, ele não será incluído na cadeia de caracteres de resultado. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a presença do dígito de décimos de segundo é opcional.

Se o especificador de formato personalizado "F" for usado sozinho, especifique "%F" para que ele não seja interpretado incorretamente como uma cadeia de caracteres de formato padrão.

O exemplo a seguir usa o especificador de formato personalizado "F" para exibir os décimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). Ele também usa este especificador de formato personalizado em uma operação de análise.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.669");
Console.WriteLine("{0} ('%F') --> {0:%F}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.091");
Console.WriteLine("{0} ('ss\\.F') --> {0:ss\\.F}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.1", "0:0:03.12" };
string fmt = @"h\:m\:ss\.F";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}                        
// The example displays the following output:
//       Formatting:
//       00:00:03.6690000 ('%F') --> 6
//       00:00:03.0910000 ('ss\.F') --> 03.
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.F') --> 00:00:03
//       0:0:03.1 ('h\:m\:ss\.F') --> 00:00:03.1000000
//       Cannot parse 0:0:03.12 with 'h\:m\:ss\.F'.
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.669")
Console.WriteLine("{0} ('%F') --> {0:%F}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.091")
Console.WriteLine("{0} ('ss\.F') --> {0:ss\.F}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.1", "0:0:03.12" }
Dim fmt As String = "h\:m\:ss\.F"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6690000 ('%F') --> 6
'       00:00:03.0910000 ('ss\.F') --> 03.
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.F') --> 00:00:03
'       0:0:03.1 ('h\:m\:ss\.F') --> 00:00:03.1000000
'       Cannot parse 0:0:03.12 with 'h\:m\:ss\.F'.
```

## <a name="the-ff-custom-format-specifier"></a>Especificador de formato personalizado "FF"

O especificador de formato personalizado "FF" gera os centésimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Se houver zeros fracionários à direita, eles não serão incluídos na cadeia de caracteres de resultado. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a presença do dígito de décimos e centésimos de segundo é opcional.

O exemplo a seguir usa o especificador de formato personalizado "FF" para exibir os centésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). Ele também usa este especificador de formato personalizado em uma operação de análise.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.697");
Console.WriteLine("{0} ('FF') --> {0:FF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.809");
Console.WriteLine("{0} ('ss\\.FF') --> {0:ss\\.FF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.1", "0:0:03.127" };
string fmt = @"h\:m\:ss\.FF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}
// The example displays the following output:
//       Formatting:
//       00:00:03.6970000 ('FF') --> 69
//       00:00:03.8090000 ('ss\.FF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FF') --> 00:00:03
//       0:0:03.1 ('h\:m\:ss\.FF') --> 00:00:03.1000000
//       Cannot parse 0:0:03.127 with 'h\:m\:ss\.FF'. 
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.697")
Console.WriteLine("{0} ('FF') --> {0:FF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.809")
Console.WriteLine("{0} ('ss\.FF') --> {0:ss\.FF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.1", "0:0:03.127" }
Dim fmt As String = "h\:m\:ss\.FF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6970000 ('FF') --> 69
'       00:00:03.8090000 ('ss\.FF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FF') --> 00:00:03
'       0:0:03.1 ('h\:m\:ss\.FF') --> 00:00:03.1000000
'       Cannot parse 0:0:03.127 with 'h\:m\:ss\.FF'.
```

## <a name="the-fff-custom-format-specifier"></a>Especificador de formato personalizado "FFF"

O especificador de formato personalizado "FFF" (com três caracteres "F") gera os milissegundos em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Se houver zeros fracionários à direita, eles não serão incluídos na cadeia de caracteres de resultado. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a presença do dígito de décimos, centésimos e milésimos de segundo é opcional.

O exemplo a seguir usa o especificador de formato personalizado "FFF" para exibir os milésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). Ele também usa este especificador de formato personalizado em uma operação de análise.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.6974");
Console.WriteLine("{0} ('FFF') --> {0:FFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.8009");
Console.WriteLine("{0} ('ss\\.FFF') --> {0:ss\\.FFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.1279" };
string fmt = @"h\:m\:ss\.FFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}
// The example displays the following output:
//       Formatting:
//       00:00:03.6974000 ('FFF') --> 697
//       00:00:03.8009000 ('ss\.FFF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FFF') --> 00:00:03
//       0:0:03.12 ('h\:m\:ss\.FFF') --> 00:00:03.1200000
//       Cannot parse 0:0:03.1279 with 'h\:m\:ss\.FFF'.  
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.6974")
Console.WriteLine("{0} ('FFF') --> {0:FFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.8009")
Console.WriteLine("{0} ('ss\.FFF') --> {0:ss\.FFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.1279" }
Dim fmt As String = "h\:m\:ss\.FFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6974000 ('FFF') --> 697
'       00:00:03.8009000 ('ss\.FFF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FFF') --> 00:00:03
'       0:0:03.12 ('h\:m\:ss\.FFF') --> 00:00:03.1200000
'       Cannot parse 0:0:03.1279 with 'h\:m\:ss\.FFF'.
```

## <a name="the-ffff-custom-format-specifier"></a>Especificador de formato personalizado "FFFF"

O especificador de formato personalizado "FFFF" (com quatro caracteres "f") gera os décimos de milésimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Se houver zeros fracionários à direita, eles não serão incluídos na cadeia de caracteres de resultado. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a presença do dígito de décimos, centésimos, milésimos e décimos de milésimos de segundo é opcional.

O exemplo a seguir usa o especificador de formato personalizado "FFFF" para exibir os décimos de milésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). Ele também usa o especificador de formato personalizado "FFFF" em uma operação de análise.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.69749");
Console.WriteLine("{0} ('FFFF') --> {0:FFFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.80009");
Console.WriteLine("{0} ('ss\\.FFFF') --> {0:ss\\.FFFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.12795" };
string fmt = @"h\:m\:ss\.FFFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}
// The example displays the following output:
//       Formatting:
//       00:00:03.6974900 ('FFFF') --> 6974
//       00:00:03.8000900 ('ss\.FFFF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FFFF') --> 00:00:03
//       0:0:03.12 ('h\:m\:ss\.FFFF') --> 00:00:03.1200000
//       Cannot parse 0:0:03.12795 with 'h\:m\:ss\.FFFF'.
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.69749")
Console.WriteLine("{0} ('FFFF') --> {0:FFFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.80009")
Console.WriteLine("{0} ('ss\.FFFF') --> {0:ss\.FFFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.12795" }
Dim fmt As String = "h\:m\:ss\.FFFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6974900 ('FFFF') --> 6974
'       00:00:03.8000900 ('ss\.FFFF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FFFF') --> 00:00:03
'       0:0:03.12 ('h\:m\:ss\.FFFF') --> 00:00:03.1200000
'       Cannot parse 0:0:03.12795 with 'h\:m\:ss\.FFFF'.
```

## <a name="the-fffff-custom-format-specifier"></a>Especificador de formato personalizado "FFFFF"

O especificador de formato personalizado "FFFFF" (com cinco caracteres "F") gera os centésimos de milésimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Se houver zeros fracionários à direita, eles não serão incluídos na cadeia de caracteres de resultado. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a presença do dígito de décimos, centésimos, milésimos e décimos de milésimos e centésimos de milésimos de segundo é opcional.

O exemplo a seguir usa o especificador de formato personalizado "FFFFF" para exibir os centésimos de milésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). Ele também usa o especificador de formato personalizado "FFFFF" em uma operação de análise.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.697497");
Console.WriteLine("{0} ('FFFFF') --> {0:FFFFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.800009");
Console.WriteLine("{0} ('ss\\.FFFFF') --> {0:ss\\.FFFFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.127956" };
string fmt = @"h\:m\:ss\.FFFFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}                       
// The example displays the following output:
//       Formatting:
//       00:00:03.6974970 ('FFFFF') --> 69749
//       00:00:03.8000090 ('ss\.FFFFF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FFFF') --> 00:00:03
//       0:0:03.12 ('h\:m\:ss\.FFFF') --> 00:00:03.1200000
//       Cannot parse 0:0:03.127956 with 'h\:m\:ss\.FFFF'. 
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.697497")
Console.WriteLine("{0} ('FFFFF') --> {0:FFFFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.800009")
Console.WriteLine("{0} ('ss\.FFFFF') --> {0:ss\.FFFFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.127956" }
Dim fmt As String = "h\:m\:ss\.FFFFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6974970 ('FFFFF') --> 69749
'       00:00:03.8000090 ('ss\.FFFFF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FFFF') --> 00:00:03
'       0:0:03.12 ('h\:m\:ss\.FFFF') --> 00:00:03.1200000
'       Cannot parse 0:0:03.127956 with 'h\:m\:ss\.FFFF'.
```

## <a name="the-ffffff-custom-format-specifier"></a>Especificador de formato personalizado "FFFFFF"

O especificador de formato personalizado "FFFFFF" (com seis caracteres "F") gera os milionésimos de segundo em um intervalo de tempo. Em uma operação de formatação, os dígitos fracionários restantes são truncados. Se houver zeros fracionários à direita, eles não serão incluídos na cadeia de caracteres de resultado. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a presença do dígito de décimos, centésimos, milésimos, décimos de milésimos, centésimos de milésimos e milionésimos de segundo é opcional.

O exemplo a seguir usa o especificador de formato personalizado "FFFFFF" para exibir os milionésimos de segundo em um valor de [TimeSpan](xref:System.TimeSpan). Ele também usa este especificador de formato personalizado em uma operação de análise.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.6974974");
Console.WriteLine("{0} ('FFFFFF') --> {0:FFFFFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.8000009");
Console.WriteLine("{0} ('ss\\.FFFFFF') --> {0:ss\\.FFFFFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.1279569" };
string fmt = @"h\:m\:ss\.FFFFFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}                       
// The example displays the following output:
//       Formatting:
//       00:00:03.6974974 ('FFFFFF') --> 697497
//       00:00:03.8000009 ('ss\.FFFFFF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FFFFFF') --> 00:00:03
//       0:0:03.12 ('h\:m\:ss\.FFFFFF') --> 00:00:03.1200000
//       Cannot parse 0:0:03.1279569 with 'h\:m\:ss\.FFFFFF'.
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.6974974")
Console.WriteLine("{0} ('FFFFFF') --> {0:FFFFFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.8000009")
Console.WriteLine("{0} ('ss\.FFFFFF') --> {0:ss\.FFFFFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.1279569" }
Dim fmt As String = "h\:m\:ss\.FFFFFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6974974 ('FFFFFF') --> 697497
'       00:00:03.8000009 ('ss\.FFFFFF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FFFFFF') --> 00:00:03
'       0:0:03.12 ('h\:m\:ss\.FFFFFF') --> 00:00:03.1200000
'       Cannot parse 0:0:03.1279569 with 'h\:m\:ss\.FFFFFF'
```

## <a name="the-fffffff-custom-format-specifier"></a>Especificador de formato personalizado "FFFFFFF"

O especificador de formato personalizado "FFFFFFF" (com sete caracteres "F") gera os décimos de milionésimos de segundo (ou o número fracionário de marcadores) em um intervalo de tempo. Se houver zeros fracionários à direita, eles não serão incluídos na cadeia de caracteres de resultado. Em uma operação de análise que chama método [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), a presença dos sete dígitos fracionários na cadeia de caracteres de entrada é opcional.

O exemplo a seguir usa o especificador de formato personalizado "FFFFFFF" para exibir as partes fracionárias de um segundo em um valor de [TimeSpan](xref:System.TimeSpan). Ele também usa este especificador de formato personalizado em uma operação de análise.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.6974974");
Console.WriteLine("{0} ('FFFFFFF') --> {0:FFFFFFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.9500000");
Console.WriteLine("{0} ('ss\\.FFFFFFF') --> {0:ss\\.FFFFFFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.1279569" };
string fmt = @"h\:m\:ss\.FFFFFFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}
// The example displays the following output:
//    Formatting:
//    00:00:03.6974974 ('FFFFFFF') --> 6974974
//    00:00:03.9500000 ('ss\.FFFFFFF') --> 03.95
//    
//    Parsing:
//    0:0:03. ('h\:m\:ss\.FFFFFFF') --> 00:00:03
//    0:0:03.12 ('h\:m\:ss\.FFFFFFF') --> 00:00:03.1200000
//    0:0:03.1279569 ('h\:m\:ss\.FFFFFFF') --> 00:00:03.1279569 
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.6974974")
Console.WriteLine("{0} ('FFFFFFF') --> {0:FFFFFFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.9500000")
Console.WriteLine("{0} ('ss\.FFFFFFF') --> {0:ss\.FFFFFFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.1279569" }
Dim fmt As String = "h\:m\:ss\.FFFFFFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'    Formatting:
'    00:00:03.6974974 ('FFFFFFF') --> 6974974
'    00:00:03.9500000 ('ss\.FFFFFFF') --> 03.95
'    
'    Parsing:
'    0:0:03. ('h\:m\:ss\.FFFFFFF') --> 00:00:03
'    0:0:03.12 ('h\:m\:ss\.FFFFFFF') --> 00:00:03.1200000
'    0:0:03.1279569 ('h\:m\:ss\.FFFFFFF') --> 00:00:03.1279569  
```

## <a name="other-characters"></a>Outros caracteres

Qualquer outro caractere sem escape em uma cadeia de caracteres de formato, incluindo um caractere de espaço em branco, é interpretado como um especificador de formato personalizado. Na maioria dos casos, a presença de qualquer outro caractere sem escape resulta em uma [FormatException](xref:System.FormatException). 

Há duas maneiras de incluir um caractere literal em uma cadeia de caracteres de formato:

* Coloque-o entre aspas simples (o delimitador de cadeia de caracteres literal). 

* Preceda-o com uma barra invertida ("\"), que é interpretada como um caractere de escape. Isso significa que, em C#, a cadeia de caracteres de formato deve demarcado por @-quoted,, ou o caractere literal deve ser precedido por uma barra invertida adicional.

  Em alguns casos, talvez você precise usar lógica condicional para incluir um literal de escape em uma cadeia de caracteres de formato. O exemplo a seguir usa lógica condicional para incluir um símbolo de sinal para intervalos de tempo negativos. 
  
  ```csharp
  using System;

  public class Example
  {
     public static void Main()
     {
        TimeSpan result = new DateTime(2010, 01, 01) - DateTime.Now; 
        String fmt = (result < TimeSpan.Zero ?  "\\-" : "") + "dd\\.hh\\:mm";

        Console.WriteLine(result.ToString(fmt));
        Console.WriteLine("Interval: {0:" + fmt + "}", result);
     }
  }
  // The example displays output like the following:
  //       -1291.10:54
  //       Interval: -1291.10:54
  ```

  ```vb
  Module Example
     Public Sub Main()
        Dim result As TimeSpan = New DateTime(2010, 01, 01) - Date.Now 
        Dim fmt As String = If(result < TimeSpan.Zero, "\-", "") + "dd\.hh\:mm"

        Console.WriteLine(result.ToString(fmt))
        Console.WriteLine("Interval: {0:" + fmt + "}", result)
     End Sub
  End Module
  ' The example displays output like the following:
  '       -1291.10:54
  '       Interval: -1291.10:54
  ```
  
O .NET não define uma gramática para separadores em intervalos de tempo. Isso significa que os separadores entre dias e horas, horas e minutos, minutos e segundos, e segundos e frações de segundo devem ser tratados como literais de caracteres em uma cadeia de caracteres de formato.

O exemplo a seguir usa o caractere de escape e a aspa simples para definir uma cadeia de caracteres de formato personalizado que inclui a palavra "minutos" na cadeia de caracteres de saída. 

```csharp
TimeSpan interval = new TimeSpan(0, 32, 45);
// Escape literal characters in a format string.
string fmt = @"mm\:ss\ \m\i\n\u\t\e\s";
Console.WriteLine(interval.ToString(fmt));
// Delimit literal characters in a format string with the ' symbol.
fmt = "mm':'ss' minutes'";      
Console.WriteLine(interval.ToString(fmt));
// The example displays the following output: 
//       32:45 minutes      
//       32:45 minutes
```

```vb
Dim interval As New TimeSpan(0, 32, 45)
' Escape literal characters in a format string.
Dim fmt As String = "mm\:ss\ \m\i\n\u\t\e\s"
Console.WriteLine(interval.ToString(fmt))
' Delimit literal characters in a format string with the ' symbol.
fmt = "mm':'ss' minutes'"
Console.WriteLine(interval.ToString(fmt))
' The example displays the following output: 
'       32:45 minutes      
'       32:45 minutes
```

## <a name="see-also"></a>Consulte também

[Formatação de tipos](formatting-types.md)

[Cadeias de caracteres de formato TimeSpan padrão](standard-timespan.md)  




<!--HONumber=Nov16_HO1-->


