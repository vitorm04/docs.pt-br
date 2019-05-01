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
ms.openlocfilehash: 810875d1b91265fe886ce3cd11970cad7fee122d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041763"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="0a060-102">Método ICorProfilerCallback::RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="0a060-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="0a060-103">Notifica o criador de perfil que o thread especificado foi retomada após ter sido suspenso.</span><span class="sxs-lookup"><span data-stu-id="0a060-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a060-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a060-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a060-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0a060-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="0a060-106">[in] A ID do thread que foi retomada.</span><span class="sxs-lookup"><span data-stu-id="0a060-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a060-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a060-107">Requirements</span></span>  
 <span data-ttu-id="0a060-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a060-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a060-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a060-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a060-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a060-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a060-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a060-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a060-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a060-112">See also</span></span>

- [<span data-ttu-id="0a060-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0a060-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="0a060-114">Método RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="0a060-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
