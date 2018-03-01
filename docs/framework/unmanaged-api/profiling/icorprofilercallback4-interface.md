---
title: Interface ICorProfilerCallback4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: efcbc9adce9b5cfc39c5eb3e1649a35d458e99c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="da69c-102">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="da69c-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="da69c-103">Fornece métodos de retorno de chamada que o common language runtime (CLR) usa para comunicar informações para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="da69c-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da69c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="da69c-104">Methods</span></span>  
  
|<span data-ttu-id="da69c-105">Método</span><span class="sxs-lookup"><span data-stu-id="da69c-105">Method</span></span>|<span data-ttu-id="da69c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="da69c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da69c-107">Método GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="da69c-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="da69c-108">Permite que o criador de perfil de código definir sinalizadores de geração de código alternativo para um novo corpo de método recompilada.</span><span class="sxs-lookup"><span data-stu-id="da69c-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="da69c-109">Método MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="da69c-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="da69c-110">Relata o novo layout dos objetos no heap como resultado de uma coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="da69c-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="da69c-111">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="da69c-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="da69c-112">Notifica o criador de perfil que o compilador just-in-time (JIT) concluiu a recompilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="da69c-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="da69c-113">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="da69c-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="da69c-114">Notifica o criador de perfil que o compilador just-in-time (JIT) foi iniciado recompilar uma função.</span><span class="sxs-lookup"><span data-stu-id="da69c-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="da69c-115">Método ReJITError</span><span class="sxs-lookup"><span data-stu-id="da69c-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="da69c-116">Relata um erro ao processar uma solicitação de recompilação.</span><span class="sxs-lookup"><span data-stu-id="da69c-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="da69c-117">Método SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="da69c-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="da69c-118">Relata o layout dos objetos no heap como resultado de uma coleta de lixo não compactar.</span><span class="sxs-lookup"><span data-stu-id="da69c-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da69c-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="da69c-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da69c-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da69c-120">Requirements</span></span>  
 <span data-ttu-id="da69c-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da69c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da69c-122">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da69c-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da69c-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da69c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da69c-124">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da69c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da69c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da69c-125">See Also</span></span>  
 [<span data-ttu-id="da69c-126">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="da69c-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="da69c-127">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="da69c-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="da69c-128">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="da69c-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
