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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788057"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="da67a-102">Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)</span><span class="sxs-lookup"><span data-stu-id="da67a-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="da67a-103">Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da67a-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="da67a-104">Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.</span><span class="sxs-lookup"><span data-stu-id="da67a-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="da67a-105">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="da67a-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="da67a-106">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="da67a-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="da67a-107">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="da67a-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="da67a-108">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="da67a-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="da67a-109">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="da67a-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="da67a-110">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="da67a-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="da67a-111">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="da67a-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="da67a-112">Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="da67a-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="da67a-113">Esse é o único evento acionado no provedor de encerramento nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="da67a-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="da67a-114">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="da67a-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="da67a-115">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="da67a-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="da67a-116">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="da67a-116">Keyword for raising the event</span></span>|<span data-ttu-id="da67a-117">Nível</span><span class="sxs-lookup"><span data-stu-id="da67a-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="da67a-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="da67a-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="da67a-119">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="da67a-119">Informational(4)</span></span>|  
|<span data-ttu-id="da67a-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="da67a-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="da67a-121">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="da67a-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="da67a-122">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="da67a-123">evento</span><span class="sxs-lookup"><span data-stu-id="da67a-123">Event</span></span>|<span data-ttu-id="da67a-124">ID do evento</span><span class="sxs-lookup"><span data-stu-id="da67a-124">Event ID</span></span>|<span data-ttu-id="da67a-125">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="da67a-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="da67a-126">85</span><span class="sxs-lookup"><span data-stu-id="da67a-126">85</span></span>|<span data-ttu-id="da67a-127">Um thread foi criado para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da67a-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="da67a-128">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="da67a-129">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="da67a-129">Field name</span></span>|<span data-ttu-id="da67a-130">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="da67a-130">Data type</span></span>|<span data-ttu-id="da67a-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="da67a-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="da67a-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="da67a-132">ThreadID</span></span>|<span data-ttu-id="da67a-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-133">win:UInt64</span></span>|<span data-ttu-id="da67a-134">ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="da67a-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="da67a-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="da67a-135">AppDomainID</span></span>|<span data-ttu-id="da67a-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-136">win:UInt64</span></span>|<span data-ttu-id="da67a-137">Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.</span><span class="sxs-lookup"><span data-stu-id="da67a-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="da67a-138">Sinalizadores</span><span class="sxs-lookup"><span data-stu-id="da67a-138">Flags</span></span>|<span data-ttu-id="da67a-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="da67a-139">win:UInt32</span></span>|<span data-ttu-id="da67a-140">Sinalizadores de criação do thread.</span><span class="sxs-lookup"><span data-stu-id="da67a-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="da67a-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="da67a-141">ManagedThreadIndex</span></span>|<span data-ttu-id="da67a-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="da67a-142">win:UInt32</span></span>|<span data-ttu-id="da67a-143">Índice gerenciado do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="da67a-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="da67a-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="da67a-144">OSThreadID</span></span>|<span data-ttu-id="da67a-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="da67a-145">win:UInt32</span></span>|<span data-ttu-id="da67a-146">ID do sistema operacional do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="da67a-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="da67a-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="da67a-147">ClrInstanceID</span></span>|<span data-ttu-id="da67a-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="da67a-148">win:UInt16</span></span>|<span data-ttu-id="da67a-149">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="da67a-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="da67a-150">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="da67a-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="da67a-151">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="da67a-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="da67a-152">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="da67a-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="da67a-153">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="da67a-153">Keyword for raising the event</span></span>|<span data-ttu-id="da67a-154">Nível</span><span class="sxs-lookup"><span data-stu-id="da67a-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="da67a-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="da67a-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="da67a-156">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="da67a-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="da67a-157">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="da67a-158">evento</span><span class="sxs-lookup"><span data-stu-id="da67a-158">Event</span></span>|<span data-ttu-id="da67a-159">ID do evento</span><span class="sxs-lookup"><span data-stu-id="da67a-159">Event ID</span></span>|<span data-ttu-id="da67a-160">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="da67a-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="da67a-161">83</span><span class="sxs-lookup"><span data-stu-id="da67a-161">83</span></span>|<span data-ttu-id="da67a-162">Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da67a-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="da67a-163">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="da67a-164">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="da67a-164">Field name</span></span>|<span data-ttu-id="da67a-165">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="da67a-165">Data type</span></span>|<span data-ttu-id="da67a-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="da67a-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="da67a-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="da67a-167">AppDomainID</span></span>|<span data-ttu-id="da67a-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-168">win:UInt64</span></span>|<span data-ttu-id="da67a-169">Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="da67a-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="da67a-170">Alocado</span><span class="sxs-lookup"><span data-stu-id="da67a-170">Allocated</span></span>|<span data-ttu-id="da67a-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-171">win:UInt64</span></span>|<span data-ttu-id="da67a-172">O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).</span><span class="sxs-lookup"><span data-stu-id="da67a-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="da67a-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="da67a-173">ClrInstanceID</span></span>|<span data-ttu-id="da67a-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="da67a-174">win:UInt16</span></span>|<span data-ttu-id="da67a-175">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="da67a-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="da67a-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="da67a-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="da67a-177">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="da67a-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="da67a-178">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="da67a-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="da67a-179">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="da67a-179">Keyword for raising the event</span></span>|<span data-ttu-id="da67a-180">Nível</span><span class="sxs-lookup"><span data-stu-id="da67a-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="da67a-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="da67a-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="da67a-182">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="da67a-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="da67a-183">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="da67a-184">evento</span><span class="sxs-lookup"><span data-stu-id="da67a-184">Event</span></span>|<span data-ttu-id="da67a-185">ID do evento</span><span class="sxs-lookup"><span data-stu-id="da67a-185">Event ID</span></span>|<span data-ttu-id="da67a-186">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="da67a-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="da67a-187">84</span><span class="sxs-lookup"><span data-stu-id="da67a-187">84</span></span>|<span data-ttu-id="da67a-188">Cada coleta de lixo é encerrada.</span><span class="sxs-lookup"><span data-stu-id="da67a-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="da67a-189">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="da67a-190">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="da67a-190">Field name</span></span>|<span data-ttu-id="da67a-191">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="da67a-191">Data type</span></span>|<span data-ttu-id="da67a-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="da67a-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="da67a-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="da67a-193">AppDomainID</span></span>|<span data-ttu-id="da67a-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-194">win:UInt64</span></span>|<span data-ttu-id="da67a-195">Identificador do domínio para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="da67a-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="da67a-196">Survived</span><span class="sxs-lookup"><span data-stu-id="da67a-196">Survived</span></span>|<span data-ttu-id="da67a-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-197">win:UInt64</span></span>|<span data-ttu-id="da67a-198">O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da67a-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="da67a-199">Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.</span><span class="sxs-lookup"><span data-stu-id="da67a-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="da67a-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="da67a-200">ProcessSurvived</span></span>|<span data-ttu-id="da67a-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-201">win:UInt64</span></span>|<span data-ttu-id="da67a-202">O total de bytes que sobreviveram da última coleta.</span><span class="sxs-lookup"><span data-stu-id="da67a-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="da67a-203">Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="da67a-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="da67a-204">Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="da67a-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="da67a-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="da67a-205">ClrInstanceID</span></span>|<span data-ttu-id="da67a-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="da67a-206">win:UInt16</span></span>|<span data-ttu-id="da67a-207">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="da67a-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="da67a-208">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="da67a-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="da67a-209">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="da67a-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="da67a-210">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="da67a-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="da67a-211">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="da67a-211">Keyword for raising the event</span></span>|<span data-ttu-id="da67a-212">Nível</span><span class="sxs-lookup"><span data-stu-id="da67a-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="da67a-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="da67a-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="da67a-214">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="da67a-214">Informational(4)</span></span>|  
|<span data-ttu-id="da67a-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="da67a-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="da67a-216">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="da67a-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="da67a-217">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="da67a-218">evento</span><span class="sxs-lookup"><span data-stu-id="da67a-218">Event</span></span>|<span data-ttu-id="da67a-219">ID do evento</span><span class="sxs-lookup"><span data-stu-id="da67a-219">Event ID</span></span>|<span data-ttu-id="da67a-220">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="da67a-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="da67a-221">87</span><span class="sxs-lookup"><span data-stu-id="da67a-221">87</span></span>|<span data-ttu-id="da67a-222">Um thread entra em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da67a-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="da67a-223">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="da67a-224">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="da67a-224">Field name</span></span>|<span data-ttu-id="da67a-225">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="da67a-225">Data type</span></span>|<span data-ttu-id="da67a-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="da67a-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="da67a-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="da67a-227">ThreadID</span></span>|<span data-ttu-id="da67a-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-228">win:UInt64</span></span>|<span data-ttu-id="da67a-229">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="da67a-229">The thread identifier.</span></span>|  
|<span data-ttu-id="da67a-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="da67a-230">AppDomainID</span></span>|<span data-ttu-id="da67a-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-231">win:UInt64</span></span>|<span data-ttu-id="da67a-232">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da67a-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="da67a-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="da67a-233">ClrInstanceID</span></span>|<span data-ttu-id="da67a-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="da67a-234">win:UInt16</span></span>|<span data-ttu-id="da67a-235">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="da67a-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="da67a-236">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="da67a-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="da67a-237">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="da67a-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="da67a-238">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="da67a-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="da67a-239">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="da67a-239">Keyword for raising the event</span></span>|<span data-ttu-id="da67a-240">Nível</span><span class="sxs-lookup"><span data-stu-id="da67a-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="da67a-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="da67a-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="da67a-242">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="da67a-242">Informational(4)</span></span>|  
|<span data-ttu-id="da67a-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="da67a-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="da67a-244">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="da67a-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="da67a-245">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="da67a-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="da67a-246">evento</span><span class="sxs-lookup"><span data-stu-id="da67a-246">Event</span></span>|<span data-ttu-id="da67a-247">ID do evento</span><span class="sxs-lookup"><span data-stu-id="da67a-247">Event ID</span></span>|<span data-ttu-id="da67a-248">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="da67a-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="da67a-249">86</span><span class="sxs-lookup"><span data-stu-id="da67a-249">86</span></span>|<span data-ttu-id="da67a-250">Um thread termina.</span><span class="sxs-lookup"><span data-stu-id="da67a-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="da67a-251">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="da67a-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="da67a-252">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="da67a-252">Field name</span></span>|<span data-ttu-id="da67a-253">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="da67a-253">Data type</span></span>|<span data-ttu-id="da67a-254">Descrição</span><span class="sxs-lookup"><span data-stu-id="da67a-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="da67a-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="da67a-255">ThreadID</span></span>|<span data-ttu-id="da67a-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-256">win:UInt64</span></span>|<span data-ttu-id="da67a-257">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="da67a-257">The thread identifier.</span></span>|  
|<span data-ttu-id="da67a-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="da67a-258">AppDomainID</span></span>|<span data-ttu-id="da67a-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="da67a-259">win:UInt64</span></span>|<span data-ttu-id="da67a-260">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da67a-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="da67a-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="da67a-261">ClrInstanceID</span></span>|<span data-ttu-id="da67a-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="da67a-262">win:UInt16</span></span>|<span data-ttu-id="da67a-263">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="da67a-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da67a-264">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da67a-264">See also</span></span>

- [<span data-ttu-id="da67a-265">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="da67a-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
