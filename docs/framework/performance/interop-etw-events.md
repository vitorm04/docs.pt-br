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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949299"
---
# <a name="interop-etw-events"></a><span data-ttu-id="d2a68-102">Eventos ETW de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d2a68-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="d2a68-103">Eventos de interoperabilidade capturam informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d2a68-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="d2a68-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="d2a68-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="d2a68-105">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="d2a68-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="d2a68-106">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="d2a68-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="d2a68-107">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="d2a68-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="d2a68-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="d2a68-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="d2a68-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="d2a68-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d2a68-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="d2a68-110">Keyword for raising the event</span></span>|<span data-ttu-id="d2a68-111">Nível</span><span class="sxs-lookup"><span data-stu-id="d2a68-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d2a68-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="d2a68-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="d2a68-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="d2a68-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="d2a68-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="d2a68-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d2a68-115">evento</span><span class="sxs-lookup"><span data-stu-id="d2a68-115">Event</span></span>|<span data-ttu-id="d2a68-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="d2a68-116">Event ID</span></span>|<span data-ttu-id="d2a68-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="d2a68-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="d2a68-118">88</span><span class="sxs-lookup"><span data-stu-id="d2a68-118">88</span></span>|<span data-ttu-id="d2a68-119">O stub em MSIL foi gerado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="d2a68-120">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="d2a68-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d2a68-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="d2a68-121">Field name</span></span>|<span data-ttu-id="d2a68-122">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="d2a68-122">Data type</span></span>|<span data-ttu-id="d2a68-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2a68-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d2a68-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="d2a68-124">ModuleID</span></span>|<span data-ttu-id="d2a68-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d2a68-125">win:UInt16</span></span>|<span data-ttu-id="d2a68-126">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="d2a68-126">The module identifier.</span></span>|  
|<span data-ttu-id="d2a68-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="d2a68-127">StubMethodID</span></span>|<span data-ttu-id="d2a68-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d2a68-128">win:UInt64</span></span>|<span data-ttu-id="d2a68-129">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="d2a68-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="d2a68-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="d2a68-130">StubFlags</span></span>|<span data-ttu-id="d2a68-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d2a68-131">win:UInt64</span></span>|<span data-ttu-id="d2a68-132">Os sinalizadores para o stub:</span><span class="sxs-lookup"><span data-stu-id="d2a68-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="d2a68-133">0x1 – interoperabilidade revesa.</span><span class="sxs-lookup"><span data-stu-id="d2a68-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="d2a68-134">0x2 – interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d2a68-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="d2a68-135">0x4 – stub gerado pelo NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="d2a68-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="d2a68-136">0x8 – delegado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="d2a68-137">0x10 – argumento variável.</span><span class="sxs-lookup"><span data-stu-id="d2a68-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="d2a68-138">0x20 – receptor não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="d2a68-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="d2a68-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="d2a68-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d2a68-140">win:UInt32</span></span>|<span data-ttu-id="d2a68-141">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="d2a68-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="d2a68-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="d2a68-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-143">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-144">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="d2a68-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="d2a68-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="d2a68-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-146">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-147">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="d2a68-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="d2a68-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="d2a68-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-149">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-150">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="d2a68-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="d2a68-151">NativeMethodSignature</span></span>|<span data-ttu-id="d2a68-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-152">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-153">A assinatura do método nativo.</span><span class="sxs-lookup"><span data-stu-id="d2a68-153">The native method signature.</span></span>|  
|<span data-ttu-id="d2a68-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="d2a68-154">StubMethodSignature</span></span>|<span data-ttu-id="d2a68-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-155">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-156">A assinatura do método de stub.</span><span class="sxs-lookup"><span data-stu-id="d2a68-156">The stub method signature.</span></span>|  
|<span data-ttu-id="d2a68-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="d2a68-157">StubMethodILCode</span></span>|<span data-ttu-id="d2a68-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-158">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-159">O código MSIL para o método de stub.</span><span class="sxs-lookup"><span data-stu-id="d2a68-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="d2a68-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d2a68-160">ClrInstanceID</span></span>|<span data-ttu-id="d2a68-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d2a68-161">win:UInt16</span></span>|<span data-ttu-id="d2a68-162">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d2a68-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d2a68-163">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="d2a68-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="d2a68-164">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="d2a68-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="d2a68-165">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="d2a68-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d2a68-166">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="d2a68-166">Keyword for raising the event</span></span>|<span data-ttu-id="d2a68-167">Nível</span><span class="sxs-lookup"><span data-stu-id="d2a68-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d2a68-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="d2a68-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="d2a68-169">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="d2a68-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="d2a68-170">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="d2a68-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d2a68-171">evento</span><span class="sxs-lookup"><span data-stu-id="d2a68-171">Event</span></span>|<span data-ttu-id="d2a68-172">ID do evento</span><span class="sxs-lookup"><span data-stu-id="d2a68-172">Event ID</span></span>|<span data-ttu-id="d2a68-173">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="d2a68-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="d2a68-174">89</span><span class="sxs-lookup"><span data-stu-id="d2a68-174">89</span></span>|<span data-ttu-id="d2a68-175">O cache MSIL foi acessado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="d2a68-176">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="d2a68-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d2a68-177">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="d2a68-177">Field name</span></span>|<span data-ttu-id="d2a68-178">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="d2a68-178">Data type</span></span>|<span data-ttu-id="d2a68-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2a68-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d2a68-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="d2a68-180">ModuleID</span></span>|<span data-ttu-id="d2a68-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d2a68-181">win:UInt16</span></span>|<span data-ttu-id="d2a68-182">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="d2a68-182">The module identifier.</span></span>|  
|<span data-ttu-id="d2a68-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="d2a68-183">StubMethodID</span></span>|<span data-ttu-id="d2a68-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d2a68-184">win:UInt64</span></span>|<span data-ttu-id="d2a68-185">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="d2a68-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="d2a68-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="d2a68-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="d2a68-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d2a68-187">win:UInt32</span></span>|<span data-ttu-id="d2a68-188">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="d2a68-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="d2a68-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="d2a68-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-190">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-191">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="d2a68-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="d2a68-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="d2a68-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-193">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-194">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="d2a68-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="d2a68-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="d2a68-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d2a68-196">win:UnicodeString</span></span>|<span data-ttu-id="d2a68-197">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d2a68-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="d2a68-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d2a68-198">ClrInstanceID</span></span>|<span data-ttu-id="d2a68-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d2a68-199">win:UInt16</span></span>|<span data-ttu-id="d2a68-200">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d2a68-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d2a68-201">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="d2a68-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="d2a68-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2a68-202">See also</span></span>

- [<span data-ttu-id="d2a68-203">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="d2a68-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
