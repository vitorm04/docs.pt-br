---
title: Interface ICorProfilerCallback8
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455277"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="6f64f-102">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="6f64f-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="6f64f-103">[Com suporte nas versões posteriores e 4.7 do .NET Framework]</span><span class="sxs-lookup"><span data-stu-id="6f64f-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="6f64f-104">Uma subclasse de [ICorProfilerCallback7](icorprofilercallback7-interface.md) que fornece métodos de retorno de chamada usados pelo common language runtime para notificar o criador de perfil que a compilação JIT de um método dinâmico foi iniciado e concluído.</span><span class="sxs-lookup"><span data-stu-id="6f64f-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="6f64f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6f64f-105">Methods</span></span>  
  
|<span data-ttu-id="6f64f-106">Método</span><span class="sxs-lookup"><span data-stu-id="6f64f-106">Method</span></span>|<span data-ttu-id="6f64f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f64f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f64f-108">Método DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="6f64f-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="6f64f-109">Notifica o criador de perfil que a compilação JIT de um método dinâmico foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="6f64f-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="6f64f-110">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="6f64f-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="6f64f-111">Notifica o criador de perfil que concluiu a compilação JIT de um método dinâmico.</span><span class="sxs-lookup"><span data-stu-id="6f64f-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f64f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f64f-112">Requirements</span></span>  
 <span data-ttu-id="6f64f-113">**Plataformas:** consulte [requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f64f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f64f-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f64f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="6f64f-115">**Versões do .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6f64f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6f64f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f64f-116">See Also</span></span>  
<span data-ttu-id="6f64f-117">[Interfaces de criação de perfil](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="6f64f-117">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
[<span data-ttu-id="6f64f-118">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="6f64f-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
