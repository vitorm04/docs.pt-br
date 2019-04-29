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
ms.openlocfilehash: 60d3b22d8dc140bf16af7f59781d5ed103dafbf4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765473"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="acbd3-102">Interface ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="acbd3-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="acbd3-103">Expõe as propriedades de bloqueio de monitoramento de objetos.</span><span class="sxs-lookup"><span data-stu-id="acbd3-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="acbd3-104">Essa interface estende as interfaces ICorDebugHeapValue e ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="acbd3-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acbd3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="acbd3-105">Methods</span></span>  
  
|<span data-ttu-id="acbd3-106">Método</span><span class="sxs-lookup"><span data-stu-id="acbd3-106">Method</span></span>|<span data-ttu-id="acbd3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="acbd3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acbd3-108">Método GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="acbd3-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="acbd3-109">Retorna o thread gerenciado que detém o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="acbd3-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="acbd3-110">Método GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="acbd3-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="acbd3-111">Fornece uma lista ordenada de threads que estão na fila o evento que está associado com um bloqueio do monitor.</span><span class="sxs-lookup"><span data-stu-id="acbd3-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acbd3-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="acbd3-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acbd3-113">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="acbd3-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acbd3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="acbd3-114">Requirements</span></span>  
 <span data-ttu-id="acbd3-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acbd3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acbd3-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acbd3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acbd3-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acbd3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acbd3-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acbd3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acbd3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acbd3-119">See also</span></span>

- [<span data-ttu-id="acbd3-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="acbd3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="acbd3-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="acbd3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
