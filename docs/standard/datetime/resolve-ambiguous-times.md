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
ms.openlocfilehash: ad69c0984a9d8c01ebd2198486cd0f6492a6116e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281499"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="55a70-102">Como: resolver horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="55a70-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="55a70-103">Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="55a70-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="55a70-104">Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão.</span><span class="sxs-lookup"><span data-stu-id="55a70-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="55a70-105">Ao processar um horário ambíguo, você pode executar uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="55a70-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="55a70-106">Faça uma suposição de como o tempo aponta para o UTC.</span><span class="sxs-lookup"><span data-stu-id="55a70-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="55a70-107">Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="55a70-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="55a70-108">Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="55a70-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="55a70-109">Este tópico mostra como resolver um tempo ambíguo supondo que ele representa o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="55a70-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="55a70-110">Para apontar um horário ambíguo para o horário padrão de um fuso horário</span><span class="sxs-lookup"><span data-stu-id="55a70-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="55a70-111">Chame o <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> método para determinar se o tempo é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="55a70-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="55a70-112">Se o tempo for ambíguo, subtraia a hora do <xref:System.TimeSpan> objeto retornado pela propriedade do fuso horário <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="55a70-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="55a70-113">Chame o `static` `Shared` método (no Visual Basic .net) <xref:System.DateTime.SpecifyKind%2A> para definir a propriedade de valor de data e hora UTC <xref:System.DateTime.Kind%2A> como <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="55a70-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="55a70-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55a70-114">Example</span></span>

<span data-ttu-id="55a70-115">O exemplo a seguir ilustra como converter um horário ambíguo em UTC supondo que ele representa o horário padrão do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="55a70-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="55a70-116">O exemplo consiste em um método chamado `ResolveAmbiguousTime` que determina se o <xref:System.DateTime> valor passado para ele é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="55a70-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="55a70-117">Se o valor for ambíguo, o método retornará um <xref:System.DateTime> valor que representa a hora UTC correspondente.</span><span class="sxs-lookup"><span data-stu-id="55a70-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="55a70-118">O método manipula essa conversão subtraindo o valor da Propriedade do fuso horário local <xref:System.TimeZoneInfo.BaseUtcOffset%2A> da hora local.</span><span class="sxs-lookup"><span data-stu-id="55a70-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="55a70-119">Normalmente, uma hora ambígua é tratada chamando o <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> método para recuperar uma matriz de <xref:System.TimeSpan> objetos que contêm os deslocamentos de UTC possíveis.</span><span class="sxs-lookup"><span data-stu-id="55a70-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="55a70-120">No entanto, esse exemplo faz a suposição arbitrária de que um horário ambíguo deve sempre apontar para o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="55a70-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="55a70-121">A <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade retorna o deslocamento entre o UTC e o horário padrão de um fuso horário.</span><span class="sxs-lookup"><span data-stu-id="55a70-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="55a70-122">Neste exemplo, todas as referências ao fuso horário local são feitas por meio da <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Propriedade; o fuso horário local nunca é atribuído a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="55a70-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="55a70-123">Essa é uma prática recomendada porque uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método invalida todos os objetos aos quais o fuso horário local está atribuído.</span><span class="sxs-lookup"><span data-stu-id="55a70-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="55a70-124">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="55a70-124">Compiling the code</span></span>

<span data-ttu-id="55a70-125">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="55a70-125">This example requires:</span></span>

- <span data-ttu-id="55a70-126">Que o <xref:System> namespace seja importado com a `using` instrução (necessária no código C#).</span><span class="sxs-lookup"><span data-stu-id="55a70-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="55a70-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="55a70-127">See also</span></span>

- [<span data-ttu-id="55a70-128">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="55a70-128">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="55a70-129">Como: permitir que os usuários resolvam tempos ambíguos</span><span class="sxs-lookup"><span data-stu-id="55a70-129">How to: Let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)
