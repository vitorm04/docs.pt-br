---
title: Método ICorProfilerCallback4::ReJITCompilationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: 074b0b11a822d2b8bcb9588484557e3e5eba69dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430200"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="e6df8-102">Método ICorProfilerCallback4::ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="e6df8-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="e6df8-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span><span class="sxs-lookup"><span data-stu-id="e6df8-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6df8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6df8-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6df8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6df8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e6df8-106">[in] The ID of the function that the JIT compiler has started to recompile.</span><span class="sxs-lookup"><span data-stu-id="e6df8-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="e6df8-107">[in] The recompilation ID of the new version of the function.</span><span class="sxs-lookup"><span data-stu-id="e6df8-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="e6df8-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span><span class="sxs-lookup"><span data-stu-id="e6df8-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="e6df8-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span><span class="sxs-lookup"><span data-stu-id="e6df8-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6df8-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6df8-110">Remarks</span></span>  
 <span data-ttu-id="e6df8-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span><span class="sxs-lookup"><span data-stu-id="e6df8-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="e6df8-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span><span class="sxs-lookup"><span data-stu-id="e6df8-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="e6df8-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span><span class="sxs-lookup"><span data-stu-id="e6df8-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="e6df8-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span><span class="sxs-lookup"><span data-stu-id="e6df8-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="e6df8-115">In this scenario, the first recompilation of method A is halted.</span><span class="sxs-lookup"><span data-stu-id="e6df8-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="e6df8-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span><span class="sxs-lookup"><span data-stu-id="e6df8-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="e6df8-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span><span class="sxs-lookup"><span data-stu-id="e6df8-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="e6df8-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span><span class="sxs-lookup"><span data-stu-id="e6df8-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="e6df8-119">However, in this case, the function ID is valid.</span><span class="sxs-lookup"><span data-stu-id="e6df8-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6df8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6df8-120">Requirements</span></span>  
 <span data-ttu-id="e6df8-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6df8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6df8-122">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e6df8-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6df8-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6df8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6df8-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6df8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6df8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6df8-125">See also</span></span>

- [<span data-ttu-id="e6df8-126">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e6df8-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e6df8-127">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="e6df8-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="e6df8-128">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="e6df8-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="e6df8-129">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="e6df8-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
