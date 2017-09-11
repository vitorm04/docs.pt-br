---
title: "Como resolver horários ambíguos"
description: "Como resolver horários ambíguos"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e86050c6-d16d-405e-8bba-7205945c9a81
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f4ab3b4bf3487e70be7e885e9b8a2281927eb30e
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="b5aa0-104">Como resolver horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="b5aa0-104">How to: resolve ambiguous times</span></span>

<span data-ttu-id="b5aa0-105">Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="b5aa0-105">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="b5aa0-106">Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-106">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="b5aa0-107">Ao processar um horário ambíguo, você pode executar uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="b5aa0-107">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="b5aa0-108">Faça uma suposição de como o tempo aponta para o UTC.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-108">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="b5aa0-109">Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-109">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="b5aa0-110">Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-110">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="b5aa0-111">Este artigo mostra como resolver um horário ambíguo supondo que ele representa o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-111">This article shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

## <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="b5aa0-112">Para apontar um horário ambíguo para o horário padrão de um fuso horário</span><span class="sxs-lookup"><span data-stu-id="b5aa0-112">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="b5aa0-113">Chame o método [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) ou [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) para determinar se o horário é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-113">Call the [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) or [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="b5aa0-114">Se o horário for ambíguo, subtraia o horário do objeto [TimeSpan](xref:System.TimeSpan) retornado pela propriedade [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-114">If the time is ambiguous, subtract the time from the [TimeSpan](xref:System.TimeSpan) object returned by the time zone's [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property.</span></span>

3. <span data-ttu-id="b5aa0-115">Chame `static` (`Shared` no Visual Basic) o método [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) para definir a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora do UTC como [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span><span class="sxs-lookup"><span data-stu-id="b5aa0-115">Call the `static` (`Shared` in Visual Basic) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method to set the UTC date and time value's [Kind](xref:System.DateTime.Kind) property to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="example"></a><span data-ttu-id="b5aa0-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5aa0-116">Example</span></span>

<span data-ttu-id="b5aa0-117">O exemplo a seguir mostra como converter um [DateTime](xref:System.DateTime) ambíguo em UTC supondo que representa o horário padrão do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-117">The following example illustrates how to convert an ambiguous [DateTime](xref:System.DateTime) to UTC by assuming that it represents the local time zone's standard time.</span></span> 

```csharp
private DateTime ResolveAmbiguousTime(DateTime ambiguousTime)
{
   // Time is not ambiguous
   if (! TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime))
   { 
      return ambiguousTime; 
   }
   // Time is ambiguous
   else
   {
      DateTime utcTime = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, 
                                              DateTimeKind.Utc);      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", 
                        ambiguousTime, utcTime, utcTime.Kind.ToString());
      return utcTime;            
   }   
}
```

```vb
Private Function ResolveAmbiguousTime(ambiguousTime As Date) As Date
   ' Time is not ambiguous
   If Not TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime) Then 
      Return TimeZoneInfo.ConvertTimeToUtc(ambiguousTime) 
   ' Time is ambiguous
   Else
      Dim utcTime As Date = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, DateTimeKind.Utc)      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", ambiguousTime, utcTime, utcTime.Kind.ToString())
      Return utcTime            
   End If   
End Function
```

<span data-ttu-id="b5aa0-118">O exemplo consiste em um método chamado `ResolveAmbiguousTime` que determina se o valor [DateTime](xref:System.DateTime) passado para ele é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-118">The example consists of a method named `ResolveAmbiguousTime` that determines whether the [DateTime](xref:System.DateTime) value passed to it is ambiguous.</span></span> <span data-ttu-id="b5aa0-119">Se o valor for ambíguo, o método retorna um valor [DateTime](xref:System.DateTime) que representa o horário UTC correspondente.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-119">If the value is ambiguous, the method returns a [DateTime](xref:System.DateTime) value that represents the corresponding UTC time.</span></span> <span data-ttu-id="b5aa0-120">O método trata essa conversão subtraindo do horário local o valor da propriedade [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-120">The method handles this conversion by subtracting the value of the local time zone's [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property from the local time.</span></span> 

<span data-ttu-id="b5aa0-121">Normalmente, um horário ambíguo é tratado chamando o método [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) para recuperar uma matriz de objetos [TimeSpan](xref:System.TimeSpan) que contêm os possíveis deslocamentos de UTC do horário ambíguo.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-121">Ordinarily, an ambiguous time is handled by calling the [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) method to retrieve an array of [TimeSpan](xref:System.TimeSpan) objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="b5aa0-122">No entanto, esse exemplo faz a suposição arbitrária de que um horário ambíguo deve sempre apontar para o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-122">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="b5aa0-123">A propriedade [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) retorna a diferença entre o UTC e o horário padrão de um fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-123">The [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property returns the offset between UTC and a time zone's standard time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5aa0-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5aa0-124">See Also</span></span>

[<span data-ttu-id="b5aa0-125">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="b5aa0-125">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="b5aa0-126">Como permitir que os usuários resolvam horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="b5aa0-126">How to: let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)


