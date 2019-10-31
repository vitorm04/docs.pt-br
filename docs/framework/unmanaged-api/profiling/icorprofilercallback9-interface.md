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
ms.openlocfilehash: c383a2e221e61770d3c28a65c561c48f6059b6d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136571"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="4f0f6-102">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="4f0f6-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="4f0f6-103">[Com suporte no .NET Framework 4.7.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="4f0f6-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="4f0f6-104">Uma subclasse de [ICorProfilerCallback8](icorprofilercallback8-interface.md) que fornece um método de retorno de chamada usado pelo Common Language Runtime para notificar o criador de perfil de que um método dinâmico tem sido coletado como lixo e subsequentemente descarregado.</span><span class="sxs-lookup"><span data-stu-id="4f0f6-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f0f6-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4f0f6-105">Methods</span></span>  
  
|<span data-ttu-id="4f0f6-106">Método</span><span class="sxs-lookup"><span data-stu-id="4f0f6-106">Method</span></span>|<span data-ttu-id="4f0f6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f0f6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f0f6-108">Método DynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="4f0f6-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="4f0f6-109">Notifica o criador de perfil de que um método dinâmico foi coletado como lixo e subsequentemente descarregado.</span><span class="sxs-lookup"><span data-stu-id="4f0f6-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f0f6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f0f6-110">Requirements</span></span>  
 <span data-ttu-id="4f0f6-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f0f6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f0f6-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4f0f6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="4f0f6-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4f0f6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4f0f6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f0f6-114">See also</span></span>

- [<span data-ttu-id="4f0f6-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="4f0f6-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4f0f6-116">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="4f0f6-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="4f0f6-117">Método ICorProfilerCallback8. DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="4f0f6-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="4f0f6-118">Método ICorProfilerCallback8. DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="4f0f6-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
