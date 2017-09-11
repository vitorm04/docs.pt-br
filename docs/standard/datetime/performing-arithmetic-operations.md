---
title: "Executando operações aritméticas com datas e horários"
description: "Executando operações aritméticas com datas e horários"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 589ac5ec-8365-4a0d-bc38-72183718110c
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: b872cc4c2b799ddafc9df263795d860754d1ec17
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="performing-arithmetic-operations-with-dates-and-times"></a><span data-ttu-id="9215c-104">Executando operações aritméticas com datas e horários</span><span class="sxs-lookup"><span data-stu-id="9215c-104">Performing arithmetic operations with dates and times</span></span>

<span data-ttu-id="9215c-105">Apesar de as estruturas [System.DateTime](xref:System.DateTime) e [System.DateTimeOffset](xref:System.DateTimeOffset) oferecerem membros que executam operações aritméticas em seus valores, os resultados das operações aritméticas são muito diferentes.</span><span class="sxs-lookup"><span data-stu-id="9215c-105">Although both the [System.DateTime](xref:System.DateTime) and the [System.DateTimeOffset](xref:System.DateTimeOffset) structures provide members that perform arithmetic operations on their values, the results of arithmetic operations are very different.</span></span> <span data-ttu-id="9215c-106">Este artigo examina tais diferenças, as relaciona a graus de reconhecimento de fuso horário em dados de data e hora e discute como executar totalmente operações de reconhecimento de fuso horário usando dados de data e hora.</span><span class="sxs-lookup"><span data-stu-id="9215c-106">This article examines those differences, relates them to degrees of time zone awareness in date and time data, and discusses how to perform fully time zone aware operations using date and time data.</span></span>

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a><span data-ttu-id="9215c-107">Comparações e operações aritméticas com valores DateTime</span><span class="sxs-lookup"><span data-stu-id="9215c-107">Comparisons and Arithmetic Operations with DateTime Values</span></span>

<span data-ttu-id="9215c-108">Os valores [System.DateTime](xref:System.DateTime) têm um grau limitado de reconhecimento de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9215c-108">[System.DateTime](xref:System.DateTime) values possess a limited degree of time zone awareness.</span></span> <span data-ttu-id="9215c-109">A propriedade [DateTime.Kind](xref:System.DateTime.Kind) permite que um valor [System.DateTimeKind](xref:System.DateTimeKind) seja atribuído à data e à hora para indicar se representa um horário local, o UTC (Tempo Universal Coordenado) ou o horário em um fuso horário não especificado.</span><span class="sxs-lookup"><span data-stu-id="9215c-109">The [DateTime.Kind](xref:System.DateTime.Kind) property allows a [System.DateTimeKind](xref:System.DateTimeKind) value to be assigned to the date and time to indicate whether it represents local time, Coordinated Universal Time (UTC), or the time in an unspecified time zone.</span></span> <span data-ttu-id="9215c-110">No entanto, essas informações de fuso horário limitado são ignoradas ao comparar ou executar a aritmética de data e hora em valores [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="9215c-110">However, this limited time zone information is ignored when comparing or performing date and time arithmetic on [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="9215c-111">O exemplo a seguir, que compara o horário local atual com o horário UTC atual, ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="9215c-111">The following example, which compares the current local time with the current UTC time, illustrates this.</span></span>

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

<span data-ttu-id="9215c-112">O método [DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) informa que o horário local é anterior (ou inferior) ao horário UTC; a operação de subtração indica que a diferença entre UTC e o horário local para um sistema no fuso horário padrão do Pacífico dos EUA é de sete horas.</span><span class="sxs-lookup"><span data-stu-id="9215c-112">The [DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) method reports that the local time is earlier than (or less than) the UTC time, and the subtraction operation indicates that the difference between UTC and the local time for a system in the U.S. Pacific Standard Time zone is seven hours.</span></span> <span data-ttu-id="9215c-113">Porém, como esses dois valores oferecem representações diferentes de um único momento, fica claro que, nesse caso, o intervalo de tempo é completamente atribuível ao deslocamento do fuso horário local em relação ao UTC.</span><span class="sxs-lookup"><span data-stu-id="9215c-113">But because these two values provide different representations of a single point in time, it is clear in this case that this time interval is completely attributable to the local time zone's offset from UTC.</span></span> 

<span data-ttu-id="9215c-114">Normalmente, a propriedade [DateTimeKind](xref:System.DateTimeKind) não afeta os resultados retornado pelos métodos aritméticos e de comparação [DateTime](xref:System.DateTime) (como indica a comparação de dois momentos idênticos), embora possa afetar a interpretação dos resultados.</span><span class="sxs-lookup"><span data-stu-id="9215c-114">More generally, the [DateTimeKind](xref:System.DateTimeKind) property does not affect the results returned by [DateTime](xref:System.DateTime) comparison and arithmetic methods (as the comparison of two identical points in time indicates), although it can affect the interpretation of those results.</span></span> <span data-ttu-id="9215c-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9215c-115">For example:</span></span>

* <span data-ttu-id="9215c-116">O resultado de qualquer operação aritmética executada em dois valores de data e hora cujas propriedades [DateTimeKind](xref:System.DateTimeKind) equivalem a [DateTimeKind](xref:System.DateTimeKind.Utc) refletem o intervalo de tempo real entre os dois valores.</span><span class="sxs-lookup"><span data-stu-id="9215c-116">The result of any arithmetic operation performed on two date and time values whose [DateTimeKind](xref:System.DateTimeKind) properties both equal [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) reflects the actual time interval between the two values.</span></span> <span data-ttu-id="9215c-117">Da mesma forma, a comparação dos dois valores de data e hora reflete com precisão a relação entre horários.</span><span class="sxs-lookup"><span data-stu-id="9215c-117">Similarly, the comparison of two such date and time values accurately reflects the relationship between times.</span></span>

* <span data-ttu-id="9215c-118">O resultado de qualquer operação aritmética ou de comparação executada em dois valores de data e hora cujas propriedades [DateTimeKind](xref:System.DateTimeKind) equivalem a [DateTimeKind.Local](xref:System.DateTimeKind.Local) ou em dois valores de data e hora com valores de propriedade [DateTimeKind](xref:System.DateTimeKind) diferentes reflete a diferença de hora do relógio entre os dois valores.</span><span class="sxs-lookup"><span data-stu-id="9215c-118">The result of any arithmetic or comparison operation performed on two date and time values whose [DateTimeKind](xref:System.DateTimeKind) properties both equal [DateTimeKind.Local](xref:System.DateTimeKind.Local) or on two date and time values with different [DateTimeKind](xref:System.DateTimeKind) property values reflects the difference in clock time between the two values.</span></span> 

* <span data-ttu-id="9215c-119">As operações aritméticas ou de comparação em valores de data e hora local não consideram se um valor específico é ambíguo ou inválido nem levam em conta o efeito de regras de ajuste que resultam da transição do fuso horário local de ou para o horário de verão.</span><span class="sxs-lookup"><span data-stu-id="9215c-119">Arithmetic or comparison operations on local date and time values do not consider whether a particular value is ambiguous or invalid, nor do they take account of the effect of any adjustment rules that result from the local time zone's transition to or from daylight saving time.</span></span>

* <span data-ttu-id="9215c-120">Qualquer operação que compara ou calcula a diferença entre o UTC e o horário local inclui um intervalo de tempo igual ao deslocamento do fuso horário local em relação ao UTC no resultado.</span><span class="sxs-lookup"><span data-stu-id="9215c-120">Any operation that compares or calculates the difference between UTC and a local time includes a time interval equal to the local time zone's offset from UTC in the result.</span></span> 

* <span data-ttu-id="9215c-121">Qualquer operação que compara ou calcula a diferença entre um horário não especificado e o UTC ou o horário local reflete a hora do relógio simples.</span><span class="sxs-lookup"><span data-stu-id="9215c-121">Any operation that compares or calculates the difference between an unspecified time and either UTC or the local time reflects simple clock time.</span></span> <span data-ttu-id="9215c-122">As diferenças de fuso horário não são consideradas; o resultado não reflete a aplicação das regras de ajuste de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9215c-122">Time zone differences are not considered, and the result does not reflect the application of time zone adjustment rules.</span></span> 

* <span data-ttu-id="9215c-123">Qualquer operação que compara ou calcula a diferença entre dois horários não especificados poderá incluir um intervalo desconhecido que reflete a diferença entre o horário em dois fusos horários diferentes.</span><span class="sxs-lookup"><span data-stu-id="9215c-123">Any operation that compares or calculates the difference between two unspecified times may include an unknown interval that reflects the difference between the time in two different time zones.</span></span>

<span data-ttu-id="9215c-124">Há muitos cenários nos quais as diferenças de fuso horário não afetam os cálculos de data e hora ou em que o contexto dos dados de data e hora define o significado das operações aritméticas ou de comparação.</span><span class="sxs-lookup"><span data-stu-id="9215c-124">There are many scenarios in which time zone differences do not affect date and time calculations or in which the context of the date and time data defines the meaning of comparison or arithmetic operations.</span></span> <span data-ttu-id="9215c-125">Para ver uma discussão entre alguns deles, consulte [Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](choosing-between-datetime.md).</span><span class="sxs-lookup"><span data-stu-id="9215c-125">For a discussion of some of these, see [Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md).</span></span>

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a><span data-ttu-id="9215c-126">Comparações e operações aritméticas com valores DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="9215c-126">Comparisons and Arithmetic Operations with DateTimeOffset Values</span></span>

<span data-ttu-id="9215c-127">Um valor [System.DateTimeOffset](xref:System.DateTimeOffset) não inclui apenas data e hora, mas também um deslocamento que define sem ambiguidade a data e hora relativas ao UTC.</span><span class="sxs-lookup"><span data-stu-id="9215c-127">A [System.DateTimeOffset](xref:System.DateTimeOffset) value includes not only a date and time, but also an offset that unambiguously defines that date and time relative to UTC.</span></span> <span data-ttu-id="9215c-128">Isso possibilita definir a igualdade de forma diferente do que para valores [System.DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="9215c-128">This makes it possible to define equality somewhat differently than for [System.DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="9215c-129">Apesar de os valores [DateTime](xref:System.DateTime) serem iguais se tiverem o mesmo valor de data e hora, os valores [DateTimeOffset](xref:System.DateTimeOffset) valores são iguais caso ambos se refiram ao mesmo momento.</span><span class="sxs-lookup"><span data-stu-id="9215c-129">Whereas [DateTime](xref:System.DateTime) values are equal if they have the same date and time value, [DateTimeOffset](xref:System.DateTimeOffset) values are equal if they both refer to the same point in time.</span></span> <span data-ttu-id="9215c-130">Isso torna um valor [DateTimeOffset](xref:System.DateTimeOffset) mais preciso e com menos necessidade de interpretação quando usado em comparações e na maioria das operações aritméticas que determinam o intervalo entre duas datas e horas.</span><span class="sxs-lookup"><span data-stu-id="9215c-130">This makes a [DateTimeOffset](xref:System.DateTimeOffset) value more accurate and less in need of interpretation when used in comparisons and in most arithmetic operations that determine the interval between two dates and times.</span></span> <span data-ttu-id="9215c-131">O exemplo a seguir, que é o equivalente [DateTimeOffset](xref:System.DateTimeOffset) ao exemplo anterior que comparou valores DateTime locais e do UTC, mostra essa diferença no comportamento.</span><span class="sxs-lookup"><span data-stu-id="9215c-131">The following example, which is the [DateTimeOffset](xref:System.DateTimeOffset) equivalent to the previous example that compared local and UTC DateTime values, illustrates this difference in behavior.</span></span>

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

<span data-ttu-id="9215c-132">Neste exemplo, o método [DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) indica que o horário local atual e o horário UTC atual são iguais; a subtração dos valores [DateTimeOffset](xref:System.DateTimeOffset) indica que a diferença entre os dois horários é [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span><span class="sxs-lookup"><span data-stu-id="9215c-132">In this example, the [DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) method indicates that the current local time and the current UTC time are equal, and subtraction of [DateTimeOffset](xref:System.DateTimeOffset) values indicates that the difference between the two times is [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> 

<span data-ttu-id="9215c-133">A limitação principal do uso de valores [DateTimeOffset](xref:System.DateTimeOffset) na aritmética de data e hora é que, apesar de os valores [DateTimeOffset](xref:System.DateTimeOffset) terem algum reconhecimento de fuso horário, não fazem reconhecimento total de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9215c-133">The chief limitation of using [DateTimeOffset](xref:System.DateTimeOffset) values in date and time arithmetic is that although [DateTimeOffset](xref:System.DateTimeOffset) values have some time zone awareness, they are not fully time zone aware.</span></span> <span data-ttu-id="9215c-134">Apesar de o deslocamento do valor [DateTimeOffset](xref:System.DateTimeOffset) refletir um deslocamento do fuso horário em relação ao UTC quando uma variável [DateTimeOffset](xref:System.DateTimeOffset) é atribuída pela primeira vez a um valor, ele se torna desassociado do fuso horário posteriormente.</span><span class="sxs-lookup"><span data-stu-id="9215c-134">Although the [DateTimeOffset](xref:System.DateTimeOffset) value's offset reflects a time zone's offset from UTC when a [DateTimeOffset](xref:System.DateTimeOffset) variable is first assigned a value, it becomes disassociated from the time zone thereafter.</span></span> <span data-ttu-id="9215c-135">Como não estão mais diretamente associadas a um horário identificável, a adição e a subtração dos intervalos de data e hora não consideram as regras de ajuste de um fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9215c-135">Because it is no longer directly associated with an identifiable time, the addition and subtraction of date and time intervals does not consider a time zone's adjustment rules.</span></span> 

<span data-ttu-id="9215c-136">Para ilustrar, a transição para o horário de verão no fuso horário padrão da região central EUA ocorre às 2h.</span><span class="sxs-lookup"><span data-stu-id="9215c-136">To illustrate, the transition to daylight saving time in the U.S. Central Standard Time zone occurs at 2:00 A.M.</span></span> <span data-ttu-id="9215c-137">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="9215c-137">on March 9, 2008.</span></span> <span data-ttu-id="9215c-138">Isso significa que adicionar um intervalo de duas horas e meia ao fuso horário padrão da região central de 1h30min</span><span class="sxs-lookup"><span data-stu-id="9215c-138">This means that adding a two and a half hour interval to a Central Standard time of 1:30 A.M.</span></span> <span data-ttu-id="9215c-139">em 9 de março de 2008 deve produzir uma data e hora de 5h</span><span class="sxs-lookup"><span data-stu-id="9215c-139">on March 9, 2008, should produce a date and time of 5:00 A.M.</span></span> <span data-ttu-id="9215c-140">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="9215c-140">on March 9, 2008.</span></span> <span data-ttu-id="9215c-141">No entanto, como mostra o exemplo a seguir, o resultado da adição é 4h</span><span class="sxs-lookup"><span data-stu-id="9215c-141">However, as the following example shows, the result of the addition is 4:00 A.M.</span></span> <span data-ttu-id="9215c-142">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="9215c-142">on March 9, 2008.</span></span> <span data-ttu-id="9215c-143">Observe que o resultado dessa operação representa o momento correto, embora não seja o horário no fuso horário em que estamos interessados (ou seja, não tem o deslocamento de fuso horário esperado).</span><span class="sxs-lookup"><span data-stu-id="9215c-143">Note that this result of this operation does represent the correct point in time, although it is not the time in the time zone in which we are interested (that is, it does not have the expected time zone offset).</span></span>

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

## <a name="arithmetic-operations-with-times-in-time-zones"></a><span data-ttu-id="9215c-144">Operações aritméticas com horários nos fusos horários</span><span class="sxs-lookup"><span data-stu-id="9215c-144">Arithmetic Operations with Times in Time Zones</span></span>

<span data-ttu-id="9215c-145">A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) não fornece os métodos que aplicam regras de ajuste automaticamente quando você executa a aritmética de data e hora.</span><span class="sxs-lookup"><span data-stu-id="9215c-145">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class does not provide any methods that automatically apply adjustment rules when you perform date and time arithmetic.</span></span> <span data-ttu-id="9215c-146">No entanto, é possível fazer isso convertendo o horário em um fuso horário para UTC, executando a operação aritmética e, em seguida, convertendo do UTC novamente para o horário no fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9215c-146">However, you can do this by converting the time in a time zone to UTC, performing the arithmetic operation, and then converting from UTC back to the time in the time zone.</span></span> <span data-ttu-id="9215c-147">Para ver detalhes, consulte [Como usar fusos horários em aritmética de data e hora](use-time-zones-in-arithmetic.md).</span><span class="sxs-lookup"><span data-stu-id="9215c-147">For details, see [How to: Use Time Zones in Date and Time Arithmetic](use-time-zones-in-arithmetic.md).</span></span>

<span data-ttu-id="9215c-148">Por exemplo, o código a seguir é semelhante ao código anterior, que adicionou duas horas e meia às 2h</span><span class="sxs-lookup"><span data-stu-id="9215c-148">For example, the following code is similar to the previous code that added two-and-a-half hours to 2:00 A.M.</span></span> <span data-ttu-id="9215c-149">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="9215c-149">on March 9, 2008.</span></span> <span data-ttu-id="9215c-150">No entanto, como converte um horário padrão da região central em UTC antes de realizar a aritmética de data e hora e, depois, converte o resultado do UTC novamente no horário padrão da região central, o horário resultante reflete a transição do fuso horário padrão da região central para o horário de verão.</span><span class="sxs-lookup"><span data-stu-id="9215c-150">However, because it converts a Central Standard time to UTC before it performs date and time arithmetic, and then converts the result from UTC back to Central Standard time, the resulting time reflects the Central Standard Time Zone's transition to daylight saving time.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9215c-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9215c-151">See Also</span></span>

[<span data-ttu-id="9215c-152">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="9215c-152">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="9215c-153">Como usar fusos horários em aritmética de data e hora</span><span class="sxs-lookup"><span data-stu-id="9215c-153">How to: use time zones in date and time arithmetic</span></span>](use-time-zones-in-arithmetic.md)



