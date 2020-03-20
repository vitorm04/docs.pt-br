---
title: Método ICorProfilerCallback::ThreadCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 7fb58c0eb2446253bd658434fc9d68bb857fe0e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175116"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="bef9d-102">Método ICorProfilerCallback::ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="bef9d-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="bef9d-103">Notifica o profiler de que um segmento foi criado.</span><span class="sxs-lookup"><span data-stu-id="bef9d-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef9d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bef9d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="bef9d-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="bef9d-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="bef9d-106">[em] O ID do segmento que foi criado.</span><span class="sxs-lookup"><span data-stu-id="bef9d-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bef9d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bef9d-107">Remarks</span></span>  
 <span data-ttu-id="bef9d-108">O `threadId` valor é imediatamente válido.</span><span class="sxs-lookup"><span data-stu-id="bef9d-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bef9d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bef9d-109">Requirements</span></span>  
 <span data-ttu-id="bef9d-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bef9d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bef9d-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bef9d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bef9d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bef9d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bef9d-113">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bef9d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef9d-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="bef9d-114">See also</span></span>

- [<span data-ttu-id="bef9d-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bef9d-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="bef9d-116">Método ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="bef9d-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
