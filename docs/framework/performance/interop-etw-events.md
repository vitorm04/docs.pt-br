---
title: Eventos ETW de interoperabilidade
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09b2848619256a255cc27f0268d46e5e6db8cbe4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083602"
---
# <a name="interop-etw-events"></a><span data-ttu-id="f007c-102">Eventos ETW de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="f007c-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f007c-103">Eventos de interoperabilidade capturam informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="f007c-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="f007c-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="f007c-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="f007c-105">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="f007c-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="f007c-106">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="f007c-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="f007c-107">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="f007c-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="f007c-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="f007c-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="f007c-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f007c-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f007c-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="f007c-110">Keyword for raising the event</span></span>|<span data-ttu-id="f007c-111">Nível</span><span class="sxs-lookup"><span data-stu-id="f007c-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f007c-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="f007c-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="f007c-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="f007c-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="f007c-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f007c-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f007c-115">evento</span><span class="sxs-lookup"><span data-stu-id="f007c-115">Event</span></span>|<span data-ttu-id="f007c-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="f007c-116">Event ID</span></span>|<span data-ttu-id="f007c-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="f007c-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="f007c-118">88</span><span class="sxs-lookup"><span data-stu-id="f007c-118">88</span></span>|<span data-ttu-id="f007c-119">O stub em MSIL foi gerado.</span><span class="sxs-lookup"><span data-stu-id="f007c-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="f007c-120">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="f007c-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f007c-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="f007c-121">Field name</span></span>|<span data-ttu-id="f007c-122">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="f007c-122">Data type</span></span>|<span data-ttu-id="f007c-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f007c-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f007c-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="f007c-124">ModuleID</span></span>|<span data-ttu-id="f007c-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f007c-125">win:UInt16</span></span>|<span data-ttu-id="f007c-126">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="f007c-126">The module identifier.</span></span>|  
|<span data-ttu-id="f007c-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="f007c-127">StubMethodID</span></span>|<span data-ttu-id="f007c-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f007c-128">win:UInt64</span></span>|<span data-ttu-id="f007c-129">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="f007c-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="f007c-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="f007c-130">StubFlags</span></span>|<span data-ttu-id="f007c-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f007c-131">win:UInt64</span></span>|<span data-ttu-id="f007c-132">Os sinalizadores para o stub:</span><span class="sxs-lookup"><span data-stu-id="f007c-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="f007c-133">0x1 – interoperabilidade revesa.</span><span class="sxs-lookup"><span data-stu-id="f007c-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="f007c-134">0x2 – interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f007c-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="f007c-135">0x4 – stub gerado pelo NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="f007c-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="f007c-136">0x8 – delegado.</span><span class="sxs-lookup"><span data-stu-id="f007c-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="f007c-137">0x10 – argumento variável.</span><span class="sxs-lookup"><span data-stu-id="f007c-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="f007c-138">0x20 – receptor não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="f007c-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="f007c-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="f007c-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f007c-140">win:UInt32</span></span>|<span data-ttu-id="f007c-141">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="f007c-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="f007c-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="f007c-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-143">win:UnicodeString</span></span>|<span data-ttu-id="f007c-144">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="f007c-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="f007c-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="f007c-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-146">win:UnicodeString</span></span>|<span data-ttu-id="f007c-147">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="f007c-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="f007c-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="f007c-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-149">win:UnicodeString</span></span>|<span data-ttu-id="f007c-150">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="f007c-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="f007c-151">NativeMethodSignature</span></span>|<span data-ttu-id="f007c-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-152">win:UnicodeString</span></span>|<span data-ttu-id="f007c-153">A assinatura do método nativo.</span><span class="sxs-lookup"><span data-stu-id="f007c-153">The native method signature.</span></span>|  
|<span data-ttu-id="f007c-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="f007c-154">StubMethodSignature</span></span>|<span data-ttu-id="f007c-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-155">win:UnicodeString</span></span>|<span data-ttu-id="f007c-156">A assinatura do método de stub.</span><span class="sxs-lookup"><span data-stu-id="f007c-156">The stub method signature.</span></span>|  
|<span data-ttu-id="f007c-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="f007c-157">StubMethodILCode</span></span>|<span data-ttu-id="f007c-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-158">win:UnicodeString</span></span>|<span data-ttu-id="f007c-159">O código MSIL para o método de stub.</span><span class="sxs-lookup"><span data-stu-id="f007c-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="f007c-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f007c-160">ClrInstanceID</span></span>|<span data-ttu-id="f007c-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f007c-161">win:UInt16</span></span>|<span data-ttu-id="f007c-162">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f007c-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f007c-163">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="f007c-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="f007c-164">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="f007c-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="f007c-165">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="f007c-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f007c-166">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="f007c-166">Keyword for raising the event</span></span>|<span data-ttu-id="f007c-167">Nível</span><span class="sxs-lookup"><span data-stu-id="f007c-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f007c-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="f007c-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="f007c-169">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="f007c-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="f007c-170">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f007c-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f007c-171">evento</span><span class="sxs-lookup"><span data-stu-id="f007c-171">Event</span></span>|<span data-ttu-id="f007c-172">ID do evento</span><span class="sxs-lookup"><span data-stu-id="f007c-172">Event ID</span></span>|<span data-ttu-id="f007c-173">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="f007c-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="f007c-174">89</span><span class="sxs-lookup"><span data-stu-id="f007c-174">89</span></span>|<span data-ttu-id="f007c-175">O cache MSIL foi acessado.</span><span class="sxs-lookup"><span data-stu-id="f007c-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="f007c-176">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="f007c-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f007c-177">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="f007c-177">Field name</span></span>|<span data-ttu-id="f007c-178">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="f007c-178">Data type</span></span>|<span data-ttu-id="f007c-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="f007c-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f007c-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="f007c-180">ModuleID</span></span>|<span data-ttu-id="f007c-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f007c-181">win:UInt16</span></span>|<span data-ttu-id="f007c-182">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="f007c-182">The module identifier.</span></span>|  
|<span data-ttu-id="f007c-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="f007c-183">StubMethodID</span></span>|<span data-ttu-id="f007c-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f007c-184">win:UInt64</span></span>|<span data-ttu-id="f007c-185">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="f007c-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="f007c-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="f007c-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="f007c-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f007c-187">win:UInt32</span></span>|<span data-ttu-id="f007c-188">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="f007c-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="f007c-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="f007c-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-190">win:UnicodeString</span></span>|<span data-ttu-id="f007c-191">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="f007c-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="f007c-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="f007c-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-193">win:UnicodeString</span></span>|<span data-ttu-id="f007c-194">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="f007c-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="f007c-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="f007c-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f007c-196">win:UnicodeString</span></span>|<span data-ttu-id="f007c-197">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f007c-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="f007c-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f007c-198">ClrInstanceID</span></span>|<span data-ttu-id="f007c-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f007c-199">win:UInt16</span></span>|<span data-ttu-id="f007c-200">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f007c-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f007c-201">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="f007c-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="f007c-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f007c-202">See also</span></span>

- [<span data-ttu-id="f007c-203">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="f007c-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
