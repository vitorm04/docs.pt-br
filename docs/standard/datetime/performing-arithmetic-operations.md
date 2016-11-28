---
title: "Executando operações aritméticas com datas e horários"
description: "Executando operações aritméticas com datas e horários"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 589ac5ec-8365-4a0d-bc38-72183718110c
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: bb5cda188b6970c23e41faf82990034c3cf144ab

---

# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Executando operações aritméticas com datas e horários

Apesar de as estruturas [System.DateTime](xref:System.DateTime) e [System.DateTimeOffset](xref:System.DateTimeOffset) oferecerem membros que executam operações aritméticas em seus valores, os resultados das operações aritméticas são muito diferentes. Este artigo examina tais diferenças, as relaciona a graus de reconhecimento de fuso horário em dados de data e hora e discute como executar totalmente operações de reconhecimento de fuso horário usando dados de data e hora.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparações e operações aritméticas com valores DateTime

Os valores [System.DateTime](xref:System.DateTime) têm um grau limitado de reconhecimento de fuso horário. A propriedade [DateTime.Kind](xref:System.DateTime.Kind) permite que um valor [System.DateTimeKind](xref:System.DateTimeKind) seja atribuído à data e à hora para indicar se representa um horário local, o UTC (Tempo Universal Coordenado) ou o horário em um fuso horário não especificado. No entanto, essas informações de fuso horário limitado são ignoradas ao comparar ou executar a aritmética de data e hora em valores [DateTime](xref:System.DateTime). O exemplo a seguir, que compara o horário local atual com o horário UTC atual, ilustra isso.

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateManipulation
{
   public static void Main()
   {
      DateTime localTime = DateTime.Now;
      DateTime utcTime = DateTime.UtcNow;

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", 
                        localTime.Kind.ToString(), 
                        utcTime.Kind.ToString(), 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The {0} time is {1} the {2} time.", 
                        localTime.Kind.ToString(), 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)), 
                        utcTime.Kind.ToString());  
   }
}
// If run in the U.S. Pacific Standard Time zone, the example displays 
// the following output to the console:
//    Difference between Local and Utc time: -7:0 hours
//    The Local time is EarlierThan the Utc time.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateManipulation
   Public Sub Main()
      Dim localTime As Date = Date.Now
      Dim utcTime As Date = Date.UtcNow

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", _
                        localTime.Kind.ToString(), _
                        utcTime.Kind.ToString(), _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The {0} time is {1} the {2} time.", _
                        localTime.Kind.ToString(), _ 
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)), _
                        utcTime.Kind.ToString())  
      ' If run in the U.S. Pacific Standard Time zone, the example displays 
      ' the following output to the console:
      '    Difference between Local and Utc time: -7:0 hours
      '    The Local time is EarlierThan the Utc time.                                                    
   End Sub
End Module
```

O método [DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) informa que o horário local é anterior (ou inferior) ao horário UTC; a operação de subtração indica que a diferença entre UTC e o horário local para um sistema no fuso horário padrão do Pacífico dos EUA é de sete horas. Porém, como esses dois valores oferecem representações diferentes de um único momento, fica claro que, nesse caso, o intervalo de tempo é completamente atribuível ao deslocamento do fuso horário local em relação ao UTC. 

Normalmente, a propriedade [DateTimeKind](xref:System.DateTimeKind) não afeta os resultados retornado pelos métodos aritméticos e de comparação [DateTime](xref:System.DateTime) (como indica a comparação de dois momentos idênticos), embora possa afetar a interpretação dos resultados. Por exemplo:

* O resultado de qualquer operação aritmética executada em dois valores de data e hora cujas propriedades [DateTimeKind](xref:System.DateTimeKind) equivalem a [DateTimeKind](xref:System.DateTimeKind.Utc) refletem o intervalo de tempo real entre os dois valores. Da mesma forma, a comparação dos dois valores de data e hora reflete com precisão a relação entre horários.

* O resultado de qualquer operação aritmética ou de comparação executada em dois valores de data e hora cujas propriedades [DateTimeKind](xref:System.DateTimeKind) equivalem a [DateTimeKind.Local](xref:System.DateTimeKind.Local) ou em dois valores de data e hora com valores de propriedade [DateTimeKind](xref:System.DateTimeKind) diferentes reflete a diferença de hora do relógio entre os dois valores. 

* As operações aritméticas ou de comparação em valores de data e hora local não consideram se um valor específico é ambíguo ou inválido nem levam em conta o efeito de regras de ajuste que resultam da transição do fuso horário local de ou para o horário de verão.

* Qualquer operação que compara ou calcula a diferença entre o UTC e o horário local inclui um intervalo de tempo igual ao deslocamento do fuso horário local em relação ao UTC no resultado. 

* Qualquer operação que compara ou calcula a diferença entre um horário não especificado e o UTC ou o horário local reflete a hora do relógio simples. As diferenças de fuso horário não são consideradas; o resultado não reflete a aplicação das regras de ajuste de fuso horário. 

* Qualquer operação que compara ou calcula a diferença entre dois horários não especificados poderá incluir um intervalo desconhecido que reflete a diferença entre o horário em dois fusos horários diferentes.

Há muitos cenários nos quais as diferenças de fuso horário não afetam os cálculos de data e hora ou em que o contexto dos dados de data e hora define o significado das operações aritméticas ou de comparação. Para ver uma discussão entre alguns deles, consulte [Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](choosing-between-datetime.md).

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparações e operações aritméticas com valores DateTimeOffset

Um valor [System.DateTimeOffset](xref:System.DateTimeOffset) não inclui apenas data e hora, mas também um deslocamento que define sem ambiguidade a data e hora relativas ao UTC. Isso possibilita definir a igualdade de forma diferente do que para valores [System.DateTime](xref:System.DateTime). Apesar de os valores [DateTime](xref:System.DateTime) serem iguais se tiverem o mesmo valor de data e hora, os valores [DateTimeOffset](xref:System.DateTimeOffset) valores são iguais caso ambos se refiram ao mesmo momento. Isso torna um valor [DateTimeOffset](xref:System.DateTimeOffset) mais preciso e com menos necessidade de interpretação quando usado em comparações e na maioria das operações aritméticas que determinam o intervalo entre duas datas e horas. O exemplo a seguir, que é o equivalente [DateTimeOffset](xref:System.DateTimeOffset) ao exemplo anterior que comparou valores DateTime locais e do UTC, mostra essa diferença no comportamento.

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateTimeOffsetManipulation
{
   public static void Main()
   {
      DateTimeOffset localTime = DateTimeOffset.Now;
      DateTimeOffset utcTime = DateTimeOffset.UtcNow;

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours", 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The local time is {0} UTC.", 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)));  
   }
}
// Regardless of the local time zone, the example displays 
// the following output to the console:
//    Difference between local time and UTC: 0:00 hours.
//    The local time is TheSameAs UTC.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateTimeOffsetManipulation
   Public Sub Main()
      Dim localTime As DateTimeOffset = DateTimeOffset.Now
      Dim utcTime As DateTimeOffset = DateTimeOffset.UtcNow

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours.", _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The local time is {0} UTC.", _
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)))  
   End Sub
End Module
' Regardless of the local time zone, the example displays 
' the following output to the console:
'    Difference between local time and UTC: 0:00 hours.
'    The local time is TheSameAs UTC.
'          Console.WriteLine(e.GetType().Name)
```

Neste exemplo, o método [DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) indica que o horário local atual e o horário UTC atual são iguais; a subtração dos valores [DateTimeOffset](xref:System.DateTimeOffset) indica que a diferença entre os dois horários é [TimeSpan.Zero](xref:System.TimeSpan.Zero). 

A limitação principal do uso de valores [DateTimeOffset](xref:System.DateTimeOffset) na aritmética de data e hora é que, apesar de os valores [DateTimeOffset](xref:System.DateTimeOffset) terem algum reconhecimento de fuso horário, não fazem reconhecimento total de fuso horário. Apesar de o deslocamento do valor [DateTimeOffset](xref:System.DateTimeOffset) refletir um deslocamento do fuso horário em relação ao UTC quando uma variável [DateTimeOffset](xref:System.DateTimeOffset) é atribuída pela primeira vez a um valor, ele se torna desassociado do fuso horário posteriormente. Como não estão mais diretamente associadas a um horário identificável, a adição e a subtração dos intervalos de data e hora não consideram as regras de ajuste de um fuso horário. 

Para ilustrar, a transição para o horário de verão no fuso horário padrão da região central EUA ocorre às 2h. em 9 de março de 2008. Isso significa que adicionar um intervalo de duas horas e meia ao fuso horário padrão da região central de 1h30min em 9 de março de 2008 deve produzir uma data e hora de 5h em 9 de março de 2008. No entanto, como mostra o exemplo a seguir, o resultado da adição é 4h em 9 de março de 2008. Observe que o resultado dessa operação representa o momento correto, embora não seja o horário no fuso horário em que estamos interessados (ou seja, não tem o deslocamento de fuso horário esperado).

```csharp
using System;

public class IntervalArithmetic
{
   public static void Main()
   {
      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      const string tzName = "Central Standard Time";
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime));

         // Add two and a half hours      
         DateTimeOffset centralTime2 = centralTime1.Add(twoAndAHalfHours);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

```vb
Module IntervalArithmetic
   Public Sub Main()
      Dim generalTime As Date = #03/09/2008 1:30AM#
      Const tzName As String = "Central Standard Time"
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime))

         ' Add two and a half hours      
         Dim centralTime2 As DateTimeOffset = centralTime1.Add(twoAndAHalfHours)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operações aritméticas com horários nos fusos horários

A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) não fornece os métodos que aplicam regras de ajuste automaticamente quando você executa a aritmética de data e hora. No entanto, é possível fazer isso convertendo o horário em um fuso horário para UTC, executando a operação aritmética e, em seguida, convertendo do UTC novamente para o horário no fuso horário. Para ver detalhes, consulte [Como usar fusos horários em aritmética de data e hora](use-time-zones-in-arithmetic.md).

Por exemplo, o código a seguir é semelhante ao código anterior, que adicionou duas horas e meia às 2h em 9 de março de 2008. No entanto, como converte um horário padrão da região central em UTC antes de realizar a aritmética de data e hora e, depois, converte o resultado do UTC novamente no horário padrão da região central, o horário resultante reflete a transição do fuso horário padrão da região central para o horário de verão.

```csharp
using System;

public class TimeZoneAwareArithmetic
{
   public static void Main()
   {
      const string tzName = "Central Standard Time";

      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                                       cst.GetUtcOffset(generalTime));

         // Add two and a half hours
         DateTimeOffset utcTime = centralTime1.ToUniversalTime();
         utcTime += twoAndAHalfHours;

         DateTimeOffset centralTime2 = TimeZoneInfo.ConvertTime(utcTime, cst);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

```vb
Module TimeZoneAwareArithmetic
   Public Sub Main()
      Const tzName As String = "Central Standard Time"

      Dim generalTime As Date = #03/09/2008 1:30AM#
      Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName) 
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    cst.GetUtcOffset(generalTime))

         ' Add two and a half hours 
         Dim utcTime As DateTimeOffset = centralTime1.ToUniversalTime()
         utcTime += twoAndAHalfHours

         Dim centralTime2 As DateTimeOffset = TimeZoneInfo.ConvertTime(utcTime, cst)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)

[Como usar fusos horários em aritmética de data e hora](use-time-zones-in-arithmetic.md)





<!--HONumber=Nov16_HO4-->


