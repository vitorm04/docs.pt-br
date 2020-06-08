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
ms.openlocfilehash: 2c4a89d5f96ef572518f25bf58a0005454f8e3f0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496120"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="02dc5-102">Método ICorProfilerInfo4::EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="02dc5-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="02dc5-103">Retorna um enumerador para todas as funções que foram previamente compiladas e recompiladas por JIT.</span><span class="sxs-lookup"><span data-stu-id="02dc5-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="02dc5-104">Esse método substitui o método [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) , que não enumera IDs de compilação JIT recompiladas.</span><span class="sxs-lookup"><span data-stu-id="02dc5-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02dc5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02dc5-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02dc5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02dc5-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="02dc5-107">fora Um ponteiro para o enumerador [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="02dc5-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02dc5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="02dc5-108">Remarks</span></span>  
 <span data-ttu-id="02dc5-109">Esse método pode se sobrepor a `JITCompilation` retornos de chamada como o método [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="02dc5-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="02dc5-110">A enumeração retornada inclui valores para o `COR_PRF_FUNCTION::reJitId` campo.</span><span class="sxs-lookup"><span data-stu-id="02dc5-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="02dc5-111">O método [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) , que esse método substitui, não enumera IDs de compilação JIT recompiladas, porque o `COR_PRF_FUNCTION::reJitId` campo é sempre definido como 0.</span><span class="sxs-lookup"><span data-stu-id="02dc5-111">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="02dc5-112">O `ICorProfilerInfo4::EnumJITedFunctions` método enumera as IDs recompiladas do JIT, porque o `COR_PRF_FUNCTION::reJitId` campo está definido corretamente.</span><span class="sxs-lookup"><span data-stu-id="02dc5-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="02dc5-113">Observe que o método [ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) pode disparar uma coleta de lixo, enquanto o [método ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) não fará.</span><span class="sxs-lookup"><span data-stu-id="02dc5-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="02dc5-114">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="02dc5-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02dc5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02dc5-115">Requirements</span></span>  
 <span data-ttu-id="02dc5-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02dc5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02dc5-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="02dc5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02dc5-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02dc5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02dc5-119">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02dc5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02dc5-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="02dc5-120">See also</span></span>

- [<span data-ttu-id="02dc5-121">Método EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="02dc5-121">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="02dc5-122">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="02dc5-122">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="02dc5-123">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="02dc5-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="02dc5-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="02dc5-124">Profiling</span></span>](index.md)
