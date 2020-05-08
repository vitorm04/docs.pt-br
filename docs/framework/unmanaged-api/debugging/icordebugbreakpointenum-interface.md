---
title: Interface ICorDebugBreakpointEnum
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: e391a02571481d75ce88ae3f3b2b6421705d661c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894709"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="33940-102">Interface ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="33940-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="33940-103">Implementa métodos ICorDebugEnum e enumera matrizes ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="33940-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33940-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="33940-104">Methods</span></span>  
  
|<span data-ttu-id="33940-105">Método</span><span class="sxs-lookup"><span data-stu-id="33940-105">Method</span></span>|<span data-ttu-id="33940-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="33940-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33940-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="33940-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="33940-108">Obtém o número especificado de `ICorDebugBreakpoint` instâncias da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="33940-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33940-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="33940-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33940-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="33940-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33940-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33940-111">Requirements</span></span>  
 <span data-ttu-id="33940-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33940-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33940-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33940-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33940-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33940-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33940-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33940-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33940-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33940-116">See also</span></span>

- [<span data-ttu-id="33940-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="33940-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
