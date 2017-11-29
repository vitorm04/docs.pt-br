---
title: "Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="fe09c-102">Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)</span><span class="sxs-lookup"><span data-stu-id="fe09c-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<span data-ttu-id="fe09c-103"><a name="top"></a> Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe09c-103"><a name="top"></a> These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="fe09c-104">Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.</span><span class="sxs-lookup"><span data-stu-id="fe09c-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="fe09c-105">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="fe09c-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="fe09c-106">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="fe09c-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="fe09c-107">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="fe09c-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="fe09c-108">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="fe09c-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="fe09c-109">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="fe09c-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="fe09c-110">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="fe09c-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="fe09c-111">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="fe09c-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="fe09c-112">Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="fe09c-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="fe09c-113">Esse é o único evento acionado no provedor de encerramento nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="fe09c-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="fe09c-114">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="fe09c-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="fe09c-115">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="fe09c-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="fe09c-116">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-116">Keyword for raising the event</span></span>|<span data-ttu-id="fe09c-117">Nível</span><span class="sxs-lookup"><span data-stu-id="fe09c-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fe09c-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe09c-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe09c-119">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="fe09c-119">Informational(4)</span></span>|  
|<span data-ttu-id="fe09c-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="fe09c-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fe09c-121">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="fe09c-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="fe09c-122">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fe09c-123">Evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-123">Event</span></span>|<span data-ttu-id="fe09c-124">ID do evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-124">Event ID</span></span>|<span data-ttu-id="fe09c-125">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="fe09c-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="fe09c-126">85</span><span class="sxs-lookup"><span data-stu-id="fe09c-126">85</span></span>|<span data-ttu-id="fe09c-127">Um thread foi criado para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe09c-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="fe09c-128">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fe09c-129">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="fe09c-129">Field name</span></span>|<span data-ttu-id="fe09c-130">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="fe09c-130">Data type</span></span>|<span data-ttu-id="fe09c-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe09c-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fe09c-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="fe09c-132">ThreadID</span></span>|<span data-ttu-id="fe09c-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-133">win:UInt64</span></span>|<span data-ttu-id="fe09c-134">ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="fe09c-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="fe09c-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe09c-135">AppDomainID</span></span>|<span data-ttu-id="fe09c-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-136">win:UInt64</span></span>|<span data-ttu-id="fe09c-137">Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.</span><span class="sxs-lookup"><span data-stu-id="fe09c-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="fe09c-138">Sinalizadores</span><span class="sxs-lookup"><span data-stu-id="fe09c-138">Flags</span></span>|<span data-ttu-id="fe09c-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="fe09c-139">win:UInt32</span></span>|<span data-ttu-id="fe09c-140">Sinalizadores de criação do thread.</span><span class="sxs-lookup"><span data-stu-id="fe09c-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="fe09c-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="fe09c-141">ManagedThreadIndex</span></span>|<span data-ttu-id="fe09c-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="fe09c-142">win:UInt32</span></span>|<span data-ttu-id="fe09c-143">Índice gerenciado do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="fe09c-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="fe09c-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="fe09c-144">OSThreadID</span></span>|<span data-ttu-id="fe09c-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="fe09c-145">win:UInt32</span></span>|<span data-ttu-id="fe09c-146">ID do sistema operacional do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="fe09c-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="fe09c-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe09c-147">ClrInstanceID</span></span>|<span data-ttu-id="fe09c-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="fe09c-148">win:UInt16</span></span>|<span data-ttu-id="fe09c-149">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe09c-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fe09c-150">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="fe09c-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="fe09c-151">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="fe09c-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="fe09c-152">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="fe09c-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fe09c-153">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-153">Keyword for raising the event</span></span>|<span data-ttu-id="fe09c-154">Nível</span><span class="sxs-lookup"><span data-stu-id="fe09c-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fe09c-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe09c-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe09c-156">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="fe09c-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="fe09c-157">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fe09c-158">Evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-158">Event</span></span>|<span data-ttu-id="fe09c-159">ID do evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-159">Event ID</span></span>|<span data-ttu-id="fe09c-160">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="fe09c-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="fe09c-161">83</span><span class="sxs-lookup"><span data-stu-id="fe09c-161">83</span></span>|<span data-ttu-id="fe09c-162">Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe09c-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="fe09c-163">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fe09c-164">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="fe09c-164">Field name</span></span>|<span data-ttu-id="fe09c-165">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="fe09c-165">Data type</span></span>|<span data-ttu-id="fe09c-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe09c-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fe09c-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe09c-167">AppDomainID</span></span>|<span data-ttu-id="fe09c-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-168">win:UInt64</span></span>|<span data-ttu-id="fe09c-169">Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="fe09c-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="fe09c-170">Alocado</span><span class="sxs-lookup"><span data-stu-id="fe09c-170">Allocated</span></span>|<span data-ttu-id="fe09c-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-171">win:UInt64</span></span>|<span data-ttu-id="fe09c-172">O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).</span><span class="sxs-lookup"><span data-stu-id="fe09c-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="fe09c-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe09c-173">ClrInstanceID</span></span>|<span data-ttu-id="fe09c-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="fe09c-174">win:UInt16</span></span>|<span data-ttu-id="fe09c-175">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe09c-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fe09c-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="fe09c-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="fe09c-177">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="fe09c-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="fe09c-178">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="fe09c-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fe09c-179">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-179">Keyword for raising the event</span></span>|<span data-ttu-id="fe09c-180">Nível</span><span class="sxs-lookup"><span data-stu-id="fe09c-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fe09c-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe09c-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe09c-182">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="fe09c-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="fe09c-183">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fe09c-184">Evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-184">Event</span></span>|<span data-ttu-id="fe09c-185">ID do evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-185">Event ID</span></span>|<span data-ttu-id="fe09c-186">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="fe09c-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="fe09c-187">84</span><span class="sxs-lookup"><span data-stu-id="fe09c-187">84</span></span>|<span data-ttu-id="fe09c-188">Cada coleta de lixo é encerrada.</span><span class="sxs-lookup"><span data-stu-id="fe09c-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="fe09c-189">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fe09c-190">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="fe09c-190">Field name</span></span>|<span data-ttu-id="fe09c-191">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="fe09c-191">Data type</span></span>|<span data-ttu-id="fe09c-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe09c-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fe09c-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe09c-193">AppDomainID</span></span>|<span data-ttu-id="fe09c-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-194">win:UInt64</span></span>|<span data-ttu-id="fe09c-195">Identificador do domínio para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="fe09c-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="fe09c-196">Survived</span><span class="sxs-lookup"><span data-stu-id="fe09c-196">Survived</span></span>|<span data-ttu-id="fe09c-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-197">win:UInt64</span></span>|<span data-ttu-id="fe09c-198">O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe09c-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="fe09c-199">Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.</span><span class="sxs-lookup"><span data-stu-id="fe09c-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="fe09c-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="fe09c-200">ProcessSurvived</span></span>|<span data-ttu-id="fe09c-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-201">win:UInt64</span></span>|<span data-ttu-id="fe09c-202">O total de bytes que sobreviveram da última coleta.</span><span class="sxs-lookup"><span data-stu-id="fe09c-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="fe09c-203">Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="fe09c-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="fe09c-204">Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="fe09c-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="fe09c-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe09c-205">ClrInstanceID</span></span>|<span data-ttu-id="fe09c-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="fe09c-206">win:UInt16</span></span>|<span data-ttu-id="fe09c-207">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe09c-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fe09c-208">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="fe09c-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="fe09c-209">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="fe09c-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="fe09c-210">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="fe09c-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fe09c-211">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-211">Keyword for raising the event</span></span>|<span data-ttu-id="fe09c-212">Nível</span><span class="sxs-lookup"><span data-stu-id="fe09c-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fe09c-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe09c-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe09c-214">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="fe09c-214">Informational(4)</span></span>|  
|<span data-ttu-id="fe09c-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="fe09c-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fe09c-216">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="fe09c-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="fe09c-217">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fe09c-218">Evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-218">Event</span></span>|<span data-ttu-id="fe09c-219">ID do evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-219">Event ID</span></span>|<span data-ttu-id="fe09c-220">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="fe09c-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="fe09c-221">87</span><span class="sxs-lookup"><span data-stu-id="fe09c-221">87</span></span>|<span data-ttu-id="fe09c-222">Um thread entra em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe09c-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="fe09c-223">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fe09c-224">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="fe09c-224">Field name</span></span>|<span data-ttu-id="fe09c-225">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="fe09c-225">Data type</span></span>|<span data-ttu-id="fe09c-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe09c-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fe09c-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="fe09c-227">ThreadID</span></span>|<span data-ttu-id="fe09c-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-228">win:UInt64</span></span>|<span data-ttu-id="fe09c-229">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="fe09c-229">The thread identifier.</span></span>|  
|<span data-ttu-id="fe09c-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe09c-230">AppDomainID</span></span>|<span data-ttu-id="fe09c-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-231">win:UInt64</span></span>|<span data-ttu-id="fe09c-232">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe09c-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="fe09c-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe09c-233">ClrInstanceID</span></span>|<span data-ttu-id="fe09c-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="fe09c-234">win:UInt16</span></span>|<span data-ttu-id="fe09c-235">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe09c-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fe09c-236">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="fe09c-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="fe09c-237">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="fe09c-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="fe09c-238">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="fe09c-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fe09c-239">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-239">Keyword for raising the event</span></span>|<span data-ttu-id="fe09c-240">Nível</span><span class="sxs-lookup"><span data-stu-id="fe09c-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fe09c-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe09c-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe09c-242">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="fe09c-242">Informational(4)</span></span>|  
|<span data-ttu-id="fe09c-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="fe09c-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fe09c-244">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="fe09c-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="fe09c-245">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="fe09c-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fe09c-246">Evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-246">Event</span></span>|<span data-ttu-id="fe09c-247">ID do evento</span><span class="sxs-lookup"><span data-stu-id="fe09c-247">Event ID</span></span>|<span data-ttu-id="fe09c-248">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="fe09c-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="fe09c-249">86</span><span class="sxs-lookup"><span data-stu-id="fe09c-249">86</span></span>|<span data-ttu-id="fe09c-250">Um thread termina.</span><span class="sxs-lookup"><span data-stu-id="fe09c-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="fe09c-251">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="fe09c-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="fe09c-252">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="fe09c-252">Field name</span></span>|<span data-ttu-id="fe09c-253">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="fe09c-253">Data type</span></span>|<span data-ttu-id="fe09c-254">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe09c-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fe09c-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="fe09c-255">ThreadID</span></span>|<span data-ttu-id="fe09c-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-256">win:UInt64</span></span>|<span data-ttu-id="fe09c-257">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="fe09c-257">The thread identifier.</span></span>|  
|<span data-ttu-id="fe09c-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe09c-258">AppDomainID</span></span>|<span data-ttu-id="fe09c-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="fe09c-259">win:UInt64</span></span>|<span data-ttu-id="fe09c-260">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe09c-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="fe09c-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe09c-261">ClrInstanceID</span></span>|<span data-ttu-id="fe09c-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="fe09c-262">win:UInt16</span></span>|<span data-ttu-id="fe09c-263">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe09c-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe09c-264">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe09c-264">See Also</span></span>  
 [<span data-ttu-id="fe09c-265">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="fe09c-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
