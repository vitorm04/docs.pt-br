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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a96aadcec6cb3c4f4680499585bf1c950bc5ddd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525304"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="d6795-102">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="d6795-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="d6795-103">Fornece métodos de retorno de chamada que o common language runtime (CLR) usa para comunicar informações ao criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="d6795-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6795-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d6795-104">Methods</span></span>  
  
|<span data-ttu-id="d6795-105">Método</span><span class="sxs-lookup"><span data-stu-id="d6795-105">Method</span></span>|<span data-ttu-id="d6795-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6795-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6795-107">Método GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="d6795-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="d6795-108">Permite que o criador de perfil de código definir sinalizadores de geração de código alternativo para um novo corpo de método recompilada.</span><span class="sxs-lookup"><span data-stu-id="d6795-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="d6795-109">Método MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="d6795-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="d6795-110">Relata o novo layout dos objetos no heap como resultado de uma coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="d6795-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="d6795-111">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="d6795-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="d6795-112">Notifica o criador de perfil que o compilador just-in-time (JIT) foi concluída a recompilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="d6795-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="d6795-113">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="d6795-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="d6795-114">Notifica o criador de perfil que o compilador just-in-time (JIT) foi iniciado recompilar uma função.</span><span class="sxs-lookup"><span data-stu-id="d6795-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="d6795-115">Método ReJITError</span><span class="sxs-lookup"><span data-stu-id="d6795-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="d6795-116">Relata um erro foi encontrado ao processar uma solicitação de recompilação.</span><span class="sxs-lookup"><span data-stu-id="d6795-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="d6795-117">Método SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="d6795-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="d6795-118">Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="d6795-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6795-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6795-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6795-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6795-120">Requirements</span></span>  
 <span data-ttu-id="d6795-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6795-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6795-122">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6795-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6795-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6795-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6795-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6795-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6795-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6795-125">See also</span></span>
- [<span data-ttu-id="d6795-126">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="d6795-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="d6795-127">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d6795-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d6795-128">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d6795-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
