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
ms.openlocfilehash: 4929d9aaf7de9af72ec5ba93f5d7e35c712ac6cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451695"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="feea6-102">Método ICorProfilerCallback::ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="feea6-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="feea6-103">Notifica o criador de perfil que um thread foi destruído.</span><span class="sxs-lookup"><span data-stu-id="feea6-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feea6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="feea6-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="feea6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="feea6-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="feea6-106">[in] A ID do thread que foi destruído.</span><span class="sxs-lookup"><span data-stu-id="feea6-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="feea6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="feea6-107">Remarks</span></span>  
 <span data-ttu-id="feea6-108">O `threadId` valor não é válido no momento desta chamada.</span><span class="sxs-lookup"><span data-stu-id="feea6-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feea6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="feea6-109">Requirements</span></span>  
 <span data-ttu-id="feea6-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feea6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feea6-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="feea6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="feea6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="feea6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="feea6-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feea6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feea6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feea6-114">See Also</span></span>  
 [<span data-ttu-id="feea6-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="feea6-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="feea6-116">Método ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="feea6-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
