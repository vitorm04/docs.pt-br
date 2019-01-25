---
title: Método ICorProfilerCallback2::FinalizeableObjectQueued
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b8a952bb2827d1946787f15151887fa25b8da52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733721"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="8709c-102">Método ICorProfilerCallback2::FinalizeableObjectQueued</span><span class="sxs-lookup"><span data-stu-id="8709c-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="8709c-103">Notifica o criador de perfil de código que um objeto com um finalizador foi enfileirado para o thread do finalizador para a execução de seu `Finalize` método.</span><span class="sxs-lookup"><span data-stu-id="8709c-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8709c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8709c-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8709c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8709c-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="8709c-106">[in] Um valor igual a [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeração que descreve os aspectos do finalizador.</span><span class="sxs-lookup"><span data-stu-id="8709c-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="8709c-107">[in] A ID do objeto que foi enfileirado.</span><span class="sxs-lookup"><span data-stu-id="8709c-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8709c-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8709c-108">Requirements</span></span>  
 <span data-ttu-id="8709c-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8709c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8709c-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8709c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8709c-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8709c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8709c-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8709c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8709c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8709c-113">See also</span></span>
- [<span data-ttu-id="8709c-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8709c-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8709c-115">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="8709c-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
