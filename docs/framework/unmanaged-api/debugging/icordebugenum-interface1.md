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
ms.openlocfilehash: cc5598f9cbec4b97bb75f83fb18ccf8742904272
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783004"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="d460f-102">Interface ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="d460f-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="d460f-103">Serve como a interface base abstrata para os enumeradores que são usados por um aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="d460f-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d460f-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d460f-104">Methods</span></span>  
  
|<span data-ttu-id="d460f-105">Método</span><span class="sxs-lookup"><span data-stu-id="d460f-105">Method</span></span>|<span data-ttu-id="d460f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d460f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d460f-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="d460f-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="d460f-108">Cria uma cópia deste objeto `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="d460f-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="d460f-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="d460f-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="d460f-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="d460f-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="d460f-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="d460f-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="d460f-112">Move o cursor para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="d460f-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="d460f-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="d460f-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="d460f-114">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="d460f-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d460f-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="d460f-115">Remarks</span></span>  
 <span data-ttu-id="d460f-116">Os seguintes enumeradores derivam de `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="d460f-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="d460f-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="d460f-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="d460f-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="d460f-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="d460f-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="d460f-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="d460f-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="d460f-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="d460f-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="d460f-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="d460f-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="d460f-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="d460f-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="d460f-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="d460f-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="d460f-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="d460f-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="d460f-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="d460f-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="d460f-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="d460f-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="d460f-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="d460f-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="d460f-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="d460f-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="d460f-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="d460f-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="d460f-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="d460f-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="d460f-138">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="d460f-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d460f-139">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d460f-139">Requirements</span></span>  
 <span data-ttu-id="d460f-140">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d460f-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d460f-141">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d460f-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d460f-142">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d460f-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d460f-143">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d460f-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d460f-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="d460f-144">See also</span></span>

- [<span data-ttu-id="d460f-145">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d460f-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
