---
title: Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo
description: Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dd84ee8-9f0f-4054-9537-155857a460cd
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: aeb1928be32584ee4b6acf7c9a4f4330daedc590
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a><span data-ttu-id="fba02-104">Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="fba02-104">Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>

<span data-ttu-id="fba02-105">Os aplicativos .NET que usam informações de data e hora são muito diferentes e podem usar essas informações de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="fba02-105">.NET applications that use date and time information are very diverse and can use that information in several ways.</span></span> <span data-ttu-id="fba02-106">Os usos de informações de data e hora mais comuns incluem uma ou mais das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="fba02-106">The more common uses of date and time information include one or more of the following:</span></span>

* <span data-ttu-id="fba02-107">Para refletir somente uma data, uma vez que a informação de tempo não é importante.</span><span class="sxs-lookup"><span data-stu-id="fba02-107">To reflect a date only, so that time information is not important.</span></span>

* <span data-ttu-id="fba02-108">Para refletir somente um tempo, uma vez que a informação de data não é importante.</span><span class="sxs-lookup"><span data-stu-id="fba02-108">To reflect a time only, so that date information is not important.</span></span>

* <span data-ttu-id="fba02-109">Para refletir uma data abstrata e um tempo que não está vinculado a uma hora e local específicos (por exemplo, a maioria das lojas em um uma cadeia internacional abre em dias da semana às 9h).</span><span class="sxs-lookup"><span data-stu-id="fba02-109">To reflect an abstract date and time that is not tied to a specific time and place (for example, most stores in an international chain open on weekdays at 9:00 A.M.).</span></span>

* <span data-ttu-id="fba02-110">Para recuperar informações de data e hora de fontes fora do aplicativo .NET, normalmente na qual as informações de data e hora são armazenadas em um tipo de dados simples.</span><span class="sxs-lookup"><span data-stu-id="fba02-110">To retrieve date and time information from sources outside of the .NET application, typically where date and time information is stored in a simple data type.</span></span>

* <span data-ttu-id="fba02-111">Para identificar um único ponto no tempo de maneira única e não ambígua.</span><span class="sxs-lookup"><span data-stu-id="fba02-111">To uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="fba02-112">Alguns aplicativos exigem que uma data e hora não seja ambígua somente no sistema host; outros exigem que ela não seja ambígua entre sistemas (ou seja, uma data serializada em um sistema pode ser significativamente desserializada e usada em outro sistema em qualquer lugar do mundo).</span><span class="sxs-lookup"><span data-stu-id="fba02-112">Some applications require that a date and time be unambiguous only on the host system; others require that it be unambiguous across systems (that is, a date serialized on one system can be meaningfully deserialized and used on another system anywhere in the world).</span></span> 

* <span data-ttu-id="fba02-113">Para preservar vários horários relacionados (como o horário local do solicitante e o horário de recebimento de uma solicitação Web pelo servidor).</span><span class="sxs-lookup"><span data-stu-id="fba02-113">To preserve multiple related times (such as the requestor's local time and the server's time of receipt for a Web request).</span></span>

* <span data-ttu-id="fba02-114">Para realizar a aritmética de data e hora, possivelmente com um resultado que identifica de maneira única e não ambígua um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="fba02-114">To perform date and time arithmetic, possibly with a result that uniquely and unambiguously identifies a single point in time.</span></span> 

<span data-ttu-id="fba02-115">O .NET inclui os tipos [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset), [System.TimeSpan](xref:System.TimeSpan) e [System.TimeZoneInfo](xref:System.TimeZoneInfo), que podem ser usados para criar aplicativos que funcionam com datas e horas.</span><span class="sxs-lookup"><span data-stu-id="fba02-115">.NET includes the [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset), [System.TimeSpan](xref:System.TimeSpan), and [System.TimeZoneInfo](xref:System.TimeZoneInfo) types, all of which can be used to build applications that work with dates and times.</span></span> 

> [!NOTE]
> <span data-ttu-id="fba02-116">Este tópico não discute o tipo `TimeZone` mais antigo, porque sua funcionalidade é quase inteiramente incorporada à classe [System.TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="fba02-116">This topic does not discuss the older `TimeZone` type, because its functionality is almost entirely incorporated in the [System.TimeZoneInfo](xref:System.TimeZoneInfo) class.</span></span> <span data-ttu-id="fba02-117">Sempre que possível, os desenvolvedores devem usar a classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) em vez da classe `TimeZone`.</span><span class="sxs-lookup"><span data-stu-id="fba02-117">Whenever possible, developers should use the [System.TimeZoneInfo](xref:System.TimeZoneInfo) class instead of the `TimeZone` class.</span></span>


## <a name="the-datetime-structure"></a><span data-ttu-id="fba02-118">A estrutura DateTime</span><span class="sxs-lookup"><span data-stu-id="fba02-118">The DateTime structure</span></span>

<span data-ttu-id="fba02-119">Um valor [System.DateTime](xref:System.DateTime) define uma data e hora específica.</span><span class="sxs-lookup"><span data-stu-id="fba02-119">A [System.DateTime](xref:System.DateTime) value defines a particular date and time.</span></span> <span data-ttu-id="fba02-120">Ele inclui uma propriedade [Kind](xref:System.DateTime.Kind) que fornece informações limitadas sobre o fuso horário ao qual essa data e hora pertencem.</span><span class="sxs-lookup"><span data-stu-id="fba02-120">It includes a [Kind](xref:System.DateTime.Kind) property that provides limited information about the time zone to which that date and time belongs.</span></span> <span data-ttu-id="fba02-121">O valor [DateTimeKind](xref:System.DateTimeKind) retornado pela propriedade [Kind](xref:System.DateTime.Kind) indica se o valor [DateTime](xref:System.DateTime) representa a hora local [DateTimeKind.Local](xref:System.DateTimeKind.Local)), UTC (Tempo Universal Coordenado) [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) ou uma hora não específicada [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span><span class="sxs-lookup"><span data-stu-id="fba02-121">The [DateTimeKind](xref:System.DateTimeKind) value returned by the [Kind](xref:System.DateTime.Kind) property indicates whether the [DateTime](xref:System.DateTime) value represents the local time [DateTimeKind.Local](xref:System.DateTimeKind.Local)), Coordinated Universal Time (UTC) [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), or an unspecified time [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span>

<span data-ttu-id="fba02-122">A estrutura [DateTime](xref:System.DateTime) é adequada para aplicativos que fazem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fba02-122">The [DateTime](xref:System.DateTime) structure is suitable for applications that do the following:</span></span> 

* <span data-ttu-id="fba02-123">Trabalhar apenas com datas.</span><span class="sxs-lookup"><span data-stu-id="fba02-123">Work with dates only.</span></span>

* <span data-ttu-id="fba02-124">Trabalhar apenas com horas.</span><span class="sxs-lookup"><span data-stu-id="fba02-124">Work with times only.</span></span>

* <span data-ttu-id="fba02-125">Trabalhar com datas e horas abstratas.</span><span class="sxs-lookup"><span data-stu-id="fba02-125">Work with abstract dates and times.</span></span>

* <span data-ttu-id="fba02-126">Trabalhar com datas e horas para as quais as informações de fuso horário estão ausentes.</span><span class="sxs-lookup"><span data-stu-id="fba02-126">Work with dates and times for which time zone information is missing.</span></span> 

* <span data-ttu-id="fba02-127">Trabalhar apenas com datas e horas UTC.</span><span class="sxs-lookup"><span data-stu-id="fba02-127">Work with UTC dates and times only.</span></span> 

* <span data-ttu-id="fba02-128">Recuperar informações de data e hora de fontes fora do .NET Framework, como bancos de dados do SQL.</span><span class="sxs-lookup"><span data-stu-id="fba02-128">Retrieve date and time information from sources outside the .NET Framework, such as SQL databases.</span></span> <span data-ttu-id="fba02-129">Normalmente, essas fontes armazenam informações de data e hora em um formato simples, compatível com a estrutura [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="fba02-129">Typically, these sources store date and time information in a simple format that is compatible with the [DateTime](xref:System.DateTime) structure.</span></span>

* <span data-ttu-id="fba02-130">Realizar aritmética de data e hora, mas que há preocupação com resultados gerais.</span><span class="sxs-lookup"><span data-stu-id="fba02-130">Perform date and time arithmetic, but are concerned with general results.</span></span> <span data-ttu-id="fba02-131">Por exemplo, em uma operação de adição que soma seis meses a uma data e hora determinada, geralmente não é importante se o resultado é ajustado para horário de verão.</span><span class="sxs-lookup"><span data-stu-id="fba02-131">For example, in an addition operation that adds six months to a particular date and time, it is often not important whether the result is adjusted for daylight saving time.</span></span>

<span data-ttu-id="fba02-132">A menos que um valor [DateTime](xref:System.DateTime) determinado represente o UTC, o valor de data e hora geralmente é ambíguo ou limitado na sua portabilidade.</span><span class="sxs-lookup"><span data-stu-id="fba02-132">Unless a particular [DateTime](xref:System.DateTime) value represents UTC, that date and time value is often ambiguous or limited in its portability.</span></span> <span data-ttu-id="fba02-133">Por exemplo, se um valor [DateTime](xref:System.DateTime) representa a hora local, ele é portátil dentro desse fuso horário local (isto é, se o valor for desserializado em outro sistema no mesmo fuso horário, esse valor ainda identificará de maneira não ambígua um único ponto no tempo).</span><span class="sxs-lookup"><span data-stu-id="fba02-133">For example, if a [DateTime](xref:System.DateTime) value represents the local time, it is portable within that local time zone (that is, if the value is deserialized on another system in the same time zone, that value still unambiguously identifies a single point in time).</span></span> <span data-ttu-id="fba02-134">Fora do fuso horário local, esse valor [DateTime](xref:System.DateTime) pode ter várias interpretações.</span><span class="sxs-lookup"><span data-stu-id="fba02-134">Outside the local time zone, that [DateTime](xref:System.DateTime) value can have multiple interpretations.</span></span> <span data-ttu-id="fba02-135">Se a propriedade [Kind](xref:System.DateTime.Kind) do valor for [DateTimeKind](xref:System.DateTimeKind.Unspecified), ela será ainda menos portátil: ela agora é ambígua dentro do mesmo fuso horário e possivelmente até no mesmo sistema no qual ele foi serializado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="fba02-135">If the value's [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), it is even less portable: it is now ambiguous within the same time zone and possibly even on the same system on which it was first serialized.</span></span> <span data-ttu-id="fba02-136">Somente se um valor [DateTime](xref:System.DateTime) representar o UTC, esse valor identifica sem ambiguidade um único ponto no tempo, independentemente do sistema ou do fuso horário em que o valor é usado.</span><span class="sxs-lookup"><span data-stu-id="fba02-136">Only if a [DateTime](xref:System.DateTime) value represents UTC does that value unambiguously identify a single point in time regardless of the system or time zone in which the value is used.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fba02-137">Ao salvar ou compartilhar os dados de [DateTime](xref:System.DateTime), o UTC deve ser usado e a propriedades [Kind](xref:System.DateTime) do valor [DateTime](xref:System.DateTime.Kind) deve ser definida como [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span><span class="sxs-lookup"><span data-stu-id="fba02-137">When saving or sharing [DateTime](xref:System.DateTime) data, UTC should be used and the [DateTime](xref:System.DateTime) value's [Kind](xref:System.DateTime.Kind) property should be set to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="the-datetimeoffset-structure"></a><span data-ttu-id="fba02-138">A estrutura DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="fba02-138">The DateTimeOffset structure</span></span>

<span data-ttu-id="fba02-139">A estrutura [System.DateTimeOffset](xref:System.DateTimeOffset) representa um valor de data e hora juntamente com um deslocamento que indica quanto o valor difere do UTC.</span><span class="sxs-lookup"><span data-stu-id="fba02-139">The [System.DateTimeOffset](xref:System.DateTimeOffset) structure represents a date and time value, together with an offset that indicates how much that value differs from UTC.</span></span> <span data-ttu-id="fba02-140">Portanto, o valor sempre identifica sem ambiguidade um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="fba02-140">Thus, the value always unambiguously identifies a single point in time.</span></span> 

<span data-ttu-id="fba02-141">O tipo [DateTimeOffset](xref:System.DateTimeOffset) inclui toda a funcionalidade do tipo [DateTime](xref:System.DateTime) juntamente com reconhecimento de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fba02-141">The [DateTimeOffset](xref:System.DateTimeOffset) type includes all of the functionality of the [DateTime](xref:System.DateTime) type along with time zone awareness.</span></span> <span data-ttu-id="fba02-142">Isso o torna adequado para aplicativos que fazem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fba02-142">This makes it is suitable for applications that do the following:</span></span> 

* <span data-ttu-id="fba02-143">Identifique de maneira única e não ambígua um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="fba02-143">Uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="fba02-144">O tipo [DateTimeOffset](xref:System.DateTimeOffset) pode ser usado para definir sem ambiguidade o significado de "agora", para tempos de transação do log, para registrar os tempos de sistema ou eventos do aplicativo e para registrar a criação do arquivo e os tempos de modificação.</span><span class="sxs-lookup"><span data-stu-id="fba02-144">The [DateTimeOffset](xref:System.DateTimeOffset) type can be used to unambiguously define the meaning of "now", to log transaction times, to log the times of system or application events, and to record file creation and modification times.</span></span> 

* <span data-ttu-id="fba02-145">Realizar aritmética geral de data e hora.</span><span class="sxs-lookup"><span data-stu-id="fba02-145">Perform general date and time arithmetic.</span></span>

* <span data-ttu-id="fba02-146">Preserve vários tempos relacionados contanto que esses tempos sejam armazenados como dois valores separados ou como dois membros de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="fba02-146">Preserve multiple related times, as long as those times are stored as two separate values or as two members of a structure.</span></span>

> [!NOTE]
> <span data-ttu-id="fba02-147">Esses usos para os valores [DateTimeOffset](xref:System.DateTimeOffset) são muito mais comuns do que aqueles para os valores [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="fba02-147">These uses for [DateTimeOffset](xref:System.DateTimeOffset) values are much more common than those for [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="fba02-148">Como resultado, [DateTimeOffset](xref:System.DateTimeOffset) deve ser considerado como o tipo de data e hora padrão para o desenvolvimento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fba02-148">As a result, [DateTimeOffset](xref:System.DateTimeOffset) should be considered the default date and time type for application development.</span></span>

<span data-ttu-id="fba02-149">Um valor [DateTimeOffset](xref:System.DateTimeOffset) não está vinculado a um fuso horário específico, mas pode se originar de qualquer um dos vários fusos horários.</span><span class="sxs-lookup"><span data-stu-id="fba02-149">A [DateTimeOffset](xref:System.DateTimeOffset) value is not tied to a particular time zone, but can originate from any of a variety of time zones.</span></span> <span data-ttu-id="fba02-150">Para ilustrar isso, o exemplo a seguir lista os fusos horários aos quais inúmeros valores [DateTimeOffset](xref:System.DateTimeOffset) (incluindo um Fuso Horário do Pacífico local) podem pertencer.</span><span class="sxs-lookup"><span data-stu-id="fba02-150">To illustrate this, the following example lists the time zones to which a number of [DateTimeOffset](xref:System.DateTimeOffset) values (including a local Pacific Standard Time) can belong.</span></span>

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

<span data-ttu-id="fba02-151">A saída mostra que cada valor de data e hora nesse exemplo pode pertencer a pelo menos três fusos horários diferentes.</span><span class="sxs-lookup"><span data-stu-id="fba02-151">The output shows that each date and time value in this example can belong to at least three different time zones.</span></span> <span data-ttu-id="fba02-152">O valor [DateTimeOffset](xref:System.DateTimeOffset) de 10/06/2007 mostra que, se um valor de data e hora representa um horário de verão, seu deslocamento do UTC não corresponde necessariamente ao deslocamento base do UTC do fuso horário originário ou ao deslocamento do UTC encontrado no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="fba02-152">The [DateTimeOffset](xref:System.DateTimeOffset) value of 6/10/2007 shows that if a date and time value represents a daylight saving time, its offset from UTC does not even necessarily correspond to the originating time zone's base UTC offset or to the offset from UTC found in its display name.</span></span> <span data-ttu-id="fba02-153">Isso significa que, como um único valor [DateTimeOffset](xref:System.DateTimeOffset) não está estritamente acoplado ao seu fuso horário, não é possível refletir a transição de um fuso horário para e do horário de verão.</span><span class="sxs-lookup"><span data-stu-id="fba02-153">This means that, because a single [DateTimeOffset](xref:System.DateTimeOffset)  value is not tightly coupled with its time zone, it cannot reflect a time zone's transition to and from daylight saving time.</span></span> <span data-ttu-id="fba02-154">Isso pode ser particularmente problemático quando a aritmética de data e hora é usada para manipular um valor [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="fba02-154">This can be particularly problematic when date and time arithmetic is used to manipulate a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="fba02-155">Para ver uma discussão sobre como realizar a aritmética de data e hora de uma forma que considere as regras de ajuste de um fuso horário, consulte [Executando operações aritméticas com datas e horas](performing-arithmetic-operations.md).</span><span class="sxs-lookup"><span data-stu-id="fba02-155">For a discussion of how to perform date and time arithmetic in a way that takes account of a time zone's adjustment rules, see [Performing arithmetic operations with dates and times](performing-arithmetic-operations.md).</span></span>

## <a name="the-timespan-structure"></a><span data-ttu-id="fba02-156">A estrutura TimeSpan</span><span class="sxs-lookup"><span data-stu-id="fba02-156">The TimeSpan structure</span></span>

<span data-ttu-id="fba02-157">A estrutura [System.TimeSpan](xref:System.TimeSpan) representa um intervalo de tempo.</span><span class="sxs-lookup"><span data-stu-id="fba02-157">The [System.TimeSpan](xref:System.TimeSpan) structure represents a time interval.</span></span> <span data-ttu-id="fba02-158">Seus dois usos típicos são:</span><span class="sxs-lookup"><span data-stu-id="fba02-158">Its two typical uses are:</span></span> 

* <span data-ttu-id="fba02-159">Refletir o intervalo de tempo entre dois valores de data e hora.</span><span class="sxs-lookup"><span data-stu-id="fba02-159">Reflecting the time interval between two date and time values.</span></span> <span data-ttu-id="fba02-160">Por exemplo, subtrair um valor [DateTime](xref:System.DateTime) de outro retorna um valor [TimeSpan](xref:System.TimeSpan).</span><span class="sxs-lookup"><span data-stu-id="fba02-160">For example, subtracting one [DateTime](xref:System.DateTime) value from another returns a [TimeSpan](xref:System.TimeSpan) value.</span></span> 

* <span data-ttu-id="fba02-161">Calcular o tempo decorrido.</span><span class="sxs-lookup"><span data-stu-id="fba02-161">Measuring elapsed time.</span></span> <span data-ttu-id="fba02-162">Por exemplo, a propriedade [Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) retorna um valor [TimeSpan](xref:System.TimeSpan) que reflete o intervalo de tempo decorrido desde a chamada para um dos métodos [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch) que começa a medir o tempo decorrido.</span><span class="sxs-lookup"><span data-stu-id="fba02-162">For example, the [Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) property returns a [TimeSpan](xref:System.TimeSpan) value that reflects the time interval that has elapsed since the call to one of the [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch) methods that begins to measure elapsed time.</span></span>

<span data-ttu-id="fba02-163">Um valor [TimeSpan](xref:System.TimeSpan) também pode ser usado como uma substituição para um valor [DateTime](xref:System.DateTime) quando esse valor reflete um tempo sem referência a uma determinada hora do dia.</span><span class="sxs-lookup"><span data-stu-id="fba02-163">A [TimeSpan](xref:System.TimeSpan) value can also be used as a replacement for a [DateTime](xref:System.DateTime) value when that value reflects a time without reference to a particular time of day.</span></span> <span data-ttu-id="fba02-164">Esse uso é semelhante às propriedades [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) e [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay), que retornam um valor [TimeSpan](xref:System.TimeSpan) que representa o tempo sem referência a uma data.</span><span class="sxs-lookup"><span data-stu-id="fba02-164">This usage is similar to the [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) and [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay) properties, which return a [TimeSpan](xref:System.TimeSpan) value that represents the time without reference to a date.</span></span> <span data-ttu-id="fba02-165">Por exemplo, a estrutura [TimeSpan](xref:System.TimeSpan) pode ser usada para refletir a hora de abertura ou de fechamento diário de um repositório ou pode ser usado para representar a hora na qual qualquer evento regular ocorre.</span><span class="sxs-lookup"><span data-stu-id="fba02-165">For example, the [TimeSpan](xref:System.TimeSpan) structure can be used to reflect a store's daily opening or closing time, or it can be used to represent the time at which any regular event occurs.</span></span>

<span data-ttu-id="fba02-166">O exemplo a seguir define uma estrutura `StoreInfo` que inclui objetos [TimeSpan](xref:System.TimeSpan) para tempos de abertura e fechamento do repositório, bem como um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa o fuso horário do repositório.</span><span class="sxs-lookup"><span data-stu-id="fba02-166">The following example defines a `StoreInfo` structure that includes [TimeSpan](xref:System.TimeSpan) objects for store opening and closing times, as well as a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the store's time zone.</span></span> <span data-ttu-id="fba02-167">A estrutura também inclui dois métodos, `IsOpenNow` e `IsOpenAt`, que indica se o repositório está aberto em um momento especificado pelo usuário, que se considera estar no fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="fba02-167">The structure also includes two methods, `IsOpenNow` and `IsOpenAt`, that indicates whether the store is open at a time specified by the user, who is assumed to be in the local time zone.</span></span>  

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

<span data-ttu-id="fba02-168">A estrutura `StoreInfo` pode ser usada pelo código do cliente como o exposto a seguir.</span><span class="sxs-lookup"><span data-stu-id="fba02-168">The `StoreInfo` structure can then be used by client code like the following.</span></span> 

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

## <a name="the-timezoneinfo-class"></a><span data-ttu-id="fba02-169">A classe TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="fba02-169">The TimeZoneInfo class</span></span>

<span data-ttu-id="fba02-170">A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) representa qualquer um dos fusos horários da Terra e permite a conversão de qualquer data e hora em um fuso horário para seu equivalente em outro fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fba02-170">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class represents any of the earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone.</span></span> <span data-ttu-id="fba02-171">A classe [TimeZoneInfo](xref:System.TimeZoneInfo) possibilita trabalhar com datas e horas de modo que qualquer valor de data e hora identifica sem ambiguidade um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="fba02-171">The [TimeZoneInfo](xref:System.TimeZoneInfo) class makes it possible to work with dates and times so that any date and time value unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="fba02-172">Em alguns casos, usar ao máximo a classe [TimeZoneInfo](xref:System.TimeZoneInfo) pode exigir trabalho de desenvolvimento adicional.</span><span class="sxs-lookup"><span data-stu-id="fba02-172">In some cases, taking full advantage of the [TimeZoneInfo](xref:System.TimeZoneInfo) class may require further development work.</span></span> <span data-ttu-id="fba02-173">Os valores de data e hora não são estritamente acoplados aos fusos horários aos quais eles pertencem.</span><span class="sxs-lookup"><span data-stu-id="fba02-173">Date and time values are not tightly coupled with the time zones to which they belong.</span></span> <span data-ttu-id="fba02-174">Como resultado, a menos que seu aplicativo ofereça algum mecanismo para vincular uma data e hora com seu fuso horário associado, é fácil para um determinado valor de data e hora se desassociar do seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fba02-174">As a result, unless your application provides some mechanism for linking a date and time with its associated time zone, it is easy for a particular date and time value to become disassociated from its time zone.</span></span> <span data-ttu-id="fba02-175">Um método de vinculação dessas informações é definir uma classe ou estrutura que contenha o valor de data e hora e seu objeto de fuso horário associado.</span><span class="sxs-lookup"><span data-stu-id="fba02-175">One method of linking this information is to define a class or structure that contains both the date and time value and its associated time zone object.</span></span>

<span data-ttu-id="fba02-176">É possível obter suporte de fuso horário no .NET apenas se o fuso horário ao qual um valor de data e hora pertence for conhecido quando a instância desse objeto de data e hora for criada.</span><span class="sxs-lookup"><span data-stu-id="fba02-176">Taking advantage of time zone support in .NET is possible only if the time zone to which a date and time value belongs is known when that date and time object is instantiated.</span></span> <span data-ttu-id="fba02-177">Geralmente isso não acontece, especialmente em aplicativos Web ou de rede.</span><span class="sxs-lookup"><span data-stu-id="fba02-177">This is often not the case, particularly in Web or network applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="fba02-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fba02-178">See Also</span></span>

[<span data-ttu-id="fba02-179">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="fba02-179">Dates, times, and time zones</span></span>](index.md)
