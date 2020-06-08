---
title: Método ICorProfilerCallback::RuntimeThreadSuspended
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: 54f7dae511c8bf25dc96451e6477acf26655430a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503192"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="6fdd0-102">Método ICorProfilerCallback::RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="6fdd0-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="6fdd0-103">Notifica o criador de perfil de que o thread especificado foi suspenso ou está prestes a ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="6fdd0-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fdd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fdd0-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fdd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fdd0-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="6fdd0-106">no A ID do thread que foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="6fdd0-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fdd0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fdd0-107">Remarks</span></span>  
 <span data-ttu-id="6fdd0-108">A `RuntimeThreadSuspended` notificação pode ocorrer a qualquer momento entre o [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) e os retornos de chamada [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) associados.</span><span class="sxs-lookup"><span data-stu-id="6fdd0-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="6fdd0-109">As notificações que ocorrem entre [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) e `RuntimeResumeStarted` são para threads que estavam em execução em código não gerenciado e foram suspensas na entrada para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6fdd0-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="6fdd0-110">Geralmente, esse retorno de chamada ocorre apenas depois que um thread é suspenso.</span><span class="sxs-lookup"><span data-stu-id="6fdd0-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="6fdd0-111">No entanto, se o thread atualmente em execução (o thread que chamou esse retorno de chamada) for aquele que está sendo suspenso, esse retorno de chamada ocorrerá logo antes de o thread ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="6fdd0-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fdd0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fdd0-112">Requirements</span></span>  
 <span data-ttu-id="6fdd0-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fdd0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fdd0-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6fdd0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6fdd0-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fdd0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fdd0-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fdd0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fdd0-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="6fdd0-117">See also</span></span>

- [<span data-ttu-id="6fdd0-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6fdd0-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6fdd0-119">Método RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="6fdd0-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
