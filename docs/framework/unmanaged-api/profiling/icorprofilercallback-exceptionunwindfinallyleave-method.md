---
title: Método ICorProfilerCallback::ExceptionUnwindFinallyLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: b6ef54297b69892f07df1aa92a92600fb20756e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445306"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="cc8f8-102">Método ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="cc8f8-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="cc8f8-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="cc8f8-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc8f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc8f8-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cc8f8-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc8f8-105">Remarks</span></span>  
 <span data-ttu-id="cc8f8-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span><span class="sxs-lookup"><span data-stu-id="cc8f8-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="cc8f8-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span><span class="sxs-lookup"><span data-stu-id="cc8f8-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="cc8f8-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span><span class="sxs-lookup"><span data-stu-id="cc8f8-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc8f8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc8f8-109">Requirements</span></span>  
 <span data-ttu-id="cc8f8-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc8f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc8f8-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc8f8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc8f8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc8f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc8f8-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc8f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc8f8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc8f8-114">See also</span></span>

- [<span data-ttu-id="cc8f8-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="cc8f8-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cc8f8-116">Método ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="cc8f8-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
