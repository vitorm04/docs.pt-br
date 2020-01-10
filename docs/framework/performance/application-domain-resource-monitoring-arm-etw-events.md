---
title: Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: 0e453b2bafffd9e07a1bdddd97282c5b97f5483d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716223"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="5bbc9-102">Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="5bbc9-103">Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="5bbc9-104">Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="5bbc9-105">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="5bbc9-105">ThreadCreated Event</span></span>

<span data-ttu-id="5bbc9-106">Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="5bbc9-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="5bbc9-107">Esse é o único evento acionado no provedor de encerramento nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="5bbc9-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="5bbc9-109">Para obter mais informações, consulte [palavras-chave e níveis do ETW do CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5bbc9-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="5bbc9-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-110">Keyword for raising the event</span></span>|<span data-ttu-id="5bbc9-111">Nível</span><span class="sxs-lookup"><span data-stu-id="5bbc9-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5bbc9-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5bbc9-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-113">Informational(4)</span></span>|
|<span data-ttu-id="5bbc9-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="5bbc9-115">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-115">Informational(4)</span></span>|

<span data-ttu-id="5bbc9-116">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-116">The following table shows the event information:</span></span>

|<span data-ttu-id="5bbc9-117">Event</span><span class="sxs-lookup"><span data-stu-id="5bbc9-117">Event</span></span>|<span data-ttu-id="5bbc9-118">ID do evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-118">Event ID</span></span>|<span data-ttu-id="5bbc9-119">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="5bbc9-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="5bbc9-120">85</span><span class="sxs-lookup"><span data-stu-id="5bbc9-120">85</span></span>|<span data-ttu-id="5bbc9-121">Um thread foi criado para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="5bbc9-122">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-122">The following table shows the event data:</span></span>

|<span data-ttu-id="5bbc9-123">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="5bbc9-123">Field name</span></span>|<span data-ttu-id="5bbc9-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="5bbc9-124">Data type</span></span>|<span data-ttu-id="5bbc9-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bbc9-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5bbc9-126">ThreadID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-126">ThreadID</span></span>|<span data-ttu-id="5bbc9-127">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-127">win:UInt64</span></span>|<span data-ttu-id="5bbc9-128">ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="5bbc9-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-129">AppDomainID</span></span>|<span data-ttu-id="5bbc9-130">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-130">win:UInt64</span></span>|<span data-ttu-id="5bbc9-131">Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="5bbc9-132">Sinalizadores</span><span class="sxs-lookup"><span data-stu-id="5bbc9-132">Flags</span></span>|<span data-ttu-id="5bbc9-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5bbc9-133">win:UInt32</span></span>|<span data-ttu-id="5bbc9-134">Sinalizadores de criação do thread.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-134">Thread creation flags.</span></span>|
|<span data-ttu-id="5bbc9-135">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="5bbc9-135">ManagedThreadIndex</span></span>|<span data-ttu-id="5bbc9-136">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5bbc9-136">win:UInt32</span></span>|<span data-ttu-id="5bbc9-137">Índice gerenciado do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="5bbc9-138">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-138">OSThreadID</span></span>|<span data-ttu-id="5bbc9-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5bbc9-139">win:UInt32</span></span>|<span data-ttu-id="5bbc9-140">ID do sistema operacional do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="5bbc9-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-141">ClrInstanceID</span></span>|<span data-ttu-id="5bbc9-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5bbc9-142">win:UInt16</span></span>|<span data-ttu-id="5bbc9-143">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="5bbc9-144">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="5bbc9-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="5bbc9-145">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5bbc9-146">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-146">Keyword for raising the event</span></span>|<span data-ttu-id="5bbc9-147">Nível</span><span class="sxs-lookup"><span data-stu-id="5bbc9-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5bbc9-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5bbc9-149">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-149">Informational(4)</span></span>|

<span data-ttu-id="5bbc9-150">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-150">The following table shows the event information:</span></span>

|<span data-ttu-id="5bbc9-151">Event</span><span class="sxs-lookup"><span data-stu-id="5bbc9-151">Event</span></span>|<span data-ttu-id="5bbc9-152">ID do evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-152">Event ID</span></span>|<span data-ttu-id="5bbc9-153">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="5bbc9-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="5bbc9-154">83</span><span class="sxs-lookup"><span data-stu-id="5bbc9-154">83</span></span>|<span data-ttu-id="5bbc9-155">Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="5bbc9-156">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-156">The following table shows the event data:</span></span>

|<span data-ttu-id="5bbc9-157">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="5bbc9-157">Field name</span></span>|<span data-ttu-id="5bbc9-158">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="5bbc9-158">Data type</span></span>|<span data-ttu-id="5bbc9-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bbc9-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5bbc9-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-160">AppDomainID</span></span>|<span data-ttu-id="5bbc9-161">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-161">win:UInt64</span></span>|<span data-ttu-id="5bbc9-162">Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="5bbc9-163">Alocado</span><span class="sxs-lookup"><span data-stu-id="5bbc9-163">Allocated</span></span>|<span data-ttu-id="5bbc9-164">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-164">win:UInt64</span></span>|<span data-ttu-id="5bbc9-165">O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).</span><span class="sxs-lookup"><span data-stu-id="5bbc9-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="5bbc9-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-166">ClrInstanceID</span></span>|<span data-ttu-id="5bbc9-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5bbc9-167">win:UInt16</span></span>|<span data-ttu-id="5bbc9-168">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="5bbc9-169">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="5bbc9-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="5bbc9-170">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5bbc9-171">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-171">Keyword for raising the event</span></span>|<span data-ttu-id="5bbc9-172">Nível</span><span class="sxs-lookup"><span data-stu-id="5bbc9-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5bbc9-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5bbc9-174">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-174">Informational(4)</span></span>|

<span data-ttu-id="5bbc9-175">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-175">The following table shows the event information:</span></span>

|<span data-ttu-id="5bbc9-176">Event</span><span class="sxs-lookup"><span data-stu-id="5bbc9-176">Event</span></span>|<span data-ttu-id="5bbc9-177">ID do evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-177">Event ID</span></span>|<span data-ttu-id="5bbc9-178">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="5bbc9-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="5bbc9-179">84</span><span class="sxs-lookup"><span data-stu-id="5bbc9-179">84</span></span>|<span data-ttu-id="5bbc9-180">Cada coleta de lixo é encerrada.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="5bbc9-181">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-181">The following table shows the event data:</span></span>

|<span data-ttu-id="5bbc9-182">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="5bbc9-182">Field name</span></span>|<span data-ttu-id="5bbc9-183">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="5bbc9-183">Data type</span></span>|<span data-ttu-id="5bbc9-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bbc9-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5bbc9-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-185">AppDomainID</span></span>|<span data-ttu-id="5bbc9-186">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-186">win:UInt64</span></span>|<span data-ttu-id="5bbc9-187">Identificador do domínio para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="5bbc9-188">Survived</span><span class="sxs-lookup"><span data-stu-id="5bbc9-188">Survived</span></span>|<span data-ttu-id="5bbc9-189">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-189">win:UInt64</span></span>|<span data-ttu-id="5bbc9-190">O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="5bbc9-191">Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="5bbc9-192">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="5bbc9-192">ProcessSurvived</span></span>|<span data-ttu-id="5bbc9-193">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-193">win:UInt64</span></span>|<span data-ttu-id="5bbc9-194">O total de bytes que sobreviveram da última coleta.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="5bbc9-195">Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="5bbc9-196">Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="5bbc9-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-197">ClrInstanceID</span></span>|<span data-ttu-id="5bbc9-198">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5bbc9-198">win:UInt16</span></span>|<span data-ttu-id="5bbc9-199">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="5bbc9-200">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="5bbc9-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="5bbc9-201">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5bbc9-202">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-202">Keyword for raising the event</span></span>|<span data-ttu-id="5bbc9-203">Nível</span><span class="sxs-lookup"><span data-stu-id="5bbc9-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5bbc9-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5bbc9-205">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-205">Informational(4)</span></span>|
|<span data-ttu-id="5bbc9-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="5bbc9-207">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-207">Informational(4)</span></span>|

<span data-ttu-id="5bbc9-208">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-208">The following table shows the event information:</span></span>

|<span data-ttu-id="5bbc9-209">Event</span><span class="sxs-lookup"><span data-stu-id="5bbc9-209">Event</span></span>|<span data-ttu-id="5bbc9-210">ID do evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-210">Event ID</span></span>|<span data-ttu-id="5bbc9-211">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="5bbc9-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="5bbc9-212">87</span><span class="sxs-lookup"><span data-stu-id="5bbc9-212">87</span></span>|<span data-ttu-id="5bbc9-213">Um thread entra em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="5bbc9-214">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-214">The following table shows the event data:</span></span>

|<span data-ttu-id="5bbc9-215">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="5bbc9-215">Field name</span></span>|<span data-ttu-id="5bbc9-216">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="5bbc9-216">Data type</span></span>|<span data-ttu-id="5bbc9-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bbc9-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5bbc9-218">ThreadID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-218">ThreadID</span></span>|<span data-ttu-id="5bbc9-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-219">win:UInt64</span></span>|<span data-ttu-id="5bbc9-220">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-220">The thread identifier.</span></span>|
|<span data-ttu-id="5bbc9-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-221">AppDomainID</span></span>|<span data-ttu-id="5bbc9-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-222">win:UInt64</span></span>|<span data-ttu-id="5bbc9-223">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-223">The application domain identifier.</span></span>|
|<span data-ttu-id="5bbc9-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-224">ClrInstanceID</span></span>|<span data-ttu-id="5bbc9-225">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5bbc9-225">win:UInt16</span></span>|<span data-ttu-id="5bbc9-226">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="5bbc9-227">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="5bbc9-227">ThreadTerminated Event</span></span>

<span data-ttu-id="5bbc9-228">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5bbc9-229">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-229">Keyword for raising the event</span></span>|<span data-ttu-id="5bbc9-230">Nível</span><span class="sxs-lookup"><span data-stu-id="5bbc9-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5bbc9-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5bbc9-232">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-232">Informational(4)</span></span>|
|<span data-ttu-id="5bbc9-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="5bbc9-234">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="5bbc9-234">Informational(4)</span></span>|

<span data-ttu-id="5bbc9-235">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-235">The following table shows the event information:</span></span>

|<span data-ttu-id="5bbc9-236">Event</span><span class="sxs-lookup"><span data-stu-id="5bbc9-236">Event</span></span>|<span data-ttu-id="5bbc9-237">ID do evento</span><span class="sxs-lookup"><span data-stu-id="5bbc9-237">Event ID</span></span>|<span data-ttu-id="5bbc9-238">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="5bbc9-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="5bbc9-239">86</span><span class="sxs-lookup"><span data-stu-id="5bbc9-239">86</span></span>|<span data-ttu-id="5bbc9-240">Um thread termina.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-240">A thread terminates.</span></span>|

<span data-ttu-id="5bbc9-241">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="5bbc9-241">The following table shows the event data:</span></span>

|<span data-ttu-id="5bbc9-242">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="5bbc9-242">Field name</span></span>|<span data-ttu-id="5bbc9-243">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="5bbc9-243">Data type</span></span>|<span data-ttu-id="5bbc9-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bbc9-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5bbc9-245">ThreadID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-245">ThreadID</span></span>|<span data-ttu-id="5bbc9-246">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-246">win:UInt64</span></span>|<span data-ttu-id="5bbc9-247">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-247">The thread identifier.</span></span>|
|<span data-ttu-id="5bbc9-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-248">AppDomainID</span></span>|<span data-ttu-id="5bbc9-249">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5bbc9-249">win:UInt64</span></span>|<span data-ttu-id="5bbc9-250">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-250">The application domain identifier.</span></span>|
|<span data-ttu-id="5bbc9-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5bbc9-251">ClrInstanceID</span></span>|<span data-ttu-id="5bbc9-252">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5bbc9-252">win:UInt16</span></span>|<span data-ttu-id="5bbc9-253">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5bbc9-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5bbc9-254">Veja também</span><span class="sxs-lookup"><span data-stu-id="5bbc9-254">See also</span></span>

- [<span data-ttu-id="5bbc9-255">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="5bbc9-255">CLR ETW Events</span></span>](clr-etw-events.md)
