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
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049720"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="3d659-102">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="3d659-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="3d659-103">[Com suporte no .NET Framework 4.7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="3d659-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="3d659-104">Uma subclasse de [ICorProfilerCallback7](icorprofilercallback7-interface.md) que fornece métodos de retorno de chamada usados pelo common language runtime para notificar o criador de perfil que a compilação JIT de um método dinâmico foi iniciado e concluído.</span><span class="sxs-lookup"><span data-stu-id="3d659-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="3d659-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3d659-105">Methods</span></span>  
  
|<span data-ttu-id="3d659-106">Método</span><span class="sxs-lookup"><span data-stu-id="3d659-106">Method</span></span>|<span data-ttu-id="3d659-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d659-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d659-108">Método DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="3d659-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="3d659-109">Notifica o criador de perfil que a compilação JIT de um método dinâmico foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="3d659-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="3d659-110">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="3d659-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="3d659-111">Notifica o criador de perfil que concluiu a compilação JIT de um método dinâmico.</span><span class="sxs-lookup"><span data-stu-id="3d659-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d659-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d659-112">Requirements</span></span>  
 <span data-ttu-id="3d659-113">**Plataformas:** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d659-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d659-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d659-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="3d659-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3d659-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3d659-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d659-116">See also</span></span>

- [<span data-ttu-id="3d659-117">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3d659-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3d659-118">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="3d659-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
