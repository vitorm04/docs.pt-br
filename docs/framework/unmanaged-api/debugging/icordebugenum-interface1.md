---
title: Interface ICorDebugEnum
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b25c47e101ad0fb8e8cbdbb2718a41c9be6c0c22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931978"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="ec522-102">Interface ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="ec522-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="ec522-103">Serve como a interface base abstrata para os enumeradores que são usados por um aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="ec522-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec522-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ec522-104">Methods</span></span>  
  
|<span data-ttu-id="ec522-105">Método</span><span class="sxs-lookup"><span data-stu-id="ec522-105">Method</span></span>|<span data-ttu-id="ec522-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec522-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec522-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="ec522-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="ec522-108">Cria uma cópia deste objeto `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="ec522-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="ec522-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="ec522-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="ec522-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="ec522-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="ec522-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="ec522-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="ec522-112">Move o cursor para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="ec522-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="ec522-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="ec522-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="ec522-114">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="ec522-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec522-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec522-115">Remarks</span></span>  
 <span data-ttu-id="ec522-116">Os seguintes enumeradores derivam `ICorDebugEnum`de:</span><span class="sxs-lookup"><span data-stu-id="ec522-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="ec522-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="ec522-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="ec522-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="ec522-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="ec522-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="ec522-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="ec522-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="ec522-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="ec522-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="ec522-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="ec522-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="ec522-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="ec522-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="ec522-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="ec522-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="ec522-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="ec522-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="ec522-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="ec522-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="ec522-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="ec522-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="ec522-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="ec522-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="ec522-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="ec522-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="ec522-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="ec522-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="ec522-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="ec522-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="ec522-138">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="ec522-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec522-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec522-139">Requirements</span></span>  
 <span data-ttu-id="ec522-140">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec522-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec522-141">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec522-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec522-142">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec522-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec522-143">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec522-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec522-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec522-144">See also</span></span>

- [<span data-ttu-id="ec522-145">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ec522-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
