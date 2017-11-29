---
title: "Método ICorProfilerCallback::RuntimeThreadSuspended"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeThreadSuspended
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d2ab0244e898a60db8fe392ccbd8c0ebfd5523
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="599b6-102">Método ICorProfilerCallback::RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="599b6-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="599b6-103">Notifica o criador de perfil que o thread especificado foi suspenso ou está prestes a ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="599b6-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="599b6-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="599b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="599b6-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="599b6-106">[in] A ID do thread foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="599b6-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="599b6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="599b6-107">Remarks</span></span>  
 <span data-ttu-id="599b6-108">O `RuntimeThreadSuspended` notificação pode ocorrer a qualquer momento entre o [Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) e associado [: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="599b6-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="599b6-109">Notificações que ocorrem entre [Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) e `RuntimeResumeStarted` para threads que estavam sendo executados em código não gerenciado e foram suspensos durante a entrada no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="599b6-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="599b6-110">Geralmente, esse retorno de chamada ocorre depois que um thread está suspenso.</span><span class="sxs-lookup"><span data-stu-id="599b6-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="599b6-111">No entanto, se o thread em execução no momento (o thread que chamou esse retorno de chamada) é a que está sendo suspenso, esse retorno de chamada ocorrerá antes que o thread está suspenso.</span><span class="sxs-lookup"><span data-stu-id="599b6-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="599b6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="599b6-112">Requirements</span></span>  
 <span data-ttu-id="599b6-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="599b6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="599b6-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="599b6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="599b6-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="599b6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="599b6-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="599b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599b6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="599b6-117">See Also</span></span>  
 [<span data-ttu-id="599b6-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="599b6-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="599b6-119">Método RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="599b6-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
