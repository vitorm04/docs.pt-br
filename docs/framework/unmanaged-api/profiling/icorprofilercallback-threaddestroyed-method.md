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
ms.openlocfilehash: c63b91c39ded58ed208f6920c2bfaeba410c093c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499851"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="7142d-102">Método ICorProfilerCallback::ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="7142d-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="7142d-103">Notifica o criador de perfil de que um thread foi destruído.</span><span class="sxs-lookup"><span data-stu-id="7142d-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7142d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7142d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7142d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7142d-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="7142d-106">no A ID do thread que foi destruído.</span><span class="sxs-lookup"><span data-stu-id="7142d-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7142d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7142d-107">Remarks</span></span>  
 <span data-ttu-id="7142d-108">O `threadId` valor não é mais válido no momento desta chamada.</span><span class="sxs-lookup"><span data-stu-id="7142d-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7142d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7142d-109">Requirements</span></span>  
 <span data-ttu-id="7142d-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7142d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7142d-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7142d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7142d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7142d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7142d-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7142d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7142d-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="7142d-114">See also</span></span>

- [<span data-ttu-id="7142d-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7142d-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="7142d-116">Método ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="7142d-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
