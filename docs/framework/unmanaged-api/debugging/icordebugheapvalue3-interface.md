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
ms.openlocfilehash: ddfe8cee8fdbca910ffa4f6989b1359ae5f7b11f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794376"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="6522b-102">Interface ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="6522b-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="6522b-103">Expõe as propriedades de bloqueio de monitoramento de objetos.</span><span class="sxs-lookup"><span data-stu-id="6522b-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="6522b-104">Essa interface estende as interfaces ICorDebugHeapValue e ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="6522b-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6522b-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6522b-105">Methods</span></span>  
  
|<span data-ttu-id="6522b-106">Método</span><span class="sxs-lookup"><span data-stu-id="6522b-106">Method</span></span>|<span data-ttu-id="6522b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6522b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6522b-108">Método GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="6522b-108">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="6522b-109">Retorna o thread gerenciado que possui o bloqueio de monitor neste objeto.</span><span class="sxs-lookup"><span data-stu-id="6522b-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="6522b-110">Método GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="6522b-110">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="6522b-111">Fornece uma lista ordenada de threads que são enfileirados no evento que está associado a um bloqueio de monitor.</span><span class="sxs-lookup"><span data-stu-id="6522b-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6522b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="6522b-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6522b-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="6522b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6522b-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="6522b-114">Requirements</span></span>  
 <span data-ttu-id="6522b-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6522b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6522b-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6522b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6522b-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6522b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6522b-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6522b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6522b-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="6522b-119">See also</span></span>

- [<span data-ttu-id="6522b-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6522b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6522b-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="6522b-121">Debugging</span></span>](index.md)
