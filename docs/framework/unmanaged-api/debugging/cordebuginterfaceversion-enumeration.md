---
title: "Enumeração CorDebugInterfaceVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b5d28e6def34c9263d519c2eeb9cc432656bd1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="1441a-102">Enumeração CorDebugInterfaceVersion</span><span class="sxs-lookup"><span data-stu-id="1441a-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="1441a-103">Especifica uma interface, uma versão do .NET Framework ou uma versão do .NET Framework na qual uma interface foi introduzida.</span><span class="sxs-lookup"><span data-stu-id="1441a-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1441a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1441a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo   
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot   
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a><span data-ttu-id="1441a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1441a-105">Members</span></span>  
 <span data-ttu-id="1441a-106">A tabela a seguir fornece links de cada valor de enumeração para a interface correspondente.</span><span class="sxs-lookup"><span data-stu-id="1441a-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="1441a-107">Além disso, a tabela indica a primeira versão do .NET Framework na qual a interface teve suporte.</span><span class="sxs-lookup"><span data-stu-id="1441a-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="1441a-108">Membro</span><span class="sxs-lookup"><span data-stu-id="1441a-108">Member</span></span>|<span data-ttu-id="1441a-109">Especifica</span><span class="sxs-lookup"><span data-stu-id="1441a-109">Specifies</span></span>|<span data-ttu-id="1441a-110">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1441a-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="1441a-111">A versão do .NET Framework é inválida.</span><span class="sxs-lookup"><span data-stu-id="1441a-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="1441a-112">A versão do .NET Framework, incluindo todos os seus service packs, é 1.0.</span><span class="sxs-lookup"><span data-stu-id="1441a-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="1441a-113">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="1441a-114">A versão do .NET Framework, incluindo todos os service packs, é 1.1.</span><span class="sxs-lookup"><span data-stu-id="1441a-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="1441a-115">1.1</span><span class="sxs-lookup"><span data-stu-id="1441a-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="1441a-116">A versão do .NET Framework, incluindo todos os service packs, é 2.0.</span><span class="sxs-lookup"><span data-stu-id="1441a-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="1441a-117">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="1441a-118">A versão do .NET Framework, incluindo todos os service packs, é 4.</span><span class="sxs-lookup"><span data-stu-id="1441a-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="1441a-119">4</span><span class="sxs-lookup"><span data-stu-id="1441a-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="1441a-120">A versão do .NET Framework, incluindo todos os service packs, é 4.5.</span><span class="sxs-lookup"><span data-stu-id="1441a-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="1441a-121">4.5</span><span class="sxs-lookup"><span data-stu-id="1441a-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="1441a-122">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="1441a-122">ICorDebugManagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)|<span data-ttu-id="1441a-123">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="1441a-124">ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="1441a-124">ICorDebugUnmanagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)|<span data-ttu-id="1441a-125">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="1441a-126">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1441a-126">ICorDebug</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)|<span data-ttu-id="1441a-127">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="1441a-128">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="1441a-128">ICorDebugController</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)|<span data-ttu-id="1441a-129">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="1441a-130">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="1441a-130">ICorDebugAppDomain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)|<span data-ttu-id="1441a-131">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="1441a-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="1441a-132">ICorDebugAssembly</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)|<span data-ttu-id="1441a-133">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="1441a-134">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="1441a-134">ICorDebugProcess</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)|<span data-ttu-id="1441a-135">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="1441a-136">ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1441a-136">ICorDebugBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)|<span data-ttu-id="1441a-137">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="1441a-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1441a-138">ICorDebugFunctionBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="1441a-139">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="1441a-140">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1441a-140">ICorDebugModuleBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="1441a-141">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="1441a-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1441a-142">ICorDebugValueBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="1441a-143">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="1441a-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="1441a-144">ICorDebugStepper</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)|<span data-ttu-id="1441a-145">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="1441a-146">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="1441a-146">ICorDebugRegisterSet</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)|<span data-ttu-id="1441a-147">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="1441a-148">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="1441a-148">ICorDebugThread</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)|<span data-ttu-id="1441a-149">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="1441a-150">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="1441a-150">ICorDebugChain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)|<span data-ttu-id="1441a-151">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="1441a-152">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="1441a-152">ICorDebugFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)|<span data-ttu-id="1441a-153">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="1441a-154">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="1441a-154">ICorDebugILFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)|<span data-ttu-id="1441a-155">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="1441a-156">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="1441a-156">ICorDebugNativeFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)|<span data-ttu-id="1441a-157">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="1441a-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="1441a-158">ICorDebugModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)|<span data-ttu-id="1441a-159">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="1441a-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="1441a-160">ICorDebugFunction</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)|<span data-ttu-id="1441a-161">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="1441a-162">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="1441a-162">ICorDebugCode</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)|<span data-ttu-id="1441a-163">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="1441a-164">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="1441a-164">ICorDebugClass</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)|<span data-ttu-id="1441a-165">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="1441a-166">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="1441a-166">ICorDebugEval</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)|<span data-ttu-id="1441a-167">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="1441a-168">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="1441a-168">ICorDebugValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)|<span data-ttu-id="1441a-169">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="1441a-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="1441a-170">ICorDebugGenericValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)|<span data-ttu-id="1441a-171">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="1441a-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="1441a-172">ICorDebugReferenceValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)|<span data-ttu-id="1441a-173">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="1441a-174">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="1441a-174">ICorDebugHeapValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)|<span data-ttu-id="1441a-175">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="1441a-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="1441a-176">ICorDebugObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)|<span data-ttu-id="1441a-177">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="1441a-178">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="1441a-178">ICorDebugBoxValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)|<span data-ttu-id="1441a-179">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="1441a-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="1441a-180">ICorDebugStringValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)|<span data-ttu-id="1441a-181">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="1441a-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="1441a-182">ICorDebugArrayValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)|<span data-ttu-id="1441a-183">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="1441a-184">ICorDebugContext</span><span class="sxs-lookup"><span data-stu-id="1441a-184">ICorDebugContext</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)|<span data-ttu-id="1441a-185">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="1441a-186">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-186">ICorDebugEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)|<span data-ttu-id="1441a-187">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="1441a-188">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-188">ICorDebugObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)|<span data-ttu-id="1441a-189">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="1441a-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-190">ICorDebugBreakpointEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)|<span data-ttu-id="1441a-191">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="1441a-192">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-192">ICorDebugStepperEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)|<span data-ttu-id="1441a-193">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="1441a-194">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-194">ICorDebugProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)|<span data-ttu-id="1441a-195">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="1441a-196">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-196">ICorDebugThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)|<span data-ttu-id="1441a-197">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="1441a-198">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-198">ICorDebugFrameEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)|<span data-ttu-id="1441a-199">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="1441a-200">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-200">ICorDebugChainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)|<span data-ttu-id="1441a-201">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="1441a-202">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-202">ICorDebugModuleEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)|<span data-ttu-id="1441a-203">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="1441a-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-204">ICorDebugValueEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-interface.md)|<span data-ttu-id="1441a-205">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="1441a-206">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-206">ICorDebugCodeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)|<span data-ttu-id="1441a-207">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="1441a-208">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-208">ICorDebugTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)|<span data-ttu-id="1441a-209">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="1441a-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-210">ICorDebugErrorInfoEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)|<span data-ttu-id="1441a-211">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="1441a-212">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-212">ICorDebugAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)|<span data-ttu-id="1441a-213">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="1441a-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-214">ICorDebugAssemblyEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)|<span data-ttu-id="1441a-215">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="1441a-216">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="1441a-216">ICorDebugEditAndContinueErrorInfo</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="1441a-217">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="1441a-218">ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="1441a-218">ICorDebugEditAndContinueSnapshot</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="1441a-219">1.0</span><span class="sxs-lookup"><span data-stu-id="1441a-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="1441a-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="1441a-220">ICorDebugManagedCallback2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)|<span data-ttu-id="1441a-221">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="1441a-222">ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="1441a-222">ICorDebugAppDomain2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)|<span data-ttu-id="1441a-223">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="1441a-224">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="1441a-224">ICorDebugProcess2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)|<span data-ttu-id="1441a-225">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="1441a-226">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="1441a-226">ICorDebugStepper2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)|<span data-ttu-id="1441a-227">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="1441a-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="1441a-228">ICorDebugRegisterSet2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)|<span data-ttu-id="1441a-229">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="1441a-230">ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="1441a-230">ICorDebugThread2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)|<span data-ttu-id="1441a-231">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="1441a-232">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="1441a-232">ICorDebugILFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)|<span data-ttu-id="1441a-233">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="1441a-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="1441a-234">ICorDebugModule2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)|<span data-ttu-id="1441a-235">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="1441a-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="1441a-236">ICorDebugFunction2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)|<span data-ttu-id="1441a-237">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="1441a-238">ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="1441a-238">ICorDebugCode2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)|<span data-ttu-id="1441a-239">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="1441a-240">"ICorDebugClass2"</span><span class="sxs-lookup"><span data-stu-id="1441a-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="1441a-241">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="1441a-242">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="1441a-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="1441a-243">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="1441a-244">O "ICorDebugEval2".</span><span class="sxs-lookup"><span data-stu-id="1441a-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="1441a-245">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="1441a-246">"ICorDebugObjectValue2"</span><span class="sxs-lookup"><span data-stu-id="1441a-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="1441a-247">2.0</span><span class="sxs-lookup"><span data-stu-id="1441a-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="1441a-248">ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="1441a-248">ICorDebugThread3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)|<span data-ttu-id="1441a-249">4</span><span class="sxs-lookup"><span data-stu-id="1441a-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="1441a-250">ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="1441a-250">ICorDebugThread4</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)|<span data-ttu-id="1441a-251">4</span><span class="sxs-lookup"><span data-stu-id="1441a-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="1441a-252">ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="1441a-252">ICorDebugStackWalk</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)|<span data-ttu-id="1441a-253">4</span><span class="sxs-lookup"><span data-stu-id="1441a-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="1441a-254">ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="1441a-254">ICorDebugNativeFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)|<span data-ttu-id="1441a-255">4</span><span class="sxs-lookup"><span data-stu-id="1441a-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="1441a-256">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="1441a-256">ICorDebugInternalFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)|<span data-ttu-id="1441a-257">4</span><span class="sxs-lookup"><span data-stu-id="1441a-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="1441a-258">ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="1441a-258">ICorDebugRuntimeUnwindableFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="1441a-259">4</span><span class="sxs-lookup"><span data-stu-id="1441a-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="1441a-260">Interface ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="1441a-260">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)|<span data-ttu-id="1441a-261">4</span><span class="sxs-lookup"><span data-stu-id="1441a-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="1441a-262">Interface ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="1441a-262">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)|<span data-ttu-id="1441a-263">4</span><span class="sxs-lookup"><span data-stu-id="1441a-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="1441a-264">ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="1441a-264">ICorDebugValue3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)|<span data-ttu-id="1441a-265">4</span><span class="sxs-lookup"><span data-stu-id="1441a-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="1441a-266">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="1441a-266">ICorDebugComObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)|<span data-ttu-id="1441a-267">4.5</span><span class="sxs-lookup"><span data-stu-id="1441a-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="1441a-268">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="1441a-268">ICorDebugAppDomain3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)|<span data-ttu-id="1441a-269">4.5</span><span class="sxs-lookup"><span data-stu-id="1441a-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="1441a-270">ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="1441a-270">ICorDebugCode3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)|<span data-ttu-id="1441a-271">4.5</span><span class="sxs-lookup"><span data-stu-id="1441a-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="1441a-272">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="1441a-272">ICorDebugILFrame3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)|<span data-ttu-id="1441a-273">4.5</span><span class="sxs-lookup"><span data-stu-id="1441a-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="1441a-274">A versão do .NET Framework, incluindo todos os service packs, é a mais recente.</span><span class="sxs-lookup"><span data-stu-id="1441a-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="1441a-275">Comentários</span><span class="sxs-lookup"><span data-stu-id="1441a-275">Remarks</span></span>  
 <span data-ttu-id="1441a-276">Um depurador pode usar o `CorDebugInterfaceVersion` enumeração no [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) função para especificar a versão mais recente do .NET Framework suportados pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="1441a-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="1441a-277">Nomes de Interface</span><span class="sxs-lookup"><span data-stu-id="1441a-277">Interface Names</span></span>  
 <span data-ttu-id="1441a-278">O número que é exibido no final dos nomes de interface na API do depurador (por exemplo, o "3" em `ICorDebugThread3`) especifica a versão da interface, não a versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1441a-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="1441a-279">Todos os nomes de interface na API do depurador incluem números da versão, exceto as interfaces que foram introduzidas na versão 1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1441a-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="1441a-280">Qualquer correspondência entre números da versão de interface e números da versão do .NET Framework são coincidentes.</span><span class="sxs-lookup"><span data-stu-id="1441a-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
-   <span data-ttu-id="1441a-281">Interfaces que foram introduzidas na versão 1.0 do .NET Framework não incluem números, pois são todas implicitamente da versão 1.</span><span class="sxs-lookup"><span data-stu-id="1441a-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
-   <span data-ttu-id="1441a-282">A versão 1.1 do .NET Framework usa interfaces da versão 1.0 e não introduz nenhuma nova interface de depuração.</span><span class="sxs-lookup"><span data-stu-id="1441a-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
-   <span data-ttu-id="1441a-283">As 14 interfaces de depuração introduzidas na versão 2.0 do .NET Framework são extensões lógicas de suas contrapartes da versão 1 e incluem o número "2" em seus nomes.</span><span class="sxs-lookup"><span data-stu-id="1441a-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
-   <span data-ttu-id="1441a-284">As versões 3.0 e 3.5 do .NET Framework usam as interfaces existentes do .NET Framework 2.0 e não introduzem nenhuma nova interface.</span><span class="sxs-lookup"><span data-stu-id="1441a-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
-   <span data-ttu-id="1441a-285">O [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] apresenta uma mistura de versões de interface.</span><span class="sxs-lookup"><span data-stu-id="1441a-285">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] introduces a mix of interface versions.</span></span> <span data-ttu-id="1441a-286">Por exemplo, `ICorDebugThread3` e `ICorDebugThread4` são exibidas como a terceira e quarta versões da interface `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="1441a-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="1441a-287">O [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] também apresenta a primeira versão do `ICorDebugStackWalk` interface e a segunda versão do `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span><span class="sxs-lookup"><span data-stu-id="1441a-287">The [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1441a-288">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1441a-288">Requirements</span></span>  
 <span data-ttu-id="1441a-289">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1441a-289">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1441a-290">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1441a-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1441a-291">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1441a-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1441a-292">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1441a-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1441a-293">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1441a-293">See Also</span></span>  
 [<span data-ttu-id="1441a-294">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="1441a-294">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
