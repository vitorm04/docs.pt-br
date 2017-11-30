---
title: "Método ICorProfilerCallback::ThreadCreated"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b62d5d1129bb71a95ac4e98624558272b08f0683
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="3fa9c-102">Método ICorProfilerCallback::ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="3fa9c-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="3fa9c-103">Notifica o criador de perfil que um thread foi criado.</span><span class="sxs-lookup"><span data-stu-id="3fa9c-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fa9c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fa9c-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fa9c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fa9c-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="3fa9c-106">[in] A ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="3fa9c-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fa9c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fa9c-107">Remarks</span></span>  
 <span data-ttu-id="3fa9c-108">O `threadId` valor é imediatamente válido.</span><span class="sxs-lookup"><span data-stu-id="3fa9c-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fa9c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fa9c-109">Requirements</span></span>  
 <span data-ttu-id="3fa9c-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fa9c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fa9c-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3fa9c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3fa9c-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fa9c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fa9c-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fa9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa9c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fa9c-114">See Also</span></span>  
 [<span data-ttu-id="3fa9c-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3fa9c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3fa9c-116">Método ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="3fa9c-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
