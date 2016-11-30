---
title: "Como usar fusos horários em aritmética de data e hora"
description: "Como usar fusos horários em aritmética de data e hora"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 26870cdc-1709-4978-831b-ff2a2f24856f
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: da4c5aec6e02393c9e6201edd766eb7579a40b5e

---

# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Como usar fusos horários em aritmética de data e hora

Normalmente, quando você executa a aritmética de data e hora usando valores de [System.DateTimeOffset](xref:System.DateTimeOffset), o resultado não reflete nenhuma regra de ajuste de fuso horário. Isso é verdadeiro mesmo quando o fuso horário do valor de data e hora é claramente identificável. Este artigo mostra como executar operações aritméticas em valores de data e hora que pertencem a um fuso horário específico. Os resultados das operações aritméticas refletirão as regras de ajuste do fuso horário.

## <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Para aplicar as regras de ajuste à aritmética de data e hora

1. Implemente um método de acoplamento próximo de um valor de data e hora com o fuso horário ao qual ele pertence. Por exemplo, declare uma estrutura que inclui o valor de data e hora e seu fuso horário. O exemplo a seguir usa essa abordagem para vincular um valor de [DateTimeOffset](xref:System.DateTimeOffset) ao seu fuso horário.

    ```csharp
    // Define a structure for DateTime values for internal use only
    internal struct TimeWithTimeZone
    {
    TimeZoneInfo TimeZone;
    DateTimeOffset Time;
    }
    ```

    ```vb
    ' Define a structure for DateTime values for internal use only
    Friend Structure TimeWithTimeZone
       Dim TimeZone As TimeZoneInfo
       Dim Time As Date
    End Structure
    ```
    
2. Converta uma hora para UTC (Tempo Universal Coordenado) chamando o método [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)).

3. Execute a operação aritmética na hora UTC.

4. Converta a hora de UTC para o fuso horário associado da hora original chamando o método [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)). 

## <a name="example"></a>Exemplo

O exemplo a seguir adiciona duas horas e trinta minutos a 9 de março de 2008, à 1h30 do Horário Padrão Central. A transição do fuso horário para o horário de verão ocorre 30 minutos depois, às 2h. em 9 de março de 2008. Como o exemplo segue as quatro etapas listadas na seção anterior, ele relata corretamente a hora resultante como 5h. em 9 de março de 2008. 

```csharp
using System;

public struct TimeZoneTime
{
   public TimeZoneInfo TimeZone;
   public DateTimeOffset Time;

   public TimeZoneTime(TimeZoneInfo tz, DateTimeOffset time)
   {
      if (tz == null) 
         throw new ArgumentNullException("The time zone cannot be a null reference.");

      this.TimeZone = tz;
      this.Time = time;   
   }

   public TimeZoneTime AddTime(TimeSpan interval)
   {
      // Convert time to UTC
      DateTimeOffset utcTime = TimeZoneInfo.ConvertTime(this.Time, TimeZoneInfo.Utc);      
      // Add time interval to time
      utcTime = utcTime.Add(interval);
      // Convert time back to time in time zone
      return new TimeZoneTime(this.TimeZone, TimeZoneInfo.ConvertTime(utcTime, this.TimeZone));
   }
}

public class TimeArithmetic
{
   public const string tzName = "Central Standard Time";

   public static void Main()
   {
      try
      {
         TimeZoneTime cstTime1, cstTime2;

         TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
         DateTime time1 = new DateTime(2008, 3, 9, 1, 30, 0);          
         TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

         cstTime1 = new TimeZoneTime(cst, 
                        new DateTimeOffset(time1, cst.GetUtcOffset(time1)));
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours);
         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, 
                                                    twoAndAHalfHours.ToString(),  
                                                    cstTime2.Time);
      }
      catch
      {
         Console.WriteLine("Unable to find {0}.", tzName);
      }
   }
}
```

```vb
Public Structure TimeZoneTime
   Public TimeZone As TimeZoneInfo
   Public Time As Date

   Public Sub New(tz As TimeZoneInfo, time As Date)
      If tz Is Nothing Then _
         Throw New ArgumentNullException("The time zone cannot be a null reference.")

      Me.TimeZone = tz
      Me.Time = time
   End Sub

   Public Function AddTime(interval As TimeSpan) As TimeZoneTime
      ' Convert time to UTC
      Dim utcTime As DateTime = TimeZoneInfo.ConvertTimeToUtc(Me.Time, _
                                                              Me.TimeZone)      
      ' Add time interval to time
      utcTime = utcTime.Add(interval)
      ' Convert time back to time in time zone
      Return New TimeZoneTime(Me.TimeZone, TimeZoneInfo.ConvertTime(utcTime, _
                              TimeZoneInfo.Utc, Me.TimeZone))
   End Function
End Structure

Module TimeArithmetic
   Public Const tzName As String = "Central Standard Time"

   Public Sub Main()
      Try
         Dim cstTime1, cstTime2 As TimeZoneTime

         Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName)
         Dim time1 As Date = #03/09/2008 1:30AM#
         Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

         cstTime1 = New TimeZoneTime(cst, time1)
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours)

         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, _
                                                    twoAndAHalfHours.ToString(), _ 
                                                    cstTime2.Time)  
      Catch
         Console.WriteLine("Unable to find {0}.", tzName)
      End Try   
   End Sub   
End Module
```

Observe que se esta adição for simplesmente realizada no valor [DateTimeOffset](xref:System.DateTimeOffset) sem primeiro convertê-lo para UTC, o resultado refletirá o ponto no tempo correto, mas seu deslocamento não refletirá o do fuso horário designado para aquela hora. 

Os valores [DateTimeOffset](xref:System.DateTimeOffset) serão desassociados de qualquer fuso horário ao qual possam pertencer. Para executar a aritmética de data e hora de uma maneira que aplique automaticamente as regras de ajuste de um fuso horário, o fuso horário ao qual qualquer valor de data e hora pertence deve ser imediatamente identificável. Isso significa que uma data e hora e seu fuso horário associado devem estar estritamente acoplados. Há várias maneiras de fazer isso, que incluem o seguinte:

* Supor que todas as horas usadas em um aplicativo pertencem a um fuso horário específico. Embora adequada em alguns casos, essa abordagem oferece flexibilidade limitada e possivelmente portabilidade limitada.

* Definir um tipo que acople estritamente uma data e hora e seu fuso horário associado incluindo ambas como campos do tipo. Essa abordagem é usada no exemplo de código, que define uma estrutura para armazenar a data e hora e o fuso horário em dois campos de membro.

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)

[Executando operações aritméticas com datas e horas](performing-arithmetic-operations.md)



<!--HONumber=Nov16_HO5-->


