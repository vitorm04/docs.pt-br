---
title: Interface ICorProfilerCallback9
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="e1d46-102">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="e1d46-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="e1d46-103">[Com suporte nas versões posteriores e 4.7.2 do .NET Framework]</span><span class="sxs-lookup"><span data-stu-id="e1d46-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="e1d46-104">Uma subclasse de [ICorProfilerCallback8](icorprofilercallback8-interface.md) que fornece um método de retorno de chamada usado pelo common language runtime para notificar o criador de perfil que um método dinâmico foi limpos e subsequentemente descarregado.</span><span class="sxs-lookup"><span data-stu-id="e1d46-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1d46-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e1d46-105">Methods</span></span>  
  
|<span data-ttu-id="e1d46-106">Método</span><span class="sxs-lookup"><span data-stu-id="e1d46-106">Method</span></span>|<span data-ttu-id="e1d46-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1d46-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1d46-108">Método DynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="e1d46-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="e1d46-109">Notifica o criador de perfil que um método dinâmico foi limpos e subsequentemente descarregado.</span><span class="sxs-lookup"><span data-stu-id="e1d46-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1d46-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e1d46-110">Requirements</span></span>  
 <span data-ttu-id="e1d46-111">**Plataformas:** consulte [requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1d46-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1d46-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1d46-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="e1d46-113">**Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e1d46-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e1d46-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1d46-114">See Also</span></span>  
<span data-ttu-id="e1d46-115">[Interfaces de criação de perfil](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="e1d46-115">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
<span data-ttu-id="e1d46-116">[Interface ICorProfilerCallback8](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="e1d46-116">[ICorProfilerCallback8 Interface](icorprofilercallback9-interface.md) </span></span>  
<span data-ttu-id="e1d46-117">[Método ICorProfilerCallback8.DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span><span class="sxs-lookup"><span data-stu-id="e1d46-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted method](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span></span>  
[<span data-ttu-id="e1d46-118">Método ICorProfilerCallback8.DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="e1d46-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
