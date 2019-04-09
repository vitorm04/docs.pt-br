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
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149728"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="0dd6b-102">Eventos ETW de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="0dd6b-103">Esses eventos coletam informações referentes à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="0dd6b-104">Eles ajudam no diagnóstico e na depuração, inclusive determinando quantas vezes a coleta de lixo foi executada, a quantidade de memória liberada durante a coleta de lixo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="0dd6b-105">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="0dd6b-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="0dd6b-106">Evento GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="0dd6b-107">Evento GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="0dd6b-108">Evento GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="0dd6b-109">Evento GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="0dd6b-110">Evento GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="0dd6b-111">Evento GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="0dd6b-112">Evento GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="0dd6b-113">Evento GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="0dd6b-114">Evento GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="0dd6b-115">Evento GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="0dd6b-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="0dd6b-116">Evento GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="0dd6b-117">Evento GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="0dd6b-118">Evento GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="0dd6b-119">Evento GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="0dd6b-120">Evento GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-121">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="0dd6b-122">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0dd6b-123">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-123">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-124">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-124">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-125">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-125">(0x1)</span></span>|<span data-ttu-id="0dd6b-126">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-127">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-128">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-128">Event</span></span>|<span data-ttu-id="0dd6b-129">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-129">Event ID</span></span>|<span data-ttu-id="0dd6b-130">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="0dd6b-131">1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-131">1</span></span>|<span data-ttu-id="0dd6b-132">Uma coleta de lixo foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="0dd6b-133">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0dd6b-134">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-134">Field name</span></span>|<span data-ttu-id="0dd6b-135">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0dd6b-135">Data type</span></span>|<span data-ttu-id="0dd6b-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0dd6b-137">Contagem</span><span class="sxs-lookup"><span data-stu-id="0dd6b-137">Count</span></span>|<span data-ttu-id="0dd6b-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-138">win:UInt32</span></span>|<span data-ttu-id="0dd6b-139">O *n*ª coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="0dd6b-140">Profundidade</span><span class="sxs-lookup"><span data-stu-id="0dd6b-140">Depth</span></span>|<span data-ttu-id="0dd6b-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-141">win:UInt32</span></span>|<span data-ttu-id="0dd6b-142">A geração que está sendo coletada.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="0dd6b-143">Motivo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-143">Reason</span></span>|<span data-ttu-id="0dd6b-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-144">win:UInt32</span></span>|<span data-ttu-id="0dd6b-145">Motivo do gatilho da coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="0dd6b-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="0dd6b-146">0x0 – Alocação de heap de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="0dd6b-147">0x1 – Induzido.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="0dd6b-148">0x2 – Memória insuficiente.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="0dd6b-149">0x3 – Vazio.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="0dd6b-150">0x4 – Alocação de heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="0dd6b-151">0x5 – Espaço insuficiente (para heap de objetos pequenos).</span><span class="sxs-lookup"><span data-stu-id="0dd6b-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="0dd6b-152">0x6 – Espaço insuficiente (para heap de objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="0dd6b-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="0dd6b-153">0x7 – Induzido, mas não forçado como bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="0dd6b-154">Tipo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-154">Type</span></span>|<span data-ttu-id="0dd6b-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-155">win:UInt32</span></span>|<span data-ttu-id="0dd6b-156">0x0 – A coleta de lixo de bloqueio ocorreu fora da coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="0dd6b-157">0x1 – Coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="0dd6b-158">0x2 – A coleta de lixo de bloqueio ocorreu durante a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="0dd6b-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0dd6b-159">ClrInstanceID</span></span>|<span data-ttu-id="0dd6b-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-160">win:UInt16</span></span>|<span data-ttu-id="0dd6b-161">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0dd6b-162">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="0dd6b-163">Evento GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-164">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-165">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-165">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-166">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-166">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-167">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-167">(0x1)</span></span>|<span data-ttu-id="0dd6b-168">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-169">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-170">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-170">Event</span></span>|<span data-ttu-id="0dd6b-171">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-171">Event ID</span></span>|<span data-ttu-id="0dd6b-172">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="0dd6b-173">2</span><span class="sxs-lookup"><span data-stu-id="0dd6b-173">2</span></span>|<span data-ttu-id="0dd6b-174">A coleta de lixo foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="0dd6b-175">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0dd6b-176">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-176">Field name</span></span>|<span data-ttu-id="0dd6b-177">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0dd6b-177">Data type</span></span>|<span data-ttu-id="0dd6b-178">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0dd6b-179">Contagem</span><span class="sxs-lookup"><span data-stu-id="0dd6b-179">Count</span></span>|<span data-ttu-id="0dd6b-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-180">win:UInt32</span></span>|<span data-ttu-id="0dd6b-181">O *n*ª coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="0dd6b-182">Profundidade</span><span class="sxs-lookup"><span data-stu-id="0dd6b-182">Depth</span></span>|<span data-ttu-id="0dd6b-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-183">win:UInt32</span></span>|<span data-ttu-id="0dd6b-184">A geração que foi coletada.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="0dd6b-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0dd6b-185">ClrInstanceID</span></span>|<span data-ttu-id="0dd6b-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-186">win:UInt16</span></span>|<span data-ttu-id="0dd6b-187">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0dd6b-188">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="0dd6b-189">Evento GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-190">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-191">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-191">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-192">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-192">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-193">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-193">(0x1)</span></span>|<span data-ttu-id="0dd6b-194">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-195">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-196">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-196">Event</span></span>|<span data-ttu-id="0dd6b-197">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-197">Event ID</span></span>|<span data-ttu-id="0dd6b-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="0dd6b-199">4</span><span class="sxs-lookup"><span data-stu-id="0dd6b-199">4</span></span>|<span data-ttu-id="0dd6b-200">Mostra as estatísticas de heap no final de cada coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="0dd6b-201">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0dd6b-202">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-202">Field name</span></span>|<span data-ttu-id="0dd6b-203">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0dd6b-203">Data type</span></span>|<span data-ttu-id="0dd6b-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0dd6b-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="0dd6b-205">GenerationSize0</span></span>|<span data-ttu-id="0dd6b-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-206">win:UInt64</span></span>|<span data-ttu-id="0dd6b-207">O tamanho, em bytes, da memória de geração 0.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="0dd6b-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="0dd6b-208">TotalPromotedSize0</span></span>|<span data-ttu-id="0dd6b-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-209">win:UInt64</span></span>|<span data-ttu-id="0dd6b-210">O número de bytes que são promovidos da geração 0 para a geração 1.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="0dd6b-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-211">GenerationSize1</span></span>|<span data-ttu-id="0dd6b-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-212">win:UInt64</span></span>|<span data-ttu-id="0dd6b-213">O tamanho, em bytes, da memória de geração 1.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="0dd6b-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-214">TotalPromotedSize1</span></span>|<span data-ttu-id="0dd6b-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-215">win:UInt64</span></span>|<span data-ttu-id="0dd6b-216">O número de bytes que são promovidos da geração 1 para a geração 2.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="0dd6b-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="0dd6b-217">GenerationSize2</span></span>|<span data-ttu-id="0dd6b-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-218">win:UInt64</span></span>|<span data-ttu-id="0dd6b-219">O tamanho, em bytes, da memória de geração 2.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="0dd6b-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="0dd6b-220">TotalPromotedSize2</span></span>|<span data-ttu-id="0dd6b-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-221">win:UInt64</span></span>|<span data-ttu-id="0dd6b-222">O número de bytes que sobreviveram na geração 2 após a última coleta.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="0dd6b-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="0dd6b-223">GenerationSize3</span></span>|<span data-ttu-id="0dd6b-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-224">win:UInt64</span></span>|<span data-ttu-id="0dd6b-225">O tamanho, em bytes, do heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="0dd6b-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="0dd6b-226">TotalPromotedSize3</span></span>|<span data-ttu-id="0dd6b-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-227">win:UInt64</span></span>|<span data-ttu-id="0dd6b-228">O número de bytes que sobreviveram no heap de objetos grandes após a última coleta.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="0dd6b-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="0dd6b-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="0dd6b-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-230">win:UInt64</span></span>|<span data-ttu-id="0dd6b-231">O tamanho total, em bytes, dos objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="0dd6b-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="0dd6b-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="0dd6b-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-233">win:UInt64</span></span>|<span data-ttu-id="0dd6b-234">O número de objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="0dd6b-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="0dd6b-235">PinnedObjectCount</span></span>|<span data-ttu-id="0dd6b-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-236">win:UInt32</span></span>|<span data-ttu-id="0dd6b-237">O número de objetos (imóveis) fixados.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="0dd6b-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="0dd6b-238">SinkBlockCount</span></span>|<span data-ttu-id="0dd6b-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-239">win:UInt32</span></span>|<span data-ttu-id="0dd6b-240">O número de blocos de sincronização em uso.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="0dd6b-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="0dd6b-241">GCHandleCount</span></span>|<span data-ttu-id="0dd6b-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-242">win:UInt32</span></span>|<span data-ttu-id="0dd6b-243">O número de manipuladores de coleta de lixo em uso.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="0dd6b-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0dd6b-244">ClrInstanceID</span></span>|<span data-ttu-id="0dd6b-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-245">win:UInt16</span></span>|<span data-ttu-id="0dd6b-246">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0dd6b-247">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="0dd6b-248">Evento GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-249">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-250">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-250">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-251">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-251">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-252">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-252">(0x1)</span></span>|<span data-ttu-id="0dd6b-253">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-254">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-255">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-255">Event</span></span>|<span data-ttu-id="0dd6b-256">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-256">Event ID</span></span>|<span data-ttu-id="0dd6b-257">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="0dd6b-258">5</span><span class="sxs-lookup"><span data-stu-id="0dd6b-258">5</span></span>|<span data-ttu-id="0dd6b-259">Um novo segmento de coleta de lixo foi criado.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="0dd6b-260">Além disso, quando o rastreamento é habilitado em um processo que já está em execução, esse evento é acionado para cada segmento existente.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="0dd6b-261">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0dd6b-262">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-262">Field name</span></span>|<span data-ttu-id="0dd6b-263">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0dd6b-263">Data type</span></span>|<span data-ttu-id="0dd6b-264">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0dd6b-265">Endereço</span><span class="sxs-lookup"><span data-stu-id="0dd6b-265">Address</span></span>|<span data-ttu-id="0dd6b-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-266">win:UInt64</span></span>|<span data-ttu-id="0dd6b-267">O endereço do segmento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-267">The address of the segment.</span></span>|  
|<span data-ttu-id="0dd6b-268">Tamanho</span><span class="sxs-lookup"><span data-stu-id="0dd6b-268">Size</span></span>|<span data-ttu-id="0dd6b-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-269">win:UInt64</span></span>|<span data-ttu-id="0dd6b-270">O tamanho do segmento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-270">The size of the segment.</span></span>|  
|<span data-ttu-id="0dd6b-271">Tipo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-271">Type</span></span>|<span data-ttu-id="0dd6b-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-272">win:UInt32</span></span>|<span data-ttu-id="0dd6b-273">0x0 – Heap de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="0dd6b-274">0x1 – Heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="0dd6b-275">0x2 – Heap somente leitura.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="0dd6b-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0dd6b-276">ClrInstanceID</span></span>|<span data-ttu-id="0dd6b-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-277">win:UInt16</span></span>|<span data-ttu-id="0dd6b-278">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="0dd6b-279">Observe que o tamanho de segmentos alocados pelo coletor de lixo é específico à implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="0dd6b-280">Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="0dd6b-281">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="0dd6b-282">Evento GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-283">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-284">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-284">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-285">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-285">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-286">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-286">(0x1)</span></span>|<span data-ttu-id="0dd6b-287">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-288">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-289">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-289">Event</span></span>|<span data-ttu-id="0dd6b-290">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-290">Event ID</span></span>|<span data-ttu-id="0dd6b-291">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="0dd6b-292">6</span><span class="sxs-lookup"><span data-stu-id="0dd6b-292">6</span></span>|<span data-ttu-id="0dd6b-293">Um segmento de coleta de lixo foi liberado.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="0dd6b-294">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0dd6b-295">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-295">Field name</span></span>|<span data-ttu-id="0dd6b-296">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0dd6b-296">Data type</span></span>|<span data-ttu-id="0dd6b-297">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0dd6b-298">Endereço</span><span class="sxs-lookup"><span data-stu-id="0dd6b-298">Address</span></span>|<span data-ttu-id="0dd6b-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-299">win:UInt64</span></span>|<span data-ttu-id="0dd6b-300">O endereço do segmento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-300">The address of the segment.</span></span>|  
|<span data-ttu-id="0dd6b-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0dd6b-301">ClrInstanceID</span></span>|<span data-ttu-id="0dd6b-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-302">win:UInt16</span></span>|<span data-ttu-id="0dd6b-303">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0dd6b-304">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="0dd6b-305">Evento GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-306">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-307">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-307">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-308">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-308">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-309">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-309">(0x1)</span></span>|<span data-ttu-id="0dd6b-310">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-311">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-312">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-312">Event</span></span>|<span data-ttu-id="0dd6b-313">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-313">Event ID</span></span>|<span data-ttu-id="0dd6b-314">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="0dd6b-315">7</span><span class="sxs-lookup"><span data-stu-id="0dd6b-315">7</span></span>|<span data-ttu-id="0dd6b-316">A continuidade da suspensão do Common Language Runtime foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="0dd6b-317">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-317">No event data.</span></span>  
  
 [<span data-ttu-id="0dd6b-318">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="0dd6b-319">Evento GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-320">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-321">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-321">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-322">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-322">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-323">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-323">(0x1)</span></span>|<span data-ttu-id="0dd6b-324">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-325">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-326">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-326">Event</span></span>|<span data-ttu-id="0dd6b-327">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-327">Event Id</span></span>|<span data-ttu-id="0dd6b-328">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="0dd6b-329">3</span><span class="sxs-lookup"><span data-stu-id="0dd6b-329">3</span></span>|<span data-ttu-id="0dd6b-330">A continuidade da suspensão do Common Language Runtime foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="0dd6b-331">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-331">No event data.</span></span>  
  
 [<span data-ttu-id="0dd6b-332">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="0dd6b-333">Evento GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-334">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-335">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-335">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-336">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-336">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-337">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-337">(0x1)</span></span>|<span data-ttu-id="0dd6b-338">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-339">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-340">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-340">Event</span></span>|<span data-ttu-id="0dd6b-341">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-341">Event ID</span></span>|<span data-ttu-id="0dd6b-342">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="0dd6b-343">9</span><span class="sxs-lookup"><span data-stu-id="0dd6b-343">9</span></span>|<span data-ttu-id="0dd6b-344">Início da suspensão do mecanismo de execução da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="0dd6b-345">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0dd6b-346">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-346">Field name</span></span>|<span data-ttu-id="0dd6b-347">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0dd6b-347">Data type</span></span>|<span data-ttu-id="0dd6b-348">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0dd6b-349">Motivo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-349">Reason</span></span>|<span data-ttu-id="0dd6b-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-350">win:UInt16</span></span>|<span data-ttu-id="0dd6b-351">0x0 – Outros.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="0dd6b-352">0x1 – Coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="0dd6b-353">0x2 – Desligamento do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="0dd6b-354">0x3 – Densidade do código.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="0dd6b-355">0x4 – Desligamento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="0dd6b-356">0x5 – Depurador.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="0dd6b-357">0x6 – Preparação para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="0dd6b-358">Contagem</span><span class="sxs-lookup"><span data-stu-id="0dd6b-358">Count</span></span>|<span data-ttu-id="0dd6b-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-359">win:UInt32</span></span>|<span data-ttu-id="0dd6b-360">A contagem de GC no momento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-360">The GC count at the time.</span></span> <span data-ttu-id="0dd6b-361">Normalmente, você verá um evento de Início de GC posterior depois disso e sua Contagem será essa Contagem + 1, conforme aumentamos o Índice de GC durante uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="0dd6b-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0dd6b-362">ClrInstanceID</span></span>|<span data-ttu-id="0dd6b-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-363">win:UInt16</span></span>|<span data-ttu-id="0dd6b-364">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0dd6b-365">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="0dd6b-366">Evento GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-367">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="0dd6b-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="0dd6b-368">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-368">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-369">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-369">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-370">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-370">(0x1)</span></span>|<span data-ttu-id="0dd6b-371">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-372">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="0dd6b-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="0dd6b-373">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-373">Event</span></span>|<span data-ttu-id="0dd6b-374">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-374">Event ID</span></span>|<span data-ttu-id="0dd6b-375">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="0dd6b-376">8</span><span class="sxs-lookup"><span data-stu-id="0dd6b-376">8</span></span>|<span data-ttu-id="0dd6b-377">Fim da suspensão do mecanismo de execução da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="0dd6b-378">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-378">No event data.</span></span>  
  
 [<span data-ttu-id="0dd6b-379">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="0dd6b-380">Evento GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="0dd6b-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="0dd6b-381">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-382">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-382">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-383">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-383">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-384">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-384">(0x1)</span></span>|<span data-ttu-id="0dd6b-385">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-386">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-387">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-387">Event</span></span>|<span data-ttu-id="0dd6b-388">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-388">Event ID</span></span>|<span data-ttu-id="0dd6b-389">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="0dd6b-390">10</span><span class="sxs-lookup"><span data-stu-id="0dd6b-390">10</span></span>|<span data-ttu-id="0dd6b-391">A cada vez, aproximadamente 100 KB são alocados.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="0dd6b-392">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0dd6b-393">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-393">Field name</span></span>|<span data-ttu-id="0dd6b-394">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0dd6b-394">Data type</span></span>|<span data-ttu-id="0dd6b-395">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0dd6b-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="0dd6b-396">AllocationAmount</span></span>|<span data-ttu-id="0dd6b-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-397">win:UInt32</span></span>|<span data-ttu-id="0dd6b-398">O tamanho de alocação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-398">The allocation size, in bytes.</span></span> <span data-ttu-id="0dd6b-399">Esse valor é preciso para alocações menores do que o tamanho de um ULONG (4.294.967.295 bytes).</span><span class="sxs-lookup"><span data-stu-id="0dd6b-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="0dd6b-400">Se a alocação for maior, esse campo conterá um valor truncado.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="0dd6b-401">Use `AllocationAmount64` para alocações muito grandes.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="0dd6b-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="0dd6b-402">AllocationKind</span></span>|<span data-ttu-id="0dd6b-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-403">win:UInt32</span></span>|<span data-ttu-id="0dd6b-404">0x0 – Alocação de objeto pequeno (a alocação está no heap de objetos pequenos).</span><span class="sxs-lookup"><span data-stu-id="0dd6b-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="0dd6b-405">0x1 – Alocação de objeto grande (a alocação está no heap de objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="0dd6b-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="0dd6b-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0dd6b-406">ClrInstanceID</span></span>|<span data-ttu-id="0dd6b-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-407">win:UInt16</span></span>|<span data-ttu-id="0dd6b-408">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="0dd6b-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-409">AllocationAmount64</span></span>|<span data-ttu-id="0dd6b-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0dd6b-410">win:UInt64</span></span>|<span data-ttu-id="0dd6b-411">O tamanho de alocação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-411">The allocation size, in bytes.</span></span> <span data-ttu-id="0dd6b-412">Esse valor é preciso para alocações muito grandes.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="0dd6b-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="0dd6b-413">TypeId</span></span>|<span data-ttu-id="0dd6b-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="0dd6b-414">win:Pointer</span></span>|<span data-ttu-id="0dd6b-415">O endereço da MethodTable.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-415">The address of the MethodTable.</span></span> <span data-ttu-id="0dd6b-416">Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o endereço da MethodTable que corresponde ao último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).</span><span class="sxs-lookup"><span data-stu-id="0dd6b-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="0dd6b-417">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-417">TypeName</span></span>|<span data-ttu-id="0dd6b-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0dd6b-418">win:UnicodeString</span></span>|<span data-ttu-id="0dd6b-419">O nome do tipo que foi alocado.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-419">The name of the type that was allocated.</span></span> <span data-ttu-id="0dd6b-420">Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o tipo do último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).</span><span class="sxs-lookup"><span data-stu-id="0dd6b-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="0dd6b-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="0dd6b-421">HeapIndex</span></span>|<span data-ttu-id="0dd6b-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-422">win:UInt32</span></span>|<span data-ttu-id="0dd6b-423">O heap em que o objeto foi alocado.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-423">The heap where the object was allocated.</span></span> <span data-ttu-id="0dd6b-424">Esse valor é 0 (zero) durante a execução da coleta de lixo da estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="0dd6b-425">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="0dd6b-426">Evento GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-427">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-428">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-428">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-429">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-429">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-430">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-430">(0x1)</span></span>|<span data-ttu-id="0dd6b-431">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-432">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-433">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-433">Event</span></span>|<span data-ttu-id="0dd6b-434">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-434">Event ID</span></span>|<span data-ttu-id="0dd6b-435">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="0dd6b-436">14</span><span class="sxs-lookup"><span data-stu-id="0dd6b-436">14</span></span>|<span data-ttu-id="0dd6b-437">O início da execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="0dd6b-438">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-438">No event data.</span></span>  
  
 [<span data-ttu-id="0dd6b-439">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="0dd6b-440">Evento GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-441">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-442">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-442">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-443">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-443">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-444">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-444">(0x1)</span></span>|<span data-ttu-id="0dd6b-445">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-446">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-447">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-447">Event</span></span>|<span data-ttu-id="0dd6b-448">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-448">Event ID</span></span>|<span data-ttu-id="0dd6b-449">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="0dd6b-450">13</span><span class="sxs-lookup"><span data-stu-id="0dd6b-450">13</span></span>|<span data-ttu-id="0dd6b-451">O fim da execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="0dd6b-452">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0dd6b-453">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0dd6b-453">Field name</span></span>|<span data-ttu-id="0dd6b-454">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0dd6b-454">Data type</span></span>|<span data-ttu-id="0dd6b-455">Descrição</span><span class="sxs-lookup"><span data-stu-id="0dd6b-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0dd6b-456">Contagem</span><span class="sxs-lookup"><span data-stu-id="0dd6b-456">Count</span></span>|<span data-ttu-id="0dd6b-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0dd6b-457">win:UInt32</span></span>|<span data-ttu-id="0dd6b-458">O número de finalizadores que foram executados.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="0dd6b-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0dd6b-459">ClrInstanceID</span></span>|<span data-ttu-id="0dd6b-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0dd6b-460">win:UInt16</span></span>|<span data-ttu-id="0dd6b-461">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0dd6b-462">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="0dd6b-463">Evento GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-464">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-465">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-465">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-466">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-466">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-467">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-467">(0x1)</span></span>|<span data-ttu-id="0dd6b-468">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-468">Informational (4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="0dd6b-469">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-469">(0x10000)</span></span>|<span data-ttu-id="0dd6b-470">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-471">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-472">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-472">Event</span></span>|<span data-ttu-id="0dd6b-473">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-473">Event ID</span></span>|<span data-ttu-id="0dd6b-474">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="0dd6b-475">11</span><span class="sxs-lookup"><span data-stu-id="0dd6b-475">11</span></span>|<span data-ttu-id="0dd6b-476">O thread da coleta de lixo simultânea foi criado.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="0dd6b-477">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-477">No event data.</span></span>  
  
 [<span data-ttu-id="0dd6b-478">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="0dd6b-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="0dd6b-479">Evento GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0dd6b-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="0dd6b-480">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0dd6b-481">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-481">Keyword for raising the event</span></span>|<span data-ttu-id="0dd6b-482">Nível</span><span class="sxs-lookup"><span data-stu-id="0dd6b-482">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0dd6b-483">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-483">(0x1)</span></span>|<span data-ttu-id="0dd6b-484">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-484">Informational (4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="0dd6b-485">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-485">(0x10000)</span></span>|<span data-ttu-id="0dd6b-486">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="0dd6b-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="0dd6b-487">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0dd6b-488">evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-488">Event</span></span>|<span data-ttu-id="0dd6b-489">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0dd6b-489">Event ID</span></span>|<span data-ttu-id="0dd6b-490">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0dd6b-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="0dd6b-491">12</span><span class="sxs-lookup"><span data-stu-id="0dd6b-491">12</span></span>|<span data-ttu-id="0dd6b-492">O thread da coleta de lixo simultânea foi terminado.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="0dd6b-493">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="0dd6b-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd6b-494">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0dd6b-494">See also</span></span>

- [<span data-ttu-id="0dd6b-495">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="0dd6b-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
