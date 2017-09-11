---
title: Eventos ETW de interoperabilidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 55097e38161ea5c76f4e46584241344ec5a52cb9
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="interop-etw-events"></a><span data-ttu-id="9e24d-102">Eventos ETW de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="9e24d-102">Interop ETW Events</span></span>
<span data-ttu-id="9e24d-103"><a name="top"></a> Eventos de interoperabilidade capturam informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="9e24d-103"><a name="top"></a> Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="9e24d-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="9e24d-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="9e24d-105">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="9e24d-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="9e24d-106">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="9e24d-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="9e24d-107">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="9e24d-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="9e24d-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="9e24d-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="9e24d-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="9e24d-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="9e24d-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="9e24d-110">Keyword for raising the event</span></span>|<span data-ttu-id="9e24d-111">Nível</span><span class="sxs-lookup"><span data-stu-id="9e24d-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="9e24d-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="9e24d-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="9e24d-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="9e24d-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="9e24d-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="9e24d-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9e24d-115">Evento</span><span class="sxs-lookup"><span data-stu-id="9e24d-115">Event</span></span>|<span data-ttu-id="9e24d-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="9e24d-116">Event ID</span></span>|<span data-ttu-id="9e24d-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="9e24d-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="9e24d-118">88</span><span class="sxs-lookup"><span data-stu-id="9e24d-118">88</span></span>|<span data-ttu-id="9e24d-119">O stub em MSIL foi gerado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="9e24d-120">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="9e24d-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9e24d-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="9e24d-121">Field name</span></span>|<span data-ttu-id="9e24d-122">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="9e24d-122">Data type</span></span>|<span data-ttu-id="9e24d-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e24d-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9e24d-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="9e24d-124">ModuleID</span></span>|<span data-ttu-id="9e24d-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9e24d-125">win:UInt16</span></span>|<span data-ttu-id="9e24d-126">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="9e24d-126">The module identifier.</span></span>|  
|<span data-ttu-id="9e24d-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="9e24d-127">StubMethodID</span></span>|<span data-ttu-id="9e24d-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9e24d-128">win:UInt64</span></span>|<span data-ttu-id="9e24d-129">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="9e24d-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="9e24d-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="9e24d-130">StubFlags</span></span>|<span data-ttu-id="9e24d-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9e24d-131">win:UInt64</span></span>|<span data-ttu-id="9e24d-132">Os sinalizadores para o stub:</span><span class="sxs-lookup"><span data-stu-id="9e24d-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="9e24d-133">0x1 – interoperabilidade revesa.</span><span class="sxs-lookup"><span data-stu-id="9e24d-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="9e24d-134">0x2 – interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="9e24d-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="9e24d-135">0x4 – stub gerado pelo NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="9e24d-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="9e24d-136">0x8 – delegado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="9e24d-137">0x10 – argumento variável.</span><span class="sxs-lookup"><span data-stu-id="9e24d-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="9e24d-138">0x20 – receptor não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="9e24d-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="9e24d-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="9e24d-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9e24d-140">win:UInt32</span></span>|<span data-ttu-id="9e24d-141">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="9e24d-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="9e24d-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="9e24d-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-143">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-144">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="9e24d-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="9e24d-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="9e24d-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-146">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-147">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="9e24d-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="9e24d-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="9e24d-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-149">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-150">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="9e24d-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="9e24d-151">NativeMethodSignature</span></span>|<span data-ttu-id="9e24d-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-152">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-153">A assinatura do método nativo.</span><span class="sxs-lookup"><span data-stu-id="9e24d-153">The native method signature.</span></span>|  
|<span data-ttu-id="9e24d-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="9e24d-154">StubMethodSignature</span></span>|<span data-ttu-id="9e24d-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-155">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-156">A assinatura do método de stub.</span><span class="sxs-lookup"><span data-stu-id="9e24d-156">The stub method signature.</span></span>|  
|<span data-ttu-id="9e24d-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="9e24d-157">StubMethodILCode</span></span>|<span data-ttu-id="9e24d-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-158">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-159">O código MSIL para o método de stub.</span><span class="sxs-lookup"><span data-stu-id="9e24d-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="9e24d-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9e24d-160">ClrInstanceID</span></span>|<span data-ttu-id="9e24d-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9e24d-161">win:UInt16</span></span>|<span data-ttu-id="9e24d-162">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9e24d-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9e24d-163">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="9e24d-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="9e24d-164">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="9e24d-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="9e24d-165">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="9e24d-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9e24d-166">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="9e24d-166">Keyword for raising the event</span></span>|<span data-ttu-id="9e24d-167">Nível</span><span class="sxs-lookup"><span data-stu-id="9e24d-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="9e24d-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="9e24d-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="9e24d-169">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="9e24d-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="9e24d-170">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="9e24d-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9e24d-171">Evento</span><span class="sxs-lookup"><span data-stu-id="9e24d-171">Event</span></span>|<span data-ttu-id="9e24d-172">ID do evento</span><span class="sxs-lookup"><span data-stu-id="9e24d-172">Event ID</span></span>|<span data-ttu-id="9e24d-173">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="9e24d-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="9e24d-174">89</span><span class="sxs-lookup"><span data-stu-id="9e24d-174">89</span></span>|<span data-ttu-id="9e24d-175">O cache MSIL foi acessado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="9e24d-176">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="9e24d-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9e24d-177">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="9e24d-177">Field name</span></span>|<span data-ttu-id="9e24d-178">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="9e24d-178">Data type</span></span>|<span data-ttu-id="9e24d-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e24d-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9e24d-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="9e24d-180">ModuleID</span></span>|<span data-ttu-id="9e24d-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9e24d-181">win:UInt16</span></span>|<span data-ttu-id="9e24d-182">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="9e24d-182">The module identifier.</span></span>|  
|<span data-ttu-id="9e24d-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="9e24d-183">StubMethodID</span></span>|<span data-ttu-id="9e24d-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9e24d-184">win:UInt64</span></span>|<span data-ttu-id="9e24d-185">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="9e24d-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="9e24d-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="9e24d-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="9e24d-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9e24d-187">win:UInt32</span></span>|<span data-ttu-id="9e24d-188">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="9e24d-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="9e24d-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="9e24d-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-190">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-191">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="9e24d-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="9e24d-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="9e24d-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-193">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-194">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="9e24d-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="9e24d-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="9e24d-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e24d-196">win:UnicodeString</span></span>|<span data-ttu-id="9e24d-197">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e24d-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="9e24d-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9e24d-198">ClrInstanceID</span></span>|<span data-ttu-id="9e24d-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9e24d-199">win:UInt16</span></span>|<span data-ttu-id="9e24d-200">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9e24d-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9e24d-201">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="9e24d-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="9e24d-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e24d-202">See Also</span></span>  
 [<span data-ttu-id="9e24d-203">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="9e24d-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)

