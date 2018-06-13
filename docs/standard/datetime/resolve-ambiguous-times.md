---
title: 'Como: resolver horários ambíguos'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a92081a164d15e5150c582b37c6c688cd15e619e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571193"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="c6765-102">Como: resolver horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="c6765-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="c6765-103">Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="c6765-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="c6765-104">Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão.</span><span class="sxs-lookup"><span data-stu-id="c6765-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="c6765-105">Ao processar um horário ambíguo, você pode executar uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="c6765-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="c6765-106">Faça uma suposição de como o tempo aponta para o UTC.</span><span class="sxs-lookup"><span data-stu-id="c6765-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="c6765-107">Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="c6765-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="c6765-108">Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="c6765-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="c6765-109">Este tópico mostra como resolver um horário ambíguo, supondo que ele representa a hora de padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="c6765-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="c6765-110">Para apontar um horário ambíguo para o horário padrão de um fuso horário</span><span class="sxs-lookup"><span data-stu-id="c6765-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="c6765-111">Chamar o <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> método para determinar se o horário é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="c6765-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="c6765-112">Se o tempo for ambíguo, subtraia o horário do <xref:System.TimeSpan> objeto retornado pelo fuso horário <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c6765-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="c6765-113">Chamar o `static` (`Shared` no Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> método para definir o UTC Data e hora do valor <xref:System.DateTime.Kind%2A> propriedade <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6765-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="c6765-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6765-114">Example</span></span>

<span data-ttu-id="c6765-115">O exemplo a seguir ilustra como converter um horário ambíguo UTC, supondo que ele representa a hora de padrão do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="c6765-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="c6765-116">O exemplo consiste em um método chamado `ResolveAmbiguousTime` que determina se o <xref:System.DateTime> valor passado a ele é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="c6765-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="c6765-117">Se o valor for ambíguo, o método retorna um <xref:System.DateTime> valor que representa a hora UTC correspondente.</span><span class="sxs-lookup"><span data-stu-id="c6765-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="c6765-118">O método trata essa conversão subtraindo o valor do fuso horário local <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade do horário local.</span><span class="sxs-lookup"><span data-stu-id="c6765-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="c6765-119">Normalmente, um tempo ambíguo é tratado chamando o <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> método para recuperar uma matriz de <xref:System.TimeSpan> deslocamentos de objetos que contêm o UTC horário ambíguo possíveis.</span><span class="sxs-lookup"><span data-stu-id="c6765-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="c6765-120">No entanto, esse exemplo faz a suposição arbitrária de que um horário ambíguo deve sempre apontar para o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="c6765-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="c6765-121">O <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade retorna a diferença entre o UTC e a hora padrão de uma zona de tempo.</span><span class="sxs-lookup"><span data-stu-id="c6765-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="c6765-122">Neste exemplo, todas as referências para o fuso horário local são feitas por meio de <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade; a hora local da zona nunca é atribuída a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="c6765-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="c6765-123">Essa é uma prática recomendada, porque uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método invalida todos os objetos que o fuso horário local é atribuído a.</span><span class="sxs-lookup"><span data-stu-id="c6765-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c6765-124">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c6765-124">Compiling the code</span></span>

<span data-ttu-id="c6765-125">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c6765-125">This example requires:</span></span>

* <span data-ttu-id="c6765-126">Que uma referência a System.Core.dll seja adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="c6765-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="c6765-127">Se o <xref:System> namespace importados com o `using` instrução (necessária em código c#).</span><span class="sxs-lookup"><span data-stu-id="c6765-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6765-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6765-128">See also</span></span>

<span data-ttu-id="c6765-129">[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[como: permitir que os usuários a resolver horários ambíguos](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="c6765-129">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span></span>
