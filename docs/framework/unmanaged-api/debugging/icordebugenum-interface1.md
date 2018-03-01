---
title: ICorDebugEnum Interface1
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
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 751cca87962473501ef29a4deb99d9d24be33396
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="8bc0e-102">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="8bc0e-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="8bc0e-103">Serve como a interface base abstrata para os enumeradores que são usados por um aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="8bc0e-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8bc0e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8bc0e-104">Methods</span></span>  
  
|<span data-ttu-id="8bc0e-105">Método</span><span class="sxs-lookup"><span data-stu-id="8bc0e-105">Method</span></span>|<span data-ttu-id="8bc0e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8bc0e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8bc0e-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="8bc0e-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="8bc0e-108">Cria uma cópia deste objeto `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="8bc0e-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="8bc0e-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="8bc0e-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="8bc0e-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="8bc0e-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="8bc0e-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="8bc0e-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="8bc0e-112">Move o cursor para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="8bc0e-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="8bc0e-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="8bc0e-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="8bc0e-114">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="8bc0e-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bc0e-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="8bc0e-115">Remarks</span></span>  
 <span data-ttu-id="8bc0e-116">Os seguintes enumeradores derivam `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="8bc0e-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="8bc0e-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="8bc0e-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="8bc0e-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="8bc0e-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="8bc0e-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="8bc0e-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="8bc0e-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="8bc0e-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="8bc0e-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="8bc0e-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="8bc0e-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="8bc0e-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="8bc0e-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="8bc0e-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="8bc0e-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="8bc0e-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="8bc0e-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="8bc0e-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="8bc0e-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="8bc0e-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="8bc0e-138">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="8bc0e-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc0e-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8bc0e-139">Requirements</span></span>  
 <span data-ttu-id="8bc0e-140">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bc0e-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bc0e-141">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bc0e-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bc0e-142">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bc0e-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bc0e-143">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bc0e-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc0e-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bc0e-144">See Also</span></span>  
 [<span data-ttu-id="8bc0e-145">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8bc0e-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
