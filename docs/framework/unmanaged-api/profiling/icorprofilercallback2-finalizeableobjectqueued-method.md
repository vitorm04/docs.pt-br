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
ms.openlocfilehash: b99a942d5c5fb205a84dd3766c99cc1126998de8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190382"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="4b68d-102">Método ICorProfilerCallback2::FinalizeableObjectQueued</span><span class="sxs-lookup"><span data-stu-id="4b68d-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="4b68d-103">Notifica o criador de perfil de código que um objeto com um finalizador foi enfileirado para o thread do finalizador para a execução de seu `Finalize` método.</span><span class="sxs-lookup"><span data-stu-id="4b68d-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b68d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b68d-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b68d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b68d-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="4b68d-106">[in] Um valor igual a [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeração que descreve os aspectos do finalizador.</span><span class="sxs-lookup"><span data-stu-id="4b68d-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="4b68d-107">[in] A ID do objeto que foi enfileirado.</span><span class="sxs-lookup"><span data-stu-id="4b68d-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b68d-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b68d-108">Requirements</span></span>  
 <span data-ttu-id="4b68d-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b68d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b68d-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b68d-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b68d-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b68d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b68d-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b68d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b68d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b68d-113">See also</span></span>

- [<span data-ttu-id="4b68d-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4b68d-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="4b68d-115">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="4b68d-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
