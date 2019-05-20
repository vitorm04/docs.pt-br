---
title: Heap de objeto grande em sistemas Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebe856b3ed904b13201c6d59752a8a00f4060d5d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753959"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="c8d92-102">Heap de objeto grande em sistemas Windows</span><span class="sxs-lookup"><span data-stu-id="c8d92-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="c8d92-103">O GC (Coletor de Lixo) do .NET divide os objetos em objetos pequenos e grandes.</span><span class="sxs-lookup"><span data-stu-id="c8d92-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="c8d92-104">Quando um objeto é grande, alguns de seus atributos se tornam mais significativos do que se o objeto for pequeno.</span><span class="sxs-lookup"><span data-stu-id="c8d92-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="c8d92-105">Por exemplo, sua compactação – ou seja, copiá-lo na memória em outro lugar do heap – pode ser cara.</span><span class="sxs-lookup"><span data-stu-id="c8d92-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="c8d92-106">Por isso, o Coletor de Lixo do .NET coloca objetos grandes no LOH (heap de objeto grande).</span><span class="sxs-lookup"><span data-stu-id="c8d92-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="c8d92-107">Neste tópico, examinaremos o heap de objeto grande em detalhes.</span><span class="sxs-lookup"><span data-stu-id="c8d92-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="c8d92-108">Falaremos sobre o que qualifica um objeto como objeto grande, como esses objetos grandes são coletados e que tipo de implicações de desempenho que os objetos grandes impõem.</span><span class="sxs-lookup"><span data-stu-id="c8d92-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8d92-109">Este tópico aborda o heap de objeto grande no .NET Framework e no .NET Core em execução somente em sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="c8d92-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="c8d92-110">Não aborda o LOH em execução em implementações do .NET em outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="c8d92-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="c8d92-111">Como um objeto termina no heap de objeto grande e ele é manipulado pelo GC</span><span class="sxs-lookup"><span data-stu-id="c8d92-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="c8d92-112">Se um objeto for maior que ou igual a 85.000 bytes, ele será considerado um objeto grande.</span><span class="sxs-lookup"><span data-stu-id="c8d92-112">If an object is greater than or equal to 85,000 bytes, it’s considered a large object.</span></span> <span data-ttu-id="c8d92-113">Esse número foi determinado por ajuste de desempenho.</span><span class="sxs-lookup"><span data-stu-id="c8d92-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="c8d92-114">Quando uma solicitação de alocação de objeto for de 85.000 ou mais bytes, o tempo de execução a alocará no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="c8d92-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="c8d92-115">Para entender o que isso significa, é útil examinar alguns conceitos básicos sobre o GC do .NET.</span><span class="sxs-lookup"><span data-stu-id="c8d92-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="c8d92-116">O Coletor de Lixo do .NET é um coletor de gerações.</span><span class="sxs-lookup"><span data-stu-id="c8d92-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="c8d92-117">Ele tem três gerações: geração 0, geração 1 e geração 2.</span><span class="sxs-lookup"><span data-stu-id="c8d92-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="c8d92-118">O motivo para ter 3 gerações é que, em um aplicativo bem ajustado, a maioria dos objetos morre na gen0.</span><span class="sxs-lookup"><span data-stu-id="c8d92-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="c8d92-119">Por exemplo, em um aplicativo para servidor, as alocações associadas a cada solicitação devem morrer após a conclusão da solicitação.</span><span class="sxs-lookup"><span data-stu-id="c8d92-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="c8d92-120">As solicitações de alocação em andamento chegarão à gen1 e morrerão lá.</span><span class="sxs-lookup"><span data-stu-id="c8d92-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="c8d92-121">Essencialmente, a gen1 atua como um buffer entre áreas de objetos jovens e áreas de objetos de vida longa.</span><span class="sxs-lookup"><span data-stu-id="c8d92-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="c8d92-122">Objetos pequenos sempre são alocados na geração 0 e, dependendo de seu tempo de vida, podem ser promovidos à geração 1 ou geração 2.</span><span class="sxs-lookup"><span data-stu-id="c8d92-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="c8d92-123">Objetos grandes sempre são alocados na geração 2.</span><span class="sxs-lookup"><span data-stu-id="c8d92-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="c8d92-124">Os objetos grandes pertencem à geração 2 porque são coletados apenas durante uma coleta de geração 2.</span><span class="sxs-lookup"><span data-stu-id="c8d92-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="c8d92-125">Quando uma geração é coletada, todas as suas gerações mais jovens também são coletadas.</span><span class="sxs-lookup"><span data-stu-id="c8d92-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="c8d92-126">Por exemplo, quando ocorre uma GC de geração 1, as gerações 1 e 0 são coletadas.</span><span class="sxs-lookup"><span data-stu-id="c8d92-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="c8d92-127">E quando ocorre uma GC de geração 2, todo o heap é coletado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="c8d92-128">Por esse motivo, um GC de geração 2 também é chamado de *GC completo*.</span><span class="sxs-lookup"><span data-stu-id="c8d92-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="c8d92-129">Este artigo se refere ao GC de geração 2, em vez de ao GC completo, mas os termos são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="c8d92-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="c8d92-130">Gerações fornecem uma exibição lógica do heap de GC.</span><span class="sxs-lookup"><span data-stu-id="c8d92-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="c8d92-131">Fisicamente, os objetos residem em segmentos de heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c8d92-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="c8d92-132">Um *segmento de heap gerenciado* é um bloco de memória que o GC reserva do sistema operacional chamando a [função VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) em nome do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="c8d92-133">Quando o CLR é carregado, o GC aloca dois segmentos de heap iniciais: um para objetos pequenos (o Heap de Objeto Pequeno ou SOH) e outro para objetos grandes (o Heap de Objeto Grande).</span><span class="sxs-lookup"><span data-stu-id="c8d92-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the Small Object Heap, or SOH), and one for large objects (the Large Object Heap).</span></span>

<span data-ttu-id="c8d92-134">As solicitações de alocação são então atendidas colocando os objetos gerenciados em um desses segmentos de heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="c8d92-135">Se o objeto for menor que 85.000 bytes, ele será colocado no segmento de SOH; caso contrário, ele será colocado em um segmento de LOH.</span><span class="sxs-lookup"><span data-stu-id="c8d92-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="c8d92-136">Os segmentos são confirmados (em blocos menores) à medida que mais objetos são alocados a eles.</span><span class="sxs-lookup"><span data-stu-id="c8d92-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="c8d92-137">Para o SOH, os objetos que sobrevivem a um GC são promovidos para a próxima geração.</span><span class="sxs-lookup"><span data-stu-id="c8d92-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="c8d92-138">Os objetos que sobrevivem a uma coleta de geração 0 são considerados objetos de geração 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c8d92-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="c8d92-139">No entanto, os objetos que sobrevivem à geração mais antiga ainda serão considerados como estando na geração mais antiga.</span><span class="sxs-lookup"><span data-stu-id="c8d92-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="c8d92-140">Em outras palavras, os sobreviventes da geração 2 são objetos de geração 2; e os sobreviventes de LOH são objetos LOH (que são coletados com a gen2).</span><span class="sxs-lookup"><span data-stu-id="c8d92-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="c8d92-141">O código do usuário pode alocar apenas na geração 0 (objetos pequenos) ou no LOH (objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="c8d92-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="c8d92-142">Apenas o GC pode "alocar" objetos na geração 1 (promovendo os sobreviventes da geração 0) e na geração 2 (promovendo os sobreviventes das gerações 1 e 2).</span><span class="sxs-lookup"><span data-stu-id="c8d92-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="c8d92-143">Quando uma coleta de lixo é disparada, o GC rastreia pelos objetos vivos e os compacta.</span><span class="sxs-lookup"><span data-stu-id="c8d92-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="c8d92-144">Mas como a compactação é cara, o GC *varre* o LOH; faz uma lista livre de objetos mortos que podem ser reutilizados mais tarde para atender a solicitações de alocação de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="c8d92-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="c8d92-145">Objetos mortos adjacentes são transformados em um objeto livre.</span><span class="sxs-lookup"><span data-stu-id="c8d92-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="c8d92-146">O .NET Core e o .NET Framework (do .NET Framework 4.5.1 em diante) incluem a propriedade <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType>, que permite aos usuários especificar que o LOH deve ser compactado durante o próximo GC de bloqueio completo.</span><span class="sxs-lookup"><span data-stu-id="c8d92-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="c8d92-147">No futuro, o .NET pode optar por compactar o LOH automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c8d92-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="c8d92-148">Isso significa que, se você aloca objetos grandes e deseja ter certeza de que eles não se moverão, você ainda deve fixá-los.</span><span class="sxs-lookup"><span data-stu-id="c8d92-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="c8d92-149">A Figura 1 ilustra um cenário em que o GC forma a geração 1 após o primeiro GC de geração 0, em que `Obj1` e `Obj3` estão mortos, e forma a geração 2 após o primeiro GC de geração 1, em que `Obj2` e `Obj5` estão mortos.</span><span class="sxs-lookup"><span data-stu-id="c8d92-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="c8d92-150">Observe que isso e as figuras a seguir são apenas para fins de ilustração; elas contêm muito poucos objetos para mostrar melhor o que acontece no heap.</span><span class="sxs-lookup"><span data-stu-id="c8d92-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="c8d92-151">Na verdade, muitos mais objetos normalmente estão envolvidos em um GC.</span><span class="sxs-lookup"><span data-stu-id="c8d92-151">In reality, many more objects are typically involved in a GC.</span></span>

![Figura 1: Um GC ger. 0 e um GC ger. 1](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="c8d92-153">Figura 1: Um GC geração 0 e um GC geração 1.</span><span class="sxs-lookup"><span data-stu-id="c8d92-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="c8d92-154">A Figura 2 mostra que depois de um GC de geração 2 que observou que `Obj1` e `Obj2` estão mortos, o GC forma um espaço livre contíguo fora da memória que costumava ser ocupado por `Obj1` e `Obj2`, que foi então usado para atender a uma solicitação de alocação para `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="c8d92-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="c8d92-155">O espaço após o último objeto, `Obj3`, ao final do segmento também pode ser usado para atender a solicitações de alocação.</span><span class="sxs-lookup"><span data-stu-id="c8d92-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Figura 2: Depois de um GC ger. 2](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="c8d92-157">Figura 2: Depois de um GC geração 2</span><span class="sxs-lookup"><span data-stu-id="c8d92-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="c8d92-158">Se não houver espaço livre suficiente para acomodar as solicitações de alocação de objeto grande, o GC primeiro tentará adquirir mais segmentos do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c8d92-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="c8d92-159">Se isso falhar, ele disparará um GC de geração 2 na esperança de liberar algum espaço.</span><span class="sxs-lookup"><span data-stu-id="c8d92-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="c8d92-160">Durante um GC de geração 1 ou 2, o coletor de lixo libera segmentos que não contêm objetos vivos novamente para o sistema operacional chamando a [função VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span><span class="sxs-lookup"><span data-stu-id="c8d92-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="c8d92-161">O espaço após o último objeto vivo até o final do segmento tem a confirmação anulada (exceto no segmento efêmero em que gen0/gen1 vivem, em que o coletor de lixo mantém alguns confirmados, porque o aplicativo alocará nele imediatamente).</span><span class="sxs-lookup"><span data-stu-id="c8d92-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="c8d92-162">E os espaços livres permanecem confirmados, embora estejam redefinidos, o que significa que o sistema operacional não precisa gravar dados neles novamente em disco.</span><span class="sxs-lookup"><span data-stu-id="c8d92-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="c8d92-163">Como o LOH é coletado apenas durante os GCs de geração 2, o segmento de LOH só pode ser liberado durante um desses GCs.</span><span class="sxs-lookup"><span data-stu-id="c8d92-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="c8d92-164">A Figura 3 ilustra um cenário em que o coletor de lixo libera um segmento (segmento 2) novamente para o sistema operacional e anula a confirmação de mais espaço nos segmentos restantes.</span><span class="sxs-lookup"><span data-stu-id="c8d92-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="c8d92-165">Se ele precisar usar o espaço com anulação de confirmação no final do segmento para atender a solicitações de alocação de objeto grande, ele confirmará a memória novamente.</span><span class="sxs-lookup"><span data-stu-id="c8d92-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="c8d92-166">(Para obter uma explicação da confirmação/anulação de confirmação, confira a documentação do [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).)</span><span class="sxs-lookup"><span data-stu-id="c8d92-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Figura 3: LOH depois de um GC ger. 2](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="c8d92-168">Figura 3: LOH depois de um GC geração 2</span><span class="sxs-lookup"><span data-stu-id="c8d92-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="c8d92-169">Quando um objeto grande é coletado?</span><span class="sxs-lookup"><span data-stu-id="c8d92-169">When is a large object collected?</span></span>

<span data-ttu-id="c8d92-170">Em geral, um GC ocorre quando uma das seguintes três condições ocorre:</span><span class="sxs-lookup"><span data-stu-id="c8d92-170">In general, a GC occurs when one of the following 3 conditions happens:</span></span>

- <span data-ttu-id="c8d92-171">A alocação excede o limite de objeto grande ou de geração 0.</span><span class="sxs-lookup"><span data-stu-id="c8d92-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="c8d92-172">O limite é uma propriedade de uma geração.</span><span class="sxs-lookup"><span data-stu-id="c8d92-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="c8d92-173">Um limite para uma geração é definido quando o coletor de lixo aloca objetos nele.</span><span class="sxs-lookup"><span data-stu-id="c8d92-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="c8d92-174">Quando o limite é excedido, um GC é disparado nessa geração.</span><span class="sxs-lookup"><span data-stu-id="c8d92-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="c8d92-175">Quando você aloca objetos pequenos ou grandes, consome os limites da geração 0 e do LOH, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c8d92-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="c8d92-176">Quando o coletor de lixo aloca na geração 1 e 2, ele consome seus limites.</span><span class="sxs-lookup"><span data-stu-id="c8d92-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="c8d92-177">Esses limites são dinamicamente ajustados à medida que o programa é executado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="c8d92-178">Esse é o caso típico; a maioria dos GCs ocorre por causa de alocações no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="c8d92-179">O método <xref:System.GC.Collect%2A?displayProperty=nameWithType> é chamado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="c8d92-180">Se o método <xref:System.GC.Collect?displayProperty=nameWithType> sem parâmetros é chamado ou outra sobrecarga recebe <xref:System.GC.MaxGeneration?displayProperty=nameWithType> como argumento, o LOH é coletado juntamente com o restante do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="c8d92-181">O sistema está em situação de pouca memória.</span><span class="sxs-lookup"><span data-stu-id="c8d92-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="c8d92-182">Isso ocorre quando o coletor de lixo recebe uma notificação de memória alta do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c8d92-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="c8d92-183">Se o coletor de lixo considera que fazer um GC de geração 2 será produtivo, ele disparará um.</span><span class="sxs-lookup"><span data-stu-id="c8d92-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="c8d92-184">Implicações de desempenho de LOH</span><span class="sxs-lookup"><span data-stu-id="c8d92-184">LOH Performance Implications</span></span>

<span data-ttu-id="c8d92-185">As alocações no heap de objeto grande afetam o desempenho das maneiras mostradas a seguir.</span><span class="sxs-lookup"><span data-stu-id="c8d92-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="c8d92-186">Custo de alocação.</span><span class="sxs-lookup"><span data-stu-id="c8d92-186">Allocation cost.</span></span>

  <span data-ttu-id="c8d92-187">O CLR garante que a memória de cada novo objeto fornecido é apagada.</span><span class="sxs-lookup"><span data-stu-id="c8d92-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="c8d92-188">Isso significa que o custo de alocação de um objeto grande é completamente dominado pela limpeza da memória (a menos que ela dispare um GC).</span><span class="sxs-lookup"><span data-stu-id="c8d92-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="c8d92-189">Se levar dois ciclos para apagar um byte, serão necessários 170.000 ciclos para apagar o menor objeto grande.</span><span class="sxs-lookup"><span data-stu-id="c8d92-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="c8d92-190">A limpeza da memória de um objeto de 16 MB em um computador de 2 GHz leva aproximadamente 16 ms.</span><span class="sxs-lookup"><span data-stu-id="c8d92-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="c8d92-191">É um custo muito alto.</span><span class="sxs-lookup"><span data-stu-id="c8d92-191">That's a rather large cost.</span></span>

- <span data-ttu-id="c8d92-192">Custo da coleção.</span><span class="sxs-lookup"><span data-stu-id="c8d92-192">Collection cost.</span></span>

  <span data-ttu-id="c8d92-193">Como o LOH e a geração 2 são coletados juntos, se o limites de um dos dois for excedido, uma coleta de geração 2 será disparada.</span><span class="sxs-lookup"><span data-stu-id="c8d92-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="c8d92-194">Se uma coleta de geração 2 for disparada devido ao LOH, a geração 2 não necessariamente será muito menor após o GC.</span><span class="sxs-lookup"><span data-stu-id="c8d92-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="c8d92-195">Se não houver muitos dados na geração 2, isso terá um impacto mínimo.</span><span class="sxs-lookup"><span data-stu-id="c8d92-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="c8d92-196">Mas se a geração 2 for grande, ela poderá causar problemas de desempenho se muitos GCs de geração 2 forem disparados.</span><span class="sxs-lookup"><span data-stu-id="c8d92-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="c8d92-197">Se vários objetos grandes forem alocados de forma muito temporária e você tiver um SOH grande, você poderá gastar muito tempo realizando GCs.</span><span class="sxs-lookup"><span data-stu-id="c8d92-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="c8d92-198">Além disso, o custo de alocação poderá realmente aumentar se você continuar alocando e liberando objetos muito grandes.</span><span class="sxs-lookup"><span data-stu-id="c8d92-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="c8d92-199">Elementos de matriz com tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="c8d92-199">Array elements with reference types.</span></span>

  <span data-ttu-id="c8d92-200">Objetos muito grandes no LOH são normalmente matrizes (é muito raro ter um objeto de instância que seja realmente muito grande).</span><span class="sxs-lookup"><span data-stu-id="c8d92-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="c8d92-201">Se os elementos de uma matriz forem ricos em referência, ela resultará em um custo que não está presente se os elementos não forem ricos em referência.</span><span class="sxs-lookup"><span data-stu-id="c8d92-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="c8d92-202">Se o elemento não contiver nenhuma referência, o coletor de lixo não precisará percorrer a matriz.</span><span class="sxs-lookup"><span data-stu-id="c8d92-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="c8d92-203">Por exemplo, se você usa uma matriz para armazenar nós em uma árvore binária, uma maneira de implementar é se referir ao nó direito e esquerdo de um nó pelos nós reais:</span><span class="sxs-lookup"><span data-stu-id="c8d92-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="c8d92-204">Se `num_nodes` for grande, o coletor de lixo precisará percorrer, pelo menos, duas referências por elemento.</span><span class="sxs-lookup"><span data-stu-id="c8d92-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="c8d92-205">Uma abordagem alternativa é armazenar o índice dos nós direito e esquerdo:</span><span class="sxs-lookup"><span data-stu-id="c8d92-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="c8d92-206">Em vez de referenciar os dados do nó esquerdo como `left.d`, você se referirá a eles como `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="c8d92-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="c8d92-207">Além disso, o coletor de lixo não precisa examinar nenhuma referência dos nós esquerdo e direito.</span><span class="sxs-lookup"><span data-stu-id="c8d92-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="c8d92-208">Entre os três fatores, os dois primeiros são geralmente mais significativos do que o terceiro.</span><span class="sxs-lookup"><span data-stu-id="c8d92-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="c8d92-209">Por isso, recomendamos que você aloque um pool de objetos grandes que você reutilizará em vez de alocar temporários.</span><span class="sxs-lookup"><span data-stu-id="c8d92-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="c8d92-210">Coletando dados de desempenho para o LOH</span><span class="sxs-lookup"><span data-stu-id="c8d92-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="c8d92-211">Antes de coletar dados de desempenho para uma área específica, você deverá já ter feito o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c8d92-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="c8d92-212">Encontrar evidência de que você deve observar essa área.</span><span class="sxs-lookup"><span data-stu-id="c8d92-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="c8d92-213">Ter esgotado outras áreas conhecidas sem encontrar algo que poderia explicar o problema de desempenho observado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="c8d92-214">Visite o blog [Entender o problema antes de tentar encontrar uma solução](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) para obter mais informações sobre os conceitos básicos sobre memória e CPU.</span><span class="sxs-lookup"><span data-stu-id="c8d92-214">See the blog [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="c8d92-215">Use as seguintes ferramentas para coletar dados sobre o desempenho de LOH:</span><span class="sxs-lookup"><span data-stu-id="c8d92-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="c8d92-216">Contadores de desempenho da memória do CLR do .NET</span><span class="sxs-lookup"><span data-stu-id="c8d92-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="c8d92-217">Eventos ETW</span><span class="sxs-lookup"><span data-stu-id="c8d92-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="c8d92-218">Um depurador</span><span class="sxs-lookup"><span data-stu-id="c8d92-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="c8d92-219">Contadores de Desempenho da Memória do CLR do .NET</span><span class="sxs-lookup"><span data-stu-id="c8d92-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="c8d92-220">Esses contadores de desempenho geralmente são uma boa primeira etapa na investigação de problemas de desempenho (embora recomendamos que você use [eventos ETW](#etw-events)).</span><span class="sxs-lookup"><span data-stu-id="c8d92-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="c8d92-221">Configure o Monitor de Desempenho adicionando os contadores desejados, como mostra a Figura 4.</span><span class="sxs-lookup"><span data-stu-id="c8d92-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="c8d92-222">Aqueles que são relevantes para o LOH são:</span><span class="sxs-lookup"><span data-stu-id="c8d92-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="c8d92-223">**Coletas de Geração 2**</span><span class="sxs-lookup"><span data-stu-id="c8d92-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="c8d92-224">Exibe o número de vezes que os GCs de geração 2 ocorreram desde o início do processo.</span><span class="sxs-lookup"><span data-stu-id="c8d92-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="c8d92-225">O contador é incrementado no final de uma coleta de geração 2 (também conhecida como uma coleta de lixo completa).</span><span class="sxs-lookup"><span data-stu-id="c8d92-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="c8d92-226">Esse contador exibe o último valor observado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="c8d92-227">**Tamanho de heap de Objeto Grande**</span><span class="sxs-lookup"><span data-stu-id="c8d92-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="c8d92-228">Exibe o tamanho atual, em bytes, incluindo o espaço livre, de LOH.</span><span class="sxs-lookup"><span data-stu-id="c8d92-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="c8d92-229">Esse contador é atualizado no final de uma coleta de lixo e não em cada alocação.</span><span class="sxs-lookup"><span data-stu-id="c8d92-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="c8d92-230">Uma maneira comum de examinar contadores de desempenho é com o Monitor de Desempenho (perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="c8d92-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="c8d92-231">Use "Adicionar Contadores" para adicionar o contador interessante a processos de seu interesse.</span><span class="sxs-lookup"><span data-stu-id="c8d92-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="c8d92-232">Você pode salvar os dados do contador de desempenho em um arquivo de log como mostra a Figura 4:</span><span class="sxs-lookup"><span data-stu-id="c8d92-232">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="c8d92-233">![Captura de tela que mostra a adição de contadores de desempenho.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="c8d92-233">![Screenshow that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="c8d92-234">Figura 4: LOH depois de um GC geração 2</span><span class="sxs-lookup"><span data-stu-id="c8d92-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="c8d92-235">Os contadores de desempenho também podem ser consultados de forma programática.</span><span class="sxs-lookup"><span data-stu-id="c8d92-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="c8d92-236">Várias pessoas os coletam dessa maneira como parte de seu processo de teste de rotina.</span><span class="sxs-lookup"><span data-stu-id="c8d92-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="c8d92-237">Quando elas identificam contadores com valores fora do comum, elas usam outro meio de obter dados mais detalhados para ajudar na investigação.</span><span class="sxs-lookup"><span data-stu-id="c8d92-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="c8d92-238">Recomendamos o uso de eventos ETW em vez de contadores de desempenho, pois o ETW fornece informações muito mais sofisticadas.</span><span class="sxs-lookup"><span data-stu-id="c8d92-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="c8d92-239">eventos ETW</span><span class="sxs-lookup"><span data-stu-id="c8d92-239">ETW events</span></span>

<span data-ttu-id="c8d92-240">O coletor de lixo fornece um conjunto rico de eventos ETW para ajudá-lo a entender o que o heap está fazendo e por quê.</span><span class="sxs-lookup"><span data-stu-id="c8d92-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="c8d92-241">As seguintes postagens no blog mostram como coletar e entender eventos GC com o ETW:</span><span class="sxs-lookup"><span data-stu-id="c8d92-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="c8d92-242">Eventos ETW de GC – 1</span><span class="sxs-lookup"><span data-stu-id="c8d92-242">GC ETW Events - 1</span></span>](https://blogs.msdn.microsoft.com/maoni/2014/12/22/gc-etw-events-1/)

- [<span data-ttu-id="c8d92-243">Eventos ETW de GC – 2</span><span class="sxs-lookup"><span data-stu-id="c8d92-243">GC ETW Events - 2</span></span>](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-2/)

- [<span data-ttu-id="c8d92-244">Eventos ETW de GC – 3</span><span class="sxs-lookup"><span data-stu-id="c8d92-244">GC ETW Events - 3</span></span>](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-3/)

- [<span data-ttu-id="c8d92-245">Eventos ETW de GC – 4</span><span class="sxs-lookup"><span data-stu-id="c8d92-245">GC ETW Events - 4</span></span>](https://blogs.msdn.microsoft.com/maoni/2014/12/30/gc-etw-events-4/)

<span data-ttu-id="c8d92-246">Para identificar GCs excessivos de geração 2 causados por alocações de LOH temporárias, veja a coluna Motivo de Gatilho dos GCs.</span><span class="sxs-lookup"><span data-stu-id="c8d92-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="c8d92-247">Para um teste simples que aloca apenas objetos grandes temporários, você pode coletar informações sobre eventos ETW com a seguinte linha de comando do [PerfView](https://www.microsoft.com/download/details.aspx?id=28567):</span><span class="sxs-lookup"><span data-stu-id="c8d92-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="c8d92-248">O resultado é semelhante a este:</span><span class="sxs-lookup"><span data-stu-id="c8d92-248">The result is something like this:</span></span>

<span data-ttu-id="c8d92-249">![Captura de tela que mostra os eventos ETW no PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="c8d92-249">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="c8d92-250">Figura 5: Eventos de ETW mostrados usando o PerfView</span><span class="sxs-lookup"><span data-stu-id="c8d92-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="c8d92-251">Como você pode ver, todos os GCs são GCs de geração 2 e são disparados por AllocLarge, o que significa que a alocação de um objeto grande disparou esse GC.</span><span class="sxs-lookup"><span data-stu-id="c8d92-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="c8d92-252">Sabemos que essas alocações são temporárias porque a coluna **% da Taxa de Sobrevivência de LOH** indica 1%.</span><span class="sxs-lookup"><span data-stu-id="c8d92-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="c8d92-253">Você pode coletar eventos ETW adicionais que indicam quem alocou esses objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="c8d92-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="c8d92-254">A seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="c8d92-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="c8d92-255">coleta um evento AllocationTick disparado aproximadamente a cada 100 mil alocações.</span><span class="sxs-lookup"><span data-stu-id="c8d92-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="c8d92-256">Em outras palavras, um evento é disparado sempre que um objeto grande é alocado.</span><span class="sxs-lookup"><span data-stu-id="c8d92-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="c8d92-257">Em seguida, você pode observar uma das exibições de Alocação de Heap de GC, que mostra as pilhas de chamadas que alocaram objetos grandes:</span><span class="sxs-lookup"><span data-stu-id="c8d92-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="c8d92-258">![Captura de tela que mostra a exibição de heap de um coletor de lixo.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="c8d92-258">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="c8d92-259">Figura 6: Uma exibição de alocação de heap de GC</span><span class="sxs-lookup"><span data-stu-id="c8d92-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="c8d92-260">Como você pode ver, esse é um teste muito simples que aloca apenas objetos grandes de seu método `Main`.</span><span class="sxs-lookup"><span data-stu-id="c8d92-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="c8d92-261">Um depurador</span><span class="sxs-lookup"><span data-stu-id="c8d92-261">A debugger</span></span>

<span data-ttu-id="c8d92-262">Se tudo o que você tem é um despejo de memória e você precisa examinar quais objetos estão realmente no LOH, use a [extensão de depurador SoS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) fornecida pelo .NET.</span><span class="sxs-lookup"><span data-stu-id="c8d92-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="c8d92-263">Os comandos de depuração mencionados nesta seção são aplicáveis aos [Depuradores do Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="c8d92-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="c8d92-264">O seguinte exemplo mostra uma saída de exemplo da análise de LOH:</span><span class="sxs-lookup"><span data-stu-id="c8d92-264">The following shows sample output from analyzing the LOH:</span></span>

```
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

<span data-ttu-id="c8d92-265">O tamanho do heap de LOH é (16.754.224 + 16.699.288 + 16.284.504) = 49.738.016 bytes.</span><span class="sxs-lookup"><span data-stu-id="c8d92-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="c8d92-266">Entre os endereços 023e1000 e 033db630, 8.008.736 bytes são ocupados por uma matriz de <xref:System.Object?displayProperty=nameWithType> objetos, 6.663.696 bytes são ocupados por uma matriz de <xref:System.Byte?displayProperty=nameWithType> objetos e 2.081.792 bytes são ocupados por espaço livre.</span><span class="sxs-lookup"><span data-stu-id="c8d92-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="c8d92-267">Às vezes, o depurador mostra que o tamanho total do LOH é menor que 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="c8d92-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="c8d92-268">Isso ocorre porque o próprio tempo de execução usa o LOH para alocar alguns objetos menores que um objeto grande.</span><span class="sxs-lookup"><span data-stu-id="c8d92-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="c8d92-269">Como o LOH não é compactado, às vezes ele é considerado uma fonte de fragmentação.</span><span class="sxs-lookup"><span data-stu-id="c8d92-269">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="c8d92-270">Fragmentação significa:</span><span class="sxs-lookup"><span data-stu-id="c8d92-270">Fragmentation means:</span></span>

- <span data-ttu-id="c8d92-271">Fragmentação do heap gerenciado, que é indicada pela quantidade de espaço livre entre objetos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c8d92-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="c8d92-272">No SoS, o comando `!dumpheap –type Free` exibe a quantidade de espaço livre entre objetos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c8d92-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="c8d92-273">Fragmentação do espaço de endereço da VM (memória virtual), que é a memória marcada como `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="c8d92-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="c8d92-274">Você pode obtê-lo usando vários comandos de depurador no windbg.</span><span class="sxs-lookup"><span data-stu-id="c8d92-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="c8d92-275">O seguinte exemplo mostra a fragmentação no espaço de VM:</span><span class="sxs-lookup"><span data-stu-id="c8d92-275">The following example shows fragmentation in the VM space:</span></span>

   ```
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

<span data-ttu-id="c8d92-276">É mais comum ver a fragmentação da VM causada por objetos grandes temporários que exigem que o coletor de lixo adquira frequentemente novos segmentos de heap gerenciado do sistema operacional e libere os segmentos vazios novamente para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c8d92-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="c8d92-277">Para verificar se o LOH está causando a fragmentação da VM, defina um ponto de interrupção em [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) e [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) para ver quem os chama.</span><span class="sxs-lookup"><span data-stu-id="c8d92-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="c8d92-278">Por exemplo, para ver quem tentou alocar blocos de memória virtual maiores que 8 MB do sistema operacional, defina um ponto de interrupção como este:</span><span class="sxs-lookup"><span data-stu-id="c8d92-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="c8d92-279">Esse comando invade o depurador e mostra a pilha de chamadas somente se [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) é chamado com um tamanho de alocação maior que 8 MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="c8d92-279">This command breaks into the debugger and shows the callstack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="c8d92-280">O CLR 2.0 adicionou um recurso chamado *VM Hoarding*, que pode ser útil para cenários em que os segmentos (incluindo heaps de objeto grande e pequeno) são frequentemente adquiridos e liberados.</span><span class="sxs-lookup"><span data-stu-id="c8d92-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="c8d92-281">Para especificar o VM Hoarding, você especifica um sinalizador de inicialização chamado `STARTUP_HOARD_GC_VM` pela API de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="c8d92-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="c8d92-282">Em vez de liberar segmentos vazios novamente para o sistema operacional, o CLR anula a confirmação da memória nesses segmentos e os coloca em uma lista de espera.</span><span class="sxs-lookup"><span data-stu-id="c8d92-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="c8d92-283">(Observe que o CLR não faz isso para segmentos muito grandes.) Posteriormente, o CLR usa esses segmentos para atender a novas solicitações de segmento.</span><span class="sxs-lookup"><span data-stu-id="c8d92-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="c8d92-284">Na próxima vez que seu aplicativo precisar de um novo segmento, o CLR usará um dessa lista de espera, caso consiga encontrar um que seja grande o suficiente.</span><span class="sxs-lookup"><span data-stu-id="c8d92-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="c8d92-285">O VM Hoarding também é útil para aplicativos que desejam manter os segmentos que eles já adquiriram, como alguns aplicativos para servidores que são os aplicativos dominantes em execução no sistema, para evitar exceções de memória insuficiente.</span><span class="sxs-lookup"><span data-stu-id="c8d92-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="c8d92-286">É altamente recomendável que você teste cuidadosamente seu aplicativo quando usar esse recurso, para garantir que o aplicativo tem um uso de memória razoavelmente estável.</span><span class="sxs-lookup"><span data-stu-id="c8d92-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
