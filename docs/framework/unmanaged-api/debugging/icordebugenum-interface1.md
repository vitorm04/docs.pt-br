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
ms.openlocfilehash: 59dcb7ae6f27f8d049cd4dc2d313f7f1130fc503
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085261"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="075ca-102">Interface ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="075ca-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="075ca-103">Serve como a interface base abstrata para os enumeradores que são usados por um aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="075ca-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="075ca-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="075ca-104">Methods</span></span>  
  
|<span data-ttu-id="075ca-105">Método</span><span class="sxs-lookup"><span data-stu-id="075ca-105">Method</span></span>|<span data-ttu-id="075ca-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="075ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="075ca-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="075ca-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="075ca-108">Cria uma cópia deste objeto `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="075ca-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="075ca-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="075ca-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="075ca-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="075ca-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="075ca-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="075ca-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="075ca-112">Move o cursor para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="075ca-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="075ca-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="075ca-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="075ca-114">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="075ca-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="075ca-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="075ca-115">Remarks</span></span>  
 <span data-ttu-id="075ca-116">Os seguintes enumeradores derivam de `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="075ca-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="075ca-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="075ca-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="075ca-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="075ca-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="075ca-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="075ca-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="075ca-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="075ca-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="075ca-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="075ca-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="075ca-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="075ca-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="075ca-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="075ca-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="075ca-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="075ca-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="075ca-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="075ca-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="075ca-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="075ca-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="075ca-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="075ca-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="075ca-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="075ca-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="075ca-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="075ca-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="075ca-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="075ca-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="075ca-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="075ca-138">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="075ca-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="075ca-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="075ca-139">Requirements</span></span>  
 <span data-ttu-id="075ca-140">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="075ca-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="075ca-141">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="075ca-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="075ca-142">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="075ca-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="075ca-143">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="075ca-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="075ca-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="075ca-144">See also</span></span>

- [<span data-ttu-id="075ca-145">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="075ca-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
