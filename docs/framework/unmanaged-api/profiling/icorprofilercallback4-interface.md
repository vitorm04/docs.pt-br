---
title: Interface ICorProfilerCallback4
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: a3394820f673e35777e1749229d4f8319841ca58
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439383"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="5319e-102">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="5319e-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="5319e-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span><span class="sxs-lookup"><span data-stu-id="5319e-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5319e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5319e-104">Methods</span></span>  
  
|<span data-ttu-id="5319e-105">Método</span><span class="sxs-lookup"><span data-stu-id="5319e-105">Method</span></span>|<span data-ttu-id="5319e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5319e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5319e-107">Método GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="5319e-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="5319e-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span><span class="sxs-lookup"><span data-stu-id="5319e-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="5319e-109">Método MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="5319e-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="5319e-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5319e-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="5319e-111">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="5319e-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="5319e-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span><span class="sxs-lookup"><span data-stu-id="5319e-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="5319e-113">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="5319e-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="5319e-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span><span class="sxs-lookup"><span data-stu-id="5319e-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="5319e-115">Método ReJITError</span><span class="sxs-lookup"><span data-stu-id="5319e-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="5319e-116">Reports an error encountered while processing a recompile request.</span><span class="sxs-lookup"><span data-stu-id="5319e-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="5319e-117">Método SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="5319e-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="5319e-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5319e-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5319e-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="5319e-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5319e-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5319e-120">Requirements</span></span>  
 <span data-ttu-id="5319e-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5319e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5319e-122">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5319e-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5319e-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5319e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5319e-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5319e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5319e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5319e-125">See also</span></span>

- [<span data-ttu-id="5319e-126">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="5319e-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="5319e-127">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5319e-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5319e-128">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5319e-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
