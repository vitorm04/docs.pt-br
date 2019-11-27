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
ms.openlocfilehash: 09d273a81ed4f956508e4fadb628b28e18d00f90
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449568"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="6b986-102">Método ICorProfilerInfo4::EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="6b986-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="6b986-103">Retorna um enumerador para todas as funções que foram previamente compiladas e recompiladas por JIT.</span><span class="sxs-lookup"><span data-stu-id="6b986-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="6b986-104">Esse método substitui o método [ICorProfilerInfo3:: EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) , que não enumera IDs de compilação JIT recompiladas.</span><span class="sxs-lookup"><span data-stu-id="6b986-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b986-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b986-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b986-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b986-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="6b986-107">fora Um ponteiro para o enumerador [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6b986-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b986-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b986-108">Remarks</span></span>  
 <span data-ttu-id="6b986-109">Esse método pode se sobrepor com `JITCompilation` retornos de chamada como o método [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6b986-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="6b986-110">A enumeração retornada inclui valores para o campo `COR_PRF_FUNCTION::reJitId`.</span><span class="sxs-lookup"><span data-stu-id="6b986-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="6b986-111">O método [ICorProfilerInfo3:: EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) , que esse método substitui, não enumera IDs de compilação JIT recompiladas, porque o campo `COR_PRF_FUNCTION::reJitId` é sempre definido como 0.</span><span class="sxs-lookup"><span data-stu-id="6b986-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="6b986-112">O método `ICorProfilerInfo4::EnumJITedFunctions` enumera as IDs recompiladas do JIT, porque o campo `COR_PRF_FUNCTION::reJitId` está definido corretamente.</span><span class="sxs-lookup"><span data-stu-id="6b986-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="6b986-113">Observe que o método [ICorProfilerInfo4:: EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) pode disparar uma coleta de lixo, enquanto o [método ICorProfilerInfo3:: EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) não fará.</span><span class="sxs-lookup"><span data-stu-id="6b986-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="6b986-114">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="6b986-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b986-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b986-115">Requirements</span></span>  
 <span data-ttu-id="6b986-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b986-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b986-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6b986-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b986-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b986-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b986-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b986-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b986-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b986-120">See also</span></span>

- [<span data-ttu-id="6b986-121">Método EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="6b986-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="6b986-122">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="6b986-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="6b986-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6b986-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6b986-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6b986-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
