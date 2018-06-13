---
title: Interface ICorDebugHeapValue3
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a59d8bce6ae565687e7ed906f6c14332f0c5c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416826"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="108bf-102">Interface ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="108bf-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="108bf-103">Expõe as propriedades de bloqueio de monitoramento de objetos.</span><span class="sxs-lookup"><span data-stu-id="108bf-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="108bf-104">Essa interface estende as interfaces ICorDebugHeapValue e em ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="108bf-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="108bf-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="108bf-105">Methods</span></span>  
  
|<span data-ttu-id="108bf-106">Método</span><span class="sxs-lookup"><span data-stu-id="108bf-106">Method</span></span>|<span data-ttu-id="108bf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="108bf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="108bf-108">Método GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="108bf-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="108bf-109">Retorna o thread gerenciado que possui o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="108bf-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="108bf-110">Método GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="108bf-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="108bf-111">Fornece uma lista ordenada de threads que estão em fila o evento que está associado com um bloqueio do monitor.</span><span class="sxs-lookup"><span data-stu-id="108bf-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="108bf-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="108bf-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="108bf-113">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="108bf-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="108bf-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="108bf-114">Requirements</span></span>  
 <span data-ttu-id="108bf-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="108bf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="108bf-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="108bf-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="108bf-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="108bf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="108bf-118">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="108bf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108bf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="108bf-119">See Also</span></span>  
 [<span data-ttu-id="108bf-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="108bf-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="108bf-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="108bf-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
