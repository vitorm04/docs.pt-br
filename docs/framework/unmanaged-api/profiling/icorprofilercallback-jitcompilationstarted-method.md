---
title: Método ICorProfilerCallback::JITCompilationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 96ab77a36c0a0bddda0fca342433666dd19082d3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426187"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="1ef95-102">Método ICorProfilerCallback::JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="1ef95-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="1ef95-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span><span class="sxs-lookup"><span data-stu-id="1ef95-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef95-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ef95-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ef95-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ef95-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="1ef95-106">[in] The ID of the function for which the compilation is starting.</span><span class="sxs-lookup"><span data-stu-id="1ef95-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="1ef95-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span><span class="sxs-lookup"><span data-stu-id="1ef95-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="1ef95-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="1ef95-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="1ef95-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span><span class="sxs-lookup"><span data-stu-id="1ef95-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef95-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ef95-110">Remarks</span></span>  
 <span data-ttu-id="1ef95-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span><span class="sxs-lookup"><span data-stu-id="1ef95-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="1ef95-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span><span class="sxs-lookup"><span data-stu-id="1ef95-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="1ef95-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span><span class="sxs-lookup"><span data-stu-id="1ef95-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="1ef95-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span><span class="sxs-lookup"><span data-stu-id="1ef95-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="1ef95-115">In this scenario, the first JIT compilation of method A is halted.</span><span class="sxs-lookup"><span data-stu-id="1ef95-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="1ef95-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span><span class="sxs-lookup"><span data-stu-id="1ef95-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="1ef95-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span><span class="sxs-lookup"><span data-stu-id="1ef95-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="1ef95-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span><span class="sxs-lookup"><span data-stu-id="1ef95-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="1ef95-119">For example, thread A calls `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="1ef95-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="1ef95-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span><span class="sxs-lookup"><span data-stu-id="1ef95-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="1ef95-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span><span class="sxs-lookup"><span data-stu-id="1ef95-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="1ef95-122">However, in a case like this one, the function ID is valid.</span><span class="sxs-lookup"><span data-stu-id="1ef95-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef95-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ef95-123">Requirements</span></span>  
 <span data-ttu-id="1ef95-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ef95-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef95-125">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1ef95-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ef95-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ef95-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ef95-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef95-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef95-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ef95-128">See also</span></span>

- [<span data-ttu-id="1ef95-129">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1ef95-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1ef95-130">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="1ef95-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
