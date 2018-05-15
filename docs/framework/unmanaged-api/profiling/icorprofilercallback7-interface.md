---
title: Interface ICorProfilerCallback7
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f681001b610f42fef28181ffe3b47d702aabdf6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="e3d98-102">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="e3d98-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="e3d98-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="e3d98-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="e3d98-104">Uma subclasse de [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) que fornece um método de retorno de chamada que usa o common language runtime para notificar o criador de perfil que o fluxo de símbolo associado a um módulo de memória está atualizado.</span><span class="sxs-lookup"><span data-stu-id="e3d98-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3d98-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e3d98-105">Methods</span></span>  
  
|<span data-ttu-id="e3d98-106">Método</span><span class="sxs-lookup"><span data-stu-id="e3d98-106">Method</span></span>|<span data-ttu-id="e3d98-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3d98-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3d98-108">Método ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="e3d98-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="e3d98-109">Notifica o criador de perfil que o fluxo de símbolo associado a um módulo de memória está atualizado.</span><span class="sxs-lookup"><span data-stu-id="e3d98-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3d98-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3d98-110">Requirements</span></span>  
 <span data-ttu-id="e3d98-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3d98-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3d98-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3d98-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3d98-113">**Versões do .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3d98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d98-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3d98-114">See Also</span></span>  
 [<span data-ttu-id="e3d98-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e3d98-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
