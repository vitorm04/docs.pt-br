---
title: Interface ICorProfilerCallback6
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 0009d935e2e3b2abf590aca270113717ceb7e2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127476"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="afdf2-102">Interface ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="afdf2-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="afdf2-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="afdf2-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="afdf2-104">Uma subclasse de [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) que fornece um método de retorno de chamada que o Common Language Runtime usa para notificar um criador de perfil que um assembly está carregando.</span><span class="sxs-lookup"><span data-stu-id="afdf2-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afdf2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="afdf2-105">Methods</span></span>  
  
|<span data-ttu-id="afdf2-106">Método</span><span class="sxs-lookup"><span data-stu-id="afdf2-106">Method</span></span>|<span data-ttu-id="afdf2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="afdf2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="afdf2-108">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="afdf2-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="afdf2-109">Notifica o criador de perfis de que um assembly está em um estágio inicial de carregamento, quando o Common Language Runtime realiza um exame de fechamento da referência do assembly.</span><span class="sxs-lookup"><span data-stu-id="afdf2-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afdf2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="afdf2-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afdf2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="afdf2-111">Requirements</span></span>  
 <span data-ttu-id="afdf2-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afdf2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afdf2-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="afdf2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="afdf2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afdf2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdf2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afdf2-115">See also</span></span>

- [<span data-ttu-id="afdf2-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="afdf2-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
