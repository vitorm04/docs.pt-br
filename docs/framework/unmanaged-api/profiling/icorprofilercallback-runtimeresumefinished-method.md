---
title: Método ICorProfilerCallback::RuntimeResumeFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
ms.openlocfilehash: 5cafbca75992a5fe8a7d3d95628e0018f1a2e8fa
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865942"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="5df1e-102">Método ICorProfilerCallback::RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="5df1e-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="5df1e-103">Notifica o criador de perfil de que o tempo de execução retomou todos os threads de tempo de execução e retornou à operação normal.</span><span class="sxs-lookup"><span data-stu-id="5df1e-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5df1e-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5df1e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5df1e-105">Remarks</span></span>  
 <span data-ttu-id="5df1e-106">Não há garantia de que o retorno de chamada de `RuntimeResumeFinished` ocorra no mesmo thread que o retorno de chamada [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5df1e-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="5df1e-107">No entanto, é garantido que ocorra no mesmo thread que o retorno de chamada [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5df1e-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5df1e-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5df1e-108">Requirements</span></span>  
 <span data-ttu-id="5df1e-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5df1e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5df1e-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5df1e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5df1e-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5df1e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5df1e-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5df1e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df1e-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="5df1e-113">See also</span></span>

- [<span data-ttu-id="5df1e-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5df1e-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
