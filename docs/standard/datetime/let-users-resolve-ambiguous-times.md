---
title: 'Como: permitir que os usuários resolvam tempos ambíguos'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: f988616a4b2a5d8202c87e3be3cb23c7f9f1f130
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122273"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="1faa3-102">Como: permitir que os usuários resolvam tempos ambíguos</span><span class="sxs-lookup"><span data-stu-id="1faa3-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="1faa3-103">Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="1faa3-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="1faa3-104">Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão.</span><span class="sxs-lookup"><span data-stu-id="1faa3-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="1faa3-105">Ao processar um horário ambíguo, você pode executar uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="1faa3-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="1faa3-106">Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="1faa3-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="1faa3-107">Faça uma suposição de como o tempo aponta para o UTC.</span><span class="sxs-lookup"><span data-stu-id="1faa3-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="1faa3-108">Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="1faa3-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="1faa3-109">Este tópico mostra como permitir que um usuário resolva um horário ambíguo.</span><span class="sxs-lookup"><span data-stu-id="1faa3-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="1faa3-110">Permitir que o usuário resolva um horário ambíguo</span><span class="sxs-lookup"><span data-stu-id="1faa3-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="1faa3-111">Obtenha a entrada de data e hora do usuário.</span><span class="sxs-lookup"><span data-stu-id="1faa3-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="1faa3-112">Chame o método <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> para determinar se o tempo é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="1faa3-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="1faa3-113">Se o tempo for ambíguo, chame o método <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> para recuperar uma matriz de objetos <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="1faa3-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="1faa3-114">Cada elemento na matriz contém um deslocamento UTC para o qual a hora ambígua pode ser mapeada.</span><span class="sxs-lookup"><span data-stu-id="1faa3-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="1faa3-115">Permita que o usuário selecione o deslocamento desejado.</span><span class="sxs-lookup"><span data-stu-id="1faa3-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="1faa3-116">Obtenha a data e hora de UTC subtraindo o deslocamento selecionado pelo usuário do horário local.</span><span class="sxs-lookup"><span data-stu-id="1faa3-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="1faa3-117">Chame o método `static` (`Shared` no Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> para definir a propriedade <xref:System.DateTime.Kind%2A> do valor de data e hora UTC como <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1faa3-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="1faa3-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1faa3-118">Example</span></span>

<span data-ttu-id="1faa3-119">O exemplo a seguir solicita que o usuário insira uma data e hora e, se ela for ambígua, permite que o usuário selecione o horário UTC para o qual o horário ambíguo aponta.</span><span class="sxs-lookup"><span data-stu-id="1faa3-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="1faa3-120">O núcleo do código de exemplo usa uma matriz de <xref:System.TimeSpan> objetos para indicar possíveis deslocamentos do tempo ambíguo do UTC.</span><span class="sxs-lookup"><span data-stu-id="1faa3-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="1faa3-121">No entanto, esses deslocamentos provavelmente não serão significativos para o usuário.</span><span class="sxs-lookup"><span data-stu-id="1faa3-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="1faa3-122">Para esclarecer o significado dos deslocamentos, o código também observa se um deslocamento representa o horário padrão do fuso horário local ou seu horário de verão.</span><span class="sxs-lookup"><span data-stu-id="1faa3-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="1faa3-123">O código determina qual é a hora padrão e em qual horário é o horário de verão comparando o deslocamento com o valor da propriedade <xref:System.TimeZoneInfo.BaseUtcOffset%2A>.</span><span class="sxs-lookup"><span data-stu-id="1faa3-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="1faa3-124">Essa propriedade indica a diferença entre o UTC e o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="1faa3-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="1faa3-125">Neste exemplo, todas as referências ao fuso horário local são feitas por meio da propriedade <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; o fuso horário local nunca é atribuído a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="1faa3-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="1faa3-126">Essa é uma prática recomendada porque uma chamada para o método <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> invalida todos os objetos aos quais o fuso horário local está atribuído.</span><span class="sxs-lookup"><span data-stu-id="1faa3-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1faa3-127">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1faa3-127">Compiling the code</span></span>

<span data-ttu-id="1faa3-128">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1faa3-128">This example requires:</span></span>

- <span data-ttu-id="1faa3-129">Que o namespace <xref:System> seja importado com a instrução `using` ( C# obrigatória no código).</span><span class="sxs-lookup"><span data-stu-id="1faa3-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="1faa3-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1faa3-130">See also</span></span>

- [<span data-ttu-id="1faa3-131">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="1faa3-131">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="1faa3-132">Como resolver horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="1faa3-132">How to: Resolve ambiguous times</span></span>](../../../docs/standard/datetime/resolve-ambiguous-times.md)
