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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b4464c72e8d189cea4831cb641b9ff05063ce25
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747222"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="72a71-102">Método ICorProfilerCallback::RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="72a71-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="72a71-103">Notifica o criador de perfil que o thread especificado foi retomada após ter sido suspenso.</span><span class="sxs-lookup"><span data-stu-id="72a71-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72a71-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72a71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72a71-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="72a71-106">[in] A ID do thread que foi retomada.</span><span class="sxs-lookup"><span data-stu-id="72a71-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a71-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72a71-107">Requirements</span></span>  
 <span data-ttu-id="72a71-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a71-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a71-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72a71-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72a71-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72a71-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72a71-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a71-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a71-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72a71-112">See also</span></span>

- [<span data-ttu-id="72a71-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="72a71-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="72a71-114">Método RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="72a71-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
