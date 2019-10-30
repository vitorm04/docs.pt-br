---
title: Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e1c2a38be6f2c15a118b35925570119b474f096
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040574"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="dee16-102">Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)</span><span class="sxs-lookup"><span data-stu-id="dee16-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="dee16-103">Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dee16-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="dee16-104">Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.</span><span class="sxs-lookup"><span data-stu-id="dee16-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="dee16-105">Evento ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="dee16-105">ThreadCreated Event</span></span>

<span data-ttu-id="dee16-106">Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="dee16-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="dee16-107">Esse é o único evento acionado no provedor de encerramento nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="dee16-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="dee16-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="dee16-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="dee16-109">Para obter mais informações, consulte [palavras-chave e níveis do ETW do CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="dee16-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="dee16-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="dee16-110">Keyword for raising the event</span></span>|<span data-ttu-id="dee16-111">Nível</span><span class="sxs-lookup"><span data-stu-id="dee16-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dee16-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dee16-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dee16-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="dee16-113">Informational(4)</span></span>|
|<span data-ttu-id="dee16-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dee16-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dee16-115">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="dee16-115">Informational(4)</span></span>|

<span data-ttu-id="dee16-116">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-116">The following table shows the event information:</span></span>

|<span data-ttu-id="dee16-117">evento</span><span class="sxs-lookup"><span data-stu-id="dee16-117">Event</span></span>|<span data-ttu-id="dee16-118">ID do evento</span><span class="sxs-lookup"><span data-stu-id="dee16-118">Event ID</span></span>|<span data-ttu-id="dee16-119">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="dee16-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="dee16-120">85</span><span class="sxs-lookup"><span data-stu-id="dee16-120">85</span></span>|<span data-ttu-id="dee16-121">Um thread foi criado para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dee16-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="dee16-122">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-122">The following table shows the event data:</span></span>

|<span data-ttu-id="dee16-123">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="dee16-123">Field name</span></span>|<span data-ttu-id="dee16-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="dee16-124">Data type</span></span>|<span data-ttu-id="dee16-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee16-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dee16-126">ThreadID</span><span class="sxs-lookup"><span data-stu-id="dee16-126">ThreadID</span></span>|<span data-ttu-id="dee16-127">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-127">win:UInt64</span></span>|<span data-ttu-id="dee16-128">ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="dee16-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="dee16-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dee16-129">AppDomainID</span></span>|<span data-ttu-id="dee16-130">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-130">win:UInt64</span></span>|<span data-ttu-id="dee16-131">Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.</span><span class="sxs-lookup"><span data-stu-id="dee16-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="dee16-132">Sinalizadores</span><span class="sxs-lookup"><span data-stu-id="dee16-132">Flags</span></span>|<span data-ttu-id="dee16-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="dee16-133">win:UInt32</span></span>|<span data-ttu-id="dee16-134">Sinalizadores de criação do thread.</span><span class="sxs-lookup"><span data-stu-id="dee16-134">Thread creation flags.</span></span>|
|<span data-ttu-id="dee16-135">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="dee16-135">ManagedThreadIndex</span></span>|<span data-ttu-id="dee16-136">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="dee16-136">win:UInt32</span></span>|<span data-ttu-id="dee16-137">Índice gerenciado do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="dee16-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="dee16-138">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="dee16-138">OSThreadID</span></span>|<span data-ttu-id="dee16-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="dee16-139">win:UInt32</span></span>|<span data-ttu-id="dee16-140">ID do sistema operacional do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="dee16-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="dee16-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dee16-141">ClrInstanceID</span></span>|<span data-ttu-id="dee16-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dee16-142">win:UInt16</span></span>|<span data-ttu-id="dee16-143">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dee16-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="dee16-144">Evento AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="dee16-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="dee16-145">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="dee16-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dee16-146">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="dee16-146">Keyword for raising the event</span></span>|<span data-ttu-id="dee16-147">Nível</span><span class="sxs-lookup"><span data-stu-id="dee16-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dee16-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dee16-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dee16-149">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="dee16-149">Informational(4)</span></span>|

<span data-ttu-id="dee16-150">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-150">The following table shows the event information:</span></span>

|<span data-ttu-id="dee16-151">evento</span><span class="sxs-lookup"><span data-stu-id="dee16-151">Event</span></span>|<span data-ttu-id="dee16-152">ID do evento</span><span class="sxs-lookup"><span data-stu-id="dee16-152">Event ID</span></span>|<span data-ttu-id="dee16-153">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="dee16-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="dee16-154">83</span><span class="sxs-lookup"><span data-stu-id="dee16-154">83</span></span>|<span data-ttu-id="dee16-155">Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dee16-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="dee16-156">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-156">The following table shows the event data:</span></span>

|<span data-ttu-id="dee16-157">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="dee16-157">Field name</span></span>|<span data-ttu-id="dee16-158">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="dee16-158">Data type</span></span>|<span data-ttu-id="dee16-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee16-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dee16-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dee16-160">AppDomainID</span></span>|<span data-ttu-id="dee16-161">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-161">win:UInt64</span></span>|<span data-ttu-id="dee16-162">Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="dee16-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="dee16-163">Alocado</span><span class="sxs-lookup"><span data-stu-id="dee16-163">Allocated</span></span>|<span data-ttu-id="dee16-164">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-164">win:UInt64</span></span>|<span data-ttu-id="dee16-165">O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).</span><span class="sxs-lookup"><span data-stu-id="dee16-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="dee16-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dee16-166">ClrInstanceID</span></span>|<span data-ttu-id="dee16-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dee16-167">win:UInt16</span></span>|<span data-ttu-id="dee16-168">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dee16-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="dee16-169">Evento AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="dee16-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="dee16-170">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="dee16-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dee16-171">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="dee16-171">Keyword for raising the event</span></span>|<span data-ttu-id="dee16-172">Nível</span><span class="sxs-lookup"><span data-stu-id="dee16-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dee16-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dee16-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dee16-174">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="dee16-174">Informational(4)</span></span>|

<span data-ttu-id="dee16-175">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-175">The following table shows the event information:</span></span>

|<span data-ttu-id="dee16-176">evento</span><span class="sxs-lookup"><span data-stu-id="dee16-176">Event</span></span>|<span data-ttu-id="dee16-177">ID do evento</span><span class="sxs-lookup"><span data-stu-id="dee16-177">Event ID</span></span>|<span data-ttu-id="dee16-178">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="dee16-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="dee16-179">84</span><span class="sxs-lookup"><span data-stu-id="dee16-179">84</span></span>|<span data-ttu-id="dee16-180">Cada coleta de lixo é encerrada.</span><span class="sxs-lookup"><span data-stu-id="dee16-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="dee16-181">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-181">The following table shows the event data:</span></span>

|<span data-ttu-id="dee16-182">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="dee16-182">Field name</span></span>|<span data-ttu-id="dee16-183">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="dee16-183">Data type</span></span>|<span data-ttu-id="dee16-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee16-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dee16-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dee16-185">AppDomainID</span></span>|<span data-ttu-id="dee16-186">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-186">win:UInt64</span></span>|<span data-ttu-id="dee16-187">Identificador do domínio para o qual o uso de recursos está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="dee16-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="dee16-188">Survived</span><span class="sxs-lookup"><span data-stu-id="dee16-188">Survived</span></span>|<span data-ttu-id="dee16-189">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-189">win:UInt64</span></span>|<span data-ttu-id="dee16-190">O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dee16-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="dee16-191">Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.</span><span class="sxs-lookup"><span data-stu-id="dee16-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="dee16-192">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="dee16-192">ProcessSurvived</span></span>|<span data-ttu-id="dee16-193">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-193">win:UInt64</span></span>|<span data-ttu-id="dee16-194">O total de bytes que sobreviveram da última coleta.</span><span class="sxs-lookup"><span data-stu-id="dee16-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="dee16-195">Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="dee16-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="dee16-196">Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="dee16-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="dee16-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dee16-197">ClrInstanceID</span></span>|<span data-ttu-id="dee16-198">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dee16-198">win:UInt16</span></span>|<span data-ttu-id="dee16-199">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dee16-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="dee16-200">Evento ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="dee16-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="dee16-201">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="dee16-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dee16-202">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="dee16-202">Keyword for raising the event</span></span>|<span data-ttu-id="dee16-203">Nível</span><span class="sxs-lookup"><span data-stu-id="dee16-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dee16-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dee16-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dee16-205">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="dee16-205">Informational(4)</span></span>|
|<span data-ttu-id="dee16-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dee16-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dee16-207">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="dee16-207">Informational(4)</span></span>|

<span data-ttu-id="dee16-208">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-208">The following table shows the event information:</span></span>

|<span data-ttu-id="dee16-209">evento</span><span class="sxs-lookup"><span data-stu-id="dee16-209">Event</span></span>|<span data-ttu-id="dee16-210">ID do evento</span><span class="sxs-lookup"><span data-stu-id="dee16-210">Event ID</span></span>|<span data-ttu-id="dee16-211">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="dee16-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="dee16-212">87</span><span class="sxs-lookup"><span data-stu-id="dee16-212">87</span></span>|<span data-ttu-id="dee16-213">Um thread entra em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dee16-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="dee16-214">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-214">The following table shows the event data:</span></span>

|<span data-ttu-id="dee16-215">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="dee16-215">Field name</span></span>|<span data-ttu-id="dee16-216">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="dee16-216">Data type</span></span>|<span data-ttu-id="dee16-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee16-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dee16-218">ThreadID</span><span class="sxs-lookup"><span data-stu-id="dee16-218">ThreadID</span></span>|<span data-ttu-id="dee16-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-219">win:UInt64</span></span>|<span data-ttu-id="dee16-220">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="dee16-220">The thread identifier.</span></span>|
|<span data-ttu-id="dee16-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dee16-221">AppDomainID</span></span>|<span data-ttu-id="dee16-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-222">win:UInt64</span></span>|<span data-ttu-id="dee16-223">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dee16-223">The application domain identifier.</span></span>|
|<span data-ttu-id="dee16-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dee16-224">ClrInstanceID</span></span>|<span data-ttu-id="dee16-225">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dee16-225">win:UInt16</span></span>|<span data-ttu-id="dee16-226">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dee16-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="dee16-227">Evento ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="dee16-227">ThreadTerminated Event</span></span>

<span data-ttu-id="dee16-228">A seguinte tabela mostra a palavra-chave e o nível:</span><span class="sxs-lookup"><span data-stu-id="dee16-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dee16-229">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="dee16-229">Keyword for raising the event</span></span>|<span data-ttu-id="dee16-230">Nível</span><span class="sxs-lookup"><span data-stu-id="dee16-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dee16-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dee16-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dee16-232">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="dee16-232">Informational(4)</span></span>|
|<span data-ttu-id="dee16-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dee16-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dee16-234">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="dee16-234">Informational(4)</span></span>|

<span data-ttu-id="dee16-235">A seguinte tabela mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-235">The following table shows the event information:</span></span>

|<span data-ttu-id="dee16-236">evento</span><span class="sxs-lookup"><span data-stu-id="dee16-236">Event</span></span>|<span data-ttu-id="dee16-237">ID do evento</span><span class="sxs-lookup"><span data-stu-id="dee16-237">Event ID</span></span>|<span data-ttu-id="dee16-238">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="dee16-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="dee16-239">86</span><span class="sxs-lookup"><span data-stu-id="dee16-239">86</span></span>|<span data-ttu-id="dee16-240">Um thread termina.</span><span class="sxs-lookup"><span data-stu-id="dee16-240">A thread terminates.</span></span>|

<span data-ttu-id="dee16-241">A seguinte tabela mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="dee16-241">The following table shows the event data:</span></span>

|<span data-ttu-id="dee16-242">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="dee16-242">Field name</span></span>|<span data-ttu-id="dee16-243">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="dee16-243">Data type</span></span>|<span data-ttu-id="dee16-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee16-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dee16-245">ThreadID</span><span class="sxs-lookup"><span data-stu-id="dee16-245">ThreadID</span></span>|<span data-ttu-id="dee16-246">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-246">win:UInt64</span></span>|<span data-ttu-id="dee16-247">O identificador de thread.</span><span class="sxs-lookup"><span data-stu-id="dee16-247">The thread identifier.</span></span>|
|<span data-ttu-id="dee16-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dee16-248">AppDomainID</span></span>|<span data-ttu-id="dee16-249">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dee16-249">win:UInt64</span></span>|<span data-ttu-id="dee16-250">O identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dee16-250">The application domain identifier.</span></span>|
|<span data-ttu-id="dee16-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dee16-251">ClrInstanceID</span></span>|<span data-ttu-id="dee16-252">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dee16-252">win:UInt16</span></span>|<span data-ttu-id="dee16-253">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dee16-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="dee16-254">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dee16-254">See also</span></span>

- [<span data-ttu-id="dee16-255">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="dee16-255">CLR ETW Events</span></span>](clr-etw-events.md)
