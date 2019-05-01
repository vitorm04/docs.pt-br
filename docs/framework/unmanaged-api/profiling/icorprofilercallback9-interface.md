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
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991985"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="65a1f-102">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="65a1f-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="65a1f-103">[Com suporte no .NET Framework 4.7.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="65a1f-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="65a1f-104">Uma subclasse de [ICorProfilerCallback8](icorprofilercallback8-interface.md) que fornece um método de retorno de chamada usado pelo common language runtime para notificar o criador de perfil que um método dinâmico tiver sido limpos e, subsequentemente, foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="65a1f-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65a1f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="65a1f-105">Methods</span></span>  
  
|<span data-ttu-id="65a1f-106">Método</span><span class="sxs-lookup"><span data-stu-id="65a1f-106">Method</span></span>|<span data-ttu-id="65a1f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="65a1f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65a1f-108">Método DynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="65a1f-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="65a1f-109">Notifica o criador de perfil que um método dinâmico tiver sido limpos e, subsequentemente, foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="65a1f-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65a1f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65a1f-110">Requirements</span></span>  
 <span data-ttu-id="65a1f-111">**Plataformas:** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65a1f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65a1f-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65a1f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="65a1f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="65a1f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="65a1f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65a1f-114">See also</span></span>

- [<span data-ttu-id="65a1f-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="65a1f-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="65a1f-116">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="65a1f-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="65a1f-117">Método ICorProfilerCallback8.DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="65a1f-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="65a1f-118">Método ICorProfilerCallback8.DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="65a1f-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
