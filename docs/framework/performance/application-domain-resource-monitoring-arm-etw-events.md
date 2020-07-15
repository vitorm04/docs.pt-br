---
title: Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)
description: Leia sobre eventos de ETW (monitoramento de recursos de domínio de aplicativo) no .NET, como ThreadCreated, AppDomainMemAllocated, AppDomainMemSurvived e muito mais.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309775"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="619bc-103">Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)</span><span class="sxs-lookup"><span data-stu-id="619bc-103">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="619bc-104"> Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="619bc-104">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="619bc-105">Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.</span><span class="sxs-lookup"><span data-stu-id="619bc-105">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="619bc-106">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="619bc-106">ThreadCreated Event</span></span>

<span data-ttu-id="619bc-107">Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="619bc-107">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="619bc-108">Esse é o único evento acionado no provedor de encerramento nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="619bc-108">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="619bc-109">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="619bc-109">The following table shows the keyword and level.</span></span> <span data-ttu-id="619bc-110">Para obter mais informações, consulte [palavras-chave e níveis do ETW do CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="619bc-110">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="619bc-111">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="619bc-111">Keyword for raising the event</span></span>|<span data-ttu-id="619bc-112">Level</span><span class="sxs-lookup"><span data-stu-id="619bc-112">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="619bc-113">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="619bc-113">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="619bc-114">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="619bc-114">Informational(4)</span></span>|
|<span data-ttu-id="619bc-115">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="619bc-115">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="619bc-116">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="619bc-116">Informational(4)</span></span>|

<span data-ttu-id="619bc-117">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-117">The following table shows the event information:</span></span>

|<span data-ttu-id="619bc-118">Evento</span><span class="sxs-lookup"><span data-stu-id="619bc-118">Event</span></span>|<span data-ttu-id="619bc-119">ID do evento</span><span class="sxs-lookup"><span data-stu-id="619bc-119">Event ID</span></span>|<span data-ttu-id="619bc-120">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="619bc-120">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="619bc-121">85</span><span class="sxs-lookup"><span data-stu-id="619bc-121">85</span></span>|<span data-ttu-id="619bc-122">Um thread foi criado para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="619bc-122">A thread was created for the application domain.</span></span>|

<span data-ttu-id="619bc-123">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-123">The following table shows the event data:</span></span>

|<span data-ttu-id="619bc-124">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="619bc-124">Field name</span></span>|<span data-ttu-id="619bc-125">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="619bc-125">Data type</span></span>|<span data-ttu-id="619bc-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="619bc-126">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="619bc-127">ThreadID</span><span class="sxs-lookup"><span data-stu-id="619bc-127">ThreadID</span></span>|<span data-ttu-id="619bc-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-128">win:UInt64</span></span>|<span data-ttu-id="619bc-129">ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="619bc-129">ID of the thread that was created.</span></span>|
|<span data-ttu-id="619bc-130">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="619bc-130">AppDomainID</span></span>|<span data-ttu-id="619bc-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-131">win:UInt64</span></span>|<span data-ttu-id="619bc-132">Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.</span><span class="sxs-lookup"><span data-stu-id="619bc-132">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="619bc-133">Flags</span><span class="sxs-lookup"><span data-stu-id="619bc-133">Flags</span></span>|<span data-ttu-id="619bc-134">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="619bc-134">win:UInt32</span></span>|<span data-ttu-id="619bc-135">Sinalizadores de criação do thread.</span><span class="sxs-lookup"><span data-stu-id="619bc-135">Thread creation flags.</span></span>|
|<span data-ttu-id="619bc-136">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="619bc-136">ManagedThreadIndex</span></span>|<span data-ttu-id="619bc-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="619bc-137">win:UInt32</span></span>|<span data-ttu-id="619bc-138">Índice gerenciado do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="619bc-138">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="619bc-139">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="619bc-139">OSThreadID</span></span>|<span data-ttu-id="619bc-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="619bc-140">win:UInt32</span></span>|<span data-ttu-id="619bc-141">ID do sistema operacional do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="619bc-141">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="619bc-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="619bc-142">ClrInstanceID</span></span>|<span data-ttu-id="619bc-143">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="619bc-143">win:UInt16</span></span>|<span data-ttu-id="619bc-144">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="619bc-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="619bc-145">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="619bc-145">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="619bc-146">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="619bc-146">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="619bc-147">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="619bc-147">Keyword for raising the event</span></span>|<span data-ttu-id="619bc-148">Level</span><span class="sxs-lookup"><span data-stu-id="619bc-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="619bc-149">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="619bc-149">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="619bc-150">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="619bc-150">Informational(4)</span></span>|

<span data-ttu-id="619bc-151">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-151">The following table shows the event information:</span></span>

|<span data-ttu-id="619bc-152">Evento</span><span class="sxs-lookup"><span data-stu-id="619bc-152">Event</span></span>|<span data-ttu-id="619bc-153">ID do evento</span><span class="sxs-lookup"><span data-stu-id="619bc-153">Event ID</span></span>|<span data-ttu-id="619bc-154">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="619bc-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="619bc-155">83</span><span class="sxs-lookup"><span data-stu-id="619bc-155">83</span></span>|<span data-ttu-id="619bc-156">Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="619bc-156">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="619bc-157">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-157">The following table shows the event data:</span></span>

|<span data-ttu-id="619bc-158">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="619bc-158">Field name</span></span>|<span data-ttu-id="619bc-159">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="619bc-159">Data type</span></span>|<span data-ttu-id="619bc-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="619bc-160">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="619bc-161">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="619bc-161">AppDomainID</span></span>|<span data-ttu-id="619bc-162">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-162">win:UInt64</span></span>|<span data-ttu-id="619bc-163">Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="619bc-163">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="619bc-164">Alocado</span><span class="sxs-lookup"><span data-stu-id="619bc-164">Allocated</span></span>|<span data-ttu-id="619bc-165">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-165">win:UInt64</span></span>|<span data-ttu-id="619bc-166">O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).</span><span class="sxs-lookup"><span data-stu-id="619bc-166">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="619bc-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="619bc-167">ClrInstanceID</span></span>|<span data-ttu-id="619bc-168">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="619bc-168">win:UInt16</span></span>|<span data-ttu-id="619bc-169">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="619bc-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="619bc-170">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="619bc-170">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="619bc-171">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="619bc-171">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="619bc-172">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="619bc-172">Keyword for raising the event</span></span>|<span data-ttu-id="619bc-173">Level</span><span class="sxs-lookup"><span data-stu-id="619bc-173">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="619bc-174">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="619bc-174">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="619bc-175">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="619bc-175">Informational(4)</span></span>|

<span data-ttu-id="619bc-176">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-176">The following table shows the event information:</span></span>

|<span data-ttu-id="619bc-177">Evento</span><span class="sxs-lookup"><span data-stu-id="619bc-177">Event</span></span>|<span data-ttu-id="619bc-178">ID do evento</span><span class="sxs-lookup"><span data-stu-id="619bc-178">Event ID</span></span>|<span data-ttu-id="619bc-179">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="619bc-179">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="619bc-180">84</span><span class="sxs-lookup"><span data-stu-id="619bc-180">84</span></span>|<span data-ttu-id="619bc-181">Cada coleta de lixo é encerrada.</span><span class="sxs-lookup"><span data-stu-id="619bc-181">Each garbage collection has ended.</span></span>|

<span data-ttu-id="619bc-182">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-182">The following table shows the event data:</span></span>

|<span data-ttu-id="619bc-183">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="619bc-183">Field name</span></span>|<span data-ttu-id="619bc-184">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="619bc-184">Data type</span></span>|<span data-ttu-id="619bc-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="619bc-185">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="619bc-186">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="619bc-186">AppDomainID</span></span>|<span data-ttu-id="619bc-187">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-187">win:UInt64</span></span>|<span data-ttu-id="619bc-188">Identificador do domínio para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="619bc-188">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="619bc-189">Survived</span><span class="sxs-lookup"><span data-stu-id="619bc-189">Survived</span></span>|<span data-ttu-id="619bc-190">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-190">win:UInt64</span></span>|<span data-ttu-id="619bc-191">O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="619bc-191">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="619bc-192">Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.</span><span class="sxs-lookup"><span data-stu-id="619bc-192">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="619bc-193">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="619bc-193">ProcessSurvived</span></span>|<span data-ttu-id="619bc-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-194">win:UInt64</span></span>|<span data-ttu-id="619bc-195">O total de bytes que sobreviveram da última coleta.</span><span class="sxs-lookup"><span data-stu-id="619bc-195">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="619bc-196">Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="619bc-196">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="619bc-197">Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="619bc-197">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="619bc-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="619bc-198">ClrInstanceID</span></span>|<span data-ttu-id="619bc-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="619bc-199">win:UInt16</span></span>|<span data-ttu-id="619bc-200">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="619bc-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="619bc-201">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="619bc-201">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="619bc-202">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="619bc-202">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="619bc-203">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="619bc-203">Keyword for raising the event</span></span>|<span data-ttu-id="619bc-204">Level</span><span class="sxs-lookup"><span data-stu-id="619bc-204">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="619bc-205">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="619bc-205">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="619bc-206">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="619bc-206">Informational(4)</span></span>|
|<span data-ttu-id="619bc-207">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="619bc-207">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="619bc-208">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="619bc-208">Informational(4)</span></span>|

<span data-ttu-id="619bc-209">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-209">The following table shows the event information:</span></span>

|<span data-ttu-id="619bc-210">Evento</span><span class="sxs-lookup"><span data-stu-id="619bc-210">Event</span></span>|<span data-ttu-id="619bc-211">ID do evento</span><span class="sxs-lookup"><span data-stu-id="619bc-211">Event ID</span></span>|<span data-ttu-id="619bc-212">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="619bc-212">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="619bc-213">87</span><span class="sxs-lookup"><span data-stu-id="619bc-213">87</span></span>|<span data-ttu-id="619bc-214">Um thread entra em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="619bc-214">A thread enters an application domain.</span></span>|

<span data-ttu-id="619bc-215">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-215">The following table shows the event data:</span></span>

|<span data-ttu-id="619bc-216">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="619bc-216">Field name</span></span>|<span data-ttu-id="619bc-217">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="619bc-217">Data type</span></span>|<span data-ttu-id="619bc-218">Descrição</span><span class="sxs-lookup"><span data-stu-id="619bc-218">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="619bc-219">ThreadID</span><span class="sxs-lookup"><span data-stu-id="619bc-219">ThreadID</span></span>|<span data-ttu-id="619bc-220">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-220">win:UInt64</span></span>|<span data-ttu-id="619bc-221">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="619bc-221">The thread identifier.</span></span>|
|<span data-ttu-id="619bc-222">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="619bc-222">AppDomainID</span></span>|<span data-ttu-id="619bc-223">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-223">win:UInt64</span></span>|<span data-ttu-id="619bc-224">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="619bc-224">The application domain identifier.</span></span>|
|<span data-ttu-id="619bc-225">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="619bc-225">ClrInstanceID</span></span>|<span data-ttu-id="619bc-226">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="619bc-226">win:UInt16</span></span>|<span data-ttu-id="619bc-227">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="619bc-227">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="619bc-228">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="619bc-228">ThreadTerminated Event</span></span>

<span data-ttu-id="619bc-229">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="619bc-229">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="619bc-230">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="619bc-230">Keyword for raising the event</span></span>|<span data-ttu-id="619bc-231">Level</span><span class="sxs-lookup"><span data-stu-id="619bc-231">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="619bc-232">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="619bc-232">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="619bc-233">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="619bc-233">Informational(4)</span></span>|
|<span data-ttu-id="619bc-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="619bc-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="619bc-235">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="619bc-235">Informational(4)</span></span>|

<span data-ttu-id="619bc-236">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-236">The following table shows the event information:</span></span>

|<span data-ttu-id="619bc-237">Evento</span><span class="sxs-lookup"><span data-stu-id="619bc-237">Event</span></span>|<span data-ttu-id="619bc-238">ID do evento</span><span class="sxs-lookup"><span data-stu-id="619bc-238">Event ID</span></span>|<span data-ttu-id="619bc-239">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="619bc-239">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="619bc-240">86</span><span class="sxs-lookup"><span data-stu-id="619bc-240">86</span></span>|<span data-ttu-id="619bc-241">Um thread termina.</span><span class="sxs-lookup"><span data-stu-id="619bc-241">A thread terminates.</span></span>|

<span data-ttu-id="619bc-242">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="619bc-242">The following table shows the event data:</span></span>

|<span data-ttu-id="619bc-243">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="619bc-243">Field name</span></span>|<span data-ttu-id="619bc-244">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="619bc-244">Data type</span></span>|<span data-ttu-id="619bc-245">Descrição</span><span class="sxs-lookup"><span data-stu-id="619bc-245">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="619bc-246">ThreadID</span><span class="sxs-lookup"><span data-stu-id="619bc-246">ThreadID</span></span>|<span data-ttu-id="619bc-247">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-247">win:UInt64</span></span>|<span data-ttu-id="619bc-248">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="619bc-248">The thread identifier.</span></span>|
|<span data-ttu-id="619bc-249">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="619bc-249">AppDomainID</span></span>|<span data-ttu-id="619bc-250">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="619bc-250">win:UInt64</span></span>|<span data-ttu-id="619bc-251">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="619bc-251">The application domain identifier.</span></span>|
|<span data-ttu-id="619bc-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="619bc-252">ClrInstanceID</span></span>|<span data-ttu-id="619bc-253">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="619bc-253">win:UInt16</span></span>|<span data-ttu-id="619bc-254">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="619bc-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="619bc-255">Confira também</span><span class="sxs-lookup"><span data-stu-id="619bc-255">See also</span></span>

- [<span data-ttu-id="619bc-256">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="619bc-256">CLR ETW Events</span></span>](clr-etw-events.md)
