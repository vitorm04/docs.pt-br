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
ms.openlocfilehash: 8fda98c20b42355b9f52595929bbf5b980b5b857
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077232"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="1a09d-102">Interface ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="1a09d-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="1a09d-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="1a09d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1a09d-104">Uma subclasse de [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) que fornece um método de retorno de chamada que o common language runtime usa para notificar um criador de perfil um assembly está carregando.</span><span class="sxs-lookup"><span data-stu-id="1a09d-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a09d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1a09d-105">Methods</span></span>  
  
|<span data-ttu-id="1a09d-106">Método</span><span class="sxs-lookup"><span data-stu-id="1a09d-106">Method</span></span>|<span data-ttu-id="1a09d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a09d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a09d-108">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="1a09d-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="1a09d-109">Notifica o criador de perfis de que um assembly está em um estágio inicial de carregamento, quando o Common Language Runtime realiza um exame de fechamento da referência do assembly.</span><span class="sxs-lookup"><span data-stu-id="1a09d-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a09d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a09d-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a09d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a09d-111">Requirements</span></span>  
 <span data-ttu-id="1a09d-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a09d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a09d-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1a09d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="1a09d-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1a09d-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a09d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a09d-115">See also</span></span>

- [<span data-ttu-id="1a09d-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="1a09d-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
