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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217335"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="e0091-102">Método ICorProfilerCallback::ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="e0091-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="e0091-103">Notifica o criador de perfil que um thread foi destruído.</span><span class="sxs-lookup"><span data-stu-id="e0091-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0091-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0091-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0091-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0091-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="e0091-106">[in] A ID do thread que foi destruída.</span><span class="sxs-lookup"><span data-stu-id="e0091-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0091-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0091-107">Remarks</span></span>  
 <span data-ttu-id="e0091-108">O `threadId` valor não é válido no momento desta chamada.</span><span class="sxs-lookup"><span data-stu-id="e0091-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0091-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0091-109">Requirements</span></span>  
 <span data-ttu-id="e0091-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0091-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0091-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0091-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0091-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0091-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e0091-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e0091-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0091-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0091-114">See also</span></span>

- [<span data-ttu-id="e0091-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e0091-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e0091-116">Método ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="e0091-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
