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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05e571149a794cbffa9e602255455d779a83e2a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="a4033-102">Interface ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="a4033-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="a4033-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="a4033-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a4033-104">Uma subclasse de [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) que fornece um método de retorno de chamada que usa o common language runtime para notificar um criador de perfil que está carregando um assembly.</span><span class="sxs-lookup"><span data-stu-id="a4033-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4033-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a4033-105">Methods</span></span>  
  
|<span data-ttu-id="a4033-106">Método</span><span class="sxs-lookup"><span data-stu-id="a4033-106">Method</span></span>|<span data-ttu-id="a4033-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4033-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4033-108">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="a4033-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="a4033-109">Notifica o criador de perfis de que um assembly está em um estágio inicial de carregamento, quando o Common Language Runtime realiza um exame de fechamento da referência do assembly.</span><span class="sxs-lookup"><span data-stu-id="a4033-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4033-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4033-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4033-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4033-111">Requirements</span></span>  
 <span data-ttu-id="a4033-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4033-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4033-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4033-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4033-114">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4033-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4033-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4033-115">See Also</span></span>  
 [<span data-ttu-id="a4033-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a4033-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
