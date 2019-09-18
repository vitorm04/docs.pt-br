---
title: Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e4002ae248022a9e4380c79174109494b5e4ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046778"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="26ef0-102">Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)</span><span class="sxs-lookup"><span data-stu-id="26ef0-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="26ef0-103">Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ef0-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="26ef0-104">Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.</span><span class="sxs-lookup"><span data-stu-id="26ef0-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="26ef0-105">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="26ef0-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="26ef0-106">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="26ef0-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="26ef0-107">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="26ef0-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="26ef0-108">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="26ef0-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="26ef0-109">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="26ef0-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="26ef0-110">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="26ef0-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="26ef0-111">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="26ef0-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="26ef0-112">Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="26ef0-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="26ef0-113">Esse é o único evento acionado no provedor de encerramento nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="26ef0-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="26ef0-114">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="26ef0-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="26ef0-115">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="26ef0-115">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="26ef0-116">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-116">Keyword for raising the event</span></span>|<span data-ttu-id="26ef0-117">Nível</span><span class="sxs-lookup"><span data-stu-id="26ef0-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="26ef0-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="26ef0-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="26ef0-119">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="26ef0-119">Informational(4)</span></span>|  
|<span data-ttu-id="26ef0-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="26ef0-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="26ef0-121">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="26ef0-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="26ef0-122">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="26ef0-123">evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-123">Event</span></span>|<span data-ttu-id="26ef0-124">ID do evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-124">Event ID</span></span>|<span data-ttu-id="26ef0-125">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="26ef0-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="26ef0-126">85</span><span class="sxs-lookup"><span data-stu-id="26ef0-126">85</span></span>|<span data-ttu-id="26ef0-127">Um thread foi criado para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ef0-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="26ef0-128">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="26ef0-129">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="26ef0-129">Field name</span></span>|<span data-ttu-id="26ef0-130">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="26ef0-130">Data type</span></span>|<span data-ttu-id="26ef0-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="26ef0-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="26ef0-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="26ef0-132">ThreadID</span></span>|<span data-ttu-id="26ef0-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-133">win:UInt64</span></span>|<span data-ttu-id="26ef0-134">ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="26ef0-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="26ef0-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="26ef0-135">AppDomainID</span></span>|<span data-ttu-id="26ef0-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-136">win:UInt64</span></span>|<span data-ttu-id="26ef0-137">Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.</span><span class="sxs-lookup"><span data-stu-id="26ef0-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="26ef0-138">Sinalizadores</span><span class="sxs-lookup"><span data-stu-id="26ef0-138">Flags</span></span>|<span data-ttu-id="26ef0-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="26ef0-139">win:UInt32</span></span>|<span data-ttu-id="26ef0-140">Sinalizadores de criação do thread.</span><span class="sxs-lookup"><span data-stu-id="26ef0-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="26ef0-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="26ef0-141">ManagedThreadIndex</span></span>|<span data-ttu-id="26ef0-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="26ef0-142">win:UInt32</span></span>|<span data-ttu-id="26ef0-143">Índice gerenciado do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="26ef0-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="26ef0-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="26ef0-144">OSThreadID</span></span>|<span data-ttu-id="26ef0-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="26ef0-145">win:UInt32</span></span>|<span data-ttu-id="26ef0-146">ID do sistema operacional do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="26ef0-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="26ef0-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="26ef0-147">ClrInstanceID</span></span>|<span data-ttu-id="26ef0-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="26ef0-148">win:UInt16</span></span>|<span data-ttu-id="26ef0-149">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="26ef0-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="26ef0-150">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="26ef0-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="26ef0-151">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="26ef0-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="26ef0-152">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="26ef0-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="26ef0-153">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-153">Keyword for raising the event</span></span>|<span data-ttu-id="26ef0-154">Nível</span><span class="sxs-lookup"><span data-stu-id="26ef0-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="26ef0-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="26ef0-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="26ef0-156">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="26ef0-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="26ef0-157">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="26ef0-158">evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-158">Event</span></span>|<span data-ttu-id="26ef0-159">ID do evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-159">Event ID</span></span>|<span data-ttu-id="26ef0-160">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="26ef0-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="26ef0-161">83</span><span class="sxs-lookup"><span data-stu-id="26ef0-161">83</span></span>|<span data-ttu-id="26ef0-162">Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ef0-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="26ef0-163">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="26ef0-164">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="26ef0-164">Field name</span></span>|<span data-ttu-id="26ef0-165">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="26ef0-165">Data type</span></span>|<span data-ttu-id="26ef0-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="26ef0-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="26ef0-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="26ef0-167">AppDomainID</span></span>|<span data-ttu-id="26ef0-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-168">win:UInt64</span></span>|<span data-ttu-id="26ef0-169">Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="26ef0-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="26ef0-170">Alocado</span><span class="sxs-lookup"><span data-stu-id="26ef0-170">Allocated</span></span>|<span data-ttu-id="26ef0-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-171">win:UInt64</span></span>|<span data-ttu-id="26ef0-172">O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).</span><span class="sxs-lookup"><span data-stu-id="26ef0-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="26ef0-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="26ef0-173">ClrInstanceID</span></span>|<span data-ttu-id="26ef0-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="26ef0-174">win:UInt16</span></span>|<span data-ttu-id="26ef0-175">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="26ef0-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="26ef0-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="26ef0-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="26ef0-177">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="26ef0-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="26ef0-178">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="26ef0-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="26ef0-179">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-179">Keyword for raising the event</span></span>|<span data-ttu-id="26ef0-180">Nível</span><span class="sxs-lookup"><span data-stu-id="26ef0-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="26ef0-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="26ef0-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="26ef0-182">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="26ef0-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="26ef0-183">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="26ef0-184">evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-184">Event</span></span>|<span data-ttu-id="26ef0-185">ID do evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-185">Event ID</span></span>|<span data-ttu-id="26ef0-186">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="26ef0-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="26ef0-187">84</span><span class="sxs-lookup"><span data-stu-id="26ef0-187">84</span></span>|<span data-ttu-id="26ef0-188">Cada coleta de lixo é encerrada.</span><span class="sxs-lookup"><span data-stu-id="26ef0-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="26ef0-189">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="26ef0-190">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="26ef0-190">Field name</span></span>|<span data-ttu-id="26ef0-191">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="26ef0-191">Data type</span></span>|<span data-ttu-id="26ef0-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="26ef0-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="26ef0-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="26ef0-193">AppDomainID</span></span>|<span data-ttu-id="26ef0-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-194">win:UInt64</span></span>|<span data-ttu-id="26ef0-195">Identificador do domínio para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="26ef0-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="26ef0-196">Survived</span><span class="sxs-lookup"><span data-stu-id="26ef0-196">Survived</span></span>|<span data-ttu-id="26ef0-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-197">win:UInt64</span></span>|<span data-ttu-id="26ef0-198">O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ef0-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="26ef0-199">Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.</span><span class="sxs-lookup"><span data-stu-id="26ef0-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="26ef0-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="26ef0-200">ProcessSurvived</span></span>|<span data-ttu-id="26ef0-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-201">win:UInt64</span></span>|<span data-ttu-id="26ef0-202">O total de bytes que sobreviveram da última coleta.</span><span class="sxs-lookup"><span data-stu-id="26ef0-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="26ef0-203">Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="26ef0-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="26ef0-204">Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="26ef0-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="26ef0-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="26ef0-205">ClrInstanceID</span></span>|<span data-ttu-id="26ef0-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="26ef0-206">win:UInt16</span></span>|<span data-ttu-id="26ef0-207">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="26ef0-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="26ef0-208">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="26ef0-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="26ef0-209">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="26ef0-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="26ef0-210">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="26ef0-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="26ef0-211">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-211">Keyword for raising the event</span></span>|<span data-ttu-id="26ef0-212">Nível</span><span class="sxs-lookup"><span data-stu-id="26ef0-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="26ef0-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="26ef0-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="26ef0-214">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="26ef0-214">Informational(4)</span></span>|  
|<span data-ttu-id="26ef0-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="26ef0-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="26ef0-216">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="26ef0-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="26ef0-217">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="26ef0-218">evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-218">Event</span></span>|<span data-ttu-id="26ef0-219">ID do evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-219">Event ID</span></span>|<span data-ttu-id="26ef0-220">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="26ef0-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="26ef0-221">87</span><span class="sxs-lookup"><span data-stu-id="26ef0-221">87</span></span>|<span data-ttu-id="26ef0-222">Um thread entra em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ef0-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="26ef0-223">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="26ef0-224">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="26ef0-224">Field name</span></span>|<span data-ttu-id="26ef0-225">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="26ef0-225">Data type</span></span>|<span data-ttu-id="26ef0-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="26ef0-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="26ef0-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="26ef0-227">ThreadID</span></span>|<span data-ttu-id="26ef0-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-228">win:UInt64</span></span>|<span data-ttu-id="26ef0-229">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="26ef0-229">The thread identifier.</span></span>|  
|<span data-ttu-id="26ef0-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="26ef0-230">AppDomainID</span></span>|<span data-ttu-id="26ef0-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-231">win:UInt64</span></span>|<span data-ttu-id="26ef0-232">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ef0-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="26ef0-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="26ef0-233">ClrInstanceID</span></span>|<span data-ttu-id="26ef0-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="26ef0-234">win:UInt16</span></span>|<span data-ttu-id="26ef0-235">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="26ef0-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="26ef0-236">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="26ef0-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="26ef0-237">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="26ef0-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="26ef0-238">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="26ef0-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="26ef0-239">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-239">Keyword for raising the event</span></span>|<span data-ttu-id="26ef0-240">Nível</span><span class="sxs-lookup"><span data-stu-id="26ef0-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="26ef0-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="26ef0-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="26ef0-242">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="26ef0-242">Informational(4)</span></span>|  
|<span data-ttu-id="26ef0-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="26ef0-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="26ef0-244">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="26ef0-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="26ef0-245">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="26ef0-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="26ef0-246">evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-246">Event</span></span>|<span data-ttu-id="26ef0-247">ID do evento</span><span class="sxs-lookup"><span data-stu-id="26ef0-247">Event ID</span></span>|<span data-ttu-id="26ef0-248">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="26ef0-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="26ef0-249">86</span><span class="sxs-lookup"><span data-stu-id="26ef0-249">86</span></span>|<span data-ttu-id="26ef0-250">Um thread termina.</span><span class="sxs-lookup"><span data-stu-id="26ef0-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="26ef0-251">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="26ef0-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="26ef0-252">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="26ef0-252">Field name</span></span>|<span data-ttu-id="26ef0-253">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="26ef0-253">Data type</span></span>|<span data-ttu-id="26ef0-254">Descrição</span><span class="sxs-lookup"><span data-stu-id="26ef0-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="26ef0-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="26ef0-255">ThreadID</span></span>|<span data-ttu-id="26ef0-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-256">win:UInt64</span></span>|<span data-ttu-id="26ef0-257">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="26ef0-257">The thread identifier.</span></span>|  
|<span data-ttu-id="26ef0-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="26ef0-258">AppDomainID</span></span>|<span data-ttu-id="26ef0-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="26ef0-259">win:UInt64</span></span>|<span data-ttu-id="26ef0-260">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ef0-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="26ef0-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="26ef0-261">ClrInstanceID</span></span>|<span data-ttu-id="26ef0-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="26ef0-262">win:UInt16</span></span>|<span data-ttu-id="26ef0-263">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="26ef0-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26ef0-264">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26ef0-264">See also</span></span>

- [<span data-ttu-id="26ef0-265">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="26ef0-265">CLR ETW Events</span></span>](clr-etw-events.md)
