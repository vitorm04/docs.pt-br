---
title: Método ICorProfilerCallback::RuntimeThreadResumed
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: 57ad0bd3ed76376421d22a84c0863d36ec2707c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430275"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="61ab4-102">Método ICorProfilerCallback::RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="61ab4-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="61ab4-103">Notifica o criador de perfil de que o thread especificado foi retomado após ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="61ab4-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ab4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61ab4-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61ab4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61ab4-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="61ab4-106">no A ID do thread que foi retomado.</span><span class="sxs-lookup"><span data-stu-id="61ab4-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61ab4-107">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="61ab4-107">Requirements</span></span>  
 <span data-ttu-id="61ab4-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61ab4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ab4-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="61ab4-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61ab4-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61ab4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61ab4-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ab4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ab4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61ab4-112">See also</span></span>

- [<span data-ttu-id="61ab4-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="61ab4-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="61ab4-114">Método RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="61ab4-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
