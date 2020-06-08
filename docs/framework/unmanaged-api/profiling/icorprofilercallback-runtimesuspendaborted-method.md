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
ms.openlocfilehash: a3fb5c398b8ccd7caba0b005bcf03e64ecef4ba5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503244"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="93b20-102">Método ICorProfilerCallback::RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="93b20-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="93b20-103">Notifica o criador de perfil de que o tempo de execução anulou a suspensão de tempo de execução que estava ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="93b20-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b20-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93b20-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="93b20-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="93b20-105">Remarks</span></span>  
 <span data-ttu-id="93b20-106">A suspensão de tempo de execução poderá ser anulada se dois threads tentarem suspender simultaneamente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="93b20-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="93b20-107">O retorno de chamada [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) ou o `RuntimeSuspendAborted` retorno de chamada ocorrerá em um único thread após um retorno de chamada [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="93b20-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="93b20-108">`RuntimeSuspendAborted`É garantido que o retorno de chamada ocorra no mesmo thread que o `RuntimeSuspendStarted` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="93b20-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93b20-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93b20-109">Requirements</span></span>  
 <span data-ttu-id="93b20-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93b20-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b20-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="93b20-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93b20-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93b20-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93b20-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93b20-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b20-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="93b20-114">See also</span></span>

- [<span data-ttu-id="93b20-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="93b20-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
