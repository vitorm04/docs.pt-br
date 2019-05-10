---
title: Eventos ETW de interoperabilidade
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38db390b8fad9cd36dacf33f9647b0272eddc4a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616417"
---
# <a name="interop-etw-events"></a><span data-ttu-id="8d893-102">Eventos ETW de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="8d893-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="8d893-103">Eventos de interoperabilidade capturam informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="8d893-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="8d893-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="8d893-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="8d893-105">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="8d893-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="8d893-106">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="8d893-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="8d893-107">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="8d893-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="8d893-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="8d893-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="8d893-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="8d893-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="8d893-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="8d893-110">Keyword for raising the event</span></span>|<span data-ttu-id="8d893-111">Nível</span><span class="sxs-lookup"><span data-stu-id="8d893-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8d893-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="8d893-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="8d893-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="8d893-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="8d893-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="8d893-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="8d893-115">evento</span><span class="sxs-lookup"><span data-stu-id="8d893-115">Event</span></span>|<span data-ttu-id="8d893-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="8d893-116">Event ID</span></span>|<span data-ttu-id="8d893-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="8d893-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="8d893-118">88</span><span class="sxs-lookup"><span data-stu-id="8d893-118">88</span></span>|<span data-ttu-id="8d893-119">O stub em MSIL foi gerado.</span><span class="sxs-lookup"><span data-stu-id="8d893-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="8d893-120">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="8d893-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="8d893-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="8d893-121">Field name</span></span>|<span data-ttu-id="8d893-122">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="8d893-122">Data type</span></span>|<span data-ttu-id="8d893-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d893-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8d893-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="8d893-124">ModuleID</span></span>|<span data-ttu-id="8d893-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8d893-125">win:UInt16</span></span>|<span data-ttu-id="8d893-126">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="8d893-126">The module identifier.</span></span>|  
|<span data-ttu-id="8d893-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="8d893-127">StubMethodID</span></span>|<span data-ttu-id="8d893-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8d893-128">win:UInt64</span></span>|<span data-ttu-id="8d893-129">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="8d893-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="8d893-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="8d893-130">StubFlags</span></span>|<span data-ttu-id="8d893-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8d893-131">win:UInt64</span></span>|<span data-ttu-id="8d893-132">Os sinalizadores para o stub:</span><span class="sxs-lookup"><span data-stu-id="8d893-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="8d893-133">0x1 – interoperabilidade revesa.</span><span class="sxs-lookup"><span data-stu-id="8d893-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="8d893-134">0x2 – interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="8d893-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="8d893-135">0x4 – stub gerado pelo NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="8d893-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="8d893-136">0x8 – delegado.</span><span class="sxs-lookup"><span data-stu-id="8d893-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="8d893-137">0x10 – argumento variável.</span><span class="sxs-lookup"><span data-stu-id="8d893-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="8d893-138">0x20 – receptor não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="8d893-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="8d893-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="8d893-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8d893-140">win:UInt32</span></span>|<span data-ttu-id="8d893-141">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="8d893-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="8d893-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="8d893-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-143">win:UnicodeString</span></span>|<span data-ttu-id="8d893-144">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="8d893-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="8d893-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="8d893-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-146">win:UnicodeString</span></span>|<span data-ttu-id="8d893-147">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="8d893-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="8d893-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="8d893-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-149">win:UnicodeString</span></span>|<span data-ttu-id="8d893-150">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="8d893-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="8d893-151">NativeMethodSignature</span></span>|<span data-ttu-id="8d893-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-152">win:UnicodeString</span></span>|<span data-ttu-id="8d893-153">A assinatura do método nativo.</span><span class="sxs-lookup"><span data-stu-id="8d893-153">The native method signature.</span></span>|  
|<span data-ttu-id="8d893-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="8d893-154">StubMethodSignature</span></span>|<span data-ttu-id="8d893-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-155">win:UnicodeString</span></span>|<span data-ttu-id="8d893-156">A assinatura do método de stub.</span><span class="sxs-lookup"><span data-stu-id="8d893-156">The stub method signature.</span></span>|  
|<span data-ttu-id="8d893-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="8d893-157">StubMethodILCode</span></span>|<span data-ttu-id="8d893-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-158">win:UnicodeString</span></span>|<span data-ttu-id="8d893-159">O código MSIL para o método de stub.</span><span class="sxs-lookup"><span data-stu-id="8d893-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="8d893-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8d893-160">ClrInstanceID</span></span>|<span data-ttu-id="8d893-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8d893-161">win:UInt16</span></span>|<span data-ttu-id="8d893-162">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="8d893-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="8d893-163">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="8d893-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="8d893-164">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="8d893-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="8d893-165">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="8d893-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="8d893-166">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="8d893-166">Keyword for raising the event</span></span>|<span data-ttu-id="8d893-167">Nível</span><span class="sxs-lookup"><span data-stu-id="8d893-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8d893-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="8d893-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="8d893-169">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="8d893-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="8d893-170">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="8d893-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="8d893-171">evento</span><span class="sxs-lookup"><span data-stu-id="8d893-171">Event</span></span>|<span data-ttu-id="8d893-172">ID do evento</span><span class="sxs-lookup"><span data-stu-id="8d893-172">Event ID</span></span>|<span data-ttu-id="8d893-173">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="8d893-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="8d893-174">89</span><span class="sxs-lookup"><span data-stu-id="8d893-174">89</span></span>|<span data-ttu-id="8d893-175">O cache MSIL foi acessado.</span><span class="sxs-lookup"><span data-stu-id="8d893-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="8d893-176">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="8d893-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="8d893-177">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="8d893-177">Field name</span></span>|<span data-ttu-id="8d893-178">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="8d893-178">Data type</span></span>|<span data-ttu-id="8d893-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d893-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8d893-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="8d893-180">ModuleID</span></span>|<span data-ttu-id="8d893-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8d893-181">win:UInt16</span></span>|<span data-ttu-id="8d893-182">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="8d893-182">The module identifier.</span></span>|  
|<span data-ttu-id="8d893-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="8d893-183">StubMethodID</span></span>|<span data-ttu-id="8d893-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8d893-184">win:UInt64</span></span>|<span data-ttu-id="8d893-185">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="8d893-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="8d893-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="8d893-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="8d893-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8d893-187">win:UInt32</span></span>|<span data-ttu-id="8d893-188">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="8d893-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="8d893-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="8d893-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-190">win:UnicodeString</span></span>|<span data-ttu-id="8d893-191">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="8d893-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="8d893-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="8d893-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-193">win:UnicodeString</span></span>|<span data-ttu-id="8d893-194">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="8d893-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="8d893-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="8d893-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d893-196">win:UnicodeString</span></span>|<span data-ttu-id="8d893-197">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d893-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="8d893-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8d893-198">ClrInstanceID</span></span>|<span data-ttu-id="8d893-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8d893-199">win:UInt16</span></span>|<span data-ttu-id="8d893-200">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="8d893-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="8d893-201">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="8d893-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="8d893-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d893-202">See also</span></span>

- [<span data-ttu-id="8d893-203">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="8d893-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
