---
title: "Como acessar os objetos de fuso horário UTC e Local predefinidos"
description: "Como acessar os objetos de fuso horário predefinidos UTC e Local"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 13454d47-d957-421b-9ecd-940058b8835e
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: fcc48e40cdad25c6142dbc3a86513b816378fa4b
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="b7e37-104">Como acessar os objetos de fuso horário UTC e Local predefinidos</span><span class="sxs-lookup"><span data-stu-id="b7e37-104">How to: access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="b7e37-105">A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) fornece duas propriedades, `Utc` e `Local`, que fornecem seu acesso de código para objetos de fuso horário predefinidos.</span><span class="sxs-lookup"><span data-stu-id="b7e37-105">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class provides two properties, `Utc` and `Local`, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="b7e37-106">Este tópico discute como acessar os objetos `TimeZoneInfo` retornados por essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="b7e37-106">This topic discusses how to access the `TimeZoneInfo` objects returned by those properties.</span></span>

## <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="b7e37-107">Para acessar o objeto TimeZoneInfo de UTC (Tempo Universal Coordenado)</span><span class="sxs-lookup"><span data-stu-id="b7e37-107">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="b7e37-108">Use a propriedade **static** (**Shared** no Visual Basic) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) para acessar o Tempo Universal Coordenado.</span><span class="sxs-lookup"><span data-stu-id="b7e37-108">Use the **static** (**Shared** in Visual Basic) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="b7e37-109">Em vez de atribuir o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) retornado pela propriedade a uma variável de objeto, continue a acessar o Tempo Universal Coordenado por meio da propriedade [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc).</span><span class="sxs-lookup"><span data-stu-id="b7e37-109">Rather than assigning the [TimeZoneInfo](xref:System.TimeZoneInfo) object returned by the property to an object variable, continue to access Coordinated Universal Time through the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property.</span></span>


## <a name="to-access-the-local-time-zone"></a><span data-ttu-id="b7e37-110">Para acessar o fuso horário local</span><span class="sxs-lookup"><span data-stu-id="b7e37-110">To access the local time zone</span></span>

1. <span data-ttu-id="b7e37-111">Use a propriedade **static** (**Shared** no Visual Basic) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) para acessar o fuso horário do sistema local.</span><span class="sxs-lookup"><span data-stu-id="b7e37-111">Use the **static** (**Shared** in Visual Basic) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property to access the local system time zone.</span></span>

2. <span data-ttu-id="b7e37-112">Em vez de atribuir o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) retornado pela propriedade a uma variável de objeto, continue a acessar o fuso horário local por meio da propriedade [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local).</span><span class="sxs-lookup"><span data-stu-id="b7e37-112">Rather than assigning the [TimeZoneInfo](xref:System.TimeZoneInfo) object returned by the property to an object variable, continue to access the local time zone through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property.</span></span>

## <a name="example"></a><span data-ttu-id="b7e37-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7e37-113">Example</span></span>

<span data-ttu-id="b7e37-114">O código a seguir usa as propriedades [TimeZoneInfo](xref:System.TimeZoneInfo.Local) e [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) para converter um horário do fuso horário Padrão do Leste do Canadá e EUA, bem como para exibir o nome do fuso horário no console.</span><span class="sxs-lookup"><span data-stu-id="b7e37-114">The following code uses the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) and [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

```csharp
// Create Eastern Standard Time value and TimeZoneInfo object      
DateTime estTime = new DateTime(2007, 1, 1, 00, 00, 00);
string timeZoneName = "Eastern Standard Time";
try
{
   TimeZoneInfo est = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName);

   // Convert EST to local time
   DateTime localTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local);
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", 
           estTime, 
           est, 
           localTime, 
           TimeZoneInfo.Local.IsDaylightSavingTime(localTime) ?
                     TimeZoneInfo.Local.DaylightName : 
                     TimeZoneInfo.Local.StandardName);

   // Convert EST to UTC
   DateTime utcTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc);
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", 
           estTime, 
           est, 
           utcTime, 
           TimeZoneInfo.Utc.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The {0} zone cannot be found in the registry.", 
                     timeZoneName);
}
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The registry contains invalid data for the {0} zone.", 
                     timeZoneName);
}
```

```vb
' Create Eastern Standard Time value and TimeZoneInfo object      
Dim estTime As Date = #01/01/2007 00:00:00#
Dim timeZoneName As String = "Eastern Standard Time"
Try
   Dim est As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName)

   ' Convert EST to local time
   Dim localTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local)
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", _
           estTime, _
           est, _
           localTime, _
           IIf(TimeZoneInfo.Local.IsDaylightSavingTime(localTime), _
               TimeZoneInfo.Local.DaylightName, _
               TimeZoneInfo.Local.StandardName))

   ' Convert EST to UTC
   Dim utcTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc)
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", _
           estTime, _
           est, _
           utcTime, _
           TimeZoneInfo.Utc.StandardName)
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The {0} zone cannot be found in the registry.", _
                     timeZoneName)
Catch e As InvalidTimeZoneException
   Console.WriteLine("The registry contains invalid data for the {0} zone.", _
                     timeZoneName)
End Try
```

<span data-ttu-id="b7e37-115">Você deve sempre acessar o fuso horário local por meio da propriedade [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) em vez de atribuir o fuso horário local a uma variável de objeto [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="b7e37-115">You should always access the local time zone through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property rather than assigning the local time zone to a [TimeZoneInfo](xref:System.TimeZoneInfo) object variable.</span></span> <span data-ttu-id="b7e37-116">Da mesma forma, você deve sempre acessar o Tempo Universal Coordenado por meio da propriedade [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) em vez de atribuir o fuso horário UTC a uma variável de objeto [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="b7e37-116">Similarly, you should always access Coordinated Universal Time through the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property rather than assigning the UTC zone to a [TimeZoneInfo](xref:System.TimeZoneInfo) object variable.</span></span> <span data-ttu-id="b7e37-117">Isso impede que a variável de objeto [TimeZoneInfo](xref:System.TimeZoneInfo) seja invalidada por um método externo.</span><span class="sxs-lookup"><span data-stu-id="b7e37-117">This prevents the [TimeZoneInfo](xref:System.TimeZoneInfo) object variable from being invalidated by an external method.</span></span>


## <a name="see-also"></a><span data-ttu-id="b7e37-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7e37-118">See Also</span></span>

[<span data-ttu-id="b7e37-119">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="b7e37-119">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="b7e37-120">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="b7e37-120">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)

