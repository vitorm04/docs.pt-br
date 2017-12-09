---
title: Eventos ETW de coleta de lixo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06fc335e4b8011afd92e698b20e4b84572b153c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="c62bf-102">Eventos ETW de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="c62bf-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="c62bf-103">Esses eventos coletam informações referentes à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="c62bf-104">Eles ajudam no diagnóstico e na depuração, inclusive determinando quantas vezes a coleta de lixo foi executada, a quantidade de memória liberada durante a coleta de lixo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c62bf-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="c62bf-105">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="c62bf-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="c62bf-106">Evento GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="c62bf-107">Evento GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="c62bf-108">Evento GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="c62bf-109">Evento GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="c62bf-110">Evento GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="c62bf-111">Evento GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="c62bf-112">Evento GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="c62bf-113">Evento GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="c62bf-114">Evento GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="c62bf-115">Evento GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="c62bf-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="c62bf-116">Evento GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="c62bf-117">Evento GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="c62bf-118">Evento GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="c62bf-119">Evento GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="c62bf-120">Evento GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="c62bf-121">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="c62bf-122">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="c62bf-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c62bf-123">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-123">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-124">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-126">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-127">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-128">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-128">Event</span></span>|<span data-ttu-id="c62bf-129">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-129">Event ID</span></span>|<span data-ttu-id="c62bf-130">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="c62bf-131">1</span><span class="sxs-lookup"><span data-stu-id="c62bf-131">1</span></span>|<span data-ttu-id="c62bf-132">Uma coleta de lixo foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="c62bf-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="c62bf-133">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c62bf-134">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c62bf-134">Field name</span></span>|<span data-ttu-id="c62bf-135">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c62bf-135">Data type</span></span>|<span data-ttu-id="c62bf-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c62bf-137">Contagem</span><span class="sxs-lookup"><span data-stu-id="c62bf-137">Count</span></span>|<span data-ttu-id="c62bf-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-138">win:UInt32</span></span>|<span data-ttu-id="c62bf-139">A *n*ª coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="c62bf-140">Profundidade</span><span class="sxs-lookup"><span data-stu-id="c62bf-140">Depth</span></span>|<span data-ttu-id="c62bf-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-141">win:UInt32</span></span>|<span data-ttu-id="c62bf-142">A geração que está sendo coletada.</span><span class="sxs-lookup"><span data-stu-id="c62bf-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="c62bf-143">Motivo</span><span class="sxs-lookup"><span data-stu-id="c62bf-143">Reason</span></span>|<span data-ttu-id="c62bf-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-144">win:UInt32</span></span>|<span data-ttu-id="c62bf-145">Motivo do gatilho da coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="c62bf-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="c62bf-146">0x0 – Alocação de heap de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="c62bf-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="c62bf-147">0x1 – Induzido.</span><span class="sxs-lookup"><span data-stu-id="c62bf-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="c62bf-148">0x2 – Memória insuficiente.</span><span class="sxs-lookup"><span data-stu-id="c62bf-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="c62bf-149">0x3 – Vazio.</span><span class="sxs-lookup"><span data-stu-id="c62bf-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="c62bf-150">0x4 – Alocação de heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="c62bf-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="c62bf-151">0x5 – Espaço insuficiente (para heap de objetos pequenos).</span><span class="sxs-lookup"><span data-stu-id="c62bf-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="c62bf-152">0x6 – Espaço insuficiente (para heap de objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="c62bf-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="c62bf-153">0x7 – Induzido, mas não forçado como bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c62bf-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="c62bf-154">Tipo</span><span class="sxs-lookup"><span data-stu-id="c62bf-154">Type</span></span>|<span data-ttu-id="c62bf-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-155">win:UInt32</span></span>|<span data-ttu-id="c62bf-156">0x0 – A coleta de lixo de bloqueio ocorreu fora da coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c62bf-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="c62bf-157">0x1 – Coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c62bf-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="c62bf-158">0x2 – A coleta de lixo de bloqueio ocorreu durante a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c62bf-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="c62bf-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c62bf-159">ClrInstanceID</span></span>|<span data-ttu-id="c62bf-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-160">win:UInt16</span></span>|<span data-ttu-id="c62bf-161">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c62bf-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c62bf-162">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="c62bf-163">Evento GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="c62bf-164">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-165">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-165">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-166">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-168">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-169">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-170">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-170">Event</span></span>|<span data-ttu-id="c62bf-171">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-171">Event ID</span></span>|<span data-ttu-id="c62bf-172">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="c62bf-173">2</span><span class="sxs-lookup"><span data-stu-id="c62bf-173">2</span></span>|<span data-ttu-id="c62bf-174">A coleta de lixo foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="c62bf-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="c62bf-175">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c62bf-176">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c62bf-176">Field name</span></span>|<span data-ttu-id="c62bf-177">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c62bf-177">Data type</span></span>|<span data-ttu-id="c62bf-178">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c62bf-179">Contagem</span><span class="sxs-lookup"><span data-stu-id="c62bf-179">Count</span></span>|<span data-ttu-id="c62bf-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-180">win:UInt32</span></span>|<span data-ttu-id="c62bf-181">A *n*ª coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="c62bf-182">Profundidade</span><span class="sxs-lookup"><span data-stu-id="c62bf-182">Depth</span></span>|<span data-ttu-id="c62bf-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-183">win:UInt32</span></span>|<span data-ttu-id="c62bf-184">A geração que foi coletada.</span><span class="sxs-lookup"><span data-stu-id="c62bf-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="c62bf-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c62bf-185">ClrInstanceID</span></span>|<span data-ttu-id="c62bf-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-186">win:UInt16</span></span>|<span data-ttu-id="c62bf-187">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c62bf-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c62bf-188">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="c62bf-189">Evento GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="c62bf-190">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-191">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-191">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-192">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-194">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-195">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-196">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-196">Event</span></span>|<span data-ttu-id="c62bf-197">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-197">Event ID</span></span>|<span data-ttu-id="c62bf-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="c62bf-199">4</span><span class="sxs-lookup"><span data-stu-id="c62bf-199">4</span></span>|<span data-ttu-id="c62bf-200">Mostra as estatísticas de heap no final de cada coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="c62bf-201">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c62bf-202">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c62bf-202">Field name</span></span>|<span data-ttu-id="c62bf-203">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c62bf-203">Data type</span></span>|<span data-ttu-id="c62bf-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c62bf-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="c62bf-205">GenerationSize0</span></span>|<span data-ttu-id="c62bf-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-206">win:UInt64</span></span>|<span data-ttu-id="c62bf-207">O tamanho, em bytes, da memória de geração 0.</span><span class="sxs-lookup"><span data-stu-id="c62bf-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="c62bf-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="c62bf-208">TotalPromotedSize0</span></span>|<span data-ttu-id="c62bf-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-209">win:UInt64</span></span>|<span data-ttu-id="c62bf-210">O número de bytes que são promovidos da geração 0 para a geração 1.</span><span class="sxs-lookup"><span data-stu-id="c62bf-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="c62bf-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="c62bf-211">GenerationSize1</span></span>|<span data-ttu-id="c62bf-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-212">win:UInt64</span></span>|<span data-ttu-id="c62bf-213">O tamanho, em bytes, da memória de geração 1.</span><span class="sxs-lookup"><span data-stu-id="c62bf-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="c62bf-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="c62bf-214">TotalPromotedSize1</span></span>|<span data-ttu-id="c62bf-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-215">win:UInt64</span></span>|<span data-ttu-id="c62bf-216">O número de bytes que são promovidos da geração 1 para a geração 2.</span><span class="sxs-lookup"><span data-stu-id="c62bf-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="c62bf-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="c62bf-217">GenerationSize2</span></span>|<span data-ttu-id="c62bf-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-218">win:UInt64</span></span>|<span data-ttu-id="c62bf-219">O tamanho, em bytes, da memória de geração 2.</span><span class="sxs-lookup"><span data-stu-id="c62bf-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="c62bf-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="c62bf-220">TotalPromotedSize2</span></span>|<span data-ttu-id="c62bf-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-221">win:UInt64</span></span>|<span data-ttu-id="c62bf-222">O número de bytes que sobreviveram na geração 2 após a última coleta.</span><span class="sxs-lookup"><span data-stu-id="c62bf-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="c62bf-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="c62bf-223">GenerationSize3</span></span>|<span data-ttu-id="c62bf-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-224">win:UInt64</span></span>|<span data-ttu-id="c62bf-225">O tamanho, em bytes, do heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="c62bf-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="c62bf-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="c62bf-226">TotalPromotedSize3</span></span>|<span data-ttu-id="c62bf-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-227">win:UInt64</span></span>|<span data-ttu-id="c62bf-228">O número de bytes que sobreviveram no heap de objetos grandes após a última coleta.</span><span class="sxs-lookup"><span data-stu-id="c62bf-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="c62bf-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="c62bf-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="c62bf-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-230">win:UInt64</span></span>|<span data-ttu-id="c62bf-231">O tamanho total, em bytes, dos objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="c62bf-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="c62bf-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="c62bf-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="c62bf-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-233">win:UInt64</span></span>|<span data-ttu-id="c62bf-234">O número de objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="c62bf-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="c62bf-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="c62bf-235">PinnedObjectCount</span></span>|<span data-ttu-id="c62bf-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-236">win:UInt32</span></span>|<span data-ttu-id="c62bf-237">O número de objetos (imóveis) fixados.</span><span class="sxs-lookup"><span data-stu-id="c62bf-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="c62bf-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="c62bf-238">SinkBlockCount</span></span>|<span data-ttu-id="c62bf-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-239">win:UInt32</span></span>|<span data-ttu-id="c62bf-240">O número de blocos de sincronização em uso.</span><span class="sxs-lookup"><span data-stu-id="c62bf-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="c62bf-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="c62bf-241">GCHandleCount</span></span>|<span data-ttu-id="c62bf-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-242">win:UInt32</span></span>|<span data-ttu-id="c62bf-243">O número de manipuladores de coleta de lixo em uso.</span><span class="sxs-lookup"><span data-stu-id="c62bf-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="c62bf-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c62bf-244">ClrInstanceID</span></span>|<span data-ttu-id="c62bf-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-245">win:UInt16</span></span>|<span data-ttu-id="c62bf-246">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c62bf-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c62bf-247">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="c62bf-248">Evento GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="c62bf-249">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-250">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-250">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-251">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-253">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-254">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-255">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-255">Event</span></span>|<span data-ttu-id="c62bf-256">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-256">Event ID</span></span>|<span data-ttu-id="c62bf-257">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="c62bf-258">5</span><span class="sxs-lookup"><span data-stu-id="c62bf-258">5</span></span>|<span data-ttu-id="c62bf-259">Um novo segmento de coleta de lixo foi criado.</span><span class="sxs-lookup"><span data-stu-id="c62bf-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="c62bf-260">Além disso, quando o rastreamento é habilitado em um processo que já está em execução, esse evento é acionado para cada segmento existente.</span><span class="sxs-lookup"><span data-stu-id="c62bf-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="c62bf-261">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c62bf-262">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c62bf-262">Field name</span></span>|<span data-ttu-id="c62bf-263">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c62bf-263">Data type</span></span>|<span data-ttu-id="c62bf-264">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c62bf-265">Endereço</span><span class="sxs-lookup"><span data-stu-id="c62bf-265">Address</span></span>|<span data-ttu-id="c62bf-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-266">win:UInt64</span></span>|<span data-ttu-id="c62bf-267">O endereço do segmento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-267">The address of the segment.</span></span>|  
|<span data-ttu-id="c62bf-268">Tamanho</span><span class="sxs-lookup"><span data-stu-id="c62bf-268">Size</span></span>|<span data-ttu-id="c62bf-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-269">win:UInt64</span></span>|<span data-ttu-id="c62bf-270">O tamanho do segmento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-270">The size of the segment.</span></span>|  
|<span data-ttu-id="c62bf-271">Tipo</span><span class="sxs-lookup"><span data-stu-id="c62bf-271">Type</span></span>|<span data-ttu-id="c62bf-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-272">win:UInt32</span></span>|<span data-ttu-id="c62bf-273">0x0 – Heap de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="c62bf-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="c62bf-274">0x1 – Heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="c62bf-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="c62bf-275">0x2 – Heap somente leitura.</span><span class="sxs-lookup"><span data-stu-id="c62bf-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="c62bf-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c62bf-276">ClrInstanceID</span></span>|<span data-ttu-id="c62bf-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-277">win:UInt16</span></span>|<span data-ttu-id="c62bf-278">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c62bf-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="c62bf-279">Observe que o tamanho de segmentos alocados pelo coletor de lixo é específico à implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas.</span><span class="sxs-lookup"><span data-stu-id="c62bf-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="c62bf-280">Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="c62bf-281">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="c62bf-282">Evento GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="c62bf-283">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-284">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-284">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-285">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-287">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-288">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-289">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-289">Event</span></span>|<span data-ttu-id="c62bf-290">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-290">Event ID</span></span>|<span data-ttu-id="c62bf-291">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="c62bf-292">6</span><span class="sxs-lookup"><span data-stu-id="c62bf-292">6</span></span>|<span data-ttu-id="c62bf-293">Um segmento de coleta de lixo foi liberado.</span><span class="sxs-lookup"><span data-stu-id="c62bf-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="c62bf-294">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c62bf-295">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c62bf-295">Field name</span></span>|<span data-ttu-id="c62bf-296">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c62bf-296">Data type</span></span>|<span data-ttu-id="c62bf-297">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c62bf-298">Endereço</span><span class="sxs-lookup"><span data-stu-id="c62bf-298">Address</span></span>|<span data-ttu-id="c62bf-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-299">win:UInt64</span></span>|<span data-ttu-id="c62bf-300">O endereço do segmento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-300">The address of the segment.</span></span>|  
|<span data-ttu-id="c62bf-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c62bf-301">ClrInstanceID</span></span>|<span data-ttu-id="c62bf-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-302">win:UInt16</span></span>|<span data-ttu-id="c62bf-303">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c62bf-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c62bf-304">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="c62bf-305">Evento GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="c62bf-306">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-307">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-307">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-308">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-310">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-311">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-312">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-312">Event</span></span>|<span data-ttu-id="c62bf-313">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-313">Event ID</span></span>|<span data-ttu-id="c62bf-314">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="c62bf-315">7</span><span class="sxs-lookup"><span data-stu-id="c62bf-315">7</span></span>|<span data-ttu-id="c62bf-316">A continuidade da suspensão do Common Language Runtime foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="c62bf-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="c62bf-317">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-317">No event data.</span></span>  
  
 [<span data-ttu-id="c62bf-318">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="c62bf-319">Evento GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="c62bf-320">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-321">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-321">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-322">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-324">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-325">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-326">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-326">Event</span></span>|<span data-ttu-id="c62bf-327">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-327">Event Id</span></span>|<span data-ttu-id="c62bf-328">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="c62bf-329">3</span><span class="sxs-lookup"><span data-stu-id="c62bf-329">3</span></span>|<span data-ttu-id="c62bf-330">A continuidade da suspensão do Common Language Runtime foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="c62bf-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="c62bf-331">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-331">No event data.</span></span>  
  
 [<span data-ttu-id="c62bf-332">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="c62bf-333">Evento GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="c62bf-334">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-335">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-335">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-336">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-338">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-339">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-340">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-340">Event</span></span>|<span data-ttu-id="c62bf-341">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-341">Event ID</span></span>|<span data-ttu-id="c62bf-342">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="c62bf-343">9</span><span class="sxs-lookup"><span data-stu-id="c62bf-343">9</span></span>|<span data-ttu-id="c62bf-344">Início da suspensão do mecanismo de execução da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="c62bf-345">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c62bf-346">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c62bf-346">Field name</span></span>|<span data-ttu-id="c62bf-347">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c62bf-347">Data type</span></span>|<span data-ttu-id="c62bf-348">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c62bf-349">Motivo</span><span class="sxs-lookup"><span data-stu-id="c62bf-349">Reason</span></span>|<span data-ttu-id="c62bf-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-350">win:UInt16</span></span>|<span data-ttu-id="c62bf-351">0x0 – Outros.</span><span class="sxs-lookup"><span data-stu-id="c62bf-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="c62bf-352">0x1 – Coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="c62bf-353">0x2 – Desligamento do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="c62bf-354">0x3 – Densidade do código.</span><span class="sxs-lookup"><span data-stu-id="c62bf-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="c62bf-355">0x4 – Desligamento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="c62bf-356">0x5 – Depurador.</span><span class="sxs-lookup"><span data-stu-id="c62bf-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="c62bf-357">0x6 – Preparação para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="c62bf-358">Contagem</span><span class="sxs-lookup"><span data-stu-id="c62bf-358">Count</span></span>|<span data-ttu-id="c62bf-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-359">win:UInt32</span></span>|<span data-ttu-id="c62bf-360">A contagem de GC no momento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-360">The GC count at the time.</span></span> <span data-ttu-id="c62bf-361">Normalmente, você verá um evento de Início de GC posterior depois disso e sua Contagem será essa Contagem + 1, conforme aumentamos o Índice de GC durante uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="c62bf-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c62bf-362">ClrInstanceID</span></span>|<span data-ttu-id="c62bf-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-363">win:UInt16</span></span>|<span data-ttu-id="c62bf-364">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c62bf-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c62bf-365">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="c62bf-366">Evento GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="c62bf-367">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="c62bf-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="c62bf-368">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-368">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-369">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-371">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-372">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c62bf-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="c62bf-373">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-373">Event</span></span>|<span data-ttu-id="c62bf-374">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-374">Event ID</span></span>|<span data-ttu-id="c62bf-375">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="c62bf-376">8</span><span class="sxs-lookup"><span data-stu-id="c62bf-376">8</span></span>|<span data-ttu-id="c62bf-377">Fim da suspensão do mecanismo de execução da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c62bf-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="c62bf-378">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-378">No event data.</span></span>  
  
 [<span data-ttu-id="c62bf-379">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="c62bf-380">Evento GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="c62bf-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="c62bf-381">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-382">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-382">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-383">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-385">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-386">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-387">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-387">Event</span></span>|<span data-ttu-id="c62bf-388">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-388">Event ID</span></span>|<span data-ttu-id="c62bf-389">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="c62bf-390">10</span><span class="sxs-lookup"><span data-stu-id="c62bf-390">10</span></span>|<span data-ttu-id="c62bf-391">A cada vez, aproximadamente 100 KB são alocados.</span><span class="sxs-lookup"><span data-stu-id="c62bf-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="c62bf-392">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c62bf-393">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c62bf-393">Field name</span></span>|<span data-ttu-id="c62bf-394">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c62bf-394">Data type</span></span>|<span data-ttu-id="c62bf-395">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c62bf-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="c62bf-396">AllocationAmount</span></span>|<span data-ttu-id="c62bf-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-397">win:UInt32</span></span>|<span data-ttu-id="c62bf-398">O tamanho de alocação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="c62bf-398">The allocation size, in bytes.</span></span> <span data-ttu-id="c62bf-399">Esse valor é preciso para alocações menores do que o tamanho de um ULONG (4.294.967.295 bytes).</span><span class="sxs-lookup"><span data-stu-id="c62bf-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="c62bf-400">Se a alocação for maior, esse campo conterá um valor truncado.</span><span class="sxs-lookup"><span data-stu-id="c62bf-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="c62bf-401">Use `AllocationAmount64` para alocações muito grandes.</span><span class="sxs-lookup"><span data-stu-id="c62bf-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="c62bf-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="c62bf-402">AllocationKind</span></span>|<span data-ttu-id="c62bf-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-403">win:UInt32</span></span>|<span data-ttu-id="c62bf-404">0x0 – Alocação de objeto pequeno (a alocação está no heap de objetos pequenos).</span><span class="sxs-lookup"><span data-stu-id="c62bf-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="c62bf-405">0x1 – Alocação de objeto grande (a alocação está no heap de objetos grandes).</span><span class="sxs-lookup"><span data-stu-id="c62bf-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="c62bf-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c62bf-406">ClrInstanceID</span></span>|<span data-ttu-id="c62bf-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-407">win:UInt16</span></span>|<span data-ttu-id="c62bf-408">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c62bf-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="c62bf-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="c62bf-409">AllocationAmount64</span></span>|<span data-ttu-id="c62bf-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c62bf-410">win:UInt64</span></span>|<span data-ttu-id="c62bf-411">O tamanho de alocação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="c62bf-411">The allocation size, in bytes.</span></span> <span data-ttu-id="c62bf-412">Esse valor é preciso para alocações muito grandes.</span><span class="sxs-lookup"><span data-stu-id="c62bf-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="c62bf-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="c62bf-413">TypeId</span></span>|<span data-ttu-id="c62bf-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="c62bf-414">win:Pointer</span></span>|<span data-ttu-id="c62bf-415">O endereço da MethodTable.</span><span class="sxs-lookup"><span data-stu-id="c62bf-415">The address of the MethodTable.</span></span> <span data-ttu-id="c62bf-416">Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o endereço da MethodTable que corresponde ao último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).</span><span class="sxs-lookup"><span data-stu-id="c62bf-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="c62bf-417">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="c62bf-417">TypeName</span></span>|<span data-ttu-id="c62bf-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c62bf-418">win:UnicodeString</span></span>|<span data-ttu-id="c62bf-419">O nome do tipo que foi alocado.</span><span class="sxs-lookup"><span data-stu-id="c62bf-419">The name of the type that was allocated.</span></span> <span data-ttu-id="c62bf-420">Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o tipo do último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).</span><span class="sxs-lookup"><span data-stu-id="c62bf-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="c62bf-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="c62bf-421">HeapIndex</span></span>|<span data-ttu-id="c62bf-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-422">win:UInt32</span></span>|<span data-ttu-id="c62bf-423">O heap em que o objeto foi alocado.</span><span class="sxs-lookup"><span data-stu-id="c62bf-423">The heap where the object was allocated.</span></span> <span data-ttu-id="c62bf-424">Esse valor é 0 (zero) durante a execução da coleta de lixo da estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c62bf-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="c62bf-425">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="c62bf-426">Evento GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="c62bf-427">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-428">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-428">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-429">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-431">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-432">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-433">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-433">Event</span></span>|<span data-ttu-id="c62bf-434">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-434">Event ID</span></span>|<span data-ttu-id="c62bf-435">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="c62bf-436">14</span><span class="sxs-lookup"><span data-stu-id="c62bf-436">14</span></span>|<span data-ttu-id="c62bf-437">O início da execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="c62bf-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="c62bf-438">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-438">No event data.</span></span>  
  
 [<span data-ttu-id="c62bf-439">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="c62bf-440">Evento GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="c62bf-441">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-442">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-442">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-443">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-445">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-446">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-447">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-447">Event</span></span>|<span data-ttu-id="c62bf-448">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-448">Event ID</span></span>|<span data-ttu-id="c62bf-449">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="c62bf-450">13</span><span class="sxs-lookup"><span data-stu-id="c62bf-450">13</span></span>|<span data-ttu-id="c62bf-451">O fim da execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="c62bf-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="c62bf-452">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c62bf-453">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c62bf-453">Field name</span></span>|<span data-ttu-id="c62bf-454">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c62bf-454">Data type</span></span>|<span data-ttu-id="c62bf-455">Descrição</span><span class="sxs-lookup"><span data-stu-id="c62bf-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c62bf-456">Contagem</span><span class="sxs-lookup"><span data-stu-id="c62bf-456">Count</span></span>|<span data-ttu-id="c62bf-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c62bf-457">win:UInt32</span></span>|<span data-ttu-id="c62bf-458">O número de finalizadores que foram executados.</span><span class="sxs-lookup"><span data-stu-id="c62bf-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="c62bf-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c62bf-459">ClrInstanceID</span></span>|<span data-ttu-id="c62bf-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c62bf-460">win:UInt16</span></span>|<span data-ttu-id="c62bf-461">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c62bf-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c62bf-462">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="c62bf-463">Evento GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="c62bf-464">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-465">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-465">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-466">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-468">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-468">Informational (4)</span></span>|  
|<span data-ttu-id="c62bf-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c62bf-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c62bf-470">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-471">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-472">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-472">Event</span></span>|<span data-ttu-id="c62bf-473">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-473">Event ID</span></span>|<span data-ttu-id="c62bf-474">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="c62bf-475">11</span><span class="sxs-lookup"><span data-stu-id="c62bf-475">11</span></span>|<span data-ttu-id="c62bf-476">O thread da coleta de lixo simultânea foi criado.</span><span class="sxs-lookup"><span data-stu-id="c62bf-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="c62bf-477">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-477">No event data.</span></span>  
  
 [<span data-ttu-id="c62bf-478">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c62bf-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="c62bf-479">Evento GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="c62bf-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="c62bf-480">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="c62bf-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c62bf-481">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-481">Keyword for raising the event</span></span>|<span data-ttu-id="c62bf-482">Nível</span><span class="sxs-lookup"><span data-stu-id="c62bf-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c62bf-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c62bf-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c62bf-484">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-484">Informational (4)</span></span>|  
|<span data-ttu-id="c62bf-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c62bf-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c62bf-486">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c62bf-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="c62bf-487">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c62bf-488">Evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-488">Event</span></span>|<span data-ttu-id="c62bf-489">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c62bf-489">Event ID</span></span>|<span data-ttu-id="c62bf-490">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c62bf-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="c62bf-491">12</span><span class="sxs-lookup"><span data-stu-id="c62bf-491">12</span></span>|<span data-ttu-id="c62bf-492">O thread da coleta de lixo simultânea foi terminado.</span><span class="sxs-lookup"><span data-stu-id="c62bf-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="c62bf-493">Nenhum dado do evento.</span><span class="sxs-lookup"><span data-stu-id="c62bf-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62bf-494">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c62bf-494">See Also</span></span>  
 [<span data-ttu-id="c62bf-495">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="c62bf-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
