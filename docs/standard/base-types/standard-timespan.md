---
title: "Cadeias de caracteres de formato TimeSpan padrão"
description: "Cadeias de caracteres de formato TimeSpan padrão"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 4e0f02f1-4abd-47b5-8995-5c3ff45b0ce1
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: bb209c7bac71960fa0a679e546bedae486b412b8

---

# <a name="standard-timespan-format-strings"></a>Cadeias de caracteres de formato TimeSpan padrão

Uma cadeia de caracteres de formato padrão [TimeSpan](xref:System.TimeSpan) usa um único especificador de formato para definir a representação de texto de um valor [TimeSpan](xref:System.TimeSpan) que resulta de uma operação de formatação. Qualquer cadeia de caracteres de formato que contenha mais de um caractere, incluindo espaço em branco, é interpretada como uma cadeia de caracteres de formato [TimeSpan](xref:System.TimeSpan) personalizada. Para obter mais informações, consulte [Cadeias de caracteres de formato TimeSpan personalizadas](custom-timespan.md).

As representações de sequência de valores [TimeSpan](xref:System.TimeSpan) são produzidas por chamadas para as sobrecargas do método [TimeSpan.ToString](xref:System.TimeSpan.ToString), bem como por métodos que oferecem suporte à formatação de composição, como o [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Para obter mais informações, consulte [Tipos de formatação](formatting-types.md) e [Formatação de composição](composite-format.md). O exemplo a seguir ilustra o uso de sequências de formato padrão em operações de formatação

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan duration = new TimeSpan(1, 12, 23, 62);
      string output = "Time of Travel: " + duration.ToString("c");
      Console.WriteLine(output);

      Console.WriteLine("Time of Travel: {0:c}", duration); 
   }
}
// The example displays the following output:
//       Time of Travel: 1.12:24:02
//       Time of Travel: 1.12:24:02
```

```vb
Module Example
   Public Sub Main()
      Dim duration As New TimeSpan(1, 12, 23, 62)
      Dim output As String = "Time of Travel: " + duration.ToString("c")
      Console.WriteLine(output)

      Console.WriteLine("Time of Travel: {0:c}", duration) 
   End Sub
End Module
' The example displays the following output:
'       Time of Travel: 1.12:24:02
'       Time of Travel: 1.12:24:02
```

As cadeias de caracteres de formato [TimeSpan](xref:System.TimeSpan) padrão também são usadas pelos métodos [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) e [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)) para definir o formato ncessário de cadeias de caracteres de entrada para operações de análise. (A análise converte a representação de sequência de um valor para esse valor). O exemplo a seguir ilustra o uso de sequências de formato padrão em operações de análise.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value = "1.03:14:56.1667";
      TimeSpan interval;
      try {
         interval = TimeSpan.ParseExact(value, "c", null);
         Console.WriteLine("Converted '{0}' to {1}", value, interval);
      }   
      catch (FormatException) {
         Console.WriteLine("{0}: Bad Format", value);
      }   
      catch (OverflowException) {
         Console.WriteLine("{0}: Out of Range", value);
      }

      if (TimeSpan.TryParseExact(value, "c", null, out interval))
         Console.WriteLine("Converted '{0}' to {1}", value, interval);
      else
         Console.WriteLine("Unable to convert {0} to a time interval.", 
                           value);
   }
}
// The example displays the following output:
//       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
//       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
```

```vb
Module Example
   Public Sub Main()
      Dim value As String = "1.03:14:56.1667"
      Dim interval As TimeSpan
      Try
         interval = TimeSpan.ParseExact(value, "c", Nothing)
         Console.WriteLine("Converted '{0}' to {1}", value, interval)
      Catch e As FormatException
         Console.WriteLine("{0}: Bad Format", value)
      Catch e As OverflowException
         Console.WriteLine("{0}: Out of Range", value)
      End Try

      If TimeSpan.TryParseExact(value, "c", Nothing, interval) Then
         Console.WriteLine("Converted '{0}' to {1}", value, interval)
      Else
         Console.WriteLine("Unable to convert {0} to a time interval.", 
                           value)
      End If                
   End Sub
End Module
' The example displays the following output:
'       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
'       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
```

A tabela a seguir lista os especificadores de formato de intervalo de tempo padrão.

Especificador de formato | Nome | Descrição | Exemplos
---------------- | ---- | ----------- | --------
"c" | Formato de constante (invariável) | Esse especificador não é sensível à cultura. Ele assume a forma [-][d’.’]hh’:’mm’:’ss[‘.’fffffff]. (As sequências de formato "t" e "T" produzem os mesmos resultados). | `TimeSpan.Zero -> 00:00:00`; `New TimeSpan(0, 0, 30, 0) -> 00:30:00`; `New TimeSpan(3, 17, 25, 30, 500) -> 3.17:25:30.5000000`
"g" | Formato curto geral | Esse especificador gera apenas o que é necessário. Ele é sensível à cultura e assume o formato [-][d’:’]h’:’mm’:’ss[.FFFFFFF]. | `New TimeSpan(1, 3, 16, 50, 500) -> 1:3:16:50.5 (en-US)`; `New TimeSpan(1, 3, 16, 50, 500) -> 1:3:16:50,5 (fr-FR)`; `New TimeSpan(1, 3, 16, 50, 599) -> 1:3:16:50.599 (en-US)`; `New TimeSpan(1, 3, 16, 50, 599) -> 1:3:16:50,599 (fr-FR)`
"G" | Formato longo geral | Esse especificador sempre gera dias e sete dígitos de fração. Ele é sensível à cultura e assume o formato [-]d’:’hh’:’mm’:’ss.fffffff. | `New TimeSpan(18, 30, 0) -> 0:18:30:00.0000000 (en-US)`; `New TimeSpan(18, 30, 0) -> 0:18:30:00,0000000 (fr-FR)` 

## <a name="the-constant-c-format-specifier"></a>O especificador de formato de constante ("c")

O especificador de formato "c" retorna a representação de cadeia de caracteres de um valor [TimeSpan](xref:System.TimeSpan) da seguinte forma:

[-][_d_.]_hh_:_mm_:_ss_[._fffffff_]

Os elementos entre colchetes ([ e ]) são opcionais. O ponto (.) e os dois pontos (:) são símbolos literais. A tabela a seguir descreve os elementos restantes. 

Elemento | Descrição
------- | -----------
- | Um sinal negativo opcional, que indica um intervalo de tempo negativo.
*d* | O número opcional de dias, sem zeros à esquerda.
*hh* | O número de horas, que varia de "00" a "23".
*mm* | O número de minutos, que varia de "00" a "59".
*ss* | O número de segundos, que varia de "00" a "59".
*fffffff* | A parte de fração opcional de um segundo. Seu valor pode variar de "0000001" (um pulso ou um décimo milionésimo de segundo) até "9999999" (9.999.999 dez milionésimos de segundo ou um segundo menos um pulso). 

Ao contrário dos especificadores de formato de "g" e "G", o especificador de formato "c" não é sensível à cultura. Ele produz a representação de cadeia de caracteres de um valor [TimeSpan](xref:System.TimeSpan) que é invariável e é comum a todas as versões anteriores do .NET Framework, antes do .NET Framework 4. A "c"é a cadeia de caracteres de formato [TimeSpan](xref:System.TimeSpan) padrão. O método [TimeSpan.ToString](xref:System.TimeSpan.ToString) formata um valor de intervalo de tempo usando a cadeia de caracteres de formato "c".

> [!NOTE]
> [TimeSpan](xref:System.TimeSpan) também oferece suporte às cadeias de caracteres de formato padrão "t" e "T", que são idênticas em comportamento à cadeia de caracteres de formato padrão "c".

O exemplo a seguir cria uma instância de dois objetos [TimeSpan](xref:System.TimeSpan), usa-os para executar operações aritméticas e exibe o resultado. Em cada caso, ele usa formatação de composição para exibir o valor [TimeSpan](xref:System.TimeSpan) usando o especificador de formato "c".

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:c} - {1:c} = {2:c}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2);

      interval1 = new TimeSpan(0, 0, 1, 14, 365);
      interval2 = TimeSpan.FromTicks(2143756);  
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       07:45:16 - 18:12:38 = -10:27:22
//       07:45:16 + 18:12:38 = 1.01:57:54
//       00:01:14.3650000 + 00:00:00.2143756 = 00:01:14.5793756
```

```vb
Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:c} - {1:c} = {2:c}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2)

      interval1 = New TimeSpan(0, 0, 1, 14, 365)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       07:45:16 - 18:12:38 = -10:27:22
'       07:45:16 + 18:12:38 = 1.01:57:54
'       00:01:14.3650000 + 00:00:00.2143756 = 00:01:14.5793756
```

## <a name="the-general-short-g-format-specifier"></a>O especificador de formato curto geral ("g")

O especificador de formato [TimeSpan](xref:System.TimeSpan) "g" retorna a representação de sequência de caracteres de um valor [TimeSpan](xref:System.TimeSpan) em um formato compacto, incluindo apenas os elementos que são necessários. Ele tem o seguinte formato:

[-][_d_:]_h_:_mm_:_ss_[._FFFFFFF_]

Os elementos entre colchetes ([ e ]) são opcionais. Os dois pontos (:) são um símbolo literal. A tabela a seguir descreve os elementos restantes.

Elemento | Descrição
------- | -----------
- | Um sinal negativo opcional, que indica um intervalo de tempo negativo.
*d* | O número opcional de dias, sem zeros à esquerda.
*hh* | O número de horas, que varia de "0" a "23", sem zeros à esquerda. 
*mm* | O número de minutos, que varia de "00" a "59".
*ss* | O número de segundos, que varia de "00" a "59".
. | O separador de fração de segundo.
*FFFFFFF* | As frações de segundo. Uma vez que é exibido o mínimo de dígitos possível.

Como o especificador de formato "G", o especificador de formato "g" é localizado. O separador de fração de segundo se baseia na cultura atual.

O exemplo a seguir cria uma instância de dois objetos [TimeSpan](xref:System.TimeSpan), usa-os para executar operações aritméticas e exibe o resultado. Em cada caso, ele usa formatação de composição para exibir o valor [TimeSpan](xref:System.TimeSpan) usando o especificador de formato "g". Além disso, ele formata o valor [TimeSpan](xref:System.TimeSpan) usando as convenções de formatação da cultura atual do sistema (que, nesse caso, é inglês – Estados Unidos ou en-US) e da cultura francês – França (fr-FR).

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:g} - {1:g} = {2:g}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), 
                        "{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2));

      interval1 = new TimeSpan(0, 0, 1, 14, 36);
      interval2 = TimeSpan.FromTicks(2143756);      
      Console.WriteLine("{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       7:45:16 - 18:12:38 = -10:27:22
//       7:45:16 + 18:12:38 = 1:1:57:54
//       0:01:14.036 + 0:00:00.2143756 = 0:01:14.2503756
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:g} - {1:g} = {2:g}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), 
                        "{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2))

      interval1 = New TimeSpan(0, 0, 1, 14, 36)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       7:45:16 - 18:12:38 = -10:27:22
'       7:45:16 + 18:12:38 = 1:1:57:54
'       0:01:14.036 + 0:00:00.2143756 = 0:01:14.2503756
```

## <a name="the-general-long-g-format-specifier"></a>O especificador de formato longo geral ("G")

O especificador de formato [TimeSpan](xref:System.TimeSpan) "G" retorna a representação de cadeia de caracteres de um valor [TimeSpan](xref:System.TimeSpan) em um formato longo que sempre inclui dias e frações de segundos. A sequência que resulta do especificador de formato padrão "G" tem o seguinte formato:

[-]*d*:*hh*:*mm*:*ss*.*fffffff*

Os elementos entre colchetes ([ e ]) são opcionais. Os dois pontos (:) são um símbolo literal. A tabela a seguir descreve os elementos restantes.

Elemento | Descrição
------- | -----------
- | Um sinal negativo opcional, que indica um intervalo de tempo negativo.
*d* | O número opcional de dias, sem zeros à esquerda.
*hh* | O número de horas, que varia de "0" a "23". 
*mm* | O número de minutos, que varia de "00" a "59".
*ss* | O número de segundos, que varia de "00" a "59".
. | O separador de fração de segundo.
*fffffff* | As frações de segundo.

Como o especificador de formato "G", o especificador de formato "g" é localizado. O separador de fração de segundo se baseia na cultura atual.

O exemplo a seguir cria uma instância de dois objetos [TimeSpan](xref:System.TimeSpan), usa-os para executar operações aritméticas e exibe o resultado. Em cada caso, ele usa formatação de composição para exibir o valor [TimeSpan](xref:System.TimeSpan) usando o especificador de formato "G". Além disso, ele formata o valor [TimeSpan](xref:System.TimeSpan) usando as convenções de formatação da cultura atual do sistema (que, nesse caso, é inglês – Estados Unidos ou en-US) e da cultura francês – França (fr-FR). 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:G} - {1:G} = {2:G}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), 
                        "{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2));

      interval1 = new TimeSpan(0, 0, 1, 14, 36);
      interval2 = TimeSpan.FromTicks(2143756);      
      Console.WriteLine("{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       0:07:45:16.0000000 - 0:18:12:38.0000000 = -0:10:27:22.0000000
//       0:07:45:16,0000000 + 0:18:12:38,0000000 = 1:01:57:54,0000000
//       0:00:01:14.0360000 + 0:00:00:00.2143756 = 0:00:01:14.2503756
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:G} - {1:G} = {2:G}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), 
                        "{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2))

      interval1 = New TimeSpan(0, 0, 1, 14, 36)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       0:07:45:16.0000000 - 0:18:12:38.0000000 = -0:10:27:22.0000000
'       0:07:45:16,0000000 + 0:18:12:38,0000000 = 1:01:57:54,0000000
'       0:00:01:14.0360000 + 0:00:00:00.2143756 = 0:00:01:14.2503756
```

## <a name="see-also"></a>Consulte também

[Formatando tipos](formatting-types.md)

[Formatação de composição](composite-format.md)

[Analisando cadeias de caracteres](parsing-strings.md)




<!--HONumber=Nov16_HO3-->


