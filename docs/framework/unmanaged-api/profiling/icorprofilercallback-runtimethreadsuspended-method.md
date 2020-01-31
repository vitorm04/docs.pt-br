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
ms.openlocfilehash: c8645bf828d0ad99bd25c1909cbee3314a11abf9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865864"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="9351b-102">Método ICorProfilerCallback::RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="9351b-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="9351b-103">Notifica o criador de perfil de que o thread especificado foi suspenso ou está prestes a ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="9351b-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9351b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9351b-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9351b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9351b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="9351b-106">no A ID do thread que foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="9351b-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9351b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9351b-107">Remarks</span></span>  
 <span data-ttu-id="9351b-108">A notificação de `RuntimeThreadSuspended` pode ocorrer a qualquer momento entre o [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) e os retornos de chamada [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) associados.</span><span class="sxs-lookup"><span data-stu-id="9351b-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="9351b-109">As notificações que ocorrem entre [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) e `RuntimeResumeStarted` são para threads que estavam sendo executados em código não gerenciado e foram suspensos na entrada para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9351b-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="9351b-110">Geralmente, esse retorno de chamada ocorre apenas depois que um thread é suspenso.</span><span class="sxs-lookup"><span data-stu-id="9351b-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="9351b-111">No entanto, se o thread atualmente em execução (o thread que chamou esse retorno de chamada) for aquele que está sendo suspenso, esse retorno de chamada ocorrerá logo antes de o thread ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="9351b-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9351b-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9351b-112">Requirements</span></span>  
 <span data-ttu-id="9351b-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9351b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9351b-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9351b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9351b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9351b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9351b-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9351b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9351b-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="9351b-117">See also</span></span>

- [<span data-ttu-id="9351b-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9351b-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9351b-119">Método RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="9351b-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
