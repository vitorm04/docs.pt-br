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
ms.openlocfilehash: 1acd53fad6b0ab173f855850353339190ebdd893
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132538"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="b8235-102">Como usar fusos horários em aritmética de data e hora</span><span class="sxs-lookup"><span data-stu-id="b8235-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="b8235-103">Normalmente, quando você executa a aritmética de data e hora usando valores <xref:System.DateTime> ou <xref:System.DateTimeOffset>, o resultado não reflete nenhuma regra de ajuste de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b8235-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="b8235-104">Isso é verdadeiro mesmo quando o fuso horário do valor de data e hora é claramente identificável (por exemplo, quando a propriedade <xref:System.DateTime.Kind%2A> é definida como <xref:System.DateTimeKind.Local>).</span><span class="sxs-lookup"><span data-stu-id="b8235-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="b8235-105">Este tópico mostra como executar operações aritméticas em valores de data e hora que pertencem a um determinado fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b8235-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="b8235-106">Os resultados das operações aritméticas refletirão as regras de ajuste do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b8235-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="b8235-107">Para aplicar as regras de ajuste à aritmética de data e hora</span><span class="sxs-lookup"><span data-stu-id="b8235-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="b8235-108">Implemente um método de acoplamento próximo de um valor de data e hora com o fuso horário ao qual ele pertence.</span><span class="sxs-lookup"><span data-stu-id="b8235-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="b8235-109">Por exemplo, declare uma estrutura que inclui o valor de data e hora e seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b8235-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="b8235-110">O exemplo a seguir usa essa abordagem para vincular um valor de <xref:System.DateTime> com seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="b8235-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="b8235-111">Converta uma hora em UTC (tempo Universal Coordenado) chamando o método <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> ou o método <xref:System.TimeZoneInfo.ConvertTime%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8235-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="b8235-112">Execute a operação aritmética na hora UTC.</span><span class="sxs-lookup"><span data-stu-id="b8235-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="b8235-113">Converta a hora de UTC para o fuso horário associado do tempo original chamando o método <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8235-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="b8235-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8235-114">Example</span></span>

<span data-ttu-id="b8235-115">O exemplo a seguir adiciona duas horas e trinta minutos a 9 de março de 2008, à 1h30 do</span><span class="sxs-lookup"><span data-stu-id="b8235-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="b8235-116">Horário Padrão Central.</span><span class="sxs-lookup"><span data-stu-id="b8235-116">Central Standard Time.</span></span> <span data-ttu-id="b8235-117">A transição do fuso horário para o horário de verão ocorre 30 minutos depois, às 2h.</span><span class="sxs-lookup"><span data-stu-id="b8235-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="b8235-118">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="b8235-118">on March 9, 2008.</span></span> <span data-ttu-id="b8235-119">Como o exemplo segue as quatro etapas listadas na seção anterior, ele relata corretamente a hora resultante como 5h.</span><span class="sxs-lookup"><span data-stu-id="b8235-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="b8235-120">em 9 de março de 2008.</span><span class="sxs-lookup"><span data-stu-id="b8235-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="b8235-121">Os valores <xref:System.DateTime> e <xref:System.DateTimeOffset> são desassociados de qualquer fuso horário ao qual possam pertencer.</span><span class="sxs-lookup"><span data-stu-id="b8235-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="b8235-122">Para executar a aritmética de data e hora de uma maneira que aplique automaticamente as regras de ajuste de um fuso horário, o fuso horário ao qual qualquer valor de data e hora pertence deve ser imediatamente identificável.</span><span class="sxs-lookup"><span data-stu-id="b8235-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="b8235-123">Isso significa que uma data e hora e seu fuso horário associado devem estar estritamente acoplados.</span><span class="sxs-lookup"><span data-stu-id="b8235-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="b8235-124">Há várias maneiras de fazer isso, que incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b8235-124">There are several ways to do this, which include the following:</span></span>

- <span data-ttu-id="b8235-125">Supor que todas as horas usadas em um aplicativo pertencem a um fuso horário específico.</span><span class="sxs-lookup"><span data-stu-id="b8235-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="b8235-126">Embora adequada em alguns casos, essa abordagem oferece flexibilidade limitada e possivelmente portabilidade limitada.</span><span class="sxs-lookup"><span data-stu-id="b8235-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

- <span data-ttu-id="b8235-127">Definir um tipo que acople estritamente uma data e hora e seu fuso horário associado incluindo ambas como campos do tipo.</span><span class="sxs-lookup"><span data-stu-id="b8235-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="b8235-128">Essa abordagem é usada no exemplo de código, que define uma estrutura para armazenar a data e hora e o fuso horário em dois campos de membro.</span><span class="sxs-lookup"><span data-stu-id="b8235-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="b8235-129">O exemplo ilustra como executar operações aritméticas em <xref:System.DateTime> valores para que as regras de ajuste de fuso horário sejam aplicadas ao resultado.</span><span class="sxs-lookup"><span data-stu-id="b8235-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="b8235-130">No entanto, <xref:System.DateTimeOffset> valores podem ser usados com a mesma facilidade.</span><span class="sxs-lookup"><span data-stu-id="b8235-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="b8235-131">O exemplo a seguir ilustra como o código no exemplo original pode ser adaptado para usar <xref:System.DateTimeOffset> em vez de valores <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="b8235-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="b8235-132">Observe que, se essa adição for simplesmente executada no valor de <xref:System.DateTimeOffset> sem primeiro convertê-la para UTC, o resultado refletirá o ponto correto no tempo, mas seu deslocamento não refletirá o fuso horário designado para esse período.</span><span class="sxs-lookup"><span data-stu-id="b8235-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b8235-133">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b8235-133">Compiling the code</span></span>

<span data-ttu-id="b8235-134">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b8235-134">This example requires:</span></span>

- <span data-ttu-id="b8235-135">Que o namespace <xref:System> seja importado com a instrução `using` ( C# obrigatória no código).</span><span class="sxs-lookup"><span data-stu-id="b8235-135">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8235-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8235-136">See also</span></span>

- [<span data-ttu-id="b8235-137">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="b8235-137">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="b8235-138">Executando operações aritméticas com datas e horas</span><span class="sxs-lookup"><span data-stu-id="b8235-138">Performing arithmetic operations with dates and times</span></span>](../../../docs/standard/datetime/performing-arithmetic-operations.md)
