---
title: Eventos ETW de coleta de lixo
description: Exiba informações detalhadas sobre eventos ETW de coleta de lixo. Os eventos cobertos incluem GCStart_V1, GCEnd_V1, GCHeapStats_V1, GCCreateSegment_V1 e muito mais.
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 58ad874ef6a12c18c404640aa66577c391573534
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309736"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="c7ada-104">Eventos ETW de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="c7ada-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="c7ada-105"> Esses eventos coletam informações referentes à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="c7ada-106">Eles ajudam no diagnóstico e na depuração, inclusive determinando quantas vezes a coleta de lixo foi executada, a quantidade de memória liberada durante a coleta de lixo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c7ada-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="c7ada-107">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="c7ada-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="c7ada-108">Evento GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="c7ada-109">Evento GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="c7ada-110">Evento GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="c7ada-111">Evento GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-111">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="c7ada-112">Evento GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-112">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="c7ada-113">Evento GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-113">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="c7ada-114">Evento GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-114">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="c7ada-115">Evento GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-115">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="c7ada-116">Evento GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-116">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="c7ada-117">Evento GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="c7ada-117">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="c7ada-118">Evento GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-118">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="c7ada-119">Evento GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-119">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="c7ada-120">Evento GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-120">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="c7ada-121">Evento GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-121">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="c7ada-122">Evento GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-122">GCStart_V1 Event</span></span>  

<span data-ttu-id="c7ada-123">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c7ada-123">The following table shows the keyword and level.</span></span> <span data-ttu-id="c7ada-124">Para obter mais informações, consulte [palavras-chave e níveis do ETW do CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c7ada-124">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="c7ada-125">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-125">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-126">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-127">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-127">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-128">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-128">Informational (4)</span></span>|

<span data-ttu-id="c7ada-129">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-129">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-130">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-130">Event</span></span>|<span data-ttu-id="c7ada-131">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-131">Event ID</span></span>|<span data-ttu-id="c7ada-132">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="c7ada-133">1</span><span class="sxs-lookup"><span data-stu-id="c7ada-133">1</span></span>|<span data-ttu-id="c7ada-134">Uma coleta de lixo foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="c7ada-134">A garbage collection has started.</span></span>|

<span data-ttu-id="c7ada-135">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-135">The following table shows the event data:</span></span>

|<span data-ttu-id="c7ada-136">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c7ada-136">Field name</span></span>|<span data-ttu-id="c7ada-137">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c7ada-137">Data type</span></span>|<span data-ttu-id="c7ada-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-138">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c7ada-139">Contagem</span><span class="sxs-lookup"><span data-stu-id="c7ada-139">Count</span></span>|<span data-ttu-id="c7ada-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-140">win:UInt32</span></span>|<span data-ttu-id="c7ada-141">A *n*° de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-141">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="c7ada-142">Profundidade</span><span class="sxs-lookup"><span data-stu-id="c7ada-142">Depth</span></span>|<span data-ttu-id="c7ada-143">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-143">win:UInt32</span></span>|<span data-ttu-id="c7ada-144">A geração que está sendo coletada.</span><span class="sxs-lookup"><span data-stu-id="c7ada-144">The generation that is being collected.</span></span>|
|<span data-ttu-id="c7ada-145">Motivo</span><span class="sxs-lookup"><span data-stu-id="c7ada-145">Reason</span></span>|<span data-ttu-id="c7ada-146">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-146">win:UInt32</span></span>|<span data-ttu-id="c7ada-147">Motivo do gatilho da coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="c7ada-147">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="c7ada-148">0x0 – Alocação de heap de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="c7ada-148">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="c7ada-149">0x1 – Induzido.</span><span class="sxs-lookup"><span data-stu-id="c7ada-149">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="c7ada-150">0x2 – Memória insuficiente.</span><span class="sxs-lookup"><span data-stu-id="c7ada-150">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="c7ada-151">0x3 – Vazio.</span><span class="sxs-lookup"><span data-stu-id="c7ada-151">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="c7ada-152">0x4 – Alocação de heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="c7ada-152">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="c7ada-153">0x5 – Espaço insuficiente (para heap de objetos pequenos).</span><span class="sxs-lookup"><span data-stu-id="c7ada-153">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="c7ada-154">0x6 – Espaço insuficiente (para heap de objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="c7ada-154">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="c7ada-155">0x7 – Induzido, mas não forçado como bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c7ada-155">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="c7ada-156">Tipo</span><span class="sxs-lookup"><span data-stu-id="c7ada-156">Type</span></span>|<span data-ttu-id="c7ada-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-157">win:UInt32</span></span>|<span data-ttu-id="c7ada-158">0x0 – A coleta de lixo de bloqueio ocorreu fora da coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c7ada-158">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="c7ada-159">0x1 – Coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c7ada-159">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="c7ada-160">0x2 – A coleta de lixo de bloqueio ocorreu durante a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c7ada-160">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="c7ada-161">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c7ada-161">ClrInstanceID</span></span>|<span data-ttu-id="c7ada-162">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-162">win:UInt16</span></span>|<span data-ttu-id="c7ada-163">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c7ada-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="c7ada-164">Evento GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-164">GCEnd_V1 Event</span></span>

<span data-ttu-id="c7ada-165">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-165">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-166">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-166">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-167">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-168">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-168">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-169">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-169">Informational (4)</span></span>|

<span data-ttu-id="c7ada-170">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-170">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-171">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-171">Event</span></span>|<span data-ttu-id="c7ada-172">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-172">Event ID</span></span>|<span data-ttu-id="c7ada-173">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="c7ada-174">2</span><span class="sxs-lookup"><span data-stu-id="c7ada-174">2</span></span>|<span data-ttu-id="c7ada-175">A coleta de lixo foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="c7ada-175">The garbage collection has ended.</span></span>|

<span data-ttu-id="c7ada-176">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-176">The following table shows the event data:</span></span>

|<span data-ttu-id="c7ada-177">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c7ada-177">Field name</span></span>|<span data-ttu-id="c7ada-178">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c7ada-178">Data type</span></span>|<span data-ttu-id="c7ada-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-179">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c7ada-180">Contagem</span><span class="sxs-lookup"><span data-stu-id="c7ada-180">Count</span></span>|<span data-ttu-id="c7ada-181">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-181">win:UInt32</span></span>|<span data-ttu-id="c7ada-182">A *n*° de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-182">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="c7ada-183">Profundidade</span><span class="sxs-lookup"><span data-stu-id="c7ada-183">Depth</span></span>|<span data-ttu-id="c7ada-184">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-184">win:UInt32</span></span>|<span data-ttu-id="c7ada-185">A geração que foi coletada.</span><span class="sxs-lookup"><span data-stu-id="c7ada-185">The generation that was collected.</span></span>|
|<span data-ttu-id="c7ada-186">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c7ada-186">ClrInstanceID</span></span>|<span data-ttu-id="c7ada-187">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-187">win:UInt16</span></span>|<span data-ttu-id="c7ada-188">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c7ada-188">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="c7ada-189">Evento GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-189">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="c7ada-190">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-190">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-191">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-191">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-192">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-192">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-194">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-194">Informational (4)</span></span>|

<span data-ttu-id="c7ada-195">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-195">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-196">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-196">Event</span></span>|<span data-ttu-id="c7ada-197">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-197">Event ID</span></span>|<span data-ttu-id="c7ada-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-198">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="c7ada-199">4</span><span class="sxs-lookup"><span data-stu-id="c7ada-199">4</span></span>|<span data-ttu-id="c7ada-200">Mostra as estatísticas de heap no final de cada coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-200">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="c7ada-201">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-201">The following table shows the event data:</span></span>

|<span data-ttu-id="c7ada-202">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c7ada-202">Field name</span></span>|<span data-ttu-id="c7ada-203">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c7ada-203">Data type</span></span>|<span data-ttu-id="c7ada-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-204">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c7ada-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="c7ada-205">GenerationSize0</span></span>|<span data-ttu-id="c7ada-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-206">win:UInt64</span></span>|<span data-ttu-id="c7ada-207">O tamanho, em bytes, da memória de geração 0.</span><span class="sxs-lookup"><span data-stu-id="c7ada-207">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="c7ada-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="c7ada-208">TotalPromotedSize0</span></span>|<span data-ttu-id="c7ada-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-209">win:UInt64</span></span>|<span data-ttu-id="c7ada-210">O número de bytes que são promovidos da geração 0 para a geração 1.</span><span class="sxs-lookup"><span data-stu-id="c7ada-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="c7ada-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="c7ada-211">GenerationSize1</span></span>|<span data-ttu-id="c7ada-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-212">win:UInt64</span></span>|<span data-ttu-id="c7ada-213">O tamanho, em bytes, da memória de geração 1.</span><span class="sxs-lookup"><span data-stu-id="c7ada-213">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="c7ada-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="c7ada-214">TotalPromotedSize1</span></span>|<span data-ttu-id="c7ada-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-215">win:UInt64</span></span>|<span data-ttu-id="c7ada-216">O número de bytes que são promovidos da geração 1 para a geração 2.</span><span class="sxs-lookup"><span data-stu-id="c7ada-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="c7ada-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="c7ada-217">GenerationSize2</span></span>|<span data-ttu-id="c7ada-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-218">win:UInt64</span></span>|<span data-ttu-id="c7ada-219">O tamanho, em bytes, da memória de geração 2.</span><span class="sxs-lookup"><span data-stu-id="c7ada-219">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="c7ada-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="c7ada-220">TotalPromotedSize2</span></span>|<span data-ttu-id="c7ada-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-221">win:UInt64</span></span>|<span data-ttu-id="c7ada-222">O número de bytes que sobreviveram na geração 2 após a última coleta.</span><span class="sxs-lookup"><span data-stu-id="c7ada-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="c7ada-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="c7ada-223">GenerationSize3</span></span>|<span data-ttu-id="c7ada-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-224">win:UInt64</span></span>|<span data-ttu-id="c7ada-225">O tamanho, em bytes, do heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="c7ada-225">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="c7ada-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="c7ada-226">TotalPromotedSize3</span></span>|<span data-ttu-id="c7ada-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-227">win:UInt64</span></span>|<span data-ttu-id="c7ada-228">O número de bytes que sobreviveram no heap de objetos grandes após a última coleta.</span><span class="sxs-lookup"><span data-stu-id="c7ada-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="c7ada-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="c7ada-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="c7ada-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-230">win:UInt64</span></span>|<span data-ttu-id="c7ada-231">O tamanho total, em bytes, dos objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="c7ada-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="c7ada-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="c7ada-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="c7ada-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-233">win:UInt64</span></span>|<span data-ttu-id="c7ada-234">O número de objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="c7ada-234">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="c7ada-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="c7ada-235">PinnedObjectCount</span></span>|<span data-ttu-id="c7ada-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-236">win:UInt32</span></span>|<span data-ttu-id="c7ada-237">O número de objetos (imóveis) fixados.</span><span class="sxs-lookup"><span data-stu-id="c7ada-237">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="c7ada-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="c7ada-238">SinkBlockCount</span></span>|<span data-ttu-id="c7ada-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-239">win:UInt32</span></span>|<span data-ttu-id="c7ada-240">O número de blocos de sincronização em uso.</span><span class="sxs-lookup"><span data-stu-id="c7ada-240">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="c7ada-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="c7ada-241">GCHandleCount</span></span>|<span data-ttu-id="c7ada-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-242">win:UInt32</span></span>|<span data-ttu-id="c7ada-243">O número de manipuladores de coleta de lixo em uso.</span><span class="sxs-lookup"><span data-stu-id="c7ada-243">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="c7ada-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c7ada-244">ClrInstanceID</span></span>|<span data-ttu-id="c7ada-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-245">win:UInt16</span></span>|<span data-ttu-id="c7ada-246">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c7ada-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="c7ada-247">Evento GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-247">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="c7ada-248">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-248">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-249">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-249">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-250">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-250">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-251">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-251">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-252">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-252">Informational (4)</span></span>|

<span data-ttu-id="c7ada-253">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-253">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-254">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-254">Event</span></span>|<span data-ttu-id="c7ada-255">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-255">Event ID</span></span>|<span data-ttu-id="c7ada-256">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-256">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="c7ada-257">5</span><span class="sxs-lookup"><span data-stu-id="c7ada-257">5</span></span>|<span data-ttu-id="c7ada-258">Um novo segmento de coleta de lixo foi criado.</span><span class="sxs-lookup"><span data-stu-id="c7ada-258">A new garbage collection segment has been created.</span></span> <span data-ttu-id="c7ada-259">Além disso, quando o rastreamento é habilitado em um processo que já está em execução, esse evento é acionado para cada segmento existente.</span><span class="sxs-lookup"><span data-stu-id="c7ada-259">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="c7ada-260">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-260">The following table shows the event data:</span></span>

|<span data-ttu-id="c7ada-261">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c7ada-261">Field name</span></span>|<span data-ttu-id="c7ada-262">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c7ada-262">Data type</span></span>|<span data-ttu-id="c7ada-263">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-263">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c7ada-264">Endereço</span><span class="sxs-lookup"><span data-stu-id="c7ada-264">Address</span></span>|<span data-ttu-id="c7ada-265">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-265">win:UInt64</span></span>|<span data-ttu-id="c7ada-266">O endereço do segmento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-266">The address of the segment.</span></span>|
|<span data-ttu-id="c7ada-267">Tamanho</span><span class="sxs-lookup"><span data-stu-id="c7ada-267">Size</span></span>|<span data-ttu-id="c7ada-268">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-268">win:UInt64</span></span>|<span data-ttu-id="c7ada-269">O tamanho do segmento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-269">The size of the segment.</span></span>|
|<span data-ttu-id="c7ada-270">Tipo</span><span class="sxs-lookup"><span data-stu-id="c7ada-270">Type</span></span>|<span data-ttu-id="c7ada-271">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-271">win:UInt32</span></span>|<span data-ttu-id="c7ada-272">0x0 – Heap de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="c7ada-272">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="c7ada-273">0x1 – Heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="c7ada-273">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="c7ada-274">0x2 – Heap somente leitura.</span><span class="sxs-lookup"><span data-stu-id="c7ada-274">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="c7ada-275">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c7ada-275">ClrInstanceID</span></span>|<span data-ttu-id="c7ada-276">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-276">win:UInt16</span></span>|<span data-ttu-id="c7ada-277">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c7ada-277">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="c7ada-278">Observe que o tamanho de segmentos alocados pelo coletor de lixo é específico à implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas.</span><span class="sxs-lookup"><span data-stu-id="c7ada-278">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="c7ada-279">Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-279">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="c7ada-280">Evento GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-280">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="c7ada-281">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-281">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-282">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-282">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-283">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-283">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-284">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-284">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-285">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-285">Informational (4)</span></span>|

<span data-ttu-id="c7ada-286">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-286">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-287">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-287">Event</span></span>|<span data-ttu-id="c7ada-288">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-288">Event ID</span></span>|<span data-ttu-id="c7ada-289">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-289">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="c7ada-290">6</span><span class="sxs-lookup"><span data-stu-id="c7ada-290">6</span></span>|<span data-ttu-id="c7ada-291">Um segmento de coleta de lixo foi liberado.</span><span class="sxs-lookup"><span data-stu-id="c7ada-291">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="c7ada-292">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-292">The following table shows the event data:</span></span>

|<span data-ttu-id="c7ada-293">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c7ada-293">Field name</span></span>|<span data-ttu-id="c7ada-294">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c7ada-294">Data type</span></span>|<span data-ttu-id="c7ada-295">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-295">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c7ada-296">Endereço</span><span class="sxs-lookup"><span data-stu-id="c7ada-296">Address</span></span>|<span data-ttu-id="c7ada-297">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-297">win:UInt64</span></span>|<span data-ttu-id="c7ada-298">O endereço do segmento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-298">The address of the segment.</span></span>|
|<span data-ttu-id="c7ada-299">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c7ada-299">ClrInstanceID</span></span>|<span data-ttu-id="c7ada-300">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-300">win:UInt16</span></span>|<span data-ttu-id="c7ada-301">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c7ada-301">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="c7ada-302">Evento GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-302">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="c7ada-303">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-303">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-304">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-304">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-305">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-305">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-306">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-306">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-307">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-307">Informational (4)</span></span>|

<span data-ttu-id="c7ada-308">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-308">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-309">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-309">Event</span></span>|<span data-ttu-id="c7ada-310">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-310">Event ID</span></span>|<span data-ttu-id="c7ada-311">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-311">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="c7ada-312">7</span><span class="sxs-lookup"><span data-stu-id="c7ada-312">7</span></span>|<span data-ttu-id="c7ada-313">A continuidade da suspensão do Common Language Runtime foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="c7ada-313">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="c7ada-314">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-314">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="c7ada-315">Evento GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-315">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="c7ada-316">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-316">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-317">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-317">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-318">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-318">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-319">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-319">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-320">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-320">Informational (4)</span></span>|

<span data-ttu-id="c7ada-321">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-321">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-322">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-322">Event</span></span>|<span data-ttu-id="c7ada-323">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-323">Event Id</span></span>|<span data-ttu-id="c7ada-324">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-324">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="c7ada-325">3</span><span class="sxs-lookup"><span data-stu-id="c7ada-325">3</span></span>|<span data-ttu-id="c7ada-326">A continuidade da suspensão do Common Language Runtime foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="c7ada-326">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="c7ada-327">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-327">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="c7ada-328">Evento GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-328">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="c7ada-329">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-329">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-330">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-330">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-331">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-331">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-332">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-332">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-333">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-333">Informational (4)</span></span>|

<span data-ttu-id="c7ada-334">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-334">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-335">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-335">Event</span></span>|<span data-ttu-id="c7ada-336">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-336">Event ID</span></span>|<span data-ttu-id="c7ada-337">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-337">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="c7ada-338">9</span><span class="sxs-lookup"><span data-stu-id="c7ada-338">9</span></span>|<span data-ttu-id="c7ada-339">Início da suspensão do mecanismo de execução da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-339">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="c7ada-340">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-340">The following table shows the event data:</span></span>

|<span data-ttu-id="c7ada-341">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c7ada-341">Field name</span></span>|<span data-ttu-id="c7ada-342">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c7ada-342">Data type</span></span>|<span data-ttu-id="c7ada-343">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-343">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c7ada-344">Motivo</span><span class="sxs-lookup"><span data-stu-id="c7ada-344">Reason</span></span>|<span data-ttu-id="c7ada-345">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-345">win:UInt16</span></span>|<span data-ttu-id="c7ada-346">0x0 – Outros.</span><span class="sxs-lookup"><span data-stu-id="c7ada-346">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="c7ada-347">0x1 – Coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-347">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="c7ada-348">0x2 – Desligamento do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-348">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="c7ada-349">0x3 – Densidade do código.</span><span class="sxs-lookup"><span data-stu-id="c7ada-349">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="c7ada-350">0x4 – Desligamento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-350">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="c7ada-351">0x5 – Depurador.</span><span class="sxs-lookup"><span data-stu-id="c7ada-351">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="c7ada-352">0x6 – Preparação para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-352">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="c7ada-353">Contagem</span><span class="sxs-lookup"><span data-stu-id="c7ada-353">Count</span></span>|<span data-ttu-id="c7ada-354">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-354">win:UInt32</span></span>|<span data-ttu-id="c7ada-355">A contagem de GC no momento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-355">The GC count at the time.</span></span> <span data-ttu-id="c7ada-356">Normalmente, você verá um evento de Início de GC posterior depois disso e sua Contagem será essa Contagem + 1, conforme aumentamos o Índice de GC durante uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-356">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="c7ada-357">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c7ada-357">ClrInstanceID</span></span>|<span data-ttu-id="c7ada-358">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-358">win:UInt16</span></span>|<span data-ttu-id="c7ada-359">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c7ada-359">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="c7ada-360">Evento GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-360">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="c7ada-361">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-361">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-362">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-362">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-363">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-363">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-364">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-364">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-365">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-365">Informational (4)</span></span>|

<span data-ttu-id="c7ada-366">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-366">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-367">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-367">Event</span></span>|<span data-ttu-id="c7ada-368">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-368">Event ID</span></span>|<span data-ttu-id="c7ada-369">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-369">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="c7ada-370">8</span><span class="sxs-lookup"><span data-stu-id="c7ada-370">8</span></span>|<span data-ttu-id="c7ada-371">Fim da suspensão do mecanismo de execução da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7ada-371">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="c7ada-372">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-372">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="c7ada-373">Evento GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="c7ada-373">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="c7ada-374">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-374">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-375">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-375">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-376">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-376">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-377">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-377">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-378">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-378">Informational (4)</span></span>|

<span data-ttu-id="c7ada-379">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-379">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-380">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-380">Event</span></span>|<span data-ttu-id="c7ada-381">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-381">Event ID</span></span>|<span data-ttu-id="c7ada-382">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-382">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="c7ada-383">10</span><span class="sxs-lookup"><span data-stu-id="c7ada-383">10</span></span>|<span data-ttu-id="c7ada-384">A cada vez, aproximadamente 100 KB são alocados.</span><span class="sxs-lookup"><span data-stu-id="c7ada-384">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="c7ada-385">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-385">The following table shows the event data:</span></span>

|<span data-ttu-id="c7ada-386">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c7ada-386">Field name</span></span>|<span data-ttu-id="c7ada-387">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c7ada-387">Data type</span></span>|<span data-ttu-id="c7ada-388">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-388">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c7ada-389">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="c7ada-389">AllocationAmount</span></span>|<span data-ttu-id="c7ada-390">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-390">win:UInt32</span></span>|<span data-ttu-id="c7ada-391">O tamanho de alocação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="c7ada-391">The allocation size, in bytes.</span></span> <span data-ttu-id="c7ada-392">Esse valor é preciso para alocações menores do que o tamanho de um ULONG (4.294.967.295 bytes).</span><span class="sxs-lookup"><span data-stu-id="c7ada-392">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="c7ada-393">Se a alocação for maior, esse campo conterá um valor truncado.</span><span class="sxs-lookup"><span data-stu-id="c7ada-393">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="c7ada-394">Use `AllocationAmount64` para alocações muito grandes.</span><span class="sxs-lookup"><span data-stu-id="c7ada-394">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="c7ada-395">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="c7ada-395">AllocationKind</span></span>|<span data-ttu-id="c7ada-396">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-396">win:UInt32</span></span>|<span data-ttu-id="c7ada-397">0x0 – Alocação de objeto pequeno (a alocação está no heap de objetos pequenos).</span><span class="sxs-lookup"><span data-stu-id="c7ada-397">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="c7ada-398">0x1 – Alocação de objeto grande (a alocação está no heap de objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="c7ada-398">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="c7ada-399">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c7ada-399">ClrInstanceID</span></span>|<span data-ttu-id="c7ada-400">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-400">win:UInt16</span></span>|<span data-ttu-id="c7ada-401">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c7ada-401">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="c7ada-402">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="c7ada-402">AllocationAmount64</span></span>|<span data-ttu-id="c7ada-403">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c7ada-403">win:UInt64</span></span>|<span data-ttu-id="c7ada-404">O tamanho de alocação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="c7ada-404">The allocation size, in bytes.</span></span> <span data-ttu-id="c7ada-405">Esse valor é preciso para alocações muito grandes.</span><span class="sxs-lookup"><span data-stu-id="c7ada-405">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="c7ada-406">TypeId</span><span class="sxs-lookup"><span data-stu-id="c7ada-406">TypeId</span></span>|<span data-ttu-id="c7ada-407">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="c7ada-407">win:Pointer</span></span>|<span data-ttu-id="c7ada-408">O endereço da MethodTable.</span><span class="sxs-lookup"><span data-stu-id="c7ada-408">The address of the MethodTable.</span></span> <span data-ttu-id="c7ada-409">Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o endereço da MethodTable que corresponde ao último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).</span><span class="sxs-lookup"><span data-stu-id="c7ada-409">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="c7ada-410">TypeName</span><span class="sxs-lookup"><span data-stu-id="c7ada-410">TypeName</span></span>|<span data-ttu-id="c7ada-411">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c7ada-411">win:UnicodeString</span></span>|<span data-ttu-id="c7ada-412">O nome do tipo que foi alocado.</span><span class="sxs-lookup"><span data-stu-id="c7ada-412">The name of the type that was allocated.</span></span> <span data-ttu-id="c7ada-413">Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o tipo do último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).</span><span class="sxs-lookup"><span data-stu-id="c7ada-413">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="c7ada-414">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="c7ada-414">HeapIndex</span></span>|<span data-ttu-id="c7ada-415">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-415">win:UInt32</span></span>|<span data-ttu-id="c7ada-416">O heap em que o objeto foi alocado.</span><span class="sxs-lookup"><span data-stu-id="c7ada-416">The heap where the object was allocated.</span></span> <span data-ttu-id="c7ada-417">Esse valor é 0 (zero) durante a execução da coleta de lixo da estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c7ada-417">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="c7ada-418">Evento GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-418">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="c7ada-419">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-419">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-420">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-420">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-421">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-421">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-422">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-422">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-423">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-423">Informational (4)</span></span>|

<span data-ttu-id="c7ada-424">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-424">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-425">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-425">Event</span></span>|<span data-ttu-id="c7ada-426">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-426">Event ID</span></span>|<span data-ttu-id="c7ada-427">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-427">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="c7ada-428">14</span><span class="sxs-lookup"><span data-stu-id="c7ada-428">14</span></span>|<span data-ttu-id="c7ada-429">O início da execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="c7ada-429">The start of running finalizers.</span></span>|

<span data-ttu-id="c7ada-430">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-430">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="c7ada-431">Evento GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-431">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="c7ada-432">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-432">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-433">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-433">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-434">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-435">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-435">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-436">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-436">Informational (4)</span></span>|

<span data-ttu-id="c7ada-437">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-437">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-438">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-438">Event</span></span>|<span data-ttu-id="c7ada-439">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-439">Event ID</span></span>|<span data-ttu-id="c7ada-440">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-440">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="c7ada-441">13</span><span class="sxs-lookup"><span data-stu-id="c7ada-441">13</span></span>|<span data-ttu-id="c7ada-442">O fim da execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="c7ada-442">The end of running finalizers.</span></span>|

<span data-ttu-id="c7ada-443">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-443">The following table shows the event data:</span></span>

|<span data-ttu-id="c7ada-444">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c7ada-444">Field name</span></span>|<span data-ttu-id="c7ada-445">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c7ada-445">Data type</span></span>|<span data-ttu-id="c7ada-446">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7ada-446">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c7ada-447">Contagem</span><span class="sxs-lookup"><span data-stu-id="c7ada-447">Count</span></span>|<span data-ttu-id="c7ada-448">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c7ada-448">win:UInt32</span></span>|<span data-ttu-id="c7ada-449">O número de finalizadores que foram executados.</span><span class="sxs-lookup"><span data-stu-id="c7ada-449">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="c7ada-450">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c7ada-450">ClrInstanceID</span></span>|<span data-ttu-id="c7ada-451">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c7ada-451">win:UInt16</span></span>|<span data-ttu-id="c7ada-452">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c7ada-452">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="c7ada-453">Evento GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-453">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="c7ada-454">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-454">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-455">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-455">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-456">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-456">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-457">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-457">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-458">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-458">Informational (4)</span></span>|
|<span data-ttu-id="c7ada-459">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c7ada-459">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c7ada-460">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-460">Informational (4)</span></span>|

<span data-ttu-id="c7ada-461">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-461">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-462">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-462">Event</span></span>|<span data-ttu-id="c7ada-463">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-463">Event ID</span></span>|<span data-ttu-id="c7ada-464">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-464">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="c7ada-465">11</span><span class="sxs-lookup"><span data-stu-id="c7ada-465">11</span></span>|<span data-ttu-id="c7ada-466">O thread da coleta de lixo simultânea foi criado.</span><span class="sxs-lookup"><span data-stu-id="c7ada-466">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="c7ada-467">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-467">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="c7ada-468">Evento GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="c7ada-468">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="c7ada-469">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c7ada-469">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c7ada-470">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-470">Keyword for raising the event</span></span>|<span data-ttu-id="c7ada-471">Level</span><span class="sxs-lookup"><span data-stu-id="c7ada-471">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c7ada-472">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c7ada-472">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c7ada-473">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-473">Informational (4)</span></span>|
|<span data-ttu-id="c7ada-474">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c7ada-474">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c7ada-475">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c7ada-475">Informational (4)</span></span>|

<span data-ttu-id="c7ada-476">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c7ada-476">The following table shows the event information:</span></span>

|<span data-ttu-id="c7ada-477">Evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-477">Event</span></span>|<span data-ttu-id="c7ada-478">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c7ada-478">Event ID</span></span>|<span data-ttu-id="c7ada-479">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c7ada-479">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="c7ada-480">12</span><span class="sxs-lookup"><span data-stu-id="c7ada-480">12</span></span>|<span data-ttu-id="c7ada-481">O thread da coleta de lixo simultânea foi terminado.</span><span class="sxs-lookup"><span data-stu-id="c7ada-481">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="c7ada-482">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c7ada-482">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7ada-483">Confira também</span><span class="sxs-lookup"><span data-stu-id="c7ada-483">See also</span></span>

- [<span data-ttu-id="c7ada-484">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="c7ada-484">CLR ETW Events</span></span>](clr-etw-events.md)
