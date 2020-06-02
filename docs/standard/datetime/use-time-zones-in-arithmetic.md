---
title: Como usar fusos horários em aritmética de data e hora
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
ms.openlocfilehash: af19145f7caa9dbe8630ae7593734769e98720d0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280914"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="6d1eb-102">Como usar fusos horários em aritmética de data e hora</span><span class="sxs-lookup"><span data-stu-id="6d1eb-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="6d1eb-103">Normalmente, quando você executa cálculos de data e hora <xref:System.DateTime> usando <xref:System.DateTimeOffset> valores ou, o resultado não reflete nenhuma regra de ajuste de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="6d1eb-104">Isso é verdadeiro mesmo quando o fuso horário do valor de data e hora é claramente identificável (por exemplo, quando a <xref:System.DateTime.Kind%2A> propriedade é definida como <xref:System.DateTimeKind.Local> ).</span><span class="sxs-lookup"><span data-stu-id="6d1eb-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="6d1eb-105">Este tópico mostra como executar operações aritméticas em valores de data e hora que pertencem a um determinado fuso horário.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="6d1eb-106">Os resultados das operações aritméticas refletirão as regras de ajuste do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="6d1eb-107">Para aplicar as regras de ajuste à aritmética de data e hora</span><span class="sxs-lookup"><span data-stu-id="6d1eb-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="6d1eb-108">Implemente um método de acoplamento próximo de um valor de data e hora com o fuso horário ao qual ele pertence.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="6d1eb-109">Por exemplo, declare uma estrutura que inclui o valor de data e hora e seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="6d1eb-110">O exemplo a seguir usa essa abordagem para vincular um <xref:System.DateTime> valor com seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="6d1eb-111">Converta uma hora em UTC (tempo Universal Coordenado) chamando o <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> método ou o <xref:System.TimeZoneInfo.ConvertTime%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="6d1eb-112">Execute a operação aritmética na hora UTC.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="6d1eb-113">Converta a hora de UTC para o fuso horário associado do tempo original chamando o <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="6d1eb-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d1eb-114">Example</span></span>

<span data-ttu-id="6d1eb-115">O exemplo a seguir adiciona duas horas e trinta minutos a 9 de março de 2008, à 1h30 do</span><span class="sxs-lookup"><span data-stu-id="6d1eb-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="6d1eb-116">Horário Padrão Central.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-116">Central Standard Time.</span></span> <span data-ttu-id="6d1eb-117">A transição do fuso horário para o horário de verão ocorre 30 minutos depois, às 2h.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="6d1eb-118">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-118">on March 9, 2008.</span></span> <span data-ttu-id="6d1eb-119">Como o exemplo segue as quatro etapas listadas na seção anterior, ele relata corretamente a hora resultante como 5h.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="6d1eb-120">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="6d1eb-121">Os <xref:System.DateTime> <xref:System.DateTimeOffset> valores e são desassociados de qualquer fuso horário ao qual possam pertencer.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="6d1eb-122">Para executar a aritmética de data e hora de uma maneira que aplique automaticamente as regras de ajuste de um fuso horário, o fuso horário ao qual qualquer valor de data e hora pertence deve ser imediatamente identificável.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="6d1eb-123">Isso significa que uma data e hora e seu fuso horário associado devem estar estritamente acoplados.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="6d1eb-124">Há várias maneiras de fazer isso, que incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6d1eb-124">There are several ways to do this, which include the following:</span></span>

- <span data-ttu-id="6d1eb-125">Supor que todas as horas usadas em um aplicativo pertencem a um fuso horário específico.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="6d1eb-126">Embora adequada em alguns casos, essa abordagem oferece flexibilidade limitada e possivelmente portabilidade limitada.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

- <span data-ttu-id="6d1eb-127">Definir um tipo que acople estritamente uma data e hora e seu fuso horário associado incluindo ambas como campos do tipo.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="6d1eb-128">Essa abordagem é usada no exemplo de código, que define uma estrutura para armazenar a data e hora e o fuso horário em dois campos de membro.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="6d1eb-129">O exemplo ilustra como executar operações aritméticas em <xref:System.DateTime> valores para que as regras de ajuste de fuso horário sejam aplicadas ao resultado.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="6d1eb-130">No entanto, <xref:System.DateTimeOffset> os valores podem ser usados com a mesma facilidade.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="6d1eb-131">O exemplo a seguir ilustra como o código no exemplo original pode ser adaptado para uso <xref:System.DateTimeOffset> em vez de <xref:System.DateTime> valores.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="6d1eb-132">Observe que, se essa adição for simplesmente executada no <xref:System.DateTimeOffset> valor sem primeiro convertê-la para UTC, o resultado refletirá o ponto correto no tempo, mas seu deslocamento não refletirá o fuso horário designado para esse tempo.</span><span class="sxs-lookup"><span data-stu-id="6d1eb-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="6d1eb-133">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6d1eb-133">Compiling the code</span></span>

<span data-ttu-id="6d1eb-134">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6d1eb-134">This example requires:</span></span>

- <span data-ttu-id="6d1eb-135">Que o <xref:System> namespace seja importado com a `using` instrução (necessária no código C#).</span><span class="sxs-lookup"><span data-stu-id="6d1eb-135">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d1eb-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="6d1eb-136">See also</span></span>

- [<span data-ttu-id="6d1eb-137">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="6d1eb-137">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="6d1eb-138">Executando operações aritméticas com datas e horas</span><span class="sxs-lookup"><span data-stu-id="6d1eb-138">Performing arithmetic operations with dates and times</span></span>](performing-arithmetic-operations.md)
