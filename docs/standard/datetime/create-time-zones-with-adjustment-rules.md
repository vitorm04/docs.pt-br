---
title: "Como: criar fusos horários com regras de ajuste"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75e1867e810090bf35a0dfc7def5785747f94382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="9c4eb-102">Como: criar fusos horários com regras de ajuste</span><span class="sxs-lookup"><span data-stu-id="9c4eb-102">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="9c4eb-103">As informações de fuso horário preciso exigidas por um aplicativo podem não estar presentes em um determinado sistema por vários motivos:</span><span class="sxs-lookup"><span data-stu-id="9c4eb-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="9c4eb-104">O fuso horário nunca foi definido no registro do sistema local.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="9c4eb-105">Dados sobre o fuso horário foi modificados ou removidos do registro.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="9c4eb-106">O fuso horário não tem informações precisas sobre ajustes de fuso horário para um período específico do histórico.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-106">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="9c4eb-107">Nesses casos, você pode chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método para definir o fuso horário exigido pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="9c4eb-108">Você pode usar as sobrecargas do método para criar um fuso horário com ou sem regras de ajuste.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="9c4eb-109">Se o fuso horário dá suporte ao horário de verão, você pode definir ajustes com a regras de ajuste fixo ou flutuante.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="9c4eb-110">(Para obter definições desses termos, consulte a seção "Terminologia de fuso horário" [visão geral de fuso horário](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="9c4eb-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c4eb-111">Fusos horários personalizados criados ao chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método não são adicionados ao registro.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="9c4eb-112">Em vez disso, eles podem ser acessados apenas pela referência de objeto retornada pelo <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> chamada de método.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="9c4eb-113">Este tópico mostra como criar um fuso horário com regras de ajuste.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-113">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="9c4eb-114">Para criar um fuso horário que não oferece suporte a regras de ajuste de horário de verão, consulte [como: criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="9c4eb-114">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="9c4eb-115">Para criar um fuso horário com regras de ajuste flutuantes</span><span class="sxs-lookup"><span data-stu-id="9c4eb-115">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="9c4eb-116">Para cada ajuste (isto é, para cada transição de e para a hora padrão de volta em um intervalo de tempo específico), faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9c4eb-116">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="9c4eb-117">Defina o tempo de transição inicial para o ajuste de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-117">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="9c4eb-118">Você deve chamar o <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> método e passá-lo um <xref:System.DateTime> valor que define o tempo de transição, um valor inteiro que define o mês de transição, um valor inteiro que define a semana em que ocorre a transição, e um <xref:System.DayOfWeek> valor que define o dia da semana em que ocorre a transição.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-118">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="9c4eb-119">Esta chamada de método instancia um <xref:System.TimeZoneInfo.TransitionTime> objeto.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-119">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="9c4eb-120">Defina o tempo de transição final para o ajuste de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-120">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="9c4eb-121">Isso requer uma outra chamada para o <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-121">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9c4eb-122">Esta chamada de método instancia um segundo <xref:System.TimeZoneInfo.TransitionTime> objeto.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-122">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="9c4eb-123">Chamar o <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> método e passá-lo a efetivo datas de início e término do ajuste, um <xref:System.TimeSpan> objeto que define a quantidade de tempo na transição e os dois <xref:System.TimeZoneInfo.TransitionTime> objetos que definem quando as transições para e de verão hora de ocorrer.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-123">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="9c4eb-124">Esta chamada de método instancia um <xref:System.TimeZoneInfo.AdjustmentRule> objeto.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-124">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="9c4eb-125">Atribuir o <xref:System.TimeZoneInfo.AdjustmentRule> objeto para uma matriz de <xref:System.TimeZoneInfo.AdjustmentRule> objetos.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-125">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="9c4eb-126">Defina nome para exibição do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-126">Define the time zone's display name.</span></span> <span data-ttu-id="9c4eb-127">O nome para exibição segue um formato razoavelmente padrão no qual o deslocamento do fuso horário do tempo Universal Coordenado (UTC) é colocado entre parênteses e é seguido por uma cadeia de caracteres que identifica o fuso horário, uma ou mais das cidades no fuso horário ou um ou mais do cou ntries ou regiões no fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-127">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="9c4eb-128">Defina o nome do padrão de tempo do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-128">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="9c4eb-129">Normalmente, essa cadeia de caracteres também é usada como identificador do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-129">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="9c4eb-130">Defina o nome do horário de verão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-130">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="9c4eb-131">Se você quiser usar um identificador diferente do nome padrão do fuso horário, defina o identificador de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-131">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="9c4eb-132">Criar uma instância de um <xref:System.TimeSpan> objeto que define o deslocamento do fuso horário do UTC.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-132">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="9c4eb-133">Fusos horários com horários posteriores ao UTC têm um deslocamento positivo.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-133">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="9c4eb-134">Fusos horários com horários anteriores ao UTC têm um deslocamento negativo.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-134">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="9c4eb-135">Chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> método para instanciar o novo fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-135">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="9c4eb-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c4eb-136">Example</span></span>

<span data-ttu-id="9c4eb-137">O exemplo a seguir define um fuso horário padrão Central para os Estados Unidos que inclui as regras de ajuste para uma variedade de intervalos de tempo desde 1918 atual.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-137">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="9c4eb-138">O fuso horário criado nesse exemplo tem várias regras de ajuste.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-138">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="9c4eb-139">Deve-se ter cuidado para garantir que o efetivo datas de início e fim de qualquer regra de ajuste não se sobrepõem com as datas de outra regra de ajuste.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-139">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="9c4eb-140">Se houver uma sobreposição, um <xref:System.InvalidTimeZoneException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-140">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="9c4eb-141">Para regras de ajuste flutuantes, o valor 5 é passado para o `week` parâmetro o <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> método para indicar que a transição ocorre na última semana de um mês específico.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-141">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="9c4eb-142">Na criação da matriz de <xref:System.TimeZoneInfo.AdjustmentRule> objetos para usar no <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> chamada de método, o código foi possível inicializar a matriz para o tamanho exigido pelo número de ajustes a serem criados para o fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-142">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="9c4eb-143">Em vez disso, este exemplo de código chama o <xref:System.Collections.Generic.List%601.Add%2A> método para adicionar cada regra de ajuste para um genérico <xref:System.Collections.Generic.List%601> coleção de <xref:System.TimeZoneInfo.AdjustmentRule> objetos.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-143">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="9c4eb-144">O código, em seguida, chama o <xref:System.Collections.Generic.List%601.CopyTo%2A> método para copiar os membros dessa coleção para a matriz.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-144">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="9c4eb-145">O exemplo também usa o <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> método para definir ajustes com data fixa.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-145">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="9c4eb-146">Isso é semelhante a chamar o <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> método, exceto que ele requer somente a hora, mês e dia dos parâmetros de transição.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-146">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="9c4eb-147">O exemplo pode ser testado usando código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9c4eb-147">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="9c4eb-148">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9c4eb-148">Compiling the code</span></span>

<span data-ttu-id="9c4eb-149">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9c4eb-149">This example requires:</span></span>

* <span data-ttu-id="9c4eb-150">Que uma referência a System.Core.dll seja adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-150">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="9c4eb-151">Se os namespaces a seguir sejam importados:</span><span class="sxs-lookup"><span data-stu-id="9c4eb-151">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="9c4eb-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c4eb-152">See also</span></span>

<span data-ttu-id="9c4eb-153">[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[visão geral de fuso horário](../../../docs/standard/datetime/time-zone-overview.md)
[como: criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="9c4eb-153">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span></span>
