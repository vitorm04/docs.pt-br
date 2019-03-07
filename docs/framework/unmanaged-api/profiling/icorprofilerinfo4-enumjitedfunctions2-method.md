---
title: Método ICorProfilerInfo4::EnumJITedFunctions2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23e70a94c65e37782b5107b688b67ed790fb8d74
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478941"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="e5ee4-102">Método ICorProfilerInfo4::EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="e5ee4-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="e5ee4-103">Retorna um enumerador para todas as funções que foram previamente compilado por JIT e recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="e5ee4-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="e5ee4-104">Esse método substitui o [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) método, que não enumera IDs recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="e5ee4-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ee4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5ee4-105">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5ee4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5ee4-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e5ee4-107">[out] Um ponteiro para o [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerador.</span><span class="sxs-lookup"><span data-stu-id="e5ee4-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5ee4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5ee4-108">Remarks</span></span>  
 <span data-ttu-id="e5ee4-109">Esse método pode se sobrepor `JITCompilation` retornos de chamada, como o [ICorProfilerCallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e5ee4-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="e5ee4-110">Enumeração retornada inclui valores para o `COR_PRF_FUNCTION::reJitId` campo.</span><span class="sxs-lookup"><span data-stu-id="e5ee4-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="e5ee4-111">O [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) método, que substitui esse método, não enumera IDs recompilado por JIT, pois o `COR_PRF_FUNCTION::reJitId` campo é sempre definido como 0.</span><span class="sxs-lookup"><span data-stu-id="e5ee4-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="e5ee4-112">O `ICorProfilerInfo4::EnumJITedFunctions` método enumerar IDs recompilado por JIT, porque o `COR_PRF_FUNCTION::reJitId` campo está definido corretamente.</span><span class="sxs-lookup"><span data-stu-id="e5ee4-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="e5ee4-113">Observe que o [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) métodos pode disparar uma coleta de lixo, enquanto [método ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) será não.</span><span class="sxs-lookup"><span data-stu-id="e5ee4-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="e5ee4-114">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="e5ee4-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ee4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5ee4-115">Requirements</span></span>  
 <span data-ttu-id="e5ee4-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ee4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ee4-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5ee4-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5ee4-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5ee4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5ee4-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ee4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ee4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5ee4-120">See also</span></span>
- [<span data-ttu-id="e5ee4-121">Método EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="e5ee4-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="e5ee4-122">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="e5ee4-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="e5ee4-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e5ee4-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="e5ee4-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e5ee4-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
