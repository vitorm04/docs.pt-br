---
title: Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bb2b0dd95877fc6492f6d23a19c14688cd78f7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133816"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="e3498-102">Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)</span><span class="sxs-lookup"><span data-stu-id="e3498-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="e3498-103">Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3498-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="e3498-104">Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.</span><span class="sxs-lookup"><span data-stu-id="e3498-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="e3498-105">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="e3498-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="e3498-106">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="e3498-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="e3498-107">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="e3498-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="e3498-108">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="e3498-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="e3498-109">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="e3498-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="e3498-110">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="e3498-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="e3498-111">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="e3498-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="e3498-112">Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="e3498-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="e3498-113">Esse é o único evento acionado no provedor de encerramento nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="e3498-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="e3498-114">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="e3498-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="e3498-115">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="e3498-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e3498-116">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="e3498-116">Keyword for raising the event</span></span>|<span data-ttu-id="e3498-117">Nível</span><span class="sxs-lookup"><span data-stu-id="e3498-117">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="e3498-118">(0x800)</span><span class="sxs-lookup"><span data-stu-id="e3498-118">(0x800)</span></span>|<span data-ttu-id="e3498-119">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="e3498-119">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="e3498-120">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="e3498-120">(0x10000)</span></span>|<span data-ttu-id="e3498-121">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="e3498-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="e3498-122">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e3498-123">evento</span><span class="sxs-lookup"><span data-stu-id="e3498-123">Event</span></span>|<span data-ttu-id="e3498-124">ID do evento</span><span class="sxs-lookup"><span data-stu-id="e3498-124">Event ID</span></span>|<span data-ttu-id="e3498-125">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="e3498-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="e3498-126">85</span><span class="sxs-lookup"><span data-stu-id="e3498-126">85</span></span>|<span data-ttu-id="e3498-127">Um thread foi criado para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3498-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="e3498-128">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e3498-129">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="e3498-129">Field name</span></span>|<span data-ttu-id="e3498-130">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="e3498-130">Data type</span></span>|<span data-ttu-id="e3498-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3498-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e3498-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e3498-132">ThreadID</span></span>|<span data-ttu-id="e3498-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-133">win:UInt64</span></span>|<span data-ttu-id="e3498-134">ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="e3498-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="e3498-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e3498-135">AppDomainID</span></span>|<span data-ttu-id="e3498-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-136">win:UInt64</span></span>|<span data-ttu-id="e3498-137">Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.</span><span class="sxs-lookup"><span data-stu-id="e3498-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="e3498-138">Sinalizadores</span><span class="sxs-lookup"><span data-stu-id="e3498-138">Flags</span></span>|<span data-ttu-id="e3498-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e3498-139">win:UInt32</span></span>|<span data-ttu-id="e3498-140">Sinalizadores de criação do thread.</span><span class="sxs-lookup"><span data-stu-id="e3498-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="e3498-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="e3498-141">ManagedThreadIndex</span></span>|<span data-ttu-id="e3498-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e3498-142">win:UInt32</span></span>|<span data-ttu-id="e3498-143">Índice gerenciado do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="e3498-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="e3498-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="e3498-144">OSThreadID</span></span>|<span data-ttu-id="e3498-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e3498-145">win:UInt32</span></span>|<span data-ttu-id="e3498-146">ID do sistema operacional do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="e3498-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="e3498-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e3498-147">ClrInstanceID</span></span>|<span data-ttu-id="e3498-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e3498-148">win:UInt16</span></span>|<span data-ttu-id="e3498-149">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e3498-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e3498-150">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="e3498-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="e3498-151">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="e3498-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="e3498-152">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="e3498-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e3498-153">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="e3498-153">Keyword for raising the event</span></span>|<span data-ttu-id="e3498-154">Nível</span><span class="sxs-lookup"><span data-stu-id="e3498-154">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="e3498-155">(0x800)</span><span class="sxs-lookup"><span data-stu-id="e3498-155">(0x800)</span></span>|<span data-ttu-id="e3498-156">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="e3498-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="e3498-157">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e3498-158">evento</span><span class="sxs-lookup"><span data-stu-id="e3498-158">Event</span></span>|<span data-ttu-id="e3498-159">ID do evento</span><span class="sxs-lookup"><span data-stu-id="e3498-159">Event ID</span></span>|<span data-ttu-id="e3498-160">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="e3498-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="e3498-161">83</span><span class="sxs-lookup"><span data-stu-id="e3498-161">83</span></span>|<span data-ttu-id="e3498-162">Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3498-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="e3498-163">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e3498-164">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="e3498-164">Field name</span></span>|<span data-ttu-id="e3498-165">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="e3498-165">Data type</span></span>|<span data-ttu-id="e3498-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3498-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e3498-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e3498-167">AppDomainID</span></span>|<span data-ttu-id="e3498-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-168">win:UInt64</span></span>|<span data-ttu-id="e3498-169">Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="e3498-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="e3498-170">Alocado</span><span class="sxs-lookup"><span data-stu-id="e3498-170">Allocated</span></span>|<span data-ttu-id="e3498-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-171">win:UInt64</span></span>|<span data-ttu-id="e3498-172">O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).</span><span class="sxs-lookup"><span data-stu-id="e3498-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="e3498-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e3498-173">ClrInstanceID</span></span>|<span data-ttu-id="e3498-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e3498-174">win:UInt16</span></span>|<span data-ttu-id="e3498-175">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e3498-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e3498-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="e3498-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="e3498-177">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="e3498-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="e3498-178">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="e3498-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e3498-179">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="e3498-179">Keyword for raising the event</span></span>|<span data-ttu-id="e3498-180">Nível</span><span class="sxs-lookup"><span data-stu-id="e3498-180">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="e3498-181">(0x800)</span><span class="sxs-lookup"><span data-stu-id="e3498-181">(0x800)</span></span>|<span data-ttu-id="e3498-182">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="e3498-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="e3498-183">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e3498-184">evento</span><span class="sxs-lookup"><span data-stu-id="e3498-184">Event</span></span>|<span data-ttu-id="e3498-185">ID do evento</span><span class="sxs-lookup"><span data-stu-id="e3498-185">Event ID</span></span>|<span data-ttu-id="e3498-186">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="e3498-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="e3498-187">84</span><span class="sxs-lookup"><span data-stu-id="e3498-187">84</span></span>|<span data-ttu-id="e3498-188">Cada coleta de lixo é encerrada.</span><span class="sxs-lookup"><span data-stu-id="e3498-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="e3498-189">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e3498-190">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="e3498-190">Field name</span></span>|<span data-ttu-id="e3498-191">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="e3498-191">Data type</span></span>|<span data-ttu-id="e3498-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3498-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e3498-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e3498-193">AppDomainID</span></span>|<span data-ttu-id="e3498-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-194">win:UInt64</span></span>|<span data-ttu-id="e3498-195">Identificador do domínio para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="e3498-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="e3498-196">Survived</span><span class="sxs-lookup"><span data-stu-id="e3498-196">Survived</span></span>|<span data-ttu-id="e3498-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-197">win:UInt64</span></span>|<span data-ttu-id="e3498-198">O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3498-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="e3498-199">Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.</span><span class="sxs-lookup"><span data-stu-id="e3498-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="e3498-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="e3498-200">ProcessSurvived</span></span>|<span data-ttu-id="e3498-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-201">win:UInt64</span></span>|<span data-ttu-id="e3498-202">O total de bytes que sobreviveram da última coleta.</span><span class="sxs-lookup"><span data-stu-id="e3498-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="e3498-203">Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e3498-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="e3498-204">Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="e3498-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="e3498-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e3498-205">ClrInstanceID</span></span>|<span data-ttu-id="e3498-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e3498-206">win:UInt16</span></span>|<span data-ttu-id="e3498-207">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e3498-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e3498-208">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="e3498-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="e3498-209">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="e3498-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="e3498-210">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="e3498-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e3498-211">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="e3498-211">Keyword for raising the event</span></span>|<span data-ttu-id="e3498-212">Nível</span><span class="sxs-lookup"><span data-stu-id="e3498-212">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="e3498-213">(0x800)</span><span class="sxs-lookup"><span data-stu-id="e3498-213">(0x800)</span></span>|<span data-ttu-id="e3498-214">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="e3498-214">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="e3498-215">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="e3498-215">(0x10000)</span></span>|<span data-ttu-id="e3498-216">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="e3498-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="e3498-217">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e3498-218">evento</span><span class="sxs-lookup"><span data-stu-id="e3498-218">Event</span></span>|<span data-ttu-id="e3498-219">ID do evento</span><span class="sxs-lookup"><span data-stu-id="e3498-219">Event ID</span></span>|<span data-ttu-id="e3498-220">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="e3498-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="e3498-221">87</span><span class="sxs-lookup"><span data-stu-id="e3498-221">87</span></span>|<span data-ttu-id="e3498-222">Um thread entra em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3498-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="e3498-223">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e3498-224">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="e3498-224">Field name</span></span>|<span data-ttu-id="e3498-225">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="e3498-225">Data type</span></span>|<span data-ttu-id="e3498-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3498-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e3498-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e3498-227">ThreadID</span></span>|<span data-ttu-id="e3498-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-228">win:UInt64</span></span>|<span data-ttu-id="e3498-229">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="e3498-229">The thread identifier.</span></span>|  
|<span data-ttu-id="e3498-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e3498-230">AppDomainID</span></span>|<span data-ttu-id="e3498-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-231">win:UInt64</span></span>|<span data-ttu-id="e3498-232">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3498-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="e3498-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e3498-233">ClrInstanceID</span></span>|<span data-ttu-id="e3498-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e3498-234">win:UInt16</span></span>|<span data-ttu-id="e3498-235">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e3498-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e3498-236">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="e3498-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="e3498-237">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="e3498-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="e3498-238">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="e3498-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e3498-239">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="e3498-239">Keyword for raising the event</span></span>|<span data-ttu-id="e3498-240">Nível</span><span class="sxs-lookup"><span data-stu-id="e3498-240">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="e3498-241">(0x800)</span><span class="sxs-lookup"><span data-stu-id="e3498-241">(0x800)</span></span>|<span data-ttu-id="e3498-242">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="e3498-242">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="e3498-243">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="e3498-243">(0x10000)</span></span>|<span data-ttu-id="e3498-244">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="e3498-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="e3498-245">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="e3498-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e3498-246">evento</span><span class="sxs-lookup"><span data-stu-id="e3498-246">Event</span></span>|<span data-ttu-id="e3498-247">ID do evento</span><span class="sxs-lookup"><span data-stu-id="e3498-247">Event ID</span></span>|<span data-ttu-id="e3498-248">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="e3498-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="e3498-249">86</span><span class="sxs-lookup"><span data-stu-id="e3498-249">86</span></span>|<span data-ttu-id="e3498-250">Um thread termina.</span><span class="sxs-lookup"><span data-stu-id="e3498-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="e3498-251">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="e3498-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="e3498-252">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="e3498-252">Field name</span></span>|<span data-ttu-id="e3498-253">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="e3498-253">Data type</span></span>|<span data-ttu-id="e3498-254">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3498-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e3498-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e3498-255">ThreadID</span></span>|<span data-ttu-id="e3498-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-256">win:UInt64</span></span>|<span data-ttu-id="e3498-257">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="e3498-257">The thread identifier.</span></span>|  
|<span data-ttu-id="e3498-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e3498-258">AppDomainID</span></span>|<span data-ttu-id="e3498-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e3498-259">win:UInt64</span></span>|<span data-ttu-id="e3498-260">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3498-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="e3498-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e3498-261">ClrInstanceID</span></span>|<span data-ttu-id="e3498-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e3498-262">win:UInt16</span></span>|<span data-ttu-id="e3498-263">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e3498-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3498-264">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3498-264">See also</span></span>

- [<span data-ttu-id="e3498-265">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="e3498-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
