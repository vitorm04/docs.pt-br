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
ms.openlocfilehash: 8ee396c512dca2bea0a7a9737d5515defce4b2b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415122"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="59269-102">Método ICorDebugController::SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="59269-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="59269-103">Define o estado de depuração de todos os threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="59269-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59269-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59269-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59269-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59269-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="59269-106">[in] Um valor da enumeração "CorDebugThreadState" que especifica o estado do thread para depuração.</span><span class="sxs-lookup"><span data-stu-id="59269-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="59269-107">[in] Um ponteiro para um objeto de "ICorDebugThread" que representa um segmento a ser isentos da configuração de estado de depuração.</span><span class="sxs-lookup"><span data-stu-id="59269-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="59269-108">Se esse valor for nulo, nenhum thread é isento.</span><span class="sxs-lookup"><span data-stu-id="59269-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59269-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="59269-109">Remarks</span></span>  
 <span data-ttu-id="59269-110">O `SetAllThreadsDebugState` método pode afetar os threads que não são visíveis por meio de [método EnumerateThreads](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), portanto threads que foram suspensos com o `SetAllThreadsDebugState` método precisará ser reiniciada com o `SetAllThreadsDebugState` método.</span><span class="sxs-lookup"><span data-stu-id="59269-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59269-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59269-111">Requirements</span></span>  
 <span data-ttu-id="59269-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59269-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59269-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59269-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59269-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59269-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59269-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59269-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59269-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59269-116">See Also</span></span>  
 
