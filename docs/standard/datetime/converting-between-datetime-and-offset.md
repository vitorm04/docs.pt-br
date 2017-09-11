---
title: Convertendo entre DateTime e DateTimeOffset
description: Convertendo entre DateTime e DateTimeOffset
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fab3af5b-5d0f-4384-a40a-1b5d99b30dd1
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 2ba70e9ea39148d040bdb46d5e00ea50dcbb8980
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="converting-between-datetime-and-datetimeoffset"></a><span data-ttu-id="86b35-104">Convertendo entre DateTime e DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="86b35-104">Converting between DateTime and DateTimeOffset</span></span>

<span data-ttu-id="86b35-105">Embora a estrutura [System.DateTimeOffset](xref:System.DateTimeOffset) ofereça um maior grau de reconhecimento de fuso horário que a estrutura [System.DateTime](xref:System.DateTime), parâmetros [DateTime](xref:System.DateTime) são usados com mais frequência em chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="86b35-105">Although the [System.DateTimeOffset](xref:System.DateTimeOffset) structure provides a greater degree of time zone awareness than the [System.DateTime](xref:System.DateTime) structure, [DateTime](xref:System.DateTime) parameters are used more commonly in method calls.</span></span> <span data-ttu-id="86b35-106">Por isso, a capacidade de converter valores [DateTimeOffset](xref:System.DateTimeOffset) em valores [DateTime](xref:System.DateTime) e vice-versa é muito importante.</span><span class="sxs-lookup"><span data-stu-id="86b35-106">Because of this, the ability to convert [DateTimeOffset](xref:System.DateTimeOffset) values to [DateTime](xref:System.DateTime) values and vice versa is particularly important.</span></span> <span data-ttu-id="86b35-107">Este artigo mostra como executar essas conversões de maneira a preservar as informações de fuso horário tanto quanto possível.</span><span class="sxs-lookup"><span data-stu-id="86b35-107">This article shows how to perform these conversions in a way that preserves as much time zone information as possible.</span></span>

> [!NOTE]
> <span data-ttu-id="86b35-108">Os tipos [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset) têm algumas limitações para representar horas em fusos horários.</span><span class="sxs-lookup"><span data-stu-id="86b35-108">Both the [DateTime](xref:System.DateTime) and the [DateTimeOffset](xref:System.DateTimeOffset) types have some limitations when representing times in time zones.</span></span> <span data-ttu-id="86b35-109">Com sua propriedade [Kind](xref:System.DateTime.Kind), [DateTime](xref:System.DateTime) pode refletir somente o UTC (Tempo Universal Coordenado) e o fuso horário local do sistema.</span><span class="sxs-lookup"><span data-stu-id="86b35-109">With its [Kind](xref:System.DateTime.Kind) property, [DateTime](xref:System.DateTime) is able to reflect only Coordinated Universal Time (UTC) and the system's local time zone.</span></span> <span data-ttu-id="86b35-110">[DateTimeOffset](xref:System.DateTimeOffset) reflete um deslocamento da hora com relação ao UTC, mas não reflete o fuso horário real ao qual esse deslocamento pertence.</span><span class="sxs-lookup"><span data-stu-id="86b35-110">[DateTimeOffset](xref:System.DateTimeOffset) reflects a time's offset from UTC, but it does not reflect the actual time zone to which that offset belongs.</span></span> <span data-ttu-id="86b35-111">Para obter detalhes sobre os valores de hora e o suporte para fusos horários, consulte [Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](choosing-between-datetime.md).</span><span class="sxs-lookup"><span data-stu-id="86b35-111">For details about time values and support for time zones, see [Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md).</span></span>

## <a name="conversions-from-datetime-to-datetimeoffset"></a><span data-ttu-id="86b35-112">Conversões de DateTime para DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="86b35-112">Conversions from DateTime to DateTimeOffset</span></span>

<span data-ttu-id="86b35-113">A estrutura [DateTimeOffset](xref:System.DateTimeOffset) fornece duas maneiras equivalentes de executar uma conversão de [DateTime](xref:System.DateTime) para [DateTimeOffset](xref:System.DateTimeOffset) que são adequadas para a maioria das conversões:</span><span class="sxs-lookup"><span data-stu-id="86b35-113">The [DateTimeOffset](xref:System.DateTimeOffset) structure provides two equivalent ways to perform [DateTime](xref:System.DateTime) to [DateTimeOffset](xref:System.DateTimeOffset) conversion that are suitable for most conversions:</span></span>

* <span data-ttu-id="86b35-114">O construtor [DateTimeOffset(DateTime)](xref:System.DateTimeOffset), que cria um novo objeto [DateTimeOffset](xref:System.DateTimeOffset) com base em um valor de [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="86b35-114">The [DateTimeOffset(DateTime)](xref:System.DateTimeOffset) constructor, which creates a new [DateTimeOffset](xref:System.DateTimeOffset) object based on a [DateTime](xref:System.DateTime) value.</span></span>

* <span data-ttu-id="86b35-115">O operador de conversão implícita, que permite que você atribua um valor [DateTime](xref:System.DateTime) a um objeto [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="86b35-115">The implicit conversion operator, which allows you to assign a [DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) object.</span></span>

<span data-ttu-id="86b35-116">Para UTC e valores locais de [DateTime](xref:System.DateTime), a propriedade [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) do valor [DateTimeOffset](xref:System.DateTimeOffset) resultante reflete com precisão o UTC ou o deslocamento do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="86b35-116">For UTC and local [DateTime](xref:System.DateTime) values, the [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) property of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value accurately reflects the UTC or local time zone offset.</span></span> <span data-ttu-id="86b35-117">Por exemplo, o código a seguir converte uma hora em UTC no valor equivalente de [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="86b35-117">For example, the following code converts a UTC time to its equivalent [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> 

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

<span data-ttu-id="86b35-118">Nesse caso, o deslocamento da variável `utcTime2` é 00:00.</span><span class="sxs-lookup"><span data-stu-id="86b35-118">In this case, the offset of the `utcTime2` variable is 00:00.</span></span> <span data-ttu-id="86b35-119">De forma semelhante, o código a seguir converte uma hora local no valor equivalente de [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="86b35-119">Similarly, the following code converts a local time to its equivalent [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

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

<span data-ttu-id="86b35-120">No entanto, para valores de [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) é [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), esses dois métodos de conversão produzem um valor de [DateTimeOffset](xref:System.DateTimeOffset) cujo deslocamento é o do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="86b35-120">However, for [DateTime](xref:System.DateTime) values whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), these two conversion methods produce a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset is that of the local time zone.</span></span> <span data-ttu-id="86b35-121">Isso é mostrado no exemplo a seguir, que é executado no Fuso horário padrão do Pacífico.</span><span class="sxs-lookup"><span data-stu-id="86b35-121">This is shown in the following example, which is run in the U.S. Pacific Standard Time zone.</span></span>

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

<span data-ttu-id="86b35-122">Se o valor de [DateTime](xref:System.DateTime) refletir a data e a hora em algo diferente do fuso horário local ou UTC, você poderá convertê-lo para um valor de [DateTimeOffset](xref:System.DateTimeOffset) e preservar suas informações de fuso horário chamando o construtor sobrecarregado [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="86b35-122">If the [DateTime](xref:System.DateTime) value reflects the date and time in something other than the local time zone or UTC, you can convert it to a [DateTimeOffset](xref:System.DateTimeOffset) value and preserve its time zone information by calling the overloaded [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset) constructor.</span></span> <span data-ttu-id="86b35-123">O exemplo a seguir instancia um objeto [DateTimeOffset](xref:System.DateTimeOffset) que reflete a Hora Padrão Central.</span><span class="sxs-lookup"><span data-stu-id="86b35-123">For example, the following example instantiates a [DateTimeOffset](xref:System.DateTimeOffset) object that reflects Central Standard Time.</span></span>

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

<span data-ttu-id="86b35-124">O segundo parâmetro para essa sobrecarga de construtor, um objeto [System.TimeSpan](xref:System.TimeSpan) que representa o deslocamento da hora com relação ao UTC, deve ser recuperado chamando o método [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) do fuso horário correspondente da hora.</span><span class="sxs-lookup"><span data-stu-id="86b35-124">The second parameter to this constructor overload, a [System.TimeSpan](xref:System.TimeSpan) object that represents the time's offset from UTC, should be retrieved by calling the [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) method of the time's corresponding time zone.</span></span> <span data-ttu-id="86b35-125">O único parâmetro do método é o valor de [DateTime](xref:System.DateTime) que representa a data e hora a ser convertida.</span><span class="sxs-lookup"><span data-stu-id="86b35-125">The method's single parameter is the [DateTime](xref:System.DateTime) value that represents the date and time to be converted.</span></span> <span data-ttu-id="86b35-126">Se o fuso horário der suporte ao horário de verão, este parâmetro permite que o método determine o deslocamento apropriado para aquela data e hora determinada.</span><span class="sxs-lookup"><span data-stu-id="86b35-126">If the time zone supports daylight saving time, this parameter allows the method to determine the appropriate offset for that particular date and time.</span></span>

## <a name="conversions-from-datetimeoffset-to-datetime"></a><span data-ttu-id="86b35-127">Conversões de DateTimeOffset em DateTime</span><span class="sxs-lookup"><span data-stu-id="86b35-127">Conversions from DateTimeOffset to DateTime</span></span>

<span data-ttu-id="86b35-128">A propriedade [DateTime](xref:System.DateTime) é usada mais comumente para executar a conversão de [DateTimeOffset](xref:System.DateTimeOffset) para [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="86b35-128">The [DateTime](xref:System.DateTime) property is most commonly used to perform [DateTimeOffset](xref:System.DateTimeOffset) to [DateTime](xref:System.DateTime) conversion.</span></span> <span data-ttu-id="86b35-129">No entanto, ela retorna um valor de [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) é [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="86b35-129">However, it returns a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), as the following example illustrates.</span></span> 

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

<span data-ttu-id="86b35-130">Isso significa que todas as informações sobre a relação do valor de [DateTimeOffset](xref:System.DateTimeOffset) com o UTC são perdidas pela conversão quando a propriedade [DateTime](xref:System.DateTime) é usada.</span><span class="sxs-lookup"><span data-stu-id="86b35-130">This means that any information about the [DateTimeOffset](xref:System.DateTimeOffset) value's relationship to UTC is lost by the conversion when the [DateTime](xref:System.DateTime) property is used.</span></span> <span data-ttu-id="86b35-131">Isso afeta valores de [DateTimeOffset](xref:System.DateTimeOffset) que correspondem à hora em UTC ou à hora do sistema local porque a estrutura [DateTime](xref:System.DateTime) reflete somente esses dois fusos horários em sua propriedade [Kind](xref:System.DateTime.Kind).</span><span class="sxs-lookup"><span data-stu-id="86b35-131">This affects [DateTimeOffset](xref:System.DateTimeOffset) values that correspond to UTC time or to the system's local time because the [DateTime](xref:System.DateTime) structure reflects only those two time zones in its [Kind](xref:System.DateTime.Kind) property.</span></span>

<span data-ttu-id="86b35-132">Para preservar o máximo possível de informações do fuso horário ao converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) para [DateTime](xref:System.DateTime), você pode usar as propriedades [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) e [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime).</span><span class="sxs-lookup"><span data-stu-id="86b35-132">To preserve as much time zone information as possible when converting a [DateTimeOffset](xref:System.DateTimeOffset) to a [DateTime](xref:System.DateTime) value, you can use the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) and [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) properties.</span></span> 

## <a name="converting-a-utc-time"></a><span data-ttu-id="86b35-133">Convertendo uma hora UTC</span><span class="sxs-lookup"><span data-stu-id="86b35-133">Converting a UTC Time</span></span>

<span data-ttu-id="86b35-134">Para indicar que um valor de [DateTime](xref:System.DateTime) convertido é a hora em UTC, você pode recuperar o valor da propriedade [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime).</span><span class="sxs-lookup"><span data-stu-id="86b35-134">To indicate that a converted [DateTime](xref:System.DateTime) value is the UTC time, you can retrieve the value of the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property.</span></span> <span data-ttu-id="86b35-135">Ele difere da propriedade [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="86b35-135">It differs from the [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) property in two ways:</span></span>

* <span data-ttu-id="86b35-136">Ele retorna um valor de [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) é [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span><span class="sxs-lookup"><span data-stu-id="86b35-136">It returns a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

* <span data-ttu-id="86b35-137">Se o valor da propriedade [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) não for igual a [TimeSpan.Zero](xref:System.TimeSpan.Zero), ele converte a hora em UTC.</span><span class="sxs-lookup"><span data-stu-id="86b35-137">If the [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) property value does not equal [TimeSpan.Zero](xref:System.TimeSpan.Zero), it converts the time to UTC.</span></span>

> [!NOTE]
> <span data-ttu-id="86b35-138">Se seu aplicativo exigir que os valores convertidos de [DateTime](xref:System.DateTime) identifiquem sem ambiguidade um único ponto no tempo, considere usar a propriedade [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) para lidar com todas as conversões de [DateTimeOffset](xref:System.DateTimeOffset) em [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="86b35-138">If your application requires that converted [DateTime](xref:System.DateTime) values unambiguously identify a single point in time, you should consider using the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property to handle all [DateTimeOffset](xref:System.DateTimeOffset) to [DateTime](xref:System.DateTime) conversions.</span></span>

<span data-ttu-id="86b35-139">O código a seguir usa a propriedade [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) para converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) cujo deslocamento é igual a [TimeSpan.Zero](xref:System.TimeSpan.Zero) em um valor de [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="86b35-139">The following code uses the [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property to convert a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset equals [TimeSpan.Zero](xref:System.TimeSpan.Zero) to a [DateTime](xref:System.DateTime) value.</span></span>

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

<span data-ttu-id="86b35-140">O código a seguir usa a propriedade UtcDateTime para executar uma conversão de fuso horário e uma conversão de tipo em um valor de [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="86b35-140">The following code uses the UtcDateTime property to perform both a time zone conversion and a type conversion on a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

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

## <a name="converting-a-local-time"></a><span data-ttu-id="86b35-141">Convertendo uma hora Local</span><span class="sxs-lookup"><span data-stu-id="86b35-141">Converting a Local Time</span></span>

<span data-ttu-id="86b35-142">Para indicar que um valor de [DateTimeOffset](xref:System.DateTimeOffset) representa a hora local, você pode passar o valor de [DateTime](xref:System.DateTime) retornado pela propriedade [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) para o método estático [DateTime.SpecifyKind (DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)).</span><span class="sxs-lookup"><span data-stu-id="86b35-142">To indicate that a [DateTimeOffset](xref:System.DateTimeOffset) value represents the local time, you can pass the [DateTime](xref:System.DateTime) value returned by the [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) property to the static [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method.</span></span> <span data-ttu-id="86b35-143">O método retorna a data e hora passada para ele como o primeiro parâmetro, mas define a propriedade [Kind](xref:System.DateTime.Kind) como o valor especificado pelo seu segundo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="86b35-143">The method returns the date and time passed to it as its first parameter, but sets the [Kind](xref:System.DateTime.Kind) property to the value specified by its second parameter.</span></span> <span data-ttu-id="86b35-144">O código a seguir usa o método [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) ao converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) cujo deslocamento corresponde ao do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="86b35-144">The following code uses the [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method when converting a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset corresponds to that of the local time zone.</span></span>

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

<span data-ttu-id="86b35-145">Você também pode usar a propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) para converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) para um valor de [DateTime](xref:System.DateTime) local.</span><span class="sxs-lookup"><span data-stu-id="86b35-145">You can also use the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to convert a [DateTimeOffset](xref:System.DateTimeOffset) value to a local [DateTime](xref:System.DateTime) value.</span></span> <span data-ttu-id="86b35-146">A propriedade [Kind](xref:System.DateTime.Kind) do valor [DateTime](xref:System.DateTime) retornado é [DateTimeKind.Local](xref:System.DateTimeKind.Local).</span><span class="sxs-lookup"><span data-stu-id="86b35-146">The [Kind](xref:System.DateTime.Kind) property of the returned [DateTime](xref:System.DateTime) value is [DateTimeKind.Local](xref:System.DateTimeKind.Local).</span></span> <span data-ttu-id="86b35-147">O código a seguir usa a propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) ao converter um valor de [DateTimeOffset](xref:System.DateTimeOffset) cujo deslocamento corresponde ao do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="86b35-147">The following code uses the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property when converting a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset corresponds to that of the local time zone.</span></span>

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

<span data-ttu-id="86b35-148">Quando você recupera um valor de [DateTime](xref:System.DateTime) usando a propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime), o acessador `get` da propriedade primeiro converte o valor de [DateTimeOffset](xref:System.DateTimeOffset) para UTC e depois o converte para a hora local chamando o método [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="86b35-148">When you retrieve a [DateTime](xref:System.DateTime) value using the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property, the property's `get` accessor first converts the [DateTimeOffset](xref:System.DateTimeOffset) value to UTC, then converts it to local time by calling the [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset) method.</span></span> <span data-ttu-id="86b35-149">Isso significa que você pode recuperar um valor a partir a propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) para executar uma conversão de fuso horário ao mesmo tempo em que executa uma conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="86b35-149">This means that you can retrieve a value from the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to perform a time zone conversion at the same time that you perform a type conversion.</span></span> <span data-ttu-id="86b35-150">Isso também significa que as regras de ajuste do fuso horário local são aplicadas na execução da conversão.</span><span class="sxs-lookup"><span data-stu-id="86b35-150">It also means that the local time zone's adjustment rules are applied in performing the conversion.</span></span> <span data-ttu-id="86b35-151">O código a seguir ilustra o uso da propriedade [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) para executar uma conversão de tipo e de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="86b35-151">The following code illustrates the use of the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to perform both a type and a time zone conversion.</span></span>

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

## <a name="a-general-purpose-conversion-method"></a><span data-ttu-id="86b35-152">Um método de conversão com finalidade geral</span><span class="sxs-lookup"><span data-stu-id="86b35-152">A General-Purpose Conversion Method</span></span>

<span data-ttu-id="86b35-153">O exemplo a seguir define um método chamado `ConvertFromDateTimeOffset` que converte valores de [DateTimeOffset](xref:System.DateTimeOffset) para valores de [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="86b35-153">The following example defines a method named `ConvertFromDateTimeOffset` that converts [DateTimeOffset](xref:System.DateTimeOffset) values to [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="86b35-154">Com base no seu deslocamento, ele determina se o valor de [DateTimeOffset](xref:System.DateTimeOffset) é uma hora no UTC, uma hora local ou outro tipo de hora e define a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora retornado de acordo com isso.</span><span class="sxs-lookup"><span data-stu-id="86b35-154">Based on its offset, it determines whether the [DateTimeOffset](xref:System.DateTimeOffset) value is a UTC time, a local time, or some other time, and defines the returned date and time value's [Kind](xref:System.DateTime.Kind) property accordingly.</span></span> 

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

<span data-ttu-id="86b35-155">O exemplo a seguir chama o método `ConvertFromDateTimeOffset` para converter valores de [DateTimeOffset](xref:System.DateTimeOffset) que representam uma hora em UTC, uma hora local e uma hora no Fuso horário padrão central.</span><span class="sxs-lookup"><span data-stu-id="86b35-155">The follow example calls the `ConvertFromDateTimeOffset` method to convert [DateTimeOffset](xref:System.DateTimeOffset) values that represent a UTC time, a local time, and a time in the U.S. Central Standard Time zone.</span></span>

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

<span data-ttu-id="86b35-156">Observe que esse código faz duas suposições que, dependendo do aplicativo e da fonte de seus valores de data e hora, podem não ser sempre válidas:</span><span class="sxs-lookup"><span data-stu-id="86b35-156">Note that this code makes two assumptions that, depending on the application and the source of its date and time values, may not always be valid:</span></span>

* <span data-ttu-id="86b35-157">Ele supõe que um valor de data e hora cujo deslocamento é [TimeSpan.Zero](xref:System.TimeSpan.Zero) representa o UTC.</span><span class="sxs-lookup"><span data-stu-id="86b35-157">It assumes that a date and time value whose offset is [TimeSpan.Zero](xref:System.TimeSpan.Zero) represents UTC.</span></span> <span data-ttu-id="86b35-158">Na verdade, UTC não é uma hora em um determinado fuso horário, mas a hora em relação à qual as horas nos fusos horários do mundo são padronizadas.</span><span class="sxs-lookup"><span data-stu-id="86b35-158">In fact, UTC is not a time in a particular time zone, but the time in relation to which the times in the world's time zones are standardized.</span></span> <span data-ttu-id="86b35-159">Os fusos horários também podem ter um deslocamento de [Zero](xref:System.TimeSpan.Zero).</span><span class="sxs-lookup"><span data-stu-id="86b35-159">Time zones can also have an offset of [Zero](xref:System.TimeSpan.Zero).</span></span>

* <span data-ttu-id="86b35-160">Ele supõe que uma data e hora cujo deslocamento é igual ao do fuso horário local representa o fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="86b35-160">It assumes that a date and time whose offset equals that of the local time zone represents the local time zone.</span></span> <span data-ttu-id="86b35-161">Como os valores de data e hora são dissociados do seu fuso horário original, este pode não ser o caso. A data e hora podem ter sido originadas em outro fuso horário com o mesmo deslocamento.</span><span class="sxs-lookup"><span data-stu-id="86b35-161">Because date and time values are disassociated from their original time zone, this may not be the case; the date and time can have originated in another time zone with the same offset.</span></span>

## <a name="see-also"></a><span data-ttu-id="86b35-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86b35-162">See Also</span></span>

[<span data-ttu-id="86b35-163">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="86b35-163">Dates, times, and time zones</span></span>](index.md)





