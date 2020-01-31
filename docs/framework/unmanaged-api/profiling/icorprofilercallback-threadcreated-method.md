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
ms.openlocfilehash: 6514606290bf006443d7011c1a428bebb4cca0f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865823"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="cf559-102">Método ICorProfilerCallback::ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="cf559-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="cf559-103">Notifica o criador de perfil de que um thread foi criado.</span><span class="sxs-lookup"><span data-stu-id="cf559-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf559-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf559-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="cf559-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf559-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="cf559-106">no A ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="cf559-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf559-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf559-107">Remarks</span></span>  
 <span data-ttu-id="cf559-108">O valor de `threadId` é imediatamente válido.</span><span class="sxs-lookup"><span data-stu-id="cf559-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf559-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cf559-109">Requirements</span></span>  
 <span data-ttu-id="cf559-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf559-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf559-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cf559-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf559-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf559-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf559-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf559-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf559-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="cf559-114">See also</span></span>

- [<span data-ttu-id="cf559-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="cf559-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cf559-116">Método ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="cf559-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
