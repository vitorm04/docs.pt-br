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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d85dcb462df0255ab5420db94f9d055cce2c78b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616922"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="58a54-102">Método ICorProfilerCallback::ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="58a54-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="58a54-103">Notifica o criador de perfil que um thread foi criado.</span><span class="sxs-lookup"><span data-stu-id="58a54-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58a54-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58a54-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="58a54-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58a54-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="58a54-106">[in] A ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="58a54-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58a54-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="58a54-107">Remarks</span></span>  
 <span data-ttu-id="58a54-108">O `threadId` valor é válido imediatamente.</span><span class="sxs-lookup"><span data-stu-id="58a54-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58a54-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58a54-109">Requirements</span></span>  
 <span data-ttu-id="58a54-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58a54-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58a54-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58a54-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58a54-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58a54-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58a54-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58a54-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a54-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58a54-114">See also</span></span>
- [<span data-ttu-id="58a54-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="58a54-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="58a54-116">Método ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="58a54-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
