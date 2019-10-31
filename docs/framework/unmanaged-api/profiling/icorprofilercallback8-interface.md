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
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136445"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="3543d-102">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="3543d-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="3543d-103">[Com suporte no .NET Framework 4,7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="3543d-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="3543d-104">Uma subclasse de [ICorProfilerCallback7](icorprofilercallback7-interface.md) que fornece métodos de retorno de chamada usados pelo Common Language Runtime para notificar o criador de perfil de que a compilação JIT de um método dinâmico foi iniciada e concluída.</span><span class="sxs-lookup"><span data-stu-id="3543d-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="3543d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3543d-105">Methods</span></span>  
  
|<span data-ttu-id="3543d-106">Método</span><span class="sxs-lookup"><span data-stu-id="3543d-106">Method</span></span>|<span data-ttu-id="3543d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3543d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3543d-108">Método DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="3543d-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="3543d-109">Notifica o criador de perfil de que a compilação JIT de um método dinâmico foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="3543d-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="3543d-110">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="3543d-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="3543d-111">Notifica o criador de perfil de que a compilação JIT de um método dinâmico foi concluída.</span><span class="sxs-lookup"><span data-stu-id="3543d-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3543d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3543d-112">Requirements</span></span>  
 <span data-ttu-id="3543d-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3543d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3543d-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3543d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="3543d-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3543d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3543d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3543d-116">See also</span></span>

- [<span data-ttu-id="3543d-117">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3543d-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3543d-118">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="3543d-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
