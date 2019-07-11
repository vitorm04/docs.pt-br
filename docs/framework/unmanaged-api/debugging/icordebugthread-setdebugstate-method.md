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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66f60b2342b6ff64f1329cbe57032291d5139384
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770594"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="1b447-102">Método ICorDebugThread::SetDebugState</span><span class="sxs-lookup"><span data-stu-id="1b447-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="1b447-103">Define os sinalizadores que descrevem o estado de depuração deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="1b447-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b447-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b447-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b447-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b447-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="1b447-106">[in] Uma combinação bit a bit dos valores de enumeração CorDebugThreadState que especificam o estado de depuração desse thread.</span><span class="sxs-lookup"><span data-stu-id="1b447-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b447-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b447-107">Remarks</span></span>  
 <span data-ttu-id="1b447-108">`SetDebugState` Define o estado de depuração atual do thread.</span><span class="sxs-lookup"><span data-stu-id="1b447-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="1b447-109">(O "estado atual de depuração" representa o estado de depuração se o processo de ser continuada, não o estado atual propriamente dito.) O valor normal é THREAD_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="1b447-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="1b447-110">Somente o depurador pode afetar o estado de depuração de um thread.</span><span class="sxs-lookup"><span data-stu-id="1b447-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="1b447-111">Estados de depuração pela última vez em continuar, portanto, se você quiser manter um thread continua THREAD_SUSPENDed ao longo de vários, você pode defini-lo uma vez e depois disso não precisa se preocupar sobre ele.</span><span class="sxs-lookup"><span data-stu-id="1b447-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="1b447-112">Suspendendo threads e reiniciando o processo podem causar deadlocks, embora seja improvável normalmente.</span><span class="sxs-lookup"><span data-stu-id="1b447-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="1b447-113">Essa é uma qualidade intrínseco de threads e processos e é por design.</span><span class="sxs-lookup"><span data-stu-id="1b447-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="1b447-114">Um depurador assincronamente pode interromper e retomar os threads para quebrar o deadlock.</span><span class="sxs-lookup"><span data-stu-id="1b447-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="1b447-115">Se o estado do usuário do thread inclui USER_UNSAFE_POINT, o thread pode bloquear uma coleta de lixo (GC).</span><span class="sxs-lookup"><span data-stu-id="1b447-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="1b447-116">Isso significa que o thread suspenso tem uma chance maior de causar um deadlock.</span><span class="sxs-lookup"><span data-stu-id="1b447-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="1b447-117">Isso pode não afetar a depuração de eventos já na fila.</span><span class="sxs-lookup"><span data-stu-id="1b447-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="1b447-118">Assim, um depurador deve drenar a fila de evento completa (chamando [icordebugcontroller:: Hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) antes de suspender ou retomar os threads.</span><span class="sxs-lookup"><span data-stu-id="1b447-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="1b447-119">Caso contrário ele poderá receber eventos em um thread que ele acredita que ele suspendeu.</span><span class="sxs-lookup"><span data-stu-id="1b447-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b447-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b447-120">Requirements</span></span>  
 <span data-ttu-id="1b447-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b447-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b447-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b447-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b447-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b447-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b447-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b447-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
