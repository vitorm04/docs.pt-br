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
ms.openlocfilehash: 35b87b3a2c0230b26fb68af44dc1aa864a6449e0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439934"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="05d32-102">Método ICorProfilerCallback::ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="05d32-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="05d32-103">Notifica o criador de perfil de que um thread foi destruído.</span><span class="sxs-lookup"><span data-stu-id="05d32-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d32-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05d32-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05d32-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05d32-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="05d32-106">no A ID do thread que foi destruído.</span><span class="sxs-lookup"><span data-stu-id="05d32-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05d32-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="05d32-107">Remarks</span></span>  
 <span data-ttu-id="05d32-108">O valor de `threadId` não é mais válido no momento desta chamada.</span><span class="sxs-lookup"><span data-stu-id="05d32-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05d32-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05d32-109">Requirements</span></span>  
 <span data-ttu-id="05d32-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05d32-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d32-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05d32-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05d32-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05d32-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05d32-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d32-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d32-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05d32-114">See also</span></span>

- [<span data-ttu-id="05d32-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="05d32-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="05d32-116">Método ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="05d32-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
