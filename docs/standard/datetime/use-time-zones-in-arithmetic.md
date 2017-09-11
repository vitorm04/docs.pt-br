---
title: "Como usar fusos horários em aritmética de data e hora"
description: "Como usar fusos horários em aritmética de data e hora"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 26870cdc-1709-4978-831b-ff2a2f24856f
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: a86471972d42adcbc412cc8eeb300410ca8a9c42
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="b4fe9-104">Como usar fusos horários em aritmética de data e hora</span><span class="sxs-lookup"><span data-stu-id="b4fe9-104">How to: use time zones in date and time arithmetic</span></span>

<span data-ttu-id="b4fe9-105">Normalmente, quando você executa a aritmética de data e hora usando valores de [System.DateTimeOffset](xref:System.DateTimeOffset), o resultado não reflete nenhuma regra de ajuste de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-105">Ordinarily, when you perform date and time arithmetic using [System.DateTimeOffset](xref:System.DateTimeOffset) values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="b4fe9-106">Isso é verdadeiro mesmo quando o fuso horário do valor de data e hora é claramente identificável.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-106">This is true even when the time zone of the date and time value is clearly identifiable.</span></span> <span data-ttu-id="b4fe9-107">Este artigo mostra como executar operações aritméticas em valores de data e hora que pertencem a um fuso horário específico.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-107">This article shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="b4fe9-108">Os resultados das operações aritméticas refletirão as regras de ajuste do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-108">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

## <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="b4fe9-109">Para aplicar as regras de ajuste à aritmética de data e hora</span><span class="sxs-lookup"><span data-stu-id="b4fe9-109">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="b4fe9-110">Implemente um método de acoplamento próximo de um valor de data e hora com o fuso horário ao qual ele pertence.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-110">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="b4fe9-111">Por exemplo, declare uma estrutura que inclui o valor de data e hora e seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-111">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="b4fe9-112">O exemplo a seguir usa essa abordagem para vincular um valor de [DateTimeOffset](xref:System.DateTimeOffset) ao seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-112">The following example uses this approach to link a [DateTimeOffset](xref:System.DateTimeOffset) value with its time zone.</span></span>

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
    
2. <span data-ttu-id="b4fe9-113">Converta uma hora para UTC (Tempo Universal Coordenado) chamando o método [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)).</span><span class="sxs-lookup"><span data-stu-id="b4fe9-113">Convert a time to Coordinated Universal Time (UTC) by calling the [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span>

3. <span data-ttu-id="b4fe9-114">Execute a operação aritmética na hora UTC.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-114">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="b4fe9-115">Converta a hora de UTC para o fuso horário associado da hora original chamando o método [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)).</span><span class="sxs-lookup"><span data-stu-id="b4fe9-115">Convert the time from UTC to the original time's associated time zone by calling the [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span> 

## <a name="example"></a><span data-ttu-id="b4fe9-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4fe9-116">Example</span></span>

<span data-ttu-id="b4fe9-117">O exemplo a seguir adiciona duas horas e trinta minutos a 9 de março de 2008, à 1h30 do</span><span class="sxs-lookup"><span data-stu-id="b4fe9-117">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="b4fe9-118">Horário Padrão Central.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-118">Central Standard Time.</span></span> <span data-ttu-id="b4fe9-119">A transição do fuso horário para o horário de verão ocorre 30 minutos depois, às 2h.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-119">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="b4fe9-120">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-120">on March 9, 2008.</span></span> <span data-ttu-id="b4fe9-121">Como o exemplo segue as quatro etapas listadas na seção anterior, ele relata corretamente a hora resultante como 5h.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-121">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="b4fe9-122">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-122">on March 9, 2008.</span></span> 

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

<span data-ttu-id="b4fe9-123">Observe que se esta adição for simplesmente realizada no valor [DateTimeOffset](xref:System.DateTimeOffset) sem primeiro convertê-lo para UTC, o resultado refletirá o ponto no tempo correto, mas seu deslocamento não refletirá o do fuso horário designado para aquela hora.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-123">Note that if this addition is simply performed on the [DateTimeOffset](xref:System.DateTimeOffset) value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span> 

<span data-ttu-id="b4fe9-124">Os valores [DateTimeOffset](xref:System.DateTimeOffset) serão desassociados de qualquer fuso horário ao qual possam pertencer.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-124">[DateTimeOffset](xref:System.DateTimeOffset) values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="b4fe9-125">Para executar a aritmética de data e hora de uma maneira que aplique automaticamente as regras de ajuste de um fuso horário, o fuso horário ao qual qualquer valor de data e hora pertence deve ser imediatamente identificável.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-125">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="b4fe9-126">Isso significa que uma data e hora e seu fuso horário associado devem estar estritamente acoplados.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-126">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="b4fe9-127">Há várias maneiras de fazer isso, que incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b4fe9-127">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="b4fe9-128">Supor que todas as horas usadas em um aplicativo pertencem a um fuso horário específico.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-128">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="b4fe9-129">Embora adequada em alguns casos, essa abordagem oferece flexibilidade limitada e possivelmente portabilidade limitada.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-129">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="b4fe9-130">Definir um tipo que acople estritamente uma data e hora e seu fuso horário associado incluindo ambas como campos do tipo.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-130">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="b4fe9-131">Essa abordagem é usada no exemplo de código, que define uma estrutura para armazenar a data e hora e o fuso horário em dois campos de membro.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-131">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4fe9-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4fe9-132">See Also</span></span>

[<span data-ttu-id="b4fe9-133">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="b4fe9-133">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="b4fe9-134">Executando operações aritméticas com datas e horas</span><span class="sxs-lookup"><span data-stu-id="b4fe9-134">Performing arithmetic operations with dates and times</span></span>](performing-arithmetic-operations.md)

