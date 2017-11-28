---
title: Eventos ETW de interoperabilidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55097e38161ea5c76f4e46584241344ec5a52cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="72eed-102">Eventos ETW de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="72eed-102">Interop ETW Events</span></span>
<span data-ttu-id="72eed-103"><a name="top"></a> Eventos de interoperabilidade capturam informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="72eed-103"><a name="top"></a> Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="72eed-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="72eed-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="72eed-105">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="72eed-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="72eed-106">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="72eed-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="72eed-107">Evento ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="72eed-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="72eed-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="72eed-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="72eed-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="72eed-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="72eed-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="72eed-110">Keyword for raising the event</span></span>|<span data-ttu-id="72eed-111">Nível</span><span class="sxs-lookup"><span data-stu-id="72eed-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="72eed-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="72eed-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="72eed-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="72eed-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="72eed-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="72eed-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="72eed-115">Evento</span><span class="sxs-lookup"><span data-stu-id="72eed-115">Event</span></span>|<span data-ttu-id="72eed-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="72eed-116">Event ID</span></span>|<span data-ttu-id="72eed-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="72eed-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="72eed-118">88</span><span class="sxs-lookup"><span data-stu-id="72eed-118">88</span></span>|<span data-ttu-id="72eed-119">O stub em MSIL foi gerado.</span><span class="sxs-lookup"><span data-stu-id="72eed-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="72eed-120">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="72eed-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="72eed-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="72eed-121">Field name</span></span>|<span data-ttu-id="72eed-122">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="72eed-122">Data type</span></span>|<span data-ttu-id="72eed-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="72eed-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="72eed-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="72eed-124">ModuleID</span></span>|<span data-ttu-id="72eed-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="72eed-125">win:UInt16</span></span>|<span data-ttu-id="72eed-126">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="72eed-126">The module identifier.</span></span>|  
|<span data-ttu-id="72eed-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="72eed-127">StubMethodID</span></span>|<span data-ttu-id="72eed-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="72eed-128">win:UInt64</span></span>|<span data-ttu-id="72eed-129">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="72eed-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="72eed-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="72eed-130">StubFlags</span></span>|<span data-ttu-id="72eed-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="72eed-131">win:UInt64</span></span>|<span data-ttu-id="72eed-132">Os sinalizadores para o stub:</span><span class="sxs-lookup"><span data-stu-id="72eed-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="72eed-133">0x1 – interoperabilidade revesa.</span><span class="sxs-lookup"><span data-stu-id="72eed-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="72eed-134">0x2 – interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="72eed-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="72eed-135">0x4 – stub gerado pelo NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="72eed-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="72eed-136">0x8 – delegado.</span><span class="sxs-lookup"><span data-stu-id="72eed-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="72eed-137">0x10 – argumento variável.</span><span class="sxs-lookup"><span data-stu-id="72eed-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="72eed-138">0x20 – receptor não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="72eed-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="72eed-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="72eed-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="72eed-140">win:UInt32</span></span>|<span data-ttu-id="72eed-141">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="72eed-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="72eed-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="72eed-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-143">win:UnicodeString</span></span>|<span data-ttu-id="72eed-144">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="72eed-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="72eed-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="72eed-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-146">win:UnicodeString</span></span>|<span data-ttu-id="72eed-147">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="72eed-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="72eed-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="72eed-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-149">win:UnicodeString</span></span>|<span data-ttu-id="72eed-150">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="72eed-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="72eed-151">NativeMethodSignature</span></span>|<span data-ttu-id="72eed-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-152">win:UnicodeString</span></span>|<span data-ttu-id="72eed-153">A assinatura do método nativo.</span><span class="sxs-lookup"><span data-stu-id="72eed-153">The native method signature.</span></span>|  
|<span data-ttu-id="72eed-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="72eed-154">StubMethodSignature</span></span>|<span data-ttu-id="72eed-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-155">win:UnicodeString</span></span>|<span data-ttu-id="72eed-156">A assinatura do método de stub.</span><span class="sxs-lookup"><span data-stu-id="72eed-156">The stub method signature.</span></span>|  
|<span data-ttu-id="72eed-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="72eed-157">StubMethodILCode</span></span>|<span data-ttu-id="72eed-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-158">win:UnicodeString</span></span>|<span data-ttu-id="72eed-159">O código MSIL para o método de stub.</span><span class="sxs-lookup"><span data-stu-id="72eed-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="72eed-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="72eed-160">ClrInstanceID</span></span>|<span data-ttu-id="72eed-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="72eed-161">win:UInt16</span></span>|<span data-ttu-id="72eed-162">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="72eed-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="72eed-163">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="72eed-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="72eed-164">Evento ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="72eed-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="72eed-165">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="72eed-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="72eed-166">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="72eed-166">Keyword for raising the event</span></span>|<span data-ttu-id="72eed-167">Nível</span><span class="sxs-lookup"><span data-stu-id="72eed-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="72eed-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="72eed-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="72eed-169">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="72eed-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="72eed-170">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="72eed-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="72eed-171">Evento</span><span class="sxs-lookup"><span data-stu-id="72eed-171">Event</span></span>|<span data-ttu-id="72eed-172">ID do evento</span><span class="sxs-lookup"><span data-stu-id="72eed-172">Event ID</span></span>|<span data-ttu-id="72eed-173">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="72eed-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="72eed-174">89</span><span class="sxs-lookup"><span data-stu-id="72eed-174">89</span></span>|<span data-ttu-id="72eed-175">O cache MSIL foi acessado.</span><span class="sxs-lookup"><span data-stu-id="72eed-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="72eed-176">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="72eed-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="72eed-177">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="72eed-177">Field name</span></span>|<span data-ttu-id="72eed-178">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="72eed-178">Data type</span></span>|<span data-ttu-id="72eed-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="72eed-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="72eed-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="72eed-180">ModuleID</span></span>|<span data-ttu-id="72eed-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="72eed-181">win:UInt16</span></span>|<span data-ttu-id="72eed-182">O identificador de módulo.</span><span class="sxs-lookup"><span data-stu-id="72eed-182">The module identifier.</span></span>|  
|<span data-ttu-id="72eed-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="72eed-183">StubMethodID</span></span>|<span data-ttu-id="72eed-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="72eed-184">win:UInt64</span></span>|<span data-ttu-id="72eed-185">O identificador do método de stub.</span><span class="sxs-lookup"><span data-stu-id="72eed-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="72eed-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="72eed-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="72eed-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="72eed-187">win:UInt32</span></span>|<span data-ttu-id="72eed-188">O token para o método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="72eed-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="72eed-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="72eed-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-190">win:UnicodeString</span></span>|<span data-ttu-id="72eed-191">O namespace do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="72eed-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="72eed-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="72eed-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-193">win:UnicodeString</span></span>|<span data-ttu-id="72eed-194">O nome do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="72eed-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="72eed-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="72eed-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="72eed-196">win:UnicodeString</span></span>|<span data-ttu-id="72eed-197">A assinatura do método de interoperabilidade gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72eed-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="72eed-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="72eed-198">ClrInstanceID</span></span>|<span data-ttu-id="72eed-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="72eed-199">win:UInt16</span></span>|<span data-ttu-id="72eed-200">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="72eed-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="72eed-201">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="72eed-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="72eed-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72eed-202">See Also</span></span>  
 [<span data-ttu-id="72eed-203">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="72eed-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
