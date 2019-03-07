---
title: Método ICorDebugController::SetAllThreadsDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dffe95df75fafe293c225c513db7ff7896765fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501767"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="6bcfc-102">Método ICorDebugController::SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="6bcfc-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="6bcfc-103">Define o estado de depuração de todos os threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bcfc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6bcfc-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bcfc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6bcfc-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="6bcfc-106">[in] Um valor de enumeração "CorDebugThreadState" que especifica o estado do thread para depuração.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="6bcfc-107">[in] Um ponteiro para um objeto de "ICorDebugThread" que representa um thread para ser isentos da configuração de estado de depuração.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="6bcfc-108">Se esse valor for nulo, nenhum thread é isento.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bcfc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6bcfc-109">Remarks</span></span>  
 <span data-ttu-id="6bcfc-110">O `SetAllThreadsDebugState` método pode afetar os threads que não estão visíveis por meio [método EnumerateThreads](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), então threads que foram suspensos com o `SetAllThreadsDebugState` método precisará ser retomada, com o `SetAllThreadsDebugState` método.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bcfc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bcfc-111">Requirements</span></span>  
 <span data-ttu-id="6bcfc-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bcfc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bcfc-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bcfc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bcfc-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bcfc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bcfc-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bcfc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcfc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bcfc-116">See also</span></span>

