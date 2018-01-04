---
title: "Método ICorProfilerCallback::RuntimeResumeFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeResumeFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ea3e28a12e4891f9e67beb1ddd705461a95118b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="001af-102">Método ICorProfilerCallback::RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="001af-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="001af-103">Notifica o criador de perfil que o tempo de execução reiniciou a todos os threads de tempo de execução e retornou à operação normal.</span><span class="sxs-lookup"><span data-stu-id="001af-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="001af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="001af-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="001af-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="001af-105">Remarks</span></span>  
 <span data-ttu-id="001af-106">O `RuntimeResumeFinished` não é garantia de retorno de chamada ocorrer no mesmo thread, como o [Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="001af-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="001af-107">No entanto, é garantido que ele ocorrer no mesmo thread, como o [: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="001af-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="001af-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="001af-108">Requirements</span></span>  
 <span data-ttu-id="001af-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="001af-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="001af-110">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="001af-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="001af-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="001af-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="001af-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="001af-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001af-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="001af-113">See Also</span></span>  
 [<span data-ttu-id="001af-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="001af-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
