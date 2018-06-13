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
ms.openlocfilehash: 7673d6fac2626bc0059204ea77a23686b11638cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452729"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="e3ecd-102">Método ICorProfilerCallback::RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="e3ecd-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="e3ecd-103">Notifica o criador de perfil que o thread especificado foi suspenso ou está prestes a ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="e3ecd-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ecd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3ecd-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3ecd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3ecd-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="e3ecd-106">[in] A ID do thread foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="e3ecd-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3ecd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3ecd-107">Remarks</span></span>  
 <span data-ttu-id="e3ecd-108">O `RuntimeThreadSuspended` notificação pode ocorrer a qualquer momento entre o [Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) e associado [: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="e3ecd-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="e3ecd-109">Notificações que ocorrem entre [Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) e `RuntimeResumeStarted` para threads que estavam sendo executados em código não gerenciado e foram suspensos durante a entrada no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e3ecd-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="e3ecd-110">Geralmente, esse retorno de chamada ocorre depois que um thread está suspenso.</span><span class="sxs-lookup"><span data-stu-id="e3ecd-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="e3ecd-111">No entanto, se o thread em execução no momento (o thread que chamou esse retorno de chamada) é a que está sendo suspenso, esse retorno de chamada ocorrerá antes que o thread está suspenso.</span><span class="sxs-lookup"><span data-stu-id="e3ecd-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3ecd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3ecd-112">Requirements</span></span>  
 <span data-ttu-id="e3ecd-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3ecd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3ecd-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3ecd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3ecd-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3ecd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3ecd-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ecd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ecd-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3ecd-117">See Also</span></span>  
 [<span data-ttu-id="e3ecd-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e3ecd-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e3ecd-119">Método RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="e3ecd-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
