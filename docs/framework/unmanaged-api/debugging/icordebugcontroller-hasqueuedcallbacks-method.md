---
title: "Método ICorDebugController::HasQueuedCallbacks"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.HasQueuedCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03d52bb31a81876a00e1af33494b14fb99fee0fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="036ae-102">Método ICorDebugController::HasQueuedCallbacks</span><span class="sxs-lookup"><span data-stu-id="036ae-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="036ae-103">Obtém um valor que indica se qualquer retornos de chamada gerenciados atualmente na fila para o segmento especificado.</span><span class="sxs-lookup"><span data-stu-id="036ae-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="036ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="036ae-104">Syntax</span></span>  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="036ae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="036ae-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="036ae-106">[in] Um ponteiro para um objeto de "ICorDebugThread" que representa o thread.</span><span class="sxs-lookup"><span data-stu-id="036ae-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="036ae-107">[out] Um ponteiro para um valor que é `true` se qualquer retornos de chamada gerenciados estão atualmente na fila para o segmento especificado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="036ae-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="036ae-108">Se null for especificado para o `pThread` parâmetro `HasQueuedCallbacks` retornará `true` se há retornos de chamada gerenciados na fila de qualquer thread.</span><span class="sxs-lookup"><span data-stu-id="036ae-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="036ae-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="036ae-109">Remarks</span></span>  
 <span data-ttu-id="036ae-110">Retornos de chamada será expedida um por vez, cada vez que [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="036ae-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="036ae-111">O depurador pode verificar esse sinalizador se deseja relatar vários eventos de depuração que ocorrem simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="036ae-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="036ae-112">Quando eventos de depuração são enfileirados, eles já tenham ocorrido, para que o depurador deve esvaziar a fila inteira para ter certeza do estado do elemento a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="036ae-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="036ae-113">(Chamar `ICorDebugController::Continue` para que a fila.) Por exemplo, se a fila contém dois eventos de depuração no thread *X*, e o depurador suspende a thread *X* após o primeiro evento de depuração e, em seguida, chama `ICorDebugController::Continue`, o segundo evento de depuração para thread *X* será enviado, embora o thread foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="036ae-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="036ae-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="036ae-114">Requirements</span></span>  
 <span data-ttu-id="036ae-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="036ae-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="036ae-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="036ae-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="036ae-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="036ae-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="036ae-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="036ae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036ae-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="036ae-119">See Also</span></span>  
 
