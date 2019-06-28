---
title: Eventos ETW de interoperabilidade
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c52c9bf37e67e4d26867d2b3754945e86e2bf609
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422418"
---
# <a name="interop-etw-events"></a><span data-ttu-id="72761-102">Eventos ETW de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="72761-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="72761-103">Eventos de interoperabilidade capturam informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="72761-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="72761-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="72761-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="72761-105">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="72761-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="72761-106">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="72761-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="72761-107">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="72761-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="72761-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="72761-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="72761-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="72761-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="72761-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="72761-110">Keyword for raising the event</span></span>|<span data-ttu-id="72761-111">Nível</span><span class="sxs-lookup"><span data-stu-id="72761-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="72761-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="72761-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="72761-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="72761-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="72761-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="72761-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="72761-115">evento</span><span class="sxs-lookup"><span data-stu-id="72761-115">Event</span></span>|<span data-ttu-id="72761-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="72761-116">Event ID</span></span>|<span data-ttu-id="72761-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="72761-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="72761-118">88</span><span class="sxs-lookup"><span data-stu-id="72761-118">88</span></span>|<span data-ttu-id="72761-119">O stub em MSIL foi gerado.</span><span class="sxs-lookup"><span data-stu-id="72761-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="72761-120">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="72761-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="72761-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="72761-121">Field name</span></span>|<span data-ttu-id="72761-122">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="72761-122">Data type</span></span>|<span data-ttu-id="72761-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="72761-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="72761-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="72761-124">ModuleID</span></span>|<span data-ttu-id="72761-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="72761-125">win:UInt16</span></span>|<span data-ttu-id="72761-126">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="72761-126">The module identifier.</span></span>|  
|<span data-ttu-id="72761-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="72761-127">StubMethodID</span></span>|<span data-ttu-id="72761-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="72761-128">win:UInt64</span></span>|<span data-ttu-id="72761-129">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="72761-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="72761-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="72761-130">StubFlags</span></span>|<span data-ttu-id="72761-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="72761-131">win:UInt64</span></span>|<span data-ttu-id="72761-132">Os sinalizadores para o stub:</span><span class="sxs-lookup"><span data-stu-id="72761-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="72761-133">0x1 – interoperabilidade revesa.</span><span class="sxs-lookup"><span data-stu-id="72761-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="72761-134">0x2 – interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="72761-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="72761-135">0x4 – stub gerado pelo NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="72761-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="72761-136">0x8 – delegado.</span><span class="sxs-lookup"><span data-stu-id="72761-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="72761-137">0x10 – argumento variável.</span><span class="sxs-lookup"><span data-stu-id="72761-137">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="72761-138">0x20 – receptor não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="72761-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="72761-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="72761-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="72761-140">win:UInt32</span></span>|<span data-ttu-id="72761-141">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="72761-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="72761-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="72761-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-143">win:UnicodeString</span></span>|<span data-ttu-id="72761-144">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="72761-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="72761-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="72761-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-146">win:UnicodeString</span></span>|<span data-ttu-id="72761-147">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="72761-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="72761-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="72761-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-149">win:UnicodeString</span></span>|<span data-ttu-id="72761-150">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="72761-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="72761-151">NativeMethodSignature</span></span>|<span data-ttu-id="72761-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-152">win:UnicodeString</span></span>|<span data-ttu-id="72761-153">A assinatura do método nativo.</span><span class="sxs-lookup"><span data-stu-id="72761-153">The native method signature.</span></span>|  
|<span data-ttu-id="72761-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="72761-154">StubMethodSignature</span></span>|<span data-ttu-id="72761-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-155">win:UnicodeString</span></span>|<span data-ttu-id="72761-156">A assinatura do método de stub.</span><span class="sxs-lookup"><span data-stu-id="72761-156">The stub method signature.</span></span>|  
|<span data-ttu-id="72761-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="72761-157">StubMethodILCode</span></span>|<span data-ttu-id="72761-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-158">win:UnicodeString</span></span>|<span data-ttu-id="72761-159">O código MSIL para o método de stub.</span><span class="sxs-lookup"><span data-stu-id="72761-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="72761-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="72761-160">ClrInstanceID</span></span>|<span data-ttu-id="72761-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="72761-161">win:UInt16</span></span>|<span data-ttu-id="72761-162">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="72761-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="72761-163">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="72761-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="72761-164">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="72761-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="72761-165">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="72761-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="72761-166">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="72761-166">Keyword for raising the event</span></span>|<span data-ttu-id="72761-167">Nível</span><span class="sxs-lookup"><span data-stu-id="72761-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="72761-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="72761-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="72761-169">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="72761-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="72761-170">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="72761-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="72761-171">evento</span><span class="sxs-lookup"><span data-stu-id="72761-171">Event</span></span>|<span data-ttu-id="72761-172">ID do evento</span><span class="sxs-lookup"><span data-stu-id="72761-172">Event ID</span></span>|<span data-ttu-id="72761-173">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="72761-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="72761-174">89</span><span class="sxs-lookup"><span data-stu-id="72761-174">89</span></span>|<span data-ttu-id="72761-175">O cache MSIL foi acessado.</span><span class="sxs-lookup"><span data-stu-id="72761-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="72761-176">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="72761-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="72761-177">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="72761-177">Field name</span></span>|<span data-ttu-id="72761-178">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="72761-178">Data type</span></span>|<span data-ttu-id="72761-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="72761-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="72761-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="72761-180">ModuleID</span></span>|<span data-ttu-id="72761-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="72761-181">win:UInt16</span></span>|<span data-ttu-id="72761-182">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="72761-182">The module identifier.</span></span>|  
|<span data-ttu-id="72761-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="72761-183">StubMethodID</span></span>|<span data-ttu-id="72761-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="72761-184">win:UInt64</span></span>|<span data-ttu-id="72761-185">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="72761-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="72761-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="72761-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="72761-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="72761-187">win:UInt32</span></span>|<span data-ttu-id="72761-188">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="72761-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="72761-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="72761-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-190">win:UnicodeString</span></span>|<span data-ttu-id="72761-191">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="72761-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="72761-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="72761-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-193">win:UnicodeString</span></span>|<span data-ttu-id="72761-194">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="72761-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="72761-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="72761-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72761-196">win:UnicodeString</span></span>|<span data-ttu-id="72761-197">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72761-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="72761-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="72761-198">ClrInstanceID</span></span>|<span data-ttu-id="72761-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="72761-199">win:UInt16</span></span>|<span data-ttu-id="72761-200">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="72761-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="72761-201">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="72761-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="72761-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72761-202">See also</span></span>

- [<span data-ttu-id="72761-203">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="72761-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
