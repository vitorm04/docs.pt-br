---
title: ICorDebugFunctionBreakpoint Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cd4c430798333dd22c36ce30e7c9ce05bdc8f56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="d686c-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="d686c-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="d686c-103">Estende a interface ICorDebugBreakpoint para dar suporte a pontos de interrupção em funções.</span><span class="sxs-lookup"><span data-stu-id="d686c-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d686c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d686c-104">Methods</span></span>  
  
|<span data-ttu-id="d686c-105">Método</span><span class="sxs-lookup"><span data-stu-id="d686c-105">Method</span></span>|<span data-ttu-id="d686c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d686c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d686c-107">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="d686c-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="d686c-108">Obtém um ponteiro de interface para um ICorDebugFunction que faz referência à função na qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="d686c-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="d686c-109">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="d686c-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="d686c-110">Obtém o deslocamento do ponto de interrupção na função.</span><span class="sxs-lookup"><span data-stu-id="d686c-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d686c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d686c-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d686c-112">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="d686c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d686c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d686c-113">Requirements</span></span>  
 <span data-ttu-id="d686c-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d686c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d686c-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d686c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d686c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d686c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d686c-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d686c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d686c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d686c-118">See Also</span></span>  
 [<span data-ttu-id="d686c-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d686c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
