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
ms.openlocfilehash: 8d1198a931b79cb469048bf5afd48f5172a45721
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517702"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="28c80-102">Método ICorProfilerCallback::RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="28c80-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="28c80-103">Notifica o criador de perfil que o thread especificado foi retomada após ter sido suspenso.</span><span class="sxs-lookup"><span data-stu-id="28c80-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28c80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28c80-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28c80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28c80-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="28c80-106">[in] A ID do thread que foi retomada.</span><span class="sxs-lookup"><span data-stu-id="28c80-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28c80-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28c80-107">Requirements</span></span>  
 <span data-ttu-id="28c80-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28c80-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28c80-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28c80-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28c80-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28c80-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28c80-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28c80-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c80-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28c80-112">See also</span></span>
- [<span data-ttu-id="28c80-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="28c80-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="28c80-114">Método RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="28c80-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
