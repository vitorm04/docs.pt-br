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
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175090"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="a9e08-102">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="a9e08-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="a9e08-103">[Suportado nas versões .NET Framework 4.7 e posteriores]</span><span class="sxs-lookup"><span data-stu-id="a9e08-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="a9e08-104">Uma subclasse do [ICorProfilerCallback7](icorprofilercallback7-interface.md) que fornece métodos de retorno de chamada usados pelo tempo de execução do idioma comum para notificar o profiler que a compilação JIT de um método dinâmico foi iniciada e concluída.</span><span class="sxs-lookup"><span data-stu-id="a9e08-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="a9e08-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a9e08-105">Methods</span></span>  
  
|<span data-ttu-id="a9e08-106">Método</span><span class="sxs-lookup"><span data-stu-id="a9e08-106">Method</span></span>|<span data-ttu-id="a9e08-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9e08-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9e08-108">Método DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="a9e08-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="a9e08-109">Notifica o profiler que a compilação JIT de um método dinâmico começou.</span><span class="sxs-lookup"><span data-stu-id="a9e08-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="a9e08-110">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="a9e08-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="a9e08-111">Notifica o profiler que a compilação JIT de um método dinâmico terminou.</span><span class="sxs-lookup"><span data-stu-id="a9e08-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9e08-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9e08-112">Requirements</span></span>  
 <span data-ttu-id="a9e08-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9e08-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9e08-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9e08-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="a9e08-115">**.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a9e08-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a9e08-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a9e08-116">See also</span></span>

- [<span data-ttu-id="a9e08-117">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="a9e08-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a9e08-118">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="a9e08-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
