---
title: "Convertendo horários entre fusos horários"
description: "Convertendo horários entre fusos horários"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf8f74e6-e7f2-4c2a-a04c-57db0e28dd36
ms.translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: c2baa48c3b79dfbc5d39652cc57fe015a2313d6e
ms.contentlocale: pt-br
ms.lasthandoff: 11/16/2016

---

# <a name="converting-times-between-time-zones"></a><span data-ttu-id="6f414-104">Convertendo horários entre fusos horários</span><span class="sxs-lookup"><span data-stu-id="6f414-104">Converting times between time zones</span></span>

<span data-ttu-id="6f414-105">Está se tornando cada vez mais importante para qualquer aplicativo que trabalha com datas e horas lidar com diferenças entre fusos horários.</span><span class="sxs-lookup"><span data-stu-id="6f414-105">It is becoming increasingly important for any application that works with dates and times to handle differences between time zones.</span></span> <span data-ttu-id="6f414-106">Os aplicativos não podem mais presumir que todos os horários podem ser expressos na hora local, que é a hora disponível na estrutura [System.DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="6f414-106">An application can no longer assume that all times can be expressed in the local time, which is the time available from the [System.DateTime](xref:System.DateTime) structure.</span></span> <span data-ttu-id="6f414-107">Por exemplo, uma página da Web que exibe a hora atual no leste dos Estados Unidos não terá credibilidade para um cliente no leste da Ásia.</span><span class="sxs-lookup"><span data-stu-id="6f414-107">For example, a Web page that displays the current time in the eastern part of the United States will lack credibility to a customer in eastern Asia.</span></span> <span data-ttu-id="6f414-108">Este tópico explica como converter horas de um fuso horário para outro, bem como converter valores de [System.DateTimeOffset](xref:System.DateTimeOffset) que têm percepção limitada de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="6f414-108">This topic explains how to convert times from one time zone to another, as well as how to convert [System.DateTimeOffset](xref:System.DateTimeOffset) values that have limited time zone awareness.</span></span>

## <a name="converting-to-coordinated-universal-time"></a><span data-ttu-id="6f414-109">Convertendo para o Tempo Universal Coordenado</span><span class="sxs-lookup"><span data-stu-id="6f414-109">Converting to Coordinated Universal Time</span></span>

<span data-ttu-id="6f414-110">O UTC (Tempo Universal Coordenado) é um padrão de tempo atômico de alta precisão.</span><span class="sxs-lookup"><span data-stu-id="6f414-110">Coordinated Universal Time (UTC) is a high-precision, atomic time standard.</span></span> <span data-ttu-id="6f414-111">Os fusos horários do mundo são expressos como deslocamentos positivos ou negativos com relação ao UTC.</span><span class="sxs-lookup"><span data-stu-id="6f414-111">The world’s time zones are expressed as positive or negative offsets from UTC.</span></span> <span data-ttu-id="6f414-112">Sendo assim, o UTC fornece uma espécie de hora livre de fuso horário ou com fuso horário neutro.</span><span class="sxs-lookup"><span data-stu-id="6f414-112">Thus, UTC provides a kind of time-zone free or time-zone neutral time.</span></span> <span data-ttu-id="6f414-113">O uso da hora em UTC é recomendado quando a portabilidade da data e hora entre computadores é importante.</span><span class="sxs-lookup"><span data-stu-id="6f414-113">The use of UTC time is recommended when a date and time's portability across computers is important.</span></span> <span data-ttu-id="6f414-114">Converter fusos horários individuais em UTC facilita comparações de hora.</span><span class="sxs-lookup"><span data-stu-id="6f414-114">Converting individual time zones to UTC makes time comparisons easy.</span></span>

> [!NOTE]
> <span data-ttu-id="6f414-115">Você também pode serializar uma estrutura [DateTimeOffset](xref:System.DateTimeOffset) para representar sem ambiguidade um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="6f414-115">You can also serialize a [DateTimeOffset](xref:System.DateTimeOffset) structure to unambiguously represent a single point in time.</span></span> <span data-ttu-id="6f414-116">Uma vez que objetos [DateTimeOffset](xref:System.DateTimeOffset) armazenam um valor de data e hora com seu deslocamento com relação ao UTC, eles sempre representam um ponto específico no tempo em relação ao UTC.</span><span class="sxs-lookup"><span data-stu-id="6f414-116">Because [DateTimeOffset](xref:System.DateTimeOffset) objects store a date and time value along with its offset from UTC, they always represent a particular point in time in relationship to UTC.</span></span>

<span data-ttu-id="6f414-117">A maneira mais fácil para converter uma hora para UTC é chamar o método `static` (`Shared` no Visual Basic) [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="6f414-117">The easiest way to convert a time to UTC is to call the `static` (`Shared` in Visual Basic) [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) method.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="6f414-118">O método `TimeZoneInfo.ConvertTimeToUtc(DateTime)` não está disponível no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f414-118">The `TimeZoneInfo.ConvertTimeToUtc(DateTime)` method isn't currently available in .NET Core.</span></span> 

<span data-ttu-id="6f414-119">A conversão exata executada pelo método depende do valor da propriedade [Kind](xref:System.DateTime.Kind) do parâmetro `DateTime`, conforme é mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f414-119">The exact conversion performed by the method depends on the value of the `DateTime` parameter's [Kind](xref:System.DateTime.Kind) property, as the following table shows.</span></span>

<span data-ttu-id="6f414-120">Propriedade [DateTime.Kind](xref:System.DateTimeKind)</span><span class="sxs-lookup"><span data-stu-id="6f414-120">[DateTime.Kind](xref:System.DateTimeKind) property</span></span> | <span data-ttu-id="6f414-121">Conversão</span><span class="sxs-lookup"><span data-stu-id="6f414-121">Conversion</span></span>
---------------------------------------------------------------------------------------------- | ----------
[<span data-ttu-id="6f414-122">DateTimeKind.Local</span><span class="sxs-lookup"><span data-stu-id="6f414-122">DateTimeKind.Local</span></span>](xref:System.DateTimeKind.Local) | <span data-ttu-id="6f414-123">Converte a hora local para UTC.</span><span class="sxs-lookup"><span data-stu-id="6f414-123">Converts local time to UTC.</span></span>
[<span data-ttu-id="6f414-124">DateTimeKind.Unspecified</span><span class="sxs-lookup"><span data-stu-id="6f414-124">DateTimeKind.Unspecified</span></span>](xref:System.DateTimeKind.Unspecified) | <span data-ttu-id="6f414-125">Presume que o parâmetro `DateTime` é a hora local e converte a hora local para UTC.</span><span class="sxs-lookup"><span data-stu-id="6f414-125">Assumes the `DateTime` parameter is local time and converts local time to UTC.</span></span>
[<span data-ttu-id="6f414-126">DateTimeKind.Utc</span><span class="sxs-lookup"><span data-stu-id="6f414-126">DateTimeKind.Utc</span></span>](xref:System.DateTimeKind.Utc) | <span data-ttu-id="6f414-127">Retorna o parâmetro `DateTime` inalterado.</span><span class="sxs-lookup"><span data-stu-id="6f414-127">Returns the `DateTime` parameter unchanged.</span></span>

<span data-ttu-id="6f414-128">O código a seguir converte a hora local atual para UTC e exibe o resultado no console.</span><span class="sxs-lookup"><span data-stu-id="6f414-128">The following code converts the current local time to UTC and displays the result to the console.</span></span>

```csharp
DateTime dateNow = DateTime.Now;
Console.WriteLine("The date and time are {0} UTC.", 
                   TimeZoneInfo.ConvertTimeToUtc(dateNow));
```

```vb
Dim dateNow As Date = Date.Now      
Console.WriteLine("The date and time are {0} UTC.", _
                  TimeZoneInfo.ConvertTimeToUtc(dateNow))
```

> [!NOTE]
><span data-ttu-id="6f414-129">O método [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) não produz necessariamente resultados idênticos aos dos métodos [TimeZone.ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) e [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime).</span><span class="sxs-lookup"><span data-stu-id="6f414-129">The [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) method does not necessarily produce results that are identical to the [TimeZone.ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) and [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) methods.</span></span> <span data-ttu-id="6f414-130">Se o fuso horário local do sistema host incluir várias regras de ajuste, [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/System.TimeZone.ConvertTimeToUtc(v=vs.110).aspx) aplica a regra apropriada a uma data e hora determinada.</span><span class="sxs-lookup"><span data-stu-id="6f414-130">If the host system's local time zone includes multiple adjustment rules, [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/System.TimeZone.ConvertTimeToUtc(v=vs.110).aspx) applies the appropriate rule to a particular date and time.</span></span> <span data-ttu-id="6f414-131">Os outros dois métodos sempre aplicam a regra de ajuste mais recente.</span><span class="sxs-lookup"><span data-stu-id="6f414-131">The other two methods always apply the latest adjustment rule.</span></span>

<span data-ttu-id="6f414-132">Se o valor de data e hora não representar a hora local ou o UTC, o método [ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) provavelmente retornará um resultado com erro.</span><span class="sxs-lookup"><span data-stu-id="6f414-132">If the date and time value does not represent either the local time or UTC, the [ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) method will likely return an erroneous result.</span></span> <span data-ttu-id="6f414-133">No entanto, você pode usar o método [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) para converter a data e hora de um fuso horário especificado.</span><span class="sxs-lookup"><span data-stu-id="6f414-133">However, you can use the [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) method to convert the date and time from a specified time zone.</span></span> <span data-ttu-id="6f414-134">Para obter detalhes sobre como recuperar um objeto TimeZoneInfo que representa o fuso horário de destino, consulte [Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md).</span><span class="sxs-lookup"><span data-stu-id="6f414-134">(For details on retrieving a TimeZoneInfo object that represents the destination time zone, see [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md).</span></span> <span data-ttu-id="6f414-135">O código a seguir usa o método [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) para converter a Zona de Tempo Oriental para UTC.</span><span class="sxs-lookup"><span data-stu-id="6f414-135">The following code uses the [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) method to convert Eastern Standard Time to UTC.</span></span>

```csharp
DateTime easternTime = new DateTime(2007, 01, 02, 12, 16, 00);
string easternZoneId = "Eastern Standard Time";
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId);
   Console.WriteLine("The date and time are {0} UTC.", 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to find the {0} zone in the registry.", 
                     easternZoneId);
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", 
                     easternZoneId);
}
```

```vb
Dim easternTime As New Date(2007, 01, 02, 12, 16, 00)
Dim easternZoneId As String = "Eastern Standard Time"
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId)
   Console.WriteLine("The date and time are {0} UTC.", _ 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to find the {0} zone in the registry.", _
                     easternZoneId)
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", _ 
                     easternZoneId)
End Try    
```

<span data-ttu-id="6f414-136">Observe que esse método lança um [ArgumentException](xref:System.ArgumentException) se a propriedade [Kind](xref:System.DateTimeKind) do objeto [DateTime](xref:System.DateTime) e o fuso horário forem incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="6f414-136">Note that this method throws an [ArgumentException](xref:System.ArgumentException) if the [DateTime](xref:System.DateTime) object's [Kind](xref:System.DateTimeKind) property and the time zone are mismatched.</span></span> <span data-ttu-id="6f414-137">Uma incompatibilidade ocorre se a propriedade Kind for é [DateTimeKind.Local](xref:System.DateTimeKind.Local), mas o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) não representar o fuso horário local ou se a propriedade Kind for [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) mas o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) não for igual a [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span><span class="sxs-lookup"><span data-stu-id="6f414-137">A mismatch occurs if the Kind property is [DateTimeKind.Local](xref:System.DateTimeKind.Local) but the [TimeZoneInfo](xref:System.TimeZoneInfo) object does not represent the local time zone, or if the Kind property is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) but the [TimeZoneInfo](xref:System.TimeZoneInfo) object does not equal [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

<span data-ttu-id="6f414-138">Todos esses métodos usam valores de [DateTime](xref:System.DateTime) como parâmetros e retornam um valor de [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="6f414-138">All of these methods take [DateTime](xref:System.DateTime) values as parameters and return a [DateTime](xref:System.DateTime) value.</span></span> <span data-ttu-id="6f414-139">Para valores de [DateTimeOffset](xref:System.DateTimeOffset), a estrutura [DateTimeOffset](xref:System.DateTimeOffset) tem um método de instância [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) que converte a data e hora da instância atual para UTC.</span><span class="sxs-lookup"><span data-stu-id="6f414-139">For [DateTimeOffset](xref:System.DateTimeOffset) values, the [DateTimeOffset](xref:System.DateTimeOffset) structure has a [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) instance method that converts the date and time of the current instance to UTC.</span></span> <span data-ttu-id="6f414-140">O exemplo a seguir chama o método [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) para converter uma hora local e várias outras horas para UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="6f414-140">The following example calls the [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) method to convert a local time and several other times to Coordinated Universal Time (UTC).</span></span>

```csharp
DateTimeOffset localTime, otherTime, universalTime;

// Define local time in local time zone
localTime = new DateTimeOffset(new DateTime(2007, 6, 15, 12, 0, 0));
Console.WriteLine("Local time: {0}", localTime);
Console.WriteLine();

// Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero);
Console.WriteLine("Other time: {0}", otherTime);
Console.WriteLine("{0} = {1}: {2}", 
                  localTime, otherTime, 
                  localTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  localTime, otherTime, 
                  localTime.EqualsExact(otherTime));
Console.WriteLine();

// Convert other time to UTC
universalTime = localTime.ToUniversalTime(); 
Console.WriteLine("Universal time: {0}", universalTime);
Console.WriteLine("{0} = {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.EqualsExact(otherTime));
Console.WriteLine();
// The example produces the following output to the console:
//    Local time: 6/15/2007 12:00:00 PM -07:00
//    
//    Other time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
//    
//    Universal time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

```vb
Dim localTime, otherTime, universalTime As DateTimeOffset

' Define local time in local time zone
localTime = New DateTimeOffset(#6/15/2007 12:00:00PM#)
Console.WriteLine("Local time: {0}", localTime)
Console.WriteLine()

' Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero)
Console.WriteLine("Other time: {0}", otherTime)
Console.WriteLine("{0} = {1}: {2}", _
                  localTime, otherTime, _
                  localTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  localTime, otherTime, _
                  localTime.EqualsExact(otherTime))
Console.WriteLine()

' Convert other time to UTC
universalTime = localTime.ToUniversalTime() 
Console.WriteLine("Universal time: {0}", universalTime)
Console.WriteLine("{0} = {1}: {2}", _
                  otherTime, universalTime, _ 
                  universalTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  otherTime, universalTime, _
                  universalTime.EqualsExact(otherTime))
Console.WriteLine()
' The example produces the following output to the console:
'    Local time: 6/15/2007 12:00:00 PM -07:00
'    
'    Other time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
'    
'    Universal time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

## <a name="converting-utc-to-a-designated-time-zone"></a><span data-ttu-id="6f414-141">Convertendo UTC em um fuso horário designado</span><span class="sxs-lookup"><span data-stu-id="6f414-141">Converting UTC to a designated time zone</span></span>

<span data-ttu-id="6f414-142">Para converter UTC em hora local, consulte a seção [Convertendo UTC em hora local](#converting-utc-to-local-time) a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f414-142">To convert UTC to local time, see the [Converting UTC to local time](#converting-utc-to-local-time) section that follows.</span></span> 

<span data-ttu-id="6f414-143">Para converter de UTC para a hora correspondente a qualquer fuso horário que você designar, chame o método [ConvertTimeFromUtc](https://msdn.microsoft.com/en-us/library/System.TimeZoneInfo.converttimefromutc(v=vs.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="6f414-143">To convert UTC to the time in any time zone that you designate, call the [ConvertTimeFromUtc](https://msdn.microsoft.com/en-us/library/System.TimeZoneInfo.converttimefromutc(v=vs.110).aspx) method.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="6f414-144">Atualmente, o método “TimeZoneInfo.ConvertTimeFromUtc” não está disponível no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f414-144">The \`TimeZoneInfo.ConvertTimeFromUtc' method isn't currently available in .NET Core.</span></span> 

<span data-ttu-id="6f414-145">O método utiliza dois parâmetros:</span><span class="sxs-lookup"><span data-stu-id="6f414-145">The method takes two parameters:</span></span>

* <span data-ttu-id="6f414-146">O UTC a ser convertido.</span><span class="sxs-lookup"><span data-stu-id="6f414-146">The UTC to convert.</span></span> <span data-ttu-id="6f414-147">Ele deve ser um valor [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) está definida como [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) ou [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span><span class="sxs-lookup"><span data-stu-id="6f414-147">This must be a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is set to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) or [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span> 

* <span data-ttu-id="6f414-148">O fuso horário no qual o UTC deve ser convertido.</span><span class="sxs-lookup"><span data-stu-id="6f414-148">The time zone to convert the UTC to.</span></span> 

<span data-ttu-id="6f414-149">O código a seguir converte o UTC para o Horário Padrão Central.</span><span class="sxs-lookup"><span data-stu-id="6f414-149">The following code converts UTC to Central Standard Time.</span></span>

```csharp
DateTime timeUtc = DateTime.UtcNow;
try
{
   TimeZoneInfo cstZone = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time");
   DateTime cstTime = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone);
   Console.WriteLine("The date and time are {0} {1}.", 
                     cstTime, 
                     cstZone.IsDaylightSavingTime(cstTime) ?
                             cstZone.DaylightName : cstZone.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Central Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.");
}
```

```vb
Dim timeUtc As Date = Date.UtcNow
Try
   Dim cstZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time")
   Dim cstTime As Date = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone)
   Console.WriteLine("The date and time are {0} {1}.", _
                     cstTime, _
                     IIf(cstZone.IsDaylightSavingTime(cstTime), _
                         cstZone.DaylightName, cstZone.StandardName))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Central Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.")
End Try
``` 

## <a name="converting-utc-to-local-time"></a><span data-ttu-id="6f414-150">Convertendo UTC em hora local</span><span class="sxs-lookup"><span data-stu-id="6f414-150">Converting UTC to local time</span></span>

<span data-ttu-id="6f414-151">Para converter UTC para a hora local, chame o método [DateTime.ToLocalTime](xref:System.DateTime) do objeto [DateTime](xref:System.DateTime) cuja hora você deseja converter.</span><span class="sxs-lookup"><span data-stu-id="6f414-151">To convert UTC to local time, call the [DateTime.ToLocalTime](xref:System.DateTime) method of the [DateTime](xref:System.DateTime) object whose time you want to convert.</span></span> <span data-ttu-id="6f414-152">O comportamento exato do método depende do valor da propriedade [Kind](xref:System.DateTime.Kind) do objeto, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f414-152">The exact behavior of the method depends on the value of the object’s [Kind](xref:System.DateTime.Kind) property, as the following table shows.</span></span>

<span data-ttu-id="6f414-153">Propriedade [DateTime.Kind](xref:System.DateTimeKind)</span><span class="sxs-lookup"><span data-stu-id="6f414-153">[DateTime.Kind](xref:System.DateTimeKind) property</span></span> | <span data-ttu-id="6f414-154">Conversão</span><span class="sxs-lookup"><span data-stu-id="6f414-154">Conversion</span></span>
---------------------------------------------------------------------------------------------- | ----------
[<span data-ttu-id="6f414-155">DateTimeKind.Local</span><span class="sxs-lookup"><span data-stu-id="6f414-155">DateTimeKind.Local</span></span>](xref:System.DateTimeKind.Local) | <span data-ttu-id="6f414-156">Retorna o valor [DateTime](xref:System.DateTime) inalterado.</span><span class="sxs-lookup"><span data-stu-id="6f414-156">Returns the [DateTime](xref:System.DateTime) value unchanged.</span></span>
[<span data-ttu-id="6f414-157">DateTimeKind.Unspecified</span><span class="sxs-lookup"><span data-stu-id="6f414-157">DateTimeKind.Unspecified</span></span>](xref:System.DateTimeKind.Unspecified) | <span data-ttu-id="6f414-158">Pressupõe que o valor [DateTime](xref:System.DateTime) está no UTC e o converte do UTC para a hora local.</span><span class="sxs-lookup"><span data-stu-id="6f414-158">Assumes that the [DateTime](xref:System.DateTime) value is UTC and converts the UTC to local time.</span></span>
[<span data-ttu-id="6f414-159">DateTimeKind.Utc</span><span class="sxs-lookup"><span data-stu-id="6f414-159">DateTimeKind.Utc</span></span>](xref:System.DateTimeKind.Utc) | <span data-ttu-id="6f414-160">Converte o valor [DateTime](xref:System.DateTime) para a hora local.</span><span class="sxs-lookup"><span data-stu-id="6f414-160">Converts the [DateTime](xref:System.DateTime) value to local time.</span></span>

## <a name="converting-between-any-two-time-zones"></a><span data-ttu-id="6f414-161">Convertendo entre dois fusos horários</span><span class="sxs-lookup"><span data-stu-id="6f414-161">Converting between any two time zones</span></span>

<span data-ttu-id="6f414-162">Você pode converter entre quaisquer dois fusos horários usando o método estático [TimeZoneInfo.ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)).</span><span class="sxs-lookup"><span data-stu-id="6f414-162">You can convert between any two time zones by using the static [TimeZoneInfo.ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span> <span data-ttu-id="6f414-163">Os parâmetros desse método são o valor de [DateTime](xref:System.DateTime) a ser convertido, um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa o fuso horário do valor de data e hora e um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa o fuso horário no qual o valor de data e hora deverá ser convertido.</span><span class="sxs-lookup"><span data-stu-id="6f414-163">This method's parameters are the [DateTime](xref:System.DateTime) value to convert, a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the time zone of the date and time value, and a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the time zone to convert the date and time value to.</span></span>

<span data-ttu-id="6f414-164">O método requer que a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora a ser convertido e o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) ou o identificador de fuso horário que representa seu fuso horário, sejam correspondentes.</span><span class="sxs-lookup"><span data-stu-id="6f414-164">The method requires that the [Kind](xref:System.DateTime.Kind) property of the date and time value to convert and the [TimeZoneInfo](xref:System.TimeZoneInfo) object or time zone identifier that represents its time zone correspond to one another.</span></span> <span data-ttu-id="6f414-165">Caso contrário, uma [ArgumentException](xref:System.ArgumentException) será gerada.</span><span class="sxs-lookup"><span data-stu-id="6f414-165">Otherwise, an [ArgumentException](xref:System.ArgumentException) is thrown.</span></span> <span data-ttu-id="6f414-166">Por exemplo, se a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora for [DateTimeKind.Local](xref:System.DateTimeKind.Local), uma exceção será lançada se o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) passado como um parâmetro para o método não for igual a [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local).</span><span class="sxs-lookup"><span data-stu-id="6f414-166">For example, if the [Kind](xref:System.DateTime.Kind) property of the date and time value is [DateTimeKind.Local](xref:System.DateTimeKind.Local), an exception is thrown if the [TimeZoneInfo](xref:System.TimeZoneInfo) object passed as a parameter to the method is not equal to [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local).</span></span> <span data-ttu-id="6f414-167">Também é gerada uma exceção se o identificador passado como parâmetro para o método não for igual a [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id).</span><span class="sxs-lookup"><span data-stu-id="6f414-167">An exception is also thrown if the identifier passed as a parameter to the method is not equal to [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id).</span></span>

<span data-ttu-id="6f414-168">O exemplo a seguir usa o método [ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) para converter da Hora Oficial do Havaí para a hora local.</span><span class="sxs-lookup"><span data-stu-id="6f414-168">The following example uses the [ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method to convert from Hawaiian Standard Time to local time.</span></span>

```csharp
DateTime hwTime = new DateTime(2007, 02, 01, 08, 00, 00);
try
{
   TimeZoneInfo hwZone = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time");
   Console.WriteLine("{0} {1} is {2} local time.", 
           hwTime, 
           hwZone.IsDaylightSavingTime(hwTime) ? hwZone.DaylightName : hwZone.StandardName, 
           TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Hawaiian STandard Time zone has been corrupted.");
}
```

```vb
Dim hwTime As Date = #2/01/2007 8:00:00 AM#
Try
   Dim hwZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time")
   Console.WriteLine("{0} {1} is {2} local time.", _
                     hwTime, _
                     IIf(hwZone.IsDaylightSavingTime(hwTime), hwZone.DaylightName, hwZone.StandardName), _
                     TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Hawaiian Standard Time zone has been corrupted.")
End Try
```

## <a name="converting-datetimeoffset-values"></a><span data-ttu-id="6f414-169">Convertendo valores de DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6f414-169">Converting DateTimeOffset values</span></span>

<span data-ttu-id="6f414-170">Valores de data e hora representados por objetos [System.DateTimeOffset](xref:System.DateTimeOffset) não são totalmente cientes do fuso horário porque o objeto é desassociado de seu fuso horário no momento em que é instanciado.</span><span class="sxs-lookup"><span data-stu-id="6f414-170">Date and time values represented by [System.DateTimeOffset](xref:System.DateTimeOffset) objects are not fully time-zone aware because the object is disassociated from its time zone at the time it is instantiated.</span></span> <span data-ttu-id="6f414-171">No entanto, em muitos casos o aplicativo precisa apenas converter uma data e hora com base em dois deslocamentos diferentes do UTC, em vez da hora em fusos horários específicos.</span><span class="sxs-lookup"><span data-stu-id="6f414-171">However, in many cases an application simply needs to convert a date and time based on two different offsets from UTC rather than on the time in particular time zones.</span></span> <span data-ttu-id="6f414-172">Para realizar essa conversão, você pode chamar o método [ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) da instância atual.</span><span class="sxs-lookup"><span data-stu-id="6f414-172">To perform this conversion, you can call the current instance's [ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) method.</span></span> <span data-ttu-id="6f414-173">O parâmetro único do método é [TimeSpan](xref:System.TimeSpan), que representa o deslocamento do novo valor de data e hora que o método deve retornar.</span><span class="sxs-lookup"><span data-stu-id="6f414-173">The method's single parameter is [TimeSpan](xref:System.TimeSpan) representing the offset of the new date and time value that the method is to return.</span></span>  

<span data-ttu-id="6f414-174">Por exemplo, se a data e hora da solicitação de um usuário de uma página da Web for conhecida e for serializada como uma cadeia de caracteres no formato MM/dd/aaaa hh:mm:ss zzzz, o seguinte método `ReturnTimeOnServer` converte esse valor de data e hora para a data e hora no servidor Web.</span><span class="sxs-lookup"><span data-stu-id="6f414-174">For example, if the date and time of a user request for a Web page is known and is serialized as a string in the format MM/dd/yyyy hh:mm:ss zzzz, the following `ReturnTimeOnServer` method converts this date and time value to the date and time on the Web server.</span></span>

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";
   TimeSpan serverOffset = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now);

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = clientTime.ToOffset(serverOffset);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"
   Dim serverOffset As TimeSpan = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now)

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = clientTime.ToOffset(serverOffset)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

<span data-ttu-id="6f414-175">Se a cadeia de caracteres "9/1/2007 5:32:07 -05:00" for passada ao método, representando a data e hora em um fuso horário cinco horas anteriores ao UTC, ele retornará 9/1/2007 3:32:07 AM -07:00 para um servidor localizado nos EUA. Fuso horário padrão do Pacífico.</span><span class="sxs-lookup"><span data-stu-id="6f414-175">If the method is passed the string "9/1/2007 5:32:07 -05:00", which represents the date and time in a time zone five hours earlier than UTC, it returns 9/1/2007 3:32:07 AM -07:00 for a server located in the U.S. Pacific Standard Time zone.</span></span>

<span data-ttu-id="6f414-176">A classe [TimeZoneInfo](xref:System.TimeZoneInfo) também inclui um método [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) com sobrecarga que realiza conversões de fuso horário com valores de [System.DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="6f414-176">The [TimeZoneInfo](xref:System.TimeZoneInfo) class also includes an overloaded [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) method that performs time zone conversions with [System.DateTimeOffset](xref:System.DateTimeOffset) values.</span></span> <span data-ttu-id="6f414-177">Os parâmetros do método são um valor de [System.DateTimeOffset](xref:System.DateTimeOffset) e uma referência ao fuso horário no qual a hora será convertida.</span><span class="sxs-lookup"><span data-stu-id="6f414-177">The method's parameters are a [System.DateTimeOffset](xref:System.DateTimeOffset) value and a reference to the time zone to which the time is to be converted.</span></span> <span data-ttu-id="6f414-178">A chamada de método retorna um valor [System.DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="6f414-178">The method call returns a [System.DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="6f414-179">Por exemplo, o método `ReturnTimeOnServer` no exemplo anterior poderia ser reescrito da seguinte maneira para chamar o método [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)).</span><span class="sxs-lookup"><span data-stu-id="6f414-179">For example, the `ReturnTimeOnServer` method in the previous example could be rewritten as follows to call the [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) method.</span></span>

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, 
                                  CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = TimeZoneInfo.ConvertTime(clientTime, 
                                  TimeZoneInfo.Local);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = TimeZoneInfo.ConvertTime(clientTime, TimeZoneInfo.Local)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

## <a name="see-also"></a><span data-ttu-id="6f414-180">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f414-180">See also</span></span>

[<span data-ttu-id="6f414-181">TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="6f414-181">TimeZoneInfo</span></span>](xref:System.TimeZoneInfo)

[<span data-ttu-id="6f414-182">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="6f414-182">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="6f414-183">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="6f414-183">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)



