---
title: "Como criar uma instância de um objeto TimeZoneInfo"
description: "Como criar uma instância de um objeto TimeZoneInfo"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bff137e5-d550-44c3-b460-b3f2dabd4035
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f2584d446c92d2df2f6d74533ef07fe96888d36a
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="5fa65-104">Como criar uma instância de um objeto TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="5fa65-104">How to: instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="5fa65-105">A maneira mais comum para criar uma instância de um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) é recuperar informações sobre ele do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="5fa65-105">The most common way to instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object is to retrieve information about it from the operating system.</span></span> <span data-ttu-id="5fa65-106">Este tópico aborda como criar uma instância de um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) do sistema local.</span><span class="sxs-lookup"><span data-stu-id="5fa65-106">This topic discusses how to instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object from the local system.</span></span>

## <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="5fa65-107">Para criar uma instância de um objeto TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="5fa65-107">To instantiate a TimeZoneInfo Object</span></span>

1. <span data-ttu-id="5fa65-108">Declare um objeto [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="5fa65-108">Declare a [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span>

2. <span data-ttu-id="5fa65-109">Chame o método `static` (`Shared` no Visual Basic) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)).</span><span class="sxs-lookup"><span data-stu-id="5fa65-109">Call the `static` (`Shared` in Visual Basic) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) method.</span></span>

3. <span data-ttu-id="5fa65-110">Solucione eventuais exceções geradas pelo método.</span><span class="sxs-lookup"><span data-stu-id="5fa65-110">Handle any exceptions thrown by the method.</span></span>

## <a name="example"></a><span data-ttu-id="5fa65-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fa65-111">Example</span></span>

<span data-ttu-id="5fa65-112">O código a seguir recupera um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa o fuso horário padrão do Leste dos EUA e exibe a hora oficial do Leste dos EUA que corresponde à hora local.</span><span class="sxs-lookup"><span data-stu-id="5fa65-112">The following code retrieves a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

```csharp
DateTime timeNow = DateTime.Now;
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
   DateTime easternTimeNow = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, 
                                                   easternZone);
   Console.WriteLine("{0} {1} corresponds to {2} {3}.",
                     timeNow, 
                     TimeZoneInfo.Local.IsDaylightSavingTime(timeNow) ?
                               TimeZoneInfo.Local.DaylightName : 
                               TimeZoneInfo.Local.StandardName,
                     easternTimeNow, 
                     easternZone.IsDaylightSavingTime(easternTimeNow) ?
                                 easternZone.DaylightName : 
                                 easternZone.StandardName);
}
// Handle exception
//
// As an alternative to simply displaying an error message, an alternate Eastern
// Standard Time TimeZoneInfo object could be instantiated here either by restoring
// it from a serialized string or by providing the necessary data to the
// CreateCustomTimeZone method.
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.");
}
catch (SecurityException)
{
   Console.WriteLine("The application lacks permission to read time zone information from the registry.");
}
catch (OutOfMemoryException)
{
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.");
}
// If we weren't passing FindSystemTimeZoneById a literal string, we also 
// would handle an ArgumentNullException.
```

```vb
Dim timeNow As Date = Date.Now
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
   Dim easternTimeNow As Date = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, easternZone)
   Console.WriteLine("{0} {1} corresponds to {2} {3}.", _
                     timeNow, _
                     IIf(TimeZoneInfo.Local.IsDaylightSavingTime(timeNow), _
                         TimeZoneInfo.Local.DaylightName, TimeZoneInfo.Local.StandardName), _
                     easternTimeNow, _
                     IIf(easternZone.IsDaylightSavingTime(easternTimeNow), _
                         easternZone.DaylightName, easternZone.StandardName))
' Handle exception
'
' As an alternative to simply displaying an error message, an alternate Eastern
' Standard Time TimeZoneInfo object could be instantiated here either by restoring
' it from a serialized string or by providing the necessary data to the
' CreateCustomTimeZone method.
Catch e As InvalidTimeZoneException
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.")   
Catch e As SecurityException
   Console.WriteLine("The application lacks permission to read time zone information from the registry.")
Catch e As OutOfMemoryException
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.")
' If we weren't passing FindSystemTimeZoneById a literal string, we also 
' would handle an ArgumentNullException.
End
``` 

<span data-ttu-id="5fa65-113">O único parâmetro do método [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) é o identificador do fuso horário que você deseja recuperar, que corresponde à propriedade [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) do objeto.</span><span class="sxs-lookup"><span data-stu-id="5fa65-113">The [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) property.</span></span> <span data-ttu-id="5fa65-114">O identificador do fuso horário é um campo de chave que identifica exclusivamente o fuso horário.</span><span class="sxs-lookup"><span data-stu-id="5fa65-114">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="5fa65-115">Enquanto a maioria das chaves são relativamente curtas, o identificador de fuso horário é comparativamente longo.</span><span class="sxs-lookup"><span data-stu-id="5fa65-115">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="5fa65-116">Na maioria dos casos, seu valor corresponde à propriedade [StandardName](xref:System.TimeZoneInfo.StandardName) do objeto [TimeZoneInfo](xref:System.TimeZoneInfo), que é usada para fornecer o nome da hora padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="5fa65-116">In most cases, its value corresponds to the [StandardName](xref:System.TimeZoneInfo.StandardName) property of a [TimeZoneInfo](xref:System.TimeZoneInfo) object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="5fa65-117">No entanto, há exceções.</span><span class="sxs-lookup"><span data-stu-id="5fa65-117">However, there are exceptions.</span></span> <span data-ttu-id="5fa65-118">A melhor maneira de certificar-se de que você forneça um identificador válido é enumerar os fusos horários disponíveis no sistema e observar os identificadores dos fusos horários presentes nele.</span><span class="sxs-lookup"><span data-stu-id="5fa65-118">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="5fa65-119">Para obter uma ilustração, veja [Como enumerar os fusos horários presentes em um computador](enumerate-time-zones.md).</span><span class="sxs-lookup"><span data-stu-id="5fa65-119">For an illustration, see [How to: enumerate time zones present on a computer](enumerate-time-zones.md).</span></span> <span data-ttu-id="5fa65-120">O tópico [Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md) também contém uma lista de identificadores de fuso horário selecionados.</span><span class="sxs-lookup"><span data-stu-id="5fa65-120">The [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="5fa65-121">Se o fuso horário for encontrado, o método retornará seu objeto [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="5fa65-121">If the time zone is found, the method returns its [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span> <span data-ttu-id="5fa65-122">Se o fuso horário for encontrado mas seus dados estiverem corrompidos ou incompletos, o método gerará uma [InvalidTimeZoneException](xref:System.InvalidTimeZoneException).</span><span class="sxs-lookup"><span data-stu-id="5fa65-122">If the time zone is found but its data is corrupted or incomplete, the method throws an [InvalidTimeZoneException](xref:System.InvalidTimeZoneException).</span></span> 

## <a name="see-also"></a><span data-ttu-id="5fa65-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fa65-123">See Also</span></span>

[<span data-ttu-id="5fa65-124">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="5fa65-124">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="5fa65-125">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="5fa65-125">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
