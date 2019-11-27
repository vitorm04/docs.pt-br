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
ms.openlocfilehash: 1d8aa231f65bad88806ee9b1d3c5df978c9740a2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446930"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="c761d-102">Método ICorProfilerCallback::ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="c761d-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="c761d-103">Notifica o criador de perfil de que um thread foi criado.</span><span class="sxs-lookup"><span data-stu-id="c761d-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c761d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c761d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c761d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c761d-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c761d-106">no A ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="c761d-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c761d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c761d-107">Remarks</span></span>  
 <span data-ttu-id="c761d-108">O valor de `threadId` é imediatamente válido.</span><span class="sxs-lookup"><span data-stu-id="c761d-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c761d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c761d-109">Requirements</span></span>  
 <span data-ttu-id="c761d-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c761d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c761d-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c761d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c761d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c761d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c761d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c761d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c761d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c761d-114">See also</span></span>

- [<span data-ttu-id="c761d-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c761d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c761d-116">Método ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="c761d-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
