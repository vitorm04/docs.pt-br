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
ms.openlocfilehash: 4f971c5175307c1e1df6890c136b306860e54d23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452703"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="5b776-102">Método ICorProfilerCallback::RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="5b776-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="5b776-103">Notifica o criador de perfil que o thread especificado foi retomado após ter sido suspenso.</span><span class="sxs-lookup"><span data-stu-id="5b776-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b776-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b776-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b776-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b776-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="5b776-106">[in] A ID do thread que foi retomado.</span><span class="sxs-lookup"><span data-stu-id="5b776-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b776-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b776-107">Requirements</span></span>  
 <span data-ttu-id="5b776-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b776-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b776-109">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b776-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b776-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b776-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b776-111">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b776-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b776-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b776-112">See Also</span></span>  
 [<span data-ttu-id="5b776-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5b776-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5b776-114">Método RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="5b776-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
