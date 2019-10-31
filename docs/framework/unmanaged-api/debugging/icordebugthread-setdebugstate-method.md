---
title: Método ICorDebugThread::SetDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
ms.openlocfilehash: 1b2f3feca15bb8add17c9fe70805347b7c6a48ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133410"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="d823f-102">Método ICorDebugThread::SetDebugState</span><span class="sxs-lookup"><span data-stu-id="d823f-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="d823f-103">Define sinalizadores que descrevem o estado de depuração deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d823f-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d823f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d823f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d823f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d823f-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="d823f-106">no Uma combinação de bits e valores de enumeração de CorDebugThreadState que especificam o estado de depuração desse thread.</span><span class="sxs-lookup"><span data-stu-id="d823f-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d823f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d823f-107">Remarks</span></span>  
 <span data-ttu-id="d823f-108">`SetDebugState` define o estado de depuração atual do thread.</span><span class="sxs-lookup"><span data-stu-id="d823f-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="d823f-109">(O "estado de depuração atual" representa o estado de depuração se o processo deveria ser continuado, não o estado atual real.) O valor normal para isso é THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="d823f-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="d823f-110">Somente o depurador pode afetar o estado de depuração de um thread.</span><span class="sxs-lookup"><span data-stu-id="d823f-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="d823f-111">Os Estados de depuração fazem por último em continuar, portanto, se você quiser manter um thread THREAD_SUSPENDed sobre vários continuar, poderá defini-lo uma vez e depois não precisará se preocupar com ele.</span><span class="sxs-lookup"><span data-stu-id="d823f-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="d823f-112">Suspender threads e retomar o processo pode causar deadlocks, embora normalmente seja improvável.</span><span class="sxs-lookup"><span data-stu-id="d823f-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="d823f-113">Essa é uma qualidade intrínseca de threads e processos e é por design.</span><span class="sxs-lookup"><span data-stu-id="d823f-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="d823f-114">Um depurador pode interromper e retomar de forma assíncrona os threads para interromper o deadlock.</span><span class="sxs-lookup"><span data-stu-id="d823f-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="d823f-115">Se o estado do usuário do thread incluir USER_UNSAFE_POINT, o thread poderá bloquear uma coleta de lixo (GC).</span><span class="sxs-lookup"><span data-stu-id="d823f-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="d823f-116">Isso significa que o thread suspenso tem uma chance muito maior de causar um deadlock.</span><span class="sxs-lookup"><span data-stu-id="d823f-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="d823f-117">Isso pode não afetar os eventos de depuração já enfileirados.</span><span class="sxs-lookup"><span data-stu-id="d823f-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="d823f-118">Portanto, um depurador deve drenar toda a fila de eventos (chamando [ICorDebugController:: HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) antes de suspender ou retomar os threads.</span><span class="sxs-lookup"><span data-stu-id="d823f-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="d823f-119">Caso contrário, ele pode receber eventos em um thread que ele acredita que já foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="d823f-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d823f-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d823f-120">Requirements</span></span>  
 <span data-ttu-id="d823f-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d823f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d823f-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d823f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d823f-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d823f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d823f-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d823f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
