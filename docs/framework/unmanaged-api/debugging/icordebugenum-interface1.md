---
title: ICorDebugEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEnum
helpviewer_keywords: ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f6596918819294f0ab68735cec12f9eab8bf83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="48429-102">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="48429-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="48429-103">Serve como a interface base abstrata para os enumeradores que são usados por um aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="48429-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48429-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="48429-104">Methods</span></span>  
  
|<span data-ttu-id="48429-105">Método</span><span class="sxs-lookup"><span data-stu-id="48429-105">Method</span></span>|<span data-ttu-id="48429-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="48429-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48429-107">Método clone</span><span class="sxs-lookup"><span data-stu-id="48429-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="48429-108">Cria uma cópia deste `ICorDebugEnum` objeto.</span><span class="sxs-lookup"><span data-stu-id="48429-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="48429-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="48429-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="48429-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="48429-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="48429-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="48429-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="48429-112">Move o cursor para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="48429-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="48429-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="48429-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="48429-114">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="48429-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48429-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="48429-115">Remarks</span></span>  
 <span data-ttu-id="48429-116">Os seguintes enumeradores derivam `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="48429-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="48429-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="48429-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="48429-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="48429-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="48429-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="48429-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="48429-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="48429-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="48429-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="48429-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="48429-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="48429-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="48429-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="48429-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="48429-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="48429-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="48429-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="48429-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="48429-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="48429-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="48429-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="48429-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="48429-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="48429-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="48429-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="48429-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="48429-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="48429-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="48429-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="48429-138">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="48429-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48429-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48429-139">Requirements</span></span>  
 <span data-ttu-id="48429-140">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48429-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48429-141">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48429-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48429-142">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48429-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48429-143">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48429-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48429-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48429-144">See Also</span></span>  
 [<span data-ttu-id="48429-145">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="48429-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
