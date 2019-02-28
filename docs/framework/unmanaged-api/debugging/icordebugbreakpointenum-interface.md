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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b5268eb4240f7c3ff254f4d3d9a13ab494530a1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968732"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="c5677-102">Interface ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="c5677-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="c5677-103">Implementa métodos ICorDebugEnum e enumera matrizes de ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="c5677-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5677-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5677-104">Methods</span></span>  
  
|<span data-ttu-id="c5677-105">Método</span><span class="sxs-lookup"><span data-stu-id="c5677-105">Method</span></span>|<span data-ttu-id="c5677-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5677-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5677-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="c5677-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="c5677-108">Obtém o número especificado de `ICorDebugBreakpoint` instâncias de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="c5677-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5677-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5677-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5677-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="c5677-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5677-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5677-111">Requirements</span></span>  
 <span data-ttu-id="c5677-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5677-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5677-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5677-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5677-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5677-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5677-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5677-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5677-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5677-116">See also</span></span>
- [<span data-ttu-id="c5677-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c5677-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
