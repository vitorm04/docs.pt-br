---
title: Interface ICorDebugHeapValue3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3
helpviewer_keywords: ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5531689a3a4ba66fddfc98cadec7dc8d51c8629a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="a8add-102">Interface ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="a8add-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="a8add-103">Expõe as propriedades de bloqueio de monitoramento de objetos.</span><span class="sxs-lookup"><span data-stu-id="a8add-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="a8add-104">Essa interface estende as interfaces ICorDebugHeapValue e em ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="a8add-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8add-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a8add-105">Methods</span></span>  
  
|<span data-ttu-id="a8add-106">Método</span><span class="sxs-lookup"><span data-stu-id="a8add-106">Method</span></span>|<span data-ttu-id="a8add-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8add-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8add-108">Método GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="a8add-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="a8add-109">Retorna o thread gerenciado que possui o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="a8add-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="a8add-110">Método GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="a8add-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="a8add-111">Fornece uma lista ordenada de threads que estão em fila o evento que está associado com um bloqueio do monitor.</span><span class="sxs-lookup"><span data-stu-id="a8add-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8add-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8add-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8add-113">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="a8add-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8add-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8add-114">Requirements</span></span>  
 <span data-ttu-id="a8add-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8add-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8add-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8add-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8add-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8add-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8add-118">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8add-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8add-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8add-119">See Also</span></span>  
 [<span data-ttu-id="a8add-120">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a8add-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a8add-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="a8add-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
