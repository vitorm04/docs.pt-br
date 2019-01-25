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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2cf80c7e02d706b0b00ea87aa62986107cdd6a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689738"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="7e6ed-102">Método ICorProfilerCallback::RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="7e6ed-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="7e6ed-103">Notifica o criador de perfil que o tempo de execução foi retomada todos os threads de tempo de execução e retornou para operação normal.</span><span class="sxs-lookup"><span data-stu-id="7e6ed-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e6ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e6ed-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7e6ed-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e6ed-105">Remarks</span></span>  
 <span data-ttu-id="7e6ed-106">O `RuntimeResumeFinished` retorno de chamada não é garantido que ocorrem no mesmo thread que o [ICorProfilerCallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7e6ed-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="7e6ed-107">No entanto, é garantido que ele ocorrer no mesmo thread que o [ICorProfilerCallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7e6ed-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e6ed-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e6ed-108">Requirements</span></span>  
 <span data-ttu-id="7e6ed-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e6ed-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e6ed-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e6ed-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e6ed-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e6ed-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e6ed-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e6ed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e6ed-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e6ed-113">See also</span></span>
- [<span data-ttu-id="7e6ed-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7e6ed-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
