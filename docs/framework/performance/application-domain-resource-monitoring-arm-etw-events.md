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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133816"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="cb839-102">Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)</span><span class="sxs-lookup"><span data-stu-id="cb839-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="cb839-103">Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb839-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="cb839-104">Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.</span><span class="sxs-lookup"><span data-stu-id="cb839-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="cb839-105">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="cb839-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="cb839-106">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="cb839-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="cb839-107">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="cb839-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="cb839-108">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="cb839-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="cb839-109">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="cb839-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="cb839-110">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="cb839-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="cb839-111">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="cb839-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="cb839-112">Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="cb839-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="cb839-113">Esse é o único evento acionado no provedor de encerramento nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="cb839-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="cb839-114">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="cb839-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="cb839-115">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="cb839-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="cb839-116">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="cb839-116">Keyword for raising the event</span></span>|<span data-ttu-id="cb839-117">Nível</span><span class="sxs-lookup"><span data-stu-id="cb839-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cb839-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="cb839-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="cb839-119">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="cb839-119">Informational(4)</span></span>|  
|<span data-ttu-id="cb839-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="cb839-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="cb839-121">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="cb839-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="cb839-122">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cb839-123">evento</span><span class="sxs-lookup"><span data-stu-id="cb839-123">Event</span></span>|<span data-ttu-id="cb839-124">ID do evento</span><span class="sxs-lookup"><span data-stu-id="cb839-124">Event ID</span></span>|<span data-ttu-id="cb839-125">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="cb839-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="cb839-126">85</span><span class="sxs-lookup"><span data-stu-id="cb839-126">85</span></span>|<span data-ttu-id="cb839-127">Um thread foi criado para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb839-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="cb839-128">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cb839-129">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="cb839-129">Field name</span></span>|<span data-ttu-id="cb839-130">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="cb839-130">Data type</span></span>|<span data-ttu-id="cb839-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb839-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cb839-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="cb839-132">ThreadID</span></span>|<span data-ttu-id="cb839-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-133">win:UInt64</span></span>|<span data-ttu-id="cb839-134">ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="cb839-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="cb839-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="cb839-135">AppDomainID</span></span>|<span data-ttu-id="cb839-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-136">win:UInt64</span></span>|<span data-ttu-id="cb839-137">Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.</span><span class="sxs-lookup"><span data-stu-id="cb839-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="cb839-138">Sinalizadores</span><span class="sxs-lookup"><span data-stu-id="cb839-138">Flags</span></span>|<span data-ttu-id="cb839-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="cb839-139">win:UInt32</span></span>|<span data-ttu-id="cb839-140">Sinalizadores de criação do thread.</span><span class="sxs-lookup"><span data-stu-id="cb839-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="cb839-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="cb839-141">ManagedThreadIndex</span></span>|<span data-ttu-id="cb839-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="cb839-142">win:UInt32</span></span>|<span data-ttu-id="cb839-143">Índice gerenciado do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="cb839-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="cb839-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="cb839-144">OSThreadID</span></span>|<span data-ttu-id="cb839-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="cb839-145">win:UInt32</span></span>|<span data-ttu-id="cb839-146">ID do sistema operacional do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="cb839-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="cb839-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cb839-147">ClrInstanceID</span></span>|<span data-ttu-id="cb839-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cb839-148">win:UInt16</span></span>|<span data-ttu-id="cb839-149">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cb839-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cb839-150">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="cb839-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="cb839-151">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="cb839-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="cb839-152">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="cb839-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cb839-153">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="cb839-153">Keyword for raising the event</span></span>|<span data-ttu-id="cb839-154">Nível</span><span class="sxs-lookup"><span data-stu-id="cb839-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cb839-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="cb839-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="cb839-156">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="cb839-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="cb839-157">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cb839-158">evento</span><span class="sxs-lookup"><span data-stu-id="cb839-158">Event</span></span>|<span data-ttu-id="cb839-159">ID do evento</span><span class="sxs-lookup"><span data-stu-id="cb839-159">Event ID</span></span>|<span data-ttu-id="cb839-160">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="cb839-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="cb839-161">83</span><span class="sxs-lookup"><span data-stu-id="cb839-161">83</span></span>|<span data-ttu-id="cb839-162">Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb839-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="cb839-163">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cb839-164">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="cb839-164">Field name</span></span>|<span data-ttu-id="cb839-165">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="cb839-165">Data type</span></span>|<span data-ttu-id="cb839-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb839-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cb839-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="cb839-167">AppDomainID</span></span>|<span data-ttu-id="cb839-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-168">win:UInt64</span></span>|<span data-ttu-id="cb839-169">Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="cb839-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="cb839-170">Alocado</span><span class="sxs-lookup"><span data-stu-id="cb839-170">Allocated</span></span>|<span data-ttu-id="cb839-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-171">win:UInt64</span></span>|<span data-ttu-id="cb839-172">O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).</span><span class="sxs-lookup"><span data-stu-id="cb839-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="cb839-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cb839-173">ClrInstanceID</span></span>|<span data-ttu-id="cb839-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cb839-174">win:UInt16</span></span>|<span data-ttu-id="cb839-175">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cb839-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cb839-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="cb839-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="cb839-177">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="cb839-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="cb839-178">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="cb839-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cb839-179">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="cb839-179">Keyword for raising the event</span></span>|<span data-ttu-id="cb839-180">Nível</span><span class="sxs-lookup"><span data-stu-id="cb839-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cb839-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="cb839-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="cb839-182">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="cb839-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="cb839-183">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cb839-184">evento</span><span class="sxs-lookup"><span data-stu-id="cb839-184">Event</span></span>|<span data-ttu-id="cb839-185">ID do evento</span><span class="sxs-lookup"><span data-stu-id="cb839-185">Event ID</span></span>|<span data-ttu-id="cb839-186">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="cb839-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="cb839-187">84</span><span class="sxs-lookup"><span data-stu-id="cb839-187">84</span></span>|<span data-ttu-id="cb839-188">Cada coleta de lixo é encerrada.</span><span class="sxs-lookup"><span data-stu-id="cb839-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="cb839-189">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cb839-190">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="cb839-190">Field name</span></span>|<span data-ttu-id="cb839-191">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="cb839-191">Data type</span></span>|<span data-ttu-id="cb839-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb839-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cb839-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="cb839-193">AppDomainID</span></span>|<span data-ttu-id="cb839-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-194">win:UInt64</span></span>|<span data-ttu-id="cb839-195">Identificador do domínio para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="cb839-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="cb839-196">Survived</span><span class="sxs-lookup"><span data-stu-id="cb839-196">Survived</span></span>|<span data-ttu-id="cb839-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-197">win:UInt64</span></span>|<span data-ttu-id="cb839-198">O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb839-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="cb839-199">Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.</span><span class="sxs-lookup"><span data-stu-id="cb839-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="cb839-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="cb839-200">ProcessSurvived</span></span>|<span data-ttu-id="cb839-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-201">win:UInt64</span></span>|<span data-ttu-id="cb839-202">O total de bytes que sobreviveram da última coleta.</span><span class="sxs-lookup"><span data-stu-id="cb839-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="cb839-203">Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="cb839-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="cb839-204">Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="cb839-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="cb839-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cb839-205">ClrInstanceID</span></span>|<span data-ttu-id="cb839-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cb839-206">win:UInt16</span></span>|<span data-ttu-id="cb839-207">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cb839-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cb839-208">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="cb839-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="cb839-209">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="cb839-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="cb839-210">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="cb839-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cb839-211">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="cb839-211">Keyword for raising the event</span></span>|<span data-ttu-id="cb839-212">Nível</span><span class="sxs-lookup"><span data-stu-id="cb839-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cb839-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="cb839-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="cb839-214">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="cb839-214">Informational(4)</span></span>|  
|<span data-ttu-id="cb839-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="cb839-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="cb839-216">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="cb839-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="cb839-217">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cb839-218">evento</span><span class="sxs-lookup"><span data-stu-id="cb839-218">Event</span></span>|<span data-ttu-id="cb839-219">ID do evento</span><span class="sxs-lookup"><span data-stu-id="cb839-219">Event ID</span></span>|<span data-ttu-id="cb839-220">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="cb839-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="cb839-221">87</span><span class="sxs-lookup"><span data-stu-id="cb839-221">87</span></span>|<span data-ttu-id="cb839-222">Um thread entra em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb839-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="cb839-223">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cb839-224">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="cb839-224">Field name</span></span>|<span data-ttu-id="cb839-225">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="cb839-225">Data type</span></span>|<span data-ttu-id="cb839-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb839-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cb839-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="cb839-227">ThreadID</span></span>|<span data-ttu-id="cb839-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-228">win:UInt64</span></span>|<span data-ttu-id="cb839-229">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="cb839-229">The thread identifier.</span></span>|  
|<span data-ttu-id="cb839-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="cb839-230">AppDomainID</span></span>|<span data-ttu-id="cb839-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-231">win:UInt64</span></span>|<span data-ttu-id="cb839-232">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb839-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="cb839-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cb839-233">ClrInstanceID</span></span>|<span data-ttu-id="cb839-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cb839-234">win:UInt16</span></span>|<span data-ttu-id="cb839-235">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cb839-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cb839-236">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="cb839-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="cb839-237">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="cb839-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="cb839-238">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="cb839-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cb839-239">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="cb839-239">Keyword for raising the event</span></span>|<span data-ttu-id="cb839-240">Nível</span><span class="sxs-lookup"><span data-stu-id="cb839-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cb839-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="cb839-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="cb839-242">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="cb839-242">Informational(4)</span></span>|  
|<span data-ttu-id="cb839-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="cb839-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="cb839-244">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="cb839-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="cb839-245">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="cb839-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cb839-246">evento</span><span class="sxs-lookup"><span data-stu-id="cb839-246">Event</span></span>|<span data-ttu-id="cb839-247">ID do evento</span><span class="sxs-lookup"><span data-stu-id="cb839-247">Event ID</span></span>|<span data-ttu-id="cb839-248">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="cb839-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="cb839-249">86</span><span class="sxs-lookup"><span data-stu-id="cb839-249">86</span></span>|<span data-ttu-id="cb839-250">Um thread termina.</span><span class="sxs-lookup"><span data-stu-id="cb839-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="cb839-251">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="cb839-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="cb839-252">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="cb839-252">Field name</span></span>|<span data-ttu-id="cb839-253">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="cb839-253">Data type</span></span>|<span data-ttu-id="cb839-254">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb839-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cb839-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="cb839-255">ThreadID</span></span>|<span data-ttu-id="cb839-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-256">win:UInt64</span></span>|<span data-ttu-id="cb839-257">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="cb839-257">The thread identifier.</span></span>|  
|<span data-ttu-id="cb839-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="cb839-258">AppDomainID</span></span>|<span data-ttu-id="cb839-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cb839-259">win:UInt64</span></span>|<span data-ttu-id="cb839-260">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb839-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="cb839-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cb839-261">ClrInstanceID</span></span>|<span data-ttu-id="cb839-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cb839-262">win:UInt16</span></span>|<span data-ttu-id="cb839-263">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cb839-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb839-264">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb839-264">See also</span></span>

- [<span data-ttu-id="cb839-265">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="cb839-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
