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
ms.openlocfilehash: 07041d06668d474a3d30968fb623854a24ebf0eb
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865812"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="15ff8-102">Método ICorProfilerCallback::ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="15ff8-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="15ff8-103">Notifica o criador de perfil de que um thread foi destruído.</span><span class="sxs-lookup"><span data-stu-id="15ff8-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15ff8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15ff8-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15ff8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15ff8-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="15ff8-106">no A ID do thread que foi destruído.</span><span class="sxs-lookup"><span data-stu-id="15ff8-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15ff8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="15ff8-107">Remarks</span></span>  
 <span data-ttu-id="15ff8-108">O valor de `threadId` não é mais válido no momento desta chamada.</span><span class="sxs-lookup"><span data-stu-id="15ff8-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15ff8-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="15ff8-109">Requirements</span></span>  
 <span data-ttu-id="15ff8-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15ff8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15ff8-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="15ff8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15ff8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15ff8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15ff8-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15ff8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ff8-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="15ff8-114">See also</span></span>

- [<span data-ttu-id="15ff8-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="15ff8-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="15ff8-116">Método ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="15ff8-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
