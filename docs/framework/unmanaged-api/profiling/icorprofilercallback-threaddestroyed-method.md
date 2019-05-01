---
title: Método ICorProfilerCallback::ThreadDestroyed
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4c45290b1ef4360e51b5ed8e1b0fac3dcdde727
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041620"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="d6c1b-102">Método ICorProfilerCallback::ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="d6c1b-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="d6c1b-103">Notifica o criador de perfil que um thread foi destruído.</span><span class="sxs-lookup"><span data-stu-id="d6c1b-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c1b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6c1b-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6c1b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6c1b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d6c1b-106">[in] A ID do thread que foi destruída.</span><span class="sxs-lookup"><span data-stu-id="d6c1b-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c1b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6c1b-107">Remarks</span></span>  
 <span data-ttu-id="d6c1b-108">O `threadId` valor não é válido no momento desta chamada.</span><span class="sxs-lookup"><span data-stu-id="d6c1b-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c1b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6c1b-109">Requirements</span></span>  
 <span data-ttu-id="d6c1b-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6c1b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c1b-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6c1b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6c1b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6c1b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6c1b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c1b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c1b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6c1b-114">See also</span></span>

- [<span data-ttu-id="d6c1b-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d6c1b-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d6c1b-116">Método ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="d6c1b-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
