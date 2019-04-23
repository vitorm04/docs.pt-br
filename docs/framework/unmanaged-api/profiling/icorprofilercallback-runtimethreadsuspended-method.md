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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0748802599926f4ec218362e6f7d086aab2d8f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080222"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="ed50f-102">Método ICorProfilerCallback::RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="ed50f-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="ed50f-103">Notifica o criador de perfil que o thread especificado foi suspenso ou está prestes a ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="ed50f-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed50f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed50f-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed50f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed50f-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ed50f-106">[in] A ID do thread que foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="ed50f-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed50f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed50f-107">Remarks</span></span>  
 <span data-ttu-id="ed50f-108">O `RuntimeThreadSuspended` notificação pode ocorrer a qualquer momento entre os [ICorProfilerCallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) e os respectivos [ICorProfilerCallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="ed50f-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="ed50f-109">As notificações que ocorrem entre [ICorProfilerCallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) e `RuntimeResumeStarted` são de threads que estavam sendo executados em código não gerenciado e foram suspensos durante a entrada para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ed50f-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="ed50f-110">Em geral, esse retorno de chamada ocorre depois que um thread é suspenso.</span><span class="sxs-lookup"><span data-stu-id="ed50f-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="ed50f-111">No entanto, se o thread em execução no momento (o thread que chamou esse retorno de chamada) é aquele que está sendo suspenso, esse retorno de chamada ocorrerá antes que o thread está suspenso.</span><span class="sxs-lookup"><span data-stu-id="ed50f-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed50f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed50f-112">Requirements</span></span>  
 <span data-ttu-id="ed50f-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed50f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed50f-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed50f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed50f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed50f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed50f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed50f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed50f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed50f-117">See also</span></span>

- [<span data-ttu-id="ed50f-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ed50f-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ed50f-119">Método RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="ed50f-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
