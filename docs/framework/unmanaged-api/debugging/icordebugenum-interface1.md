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
ms.openlocfilehash: eb3aca0713b8b11bdfaa23bf33c8e1a0b302e272
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606532"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="408a7-102">Interface ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="408a7-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="408a7-103">Serve como a interface base abstrata para os enumeradores que são usados por um aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="408a7-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="408a7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="408a7-104">Methods</span></span>  
  
|<span data-ttu-id="408a7-105">Método</span><span class="sxs-lookup"><span data-stu-id="408a7-105">Method</span></span>|<span data-ttu-id="408a7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="408a7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="408a7-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="408a7-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="408a7-108">Cria uma cópia deste objeto `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="408a7-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="408a7-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="408a7-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="408a7-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="408a7-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="408a7-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="408a7-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="408a7-112">Move o cursor para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="408a7-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="408a7-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="408a7-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="408a7-114">Move o cursor para frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="408a7-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="408a7-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="408a7-115">Remarks</span></span>  
 <span data-ttu-id="408a7-116">Os enumeradores seguintes derivam `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="408a7-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="408a7-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="408a7-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="408a7-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="408a7-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="408a7-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="408a7-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="408a7-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="408a7-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="408a7-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="408a7-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="408a7-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="408a7-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="408a7-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="408a7-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="408a7-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="408a7-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="408a7-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="408a7-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="408a7-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="408a7-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="408a7-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="408a7-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="408a7-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="408a7-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="408a7-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="408a7-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="408a7-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="408a7-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="408a7-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="408a7-138">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="408a7-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="408a7-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="408a7-139">Requirements</span></span>  
 <span data-ttu-id="408a7-140">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="408a7-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="408a7-141">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="408a7-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="408a7-142">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="408a7-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="408a7-143">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="408a7-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408a7-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="408a7-144">See also</span></span>

- [<span data-ttu-id="408a7-145">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="408a7-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
