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
ms.openlocfilehash: 3903ebf1ad35bd7eb1ba49b4f1acda9024678423
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862198"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="b60a2-102">Método ICorProfilerInfo4::EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="b60a2-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="b60a2-103">Retorna um enumerador para todas as funções que foram previamente compiladas e recompiladas por JIT.</span><span class="sxs-lookup"><span data-stu-id="b60a2-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="b60a2-104">Esse método substitui o método [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) , que não enumera IDs de compilação JIT recompiladas.</span><span class="sxs-lookup"><span data-stu-id="b60a2-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b60a2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b60a2-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b60a2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b60a2-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="b60a2-107">fora Um ponteiro para o enumerador [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b60a2-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b60a2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b60a2-108">Remarks</span></span>  
 <span data-ttu-id="b60a2-109">Esse método pode se sobrepor com `JITCompilation` retornos de chamada como o método [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b60a2-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="b60a2-110">A enumeração retornada inclui valores para o campo `COR_PRF_FUNCTION::reJitId`.</span><span class="sxs-lookup"><span data-stu-id="b60a2-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="b60a2-111">O método [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) , que esse método substitui, não enumera IDs de compilação JIT recompiladas, porque o campo `COR_PRF_FUNCTION::reJitId` é sempre definido como 0.</span><span class="sxs-lookup"><span data-stu-id="b60a2-111">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="b60a2-112">O método `ICorProfilerInfo4::EnumJITedFunctions` enumera as IDs recompiladas do JIT, porque o campo `COR_PRF_FUNCTION::reJitId` está definido corretamente.</span><span class="sxs-lookup"><span data-stu-id="b60a2-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="b60a2-113">Observe que o método [ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) pode disparar uma coleta de lixo, enquanto o [método ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) não fará.</span><span class="sxs-lookup"><span data-stu-id="b60a2-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="b60a2-114">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="b60a2-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b60a2-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b60a2-115">Requirements</span></span>  
 <span data-ttu-id="b60a2-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b60a2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b60a2-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b60a2-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b60a2-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b60a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b60a2-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b60a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b60a2-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="b60a2-120">See also</span></span>

- [<span data-ttu-id="b60a2-121">Método EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="b60a2-121">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="b60a2-122">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="b60a2-122">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b60a2-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b60a2-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b60a2-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b60a2-124">Profiling</span></span>](index.md)
