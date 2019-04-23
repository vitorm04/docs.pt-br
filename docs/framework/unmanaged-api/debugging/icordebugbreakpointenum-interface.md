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
ms.openlocfilehash: 7fd42f13f699b0b79fd69311186f2b2ca0c9998a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149065"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="c3a48-102">Interface ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="c3a48-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="c3a48-103">Implementa métodos ICorDebugEnum e enumera matrizes de ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="c3a48-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3a48-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c3a48-104">Methods</span></span>  
  
|<span data-ttu-id="c3a48-105">Método</span><span class="sxs-lookup"><span data-stu-id="c3a48-105">Method</span></span>|<span data-ttu-id="c3a48-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3a48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3a48-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="c3a48-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="c3a48-108">Obtém o número especificado de `ICorDebugBreakpoint` instâncias de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="c3a48-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3a48-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3a48-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3a48-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="c3a48-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a48-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3a48-111">Requirements</span></span>  
 <span data-ttu-id="c3a48-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3a48-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a48-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3a48-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3a48-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3a48-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3a48-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a48-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a48-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3a48-116">See also</span></span>

- [<span data-ttu-id="c3a48-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c3a48-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
