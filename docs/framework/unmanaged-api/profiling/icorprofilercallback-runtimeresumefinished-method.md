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
ms.openlocfilehash: f6b983db7da258fb94f941d01914ece0f7b1359f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453294"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="900ca-102">Método ICorProfilerCallback::RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="900ca-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="900ca-103">Notifica o criador de perfil que o tempo de execução reiniciou a todos os threads de tempo de execução e retornou à operação normal.</span><span class="sxs-lookup"><span data-stu-id="900ca-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="900ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="900ca-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="900ca-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="900ca-105">Remarks</span></span>  
 <span data-ttu-id="900ca-106">O `RuntimeResumeFinished` não é garantia de retorno de chamada ocorrer no mesmo thread, como o [Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="900ca-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="900ca-107">No entanto, é garantido que ele ocorrer no mesmo thread, como o [: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="900ca-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="900ca-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="900ca-108">Requirements</span></span>  
 <span data-ttu-id="900ca-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="900ca-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="900ca-110">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="900ca-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="900ca-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="900ca-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="900ca-112">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="900ca-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="900ca-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="900ca-113">See Also</span></span>  
 [<span data-ttu-id="900ca-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="900ca-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
