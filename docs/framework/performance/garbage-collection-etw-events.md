---
title: Eventos ETW de coleta de lixo
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd4a4699f115c5b134ea60e703607ff36c229a78
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040577"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="a267a-102">Eventos ETW de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="a267a-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="a267a-103">Esses eventos coletam informações relacionadas à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="a267a-104">Eles ajudam no diagnóstico e na depuração, inclusive determinando quantas vezes a coleta de lixo foi executada, a quantidade de memória liberada durante a coleta de lixo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a267a-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="a267a-105">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="a267a-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="a267a-106">Evento GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="a267a-107">Evento GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="a267a-108">Evento GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="a267a-109">Evento GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="a267a-110">Evento GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="a267a-111">Evento GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="a267a-112">Evento GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="a267a-113">Evento GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="a267a-114">Evento GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="a267a-115">Evento GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="a267a-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="a267a-116">Evento GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="a267a-117">Evento GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="a267a-118">Evento GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="a267a-119">Evento GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="a267a-120">Evento GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="a267a-121">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="a267a-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="a267a-122">Para obter mais informações, consulte [palavras-chave e níveis do ETW do CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a267a-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="a267a-123">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-123">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-124">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-126">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-126">Informational (4)</span></span>|

<span data-ttu-id="a267a-127">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-127">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-128">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-128">Event</span></span>|<span data-ttu-id="a267a-129">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-129">Event ID</span></span>|<span data-ttu-id="a267a-130">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="a267a-131">1</span><span class="sxs-lookup"><span data-stu-id="a267a-131">1</span></span>|<span data-ttu-id="a267a-132">Uma coleta de lixo foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="a267a-132">A garbage collection has started.</span></span>|

<span data-ttu-id="a267a-133">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-133">The following table shows the event data:</span></span>

|<span data-ttu-id="a267a-134">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="a267a-134">Field name</span></span>|<span data-ttu-id="a267a-135">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a267a-135">Data type</span></span>|<span data-ttu-id="a267a-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a267a-137">Contagem</span><span class="sxs-lookup"><span data-stu-id="a267a-137">Count</span></span>|<span data-ttu-id="a267a-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-138">win:UInt32</span></span>|<span data-ttu-id="a267a-139">A *n*° de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="a267a-140">Profundidade</span><span class="sxs-lookup"><span data-stu-id="a267a-140">Depth</span></span>|<span data-ttu-id="a267a-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-141">win:UInt32</span></span>|<span data-ttu-id="a267a-142">A geração que está sendo coletada.</span><span class="sxs-lookup"><span data-stu-id="a267a-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="a267a-143">Motivo</span><span class="sxs-lookup"><span data-stu-id="a267a-143">Reason</span></span>|<span data-ttu-id="a267a-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-144">win:UInt32</span></span>|<span data-ttu-id="a267a-145">Motivo do gatilho da coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="a267a-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="a267a-146">0x0 – Alocação de heap de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="a267a-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="a267a-147">0x1 – Induzido.</span><span class="sxs-lookup"><span data-stu-id="a267a-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="a267a-148">0x2 – Memória insuficiente.</span><span class="sxs-lookup"><span data-stu-id="a267a-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="a267a-149">0x3 – Vazio.</span><span class="sxs-lookup"><span data-stu-id="a267a-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="a267a-150">0x4 – Alocação de heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="a267a-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="a267a-151">0x5 – Espaço insuficiente (para heap de objetos pequenos).</span><span class="sxs-lookup"><span data-stu-id="a267a-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="a267a-152">0x6 – Espaço insuficiente (para heap de objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="a267a-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="a267a-153">0x7 – Induzido, mas não forçado como bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a267a-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="a267a-154">Digite</span><span class="sxs-lookup"><span data-stu-id="a267a-154">Type</span></span>|<span data-ttu-id="a267a-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-155">win:UInt32</span></span>|<span data-ttu-id="a267a-156">0x0 – A coleta de lixo de bloqueio ocorreu fora da coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="a267a-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="a267a-157">0x1 – Coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="a267a-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="a267a-158">0x2 – A coleta de lixo de bloqueio ocorreu durante a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="a267a-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="a267a-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a267a-159">ClrInstanceID</span></span>|<span data-ttu-id="a267a-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-160">win:UInt16</span></span>|<span data-ttu-id="a267a-161">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a267a-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="a267a-162">Evento GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="a267a-163">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-164">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-164">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-165">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-167">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-167">Informational (4)</span></span>|

<span data-ttu-id="a267a-168">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-168">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-169">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-169">Event</span></span>|<span data-ttu-id="a267a-170">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-170">Event ID</span></span>|<span data-ttu-id="a267a-171">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="a267a-172">2</span><span class="sxs-lookup"><span data-stu-id="a267a-172">2</span></span>|<span data-ttu-id="a267a-173">A coleta de lixo foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="a267a-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="a267a-174">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-174">The following table shows the event data:</span></span>

|<span data-ttu-id="a267a-175">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="a267a-175">Field name</span></span>|<span data-ttu-id="a267a-176">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a267a-176">Data type</span></span>|<span data-ttu-id="a267a-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a267a-178">Contagem</span><span class="sxs-lookup"><span data-stu-id="a267a-178">Count</span></span>|<span data-ttu-id="a267a-179">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-179">win:UInt32</span></span>|<span data-ttu-id="a267a-180">A *n*° de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="a267a-181">Profundidade</span><span class="sxs-lookup"><span data-stu-id="a267a-181">Depth</span></span>|<span data-ttu-id="a267a-182">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-182">win:UInt32</span></span>|<span data-ttu-id="a267a-183">A geração que foi coletada.</span><span class="sxs-lookup"><span data-stu-id="a267a-183">The generation that was collected.</span></span>|
|<span data-ttu-id="a267a-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a267a-184">ClrInstanceID</span></span>|<span data-ttu-id="a267a-185">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-185">win:UInt16</span></span>|<span data-ttu-id="a267a-186">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a267a-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="a267a-187">Evento GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="a267a-188">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-189">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-189">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-190">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-192">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-192">Informational (4)</span></span>|

<span data-ttu-id="a267a-193">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-193">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-194">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-194">Event</span></span>|<span data-ttu-id="a267a-195">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-195">Event ID</span></span>|<span data-ttu-id="a267a-196">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="a267a-197">4</span><span class="sxs-lookup"><span data-stu-id="a267a-197">4</span></span>|<span data-ttu-id="a267a-198">Mostra as estatísticas de heap no final de cada coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="a267a-199">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-199">The following table shows the event data:</span></span>

|<span data-ttu-id="a267a-200">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="a267a-200">Field name</span></span>|<span data-ttu-id="a267a-201">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a267a-201">Data type</span></span>|<span data-ttu-id="a267a-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a267a-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="a267a-203">GenerationSize0</span></span>|<span data-ttu-id="a267a-204">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-204">win:UInt64</span></span>|<span data-ttu-id="a267a-205">O tamanho, em bytes, da memória de geração 0.</span><span class="sxs-lookup"><span data-stu-id="a267a-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="a267a-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="a267a-206">TotalPromotedSize0</span></span>|<span data-ttu-id="a267a-207">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-207">win:UInt64</span></span>|<span data-ttu-id="a267a-208">O número de bytes que são promovidos da geração 0 para a geração 1.</span><span class="sxs-lookup"><span data-stu-id="a267a-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="a267a-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="a267a-209">GenerationSize1</span></span>|<span data-ttu-id="a267a-210">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-210">win:UInt64</span></span>|<span data-ttu-id="a267a-211">O tamanho, em bytes, da memória de geração 1.</span><span class="sxs-lookup"><span data-stu-id="a267a-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="a267a-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="a267a-212">TotalPromotedSize1</span></span>|<span data-ttu-id="a267a-213">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-213">win:UInt64</span></span>|<span data-ttu-id="a267a-214">O número de bytes que são promovidos da geração 1 para a geração 2.</span><span class="sxs-lookup"><span data-stu-id="a267a-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="a267a-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="a267a-215">GenerationSize2</span></span>|<span data-ttu-id="a267a-216">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-216">win:UInt64</span></span>|<span data-ttu-id="a267a-217">O tamanho, em bytes, da memória de geração 2.</span><span class="sxs-lookup"><span data-stu-id="a267a-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="a267a-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="a267a-218">TotalPromotedSize2</span></span>|<span data-ttu-id="a267a-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-219">win:UInt64</span></span>|<span data-ttu-id="a267a-220">O número de bytes que sobreviveram na geração 2 após a última coleta.</span><span class="sxs-lookup"><span data-stu-id="a267a-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="a267a-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="a267a-221">GenerationSize3</span></span>|<span data-ttu-id="a267a-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-222">win:UInt64</span></span>|<span data-ttu-id="a267a-223">O tamanho, em bytes, do heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="a267a-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="a267a-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="a267a-224">TotalPromotedSize3</span></span>|<span data-ttu-id="a267a-225">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-225">win:UInt64</span></span>|<span data-ttu-id="a267a-226">O número de bytes que sobreviveram no heap de objetos grandes após a última coleta.</span><span class="sxs-lookup"><span data-stu-id="a267a-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="a267a-227">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="a267a-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="a267a-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-228">win:UInt64</span></span>|<span data-ttu-id="a267a-229">O tamanho total, em bytes, dos objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="a267a-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="a267a-230">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="a267a-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="a267a-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-231">win:UInt64</span></span>|<span data-ttu-id="a267a-232">O número de objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="a267a-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="a267a-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="a267a-233">PinnedObjectCount</span></span>|<span data-ttu-id="a267a-234">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-234">win:UInt32</span></span>|<span data-ttu-id="a267a-235">O número de objetos (imóveis) fixados.</span><span class="sxs-lookup"><span data-stu-id="a267a-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="a267a-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="a267a-236">SinkBlockCount</span></span>|<span data-ttu-id="a267a-237">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-237">win:UInt32</span></span>|<span data-ttu-id="a267a-238">O número de blocos de sincronização em uso.</span><span class="sxs-lookup"><span data-stu-id="a267a-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="a267a-239">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="a267a-239">GCHandleCount</span></span>|<span data-ttu-id="a267a-240">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-240">win:UInt32</span></span>|<span data-ttu-id="a267a-241">O número de manipuladores de coleta de lixo em uso.</span><span class="sxs-lookup"><span data-stu-id="a267a-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="a267a-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a267a-242">ClrInstanceID</span></span>|<span data-ttu-id="a267a-243">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-243">win:UInt16</span></span>|<span data-ttu-id="a267a-244">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a267a-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="a267a-245">Evento GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="a267a-246">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-247">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-247">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-248">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-250">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-250">Informational (4)</span></span>|

<span data-ttu-id="a267a-251">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-251">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-252">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-252">Event</span></span>|<span data-ttu-id="a267a-253">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-253">Event ID</span></span>|<span data-ttu-id="a267a-254">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="a267a-255">5</span><span class="sxs-lookup"><span data-stu-id="a267a-255">5</span></span>|<span data-ttu-id="a267a-256">Um novo segmento de coleta de lixo foi criado.</span><span class="sxs-lookup"><span data-stu-id="a267a-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="a267a-257">Além disso, quando o rastreamento é habilitado em um processo que já está em execução, esse evento é acionado para cada segmento existente.</span><span class="sxs-lookup"><span data-stu-id="a267a-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="a267a-258">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-258">The following table shows the event data:</span></span>

|<span data-ttu-id="a267a-259">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="a267a-259">Field name</span></span>|<span data-ttu-id="a267a-260">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a267a-260">Data type</span></span>|<span data-ttu-id="a267a-261">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a267a-262">Endereço</span><span class="sxs-lookup"><span data-stu-id="a267a-262">Address</span></span>|<span data-ttu-id="a267a-263">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-263">win:UInt64</span></span>|<span data-ttu-id="a267a-264">O endereço do segmento.</span><span class="sxs-lookup"><span data-stu-id="a267a-264">The address of the segment.</span></span>|
|<span data-ttu-id="a267a-265">Tamanho</span><span class="sxs-lookup"><span data-stu-id="a267a-265">Size</span></span>|<span data-ttu-id="a267a-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-266">win:UInt64</span></span>|<span data-ttu-id="a267a-267">O tamanho do segmento.</span><span class="sxs-lookup"><span data-stu-id="a267a-267">The size of the segment.</span></span>|
|<span data-ttu-id="a267a-268">Digite</span><span class="sxs-lookup"><span data-stu-id="a267a-268">Type</span></span>|<span data-ttu-id="a267a-269">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-269">win:UInt32</span></span>|<span data-ttu-id="a267a-270">0x0 – Heap de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="a267a-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="a267a-271">0x1 – Heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="a267a-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="a267a-272">0x2 – Heap somente leitura.</span><span class="sxs-lookup"><span data-stu-id="a267a-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="a267a-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a267a-273">ClrInstanceID</span></span>|<span data-ttu-id="a267a-274">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-274">win:UInt16</span></span>|<span data-ttu-id="a267a-275">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a267a-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="a267a-276">Observe que o tamanho de segmentos alocados pelo coletor de lixo é específico à implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas.</span><span class="sxs-lookup"><span data-stu-id="a267a-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="a267a-277">Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.</span><span class="sxs-lookup"><span data-stu-id="a267a-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="a267a-278">Evento GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="a267a-279">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-280">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-280">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-281">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-283">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-283">Informational (4)</span></span>|

<span data-ttu-id="a267a-284">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-284">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-285">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-285">Event</span></span>|<span data-ttu-id="a267a-286">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-286">Event ID</span></span>|<span data-ttu-id="a267a-287">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="a267a-288">6</span><span class="sxs-lookup"><span data-stu-id="a267a-288">6</span></span>|<span data-ttu-id="a267a-289">Um segmento de coleta de lixo foi liberado.</span><span class="sxs-lookup"><span data-stu-id="a267a-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="a267a-290">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-290">The following table shows the event data:</span></span>

|<span data-ttu-id="a267a-291">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="a267a-291">Field name</span></span>|<span data-ttu-id="a267a-292">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a267a-292">Data type</span></span>|<span data-ttu-id="a267a-293">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a267a-294">Endereço</span><span class="sxs-lookup"><span data-stu-id="a267a-294">Address</span></span>|<span data-ttu-id="a267a-295">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-295">win:UInt64</span></span>|<span data-ttu-id="a267a-296">O endereço do segmento.</span><span class="sxs-lookup"><span data-stu-id="a267a-296">The address of the segment.</span></span>|
|<span data-ttu-id="a267a-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a267a-297">ClrInstanceID</span></span>|<span data-ttu-id="a267a-298">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-298">win:UInt16</span></span>|<span data-ttu-id="a267a-299">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a267a-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="a267a-300">Evento GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="a267a-301">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-302">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-302">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-303">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-305">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-305">Informational (4)</span></span>|

<span data-ttu-id="a267a-306">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-306">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-307">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-307">Event</span></span>|<span data-ttu-id="a267a-308">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-308">Event ID</span></span>|<span data-ttu-id="a267a-309">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="a267a-310">7</span><span class="sxs-lookup"><span data-stu-id="a267a-310">7</span></span>|<span data-ttu-id="a267a-311">A continuidade da suspensão do Common Language Runtime foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="a267a-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="a267a-312">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="a267a-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="a267a-313">Evento GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="a267a-314">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-315">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-315">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-316">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-318">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-318">Informational (4)</span></span>|

<span data-ttu-id="a267a-319">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-319">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-320">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-320">Event</span></span>|<span data-ttu-id="a267a-321">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-321">Event Id</span></span>|<span data-ttu-id="a267a-322">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="a267a-323">3</span><span class="sxs-lookup"><span data-stu-id="a267a-323">3</span></span>|<span data-ttu-id="a267a-324">A continuidade da suspensão do Common Language Runtime foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="a267a-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="a267a-325">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="a267a-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="a267a-326">Evento GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="a267a-327">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-328">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-328">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-329">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-331">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-331">Informational (4)</span></span>|

<span data-ttu-id="a267a-332">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-332">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-333">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-333">Event</span></span>|<span data-ttu-id="a267a-334">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-334">Event ID</span></span>|<span data-ttu-id="a267a-335">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="a267a-336">9</span><span class="sxs-lookup"><span data-stu-id="a267a-336">9</span></span>|<span data-ttu-id="a267a-337">Início da suspensão do mecanismo de execução da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="a267a-338">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-338">The following table shows the event data:</span></span>

|<span data-ttu-id="a267a-339">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="a267a-339">Field name</span></span>|<span data-ttu-id="a267a-340">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a267a-340">Data type</span></span>|<span data-ttu-id="a267a-341">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a267a-342">Motivo</span><span class="sxs-lookup"><span data-stu-id="a267a-342">Reason</span></span>|<span data-ttu-id="a267a-343">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-343">win:UInt16</span></span>|<span data-ttu-id="a267a-344">0x0 – Outros.</span><span class="sxs-lookup"><span data-stu-id="a267a-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="a267a-345">0x1 – Coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="a267a-346">0x2 – Desligamento do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a267a-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="a267a-347">0x3 – Densidade do código.</span><span class="sxs-lookup"><span data-stu-id="a267a-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="a267a-348">0x4 – Desligamento.</span><span class="sxs-lookup"><span data-stu-id="a267a-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="a267a-349">0x5 – Depurador.</span><span class="sxs-lookup"><span data-stu-id="a267a-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="a267a-350">0x6 – Preparação para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="a267a-351">Contagem</span><span class="sxs-lookup"><span data-stu-id="a267a-351">Count</span></span>|<span data-ttu-id="a267a-352">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-352">win:UInt32</span></span>|<span data-ttu-id="a267a-353">A contagem de GC no momento.</span><span class="sxs-lookup"><span data-stu-id="a267a-353">The GC count at the time.</span></span> <span data-ttu-id="a267a-354">Normalmente, você verá um evento de Início de GC posterior depois disso e sua Contagem será essa Contagem + 1, conforme aumentamos o Índice de GC durante uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="a267a-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a267a-355">ClrInstanceID</span></span>|<span data-ttu-id="a267a-356">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-356">win:UInt16</span></span>|<span data-ttu-id="a267a-357">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a267a-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="a267a-358">Evento GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="a267a-359">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-360">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-360">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-361">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-363">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-363">Informational (4)</span></span>|

<span data-ttu-id="a267a-364">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-364">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-365">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-365">Event</span></span>|<span data-ttu-id="a267a-366">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-366">Event ID</span></span>|<span data-ttu-id="a267a-367">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="a267a-368">8</span><span class="sxs-lookup"><span data-stu-id="a267a-368">8</span></span>|<span data-ttu-id="a267a-369">Fim da suspensão do mecanismo de execução da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a267a-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="a267a-370">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="a267a-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="a267a-371">Evento GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="a267a-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="a267a-372">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-373">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-373">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-374">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-376">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-376">Informational (4)</span></span>|

<span data-ttu-id="a267a-377">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-377">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-378">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-378">Event</span></span>|<span data-ttu-id="a267a-379">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-379">Event ID</span></span>|<span data-ttu-id="a267a-380">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="a267a-381">10</span><span class="sxs-lookup"><span data-stu-id="a267a-381">10</span></span>|<span data-ttu-id="a267a-382">A cada vez, aproximadamente 100 KB são alocados.</span><span class="sxs-lookup"><span data-stu-id="a267a-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="a267a-383">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-383">The following table shows the event data:</span></span>

|<span data-ttu-id="a267a-384">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="a267a-384">Field name</span></span>|<span data-ttu-id="a267a-385">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a267a-385">Data type</span></span>|<span data-ttu-id="a267a-386">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a267a-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="a267a-387">AllocationAmount</span></span>|<span data-ttu-id="a267a-388">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-388">win:UInt32</span></span>|<span data-ttu-id="a267a-389">O tamanho de alocação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="a267a-389">The allocation size, in bytes.</span></span> <span data-ttu-id="a267a-390">Esse valor é preciso para alocações menores do que o tamanho de um ULONG (4.294.967.295 bytes).</span><span class="sxs-lookup"><span data-stu-id="a267a-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="a267a-391">Se a alocação for maior, esse campo conterá um valor truncado.</span><span class="sxs-lookup"><span data-stu-id="a267a-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="a267a-392">Use `AllocationAmount64` para alocações muito grandes.</span><span class="sxs-lookup"><span data-stu-id="a267a-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="a267a-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="a267a-393">AllocationKind</span></span>|<span data-ttu-id="a267a-394">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-394">win:UInt32</span></span>|<span data-ttu-id="a267a-395">0x0 – Alocação de objeto pequeno (a alocação está no heap de objetos pequenos).</span><span class="sxs-lookup"><span data-stu-id="a267a-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="a267a-396">0x1 – Alocação de objeto grande (a alocação está no heap de objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="a267a-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="a267a-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a267a-397">ClrInstanceID</span></span>|<span data-ttu-id="a267a-398">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-398">win:UInt16</span></span>|<span data-ttu-id="a267a-399">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a267a-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="a267a-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="a267a-400">AllocationAmount64</span></span>|<span data-ttu-id="a267a-401">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a267a-401">win:UInt64</span></span>|<span data-ttu-id="a267a-402">O tamanho de alocação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="a267a-402">The allocation size, in bytes.</span></span> <span data-ttu-id="a267a-403">Esse valor é preciso para alocações muito grandes.</span><span class="sxs-lookup"><span data-stu-id="a267a-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="a267a-404">TypeId</span><span class="sxs-lookup"><span data-stu-id="a267a-404">TypeId</span></span>|<span data-ttu-id="a267a-405">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="a267a-405">win:Pointer</span></span>|<span data-ttu-id="a267a-406">O endereço da MethodTable.</span><span class="sxs-lookup"><span data-stu-id="a267a-406">The address of the MethodTable.</span></span> <span data-ttu-id="a267a-407">Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o endereço da MethodTable que corresponde ao último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).</span><span class="sxs-lookup"><span data-stu-id="a267a-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="a267a-408">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="a267a-408">TypeName</span></span>|<span data-ttu-id="a267a-409">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a267a-409">win:UnicodeString</span></span>|<span data-ttu-id="a267a-410">O nome do tipo que foi alocado.</span><span class="sxs-lookup"><span data-stu-id="a267a-410">The name of the type that was allocated.</span></span> <span data-ttu-id="a267a-411">Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o tipo do último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).</span><span class="sxs-lookup"><span data-stu-id="a267a-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="a267a-412">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="a267a-412">HeapIndex</span></span>|<span data-ttu-id="a267a-413">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-413">win:UInt32</span></span>|<span data-ttu-id="a267a-414">O heap em que o objeto foi alocado.</span><span class="sxs-lookup"><span data-stu-id="a267a-414">The heap where the object was allocated.</span></span> <span data-ttu-id="a267a-415">Esse valor é 0 (zero) durante a execução da coleta de lixo da estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a267a-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="a267a-416">Evento GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="a267a-417">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-418">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-418">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-419">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-421">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-421">Informational (4)</span></span>|

<span data-ttu-id="a267a-422">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-422">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-423">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-423">Event</span></span>|<span data-ttu-id="a267a-424">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-424">Event ID</span></span>|<span data-ttu-id="a267a-425">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="a267a-426">14</span><span class="sxs-lookup"><span data-stu-id="a267a-426">14</span></span>|<span data-ttu-id="a267a-427">O início da execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="a267a-427">The start of running finalizers.</span></span>|

<span data-ttu-id="a267a-428">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="a267a-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="a267a-429">Evento GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="a267a-430">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-431">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-431">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-432">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-434">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-434">Informational (4)</span></span>|

<span data-ttu-id="a267a-435">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-435">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-436">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-436">Event</span></span>|<span data-ttu-id="a267a-437">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-437">Event ID</span></span>|<span data-ttu-id="a267a-438">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="a267a-439">13</span><span class="sxs-lookup"><span data-stu-id="a267a-439">13</span></span>|<span data-ttu-id="a267a-440">O fim da execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="a267a-440">The end of running finalizers.</span></span>|

<span data-ttu-id="a267a-441">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-441">The following table shows the event data:</span></span>

|<span data-ttu-id="a267a-442">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="a267a-442">Field name</span></span>|<span data-ttu-id="a267a-443">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a267a-443">Data type</span></span>|<span data-ttu-id="a267a-444">Descrição</span><span class="sxs-lookup"><span data-stu-id="a267a-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a267a-445">Contagem</span><span class="sxs-lookup"><span data-stu-id="a267a-445">Count</span></span>|<span data-ttu-id="a267a-446">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a267a-446">win:UInt32</span></span>|<span data-ttu-id="a267a-447">O número de finalizadores que foram executados.</span><span class="sxs-lookup"><span data-stu-id="a267a-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="a267a-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a267a-448">ClrInstanceID</span></span>|<span data-ttu-id="a267a-449">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a267a-449">win:UInt16</span></span>|<span data-ttu-id="a267a-450">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a267a-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="a267a-451">Evento GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="a267a-452">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-453">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-453">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-454">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-456">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-456">Informational (4)</span></span>|
|<span data-ttu-id="a267a-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a267a-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a267a-458">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-458">Informational (4)</span></span>|

<span data-ttu-id="a267a-459">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-459">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-460">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-460">Event</span></span>|<span data-ttu-id="a267a-461">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-461">Event ID</span></span>|<span data-ttu-id="a267a-462">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="a267a-463">11</span><span class="sxs-lookup"><span data-stu-id="a267a-463">11</span></span>|<span data-ttu-id="a267a-464">O thread da coleta de lixo simultânea foi criado.</span><span class="sxs-lookup"><span data-stu-id="a267a-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="a267a-465">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="a267a-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="a267a-466">Evento GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="a267a-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="a267a-467">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="a267a-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a267a-468">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="a267a-468">Keyword for raising the event</span></span>|<span data-ttu-id="a267a-469">Nível</span><span class="sxs-lookup"><span data-stu-id="a267a-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a267a-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a267a-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a267a-471">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-471">Informational (4)</span></span>|
|<span data-ttu-id="a267a-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a267a-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a267a-473">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="a267a-473">Informational (4)</span></span>|

<span data-ttu-id="a267a-474">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="a267a-474">The following table shows the event information:</span></span>

|<span data-ttu-id="a267a-475">evento</span><span class="sxs-lookup"><span data-stu-id="a267a-475">Event</span></span>|<span data-ttu-id="a267a-476">ID do evento</span><span class="sxs-lookup"><span data-stu-id="a267a-476">Event ID</span></span>|<span data-ttu-id="a267a-477">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="a267a-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="a267a-478">12</span><span class="sxs-lookup"><span data-stu-id="a267a-478">12</span></span>|<span data-ttu-id="a267a-479">O thread da coleta de lixo simultânea foi terminado.</span><span class="sxs-lookup"><span data-stu-id="a267a-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="a267a-480">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="a267a-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="a267a-481">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a267a-481">See also</span></span>

- [<span data-ttu-id="a267a-482">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="a267a-482">CLR ETW Events</span></span>](clr-etw-events.md)
