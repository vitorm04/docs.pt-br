---
title: "Método ICorProfilerCallback::RuntimeSuspendAborted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d62df6fc90a2601997aeb7ecbe410f1a35d7012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="89be6-102">Método ICorProfilerCallback::RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="89be6-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="89be6-103">Notifica o criador de perfil que o tempo de execução foi anulada a suspensão de tempo de execução estava ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="89be6-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89be6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89be6-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="89be6-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="89be6-105">Remarks</span></span>  
 <span data-ttu-id="89be6-106">A suspensão de tempo de execução pode ser anulada se dois threads simultaneamente tentarem suspender o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="89be6-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="89be6-107">Ambos o [Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) retorno de chamada ou `RuntimeSuspendAborted` retorno de chamada será feita na seguinte único thread um [Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="89be6-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="89be6-108">O `RuntimeSuspendAborted` tem garantia de retorno de chamada ocorrer no mesmo thread, como o `RuntimeSuspendStarted` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="89be6-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89be6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89be6-109">Requirements</span></span>  
 <span data-ttu-id="89be6-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89be6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89be6-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89be6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89be6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89be6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89be6-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89be6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89be6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89be6-114">See Also</span></span>  
 [<span data-ttu-id="89be6-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="89be6-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
