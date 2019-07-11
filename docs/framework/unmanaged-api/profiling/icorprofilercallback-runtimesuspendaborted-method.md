---
title: Método ICorProfilerCallback::RuntimeSuspendAborted
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62682ca19b9f987370ca11d2bda63fba27f28474
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783000"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="6dbb0-102">Método ICorProfilerCallback::RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="6dbb0-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="6dbb0-103">Notifica o criador de perfil que o tempo de execução foi anulada a suspensão de tempo de execução que estava ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="6dbb0-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dbb0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6dbb0-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6dbb0-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="6dbb0-105">Remarks</span></span>  
 <span data-ttu-id="6dbb0-106">A suspensão de tempo de execução pode ser anulada se dois threads simultaneamente tentam suspender o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6dbb0-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="6dbb0-107">Ambos os [ICorProfilerCallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) retorno de chamada ou o `RuntimeSuspendAborted` retorno de chamada será feita na seguinte único thread um [ICorProfilerCallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="6dbb0-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="6dbb0-108">O `RuntimeSuspendAborted` retorno de chamada é garantido que ocorrem no mesmo thread que o `RuntimeSuspendStarted` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="6dbb0-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dbb0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6dbb0-109">Requirements</span></span>  
 <span data-ttu-id="6dbb0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dbb0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dbb0-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6dbb0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6dbb0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dbb0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dbb0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dbb0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbb0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dbb0-114">See also</span></span>

- [<span data-ttu-id="6dbb0-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6dbb0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
