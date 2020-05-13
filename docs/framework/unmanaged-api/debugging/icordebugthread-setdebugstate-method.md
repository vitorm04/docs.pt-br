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
ms.openlocfilehash: 05ae2791ee7f8bd31be38ec4d2117ddc3c2ea2bc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377940"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="d39bb-102">Método ICorDebugThread::SetDebugState</span><span class="sxs-lookup"><span data-stu-id="d39bb-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="d39bb-103">Define sinalizadores que descrevem o estado de depuração deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d39bb-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d39bb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d39bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d39bb-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="d39bb-106">no Uma combinação de bits e valores de enumeração de CorDebugThreadState que especificam o estado de depuração desse thread.</span><span class="sxs-lookup"><span data-stu-id="d39bb-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d39bb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d39bb-107">Remarks</span></span>  
 <span data-ttu-id="d39bb-108">`SetDebugState`define o estado de depuração atual do thread.</span><span class="sxs-lookup"><span data-stu-id="d39bb-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="d39bb-109">(O "estado de depuração atual" representa o estado de depuração se o processo deveria ser continuado, não o estado atual real.) O valor normal para isso é THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="d39bb-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="d39bb-110">Somente o depurador pode afetar o estado de depuração de um thread.</span><span class="sxs-lookup"><span data-stu-id="d39bb-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="d39bb-111">Os Estados de depuração fazem a última vez em continuar, portanto, se você quiser manter um thread THREAD_SUSPENDed em várias vezes, poderá defini-lo uma vez e depois não precisará se preocupar com ele.</span><span class="sxs-lookup"><span data-stu-id="d39bb-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="d39bb-112">Suspender threads e retomar o processo pode causar deadlocks, embora normalmente seja improvável.</span><span class="sxs-lookup"><span data-stu-id="d39bb-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="d39bb-113">Essa é uma qualidade intrínseca de threads e processos e é por design.</span><span class="sxs-lookup"><span data-stu-id="d39bb-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="d39bb-114">Um depurador pode interromper e retomar de forma assíncrona os threads para interromper o deadlock.</span><span class="sxs-lookup"><span data-stu-id="d39bb-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="d39bb-115">Se o estado do usuário do thread incluir USER_UNSAFE_POINT, o thread poderá bloquear uma coleta de lixo (GC).</span><span class="sxs-lookup"><span data-stu-id="d39bb-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="d39bb-116">Isso significa que o thread suspenso tem uma chance muito maior de causar um deadlock.</span><span class="sxs-lookup"><span data-stu-id="d39bb-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="d39bb-117">Isso pode não afetar os eventos de depuração já enfileirados.</span><span class="sxs-lookup"><span data-stu-id="d39bb-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="d39bb-118">Portanto, um depurador deve drenar toda a fila de eventos (chamando [ICorDebugController:: HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) antes de suspender ou retomar os threads.</span><span class="sxs-lookup"><span data-stu-id="d39bb-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="d39bb-119">Caso contrário, ele pode receber eventos em um thread que ele acredita que já foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="d39bb-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d39bb-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d39bb-120">Requirements</span></span>  
 <span data-ttu-id="d39bb-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d39bb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d39bb-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d39bb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d39bb-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d39bb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d39bb-124">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d39bb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
