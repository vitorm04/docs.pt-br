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
ms.openlocfilehash: 1190f83e2671216cf1627eeb710ba576e4b2ec93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125352"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="91815-102">Método ICorDebugController::SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="91815-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="91815-103">Define o estado de depuração de todos os threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="91815-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91815-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91815-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91815-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91815-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="91815-106">no Um valor da enumeração "CorDebugThreadState" que especifica o estado do thread para depuração.</span><span class="sxs-lookup"><span data-stu-id="91815-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="91815-107">no Um ponteiro para um objeto "ICorDebugThread" que representa um thread a ser isento da configuração de estado de depuração.</span><span class="sxs-lookup"><span data-stu-id="91815-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="91815-108">Se esse valor for NULL, nenhum thread será isento.</span><span class="sxs-lookup"><span data-stu-id="91815-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91815-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="91815-109">Remarks</span></span>  
 <span data-ttu-id="91815-110">O método `SetAllThreadsDebugState` pode afetar os threads que não são visíveis por meio do [método EnumerateThreads](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), de modo que os threads que foram suspensos com o método `SetAllThreadsDebugState` precisarão ser retomados com o método `SetAllThreadsDebugState`.</span><span class="sxs-lookup"><span data-stu-id="91815-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91815-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91815-111">Requirements</span></span>  
 <span data-ttu-id="91815-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91815-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91815-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91815-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91815-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91815-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91815-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91815-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91815-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91815-116">See also</span></span>
