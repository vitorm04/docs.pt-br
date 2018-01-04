---
title: Interface ICorProfilerCallback7
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09de947b3f965f25942bd3e3081d91d3028532f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="cb7b0-102">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="cb7b0-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="cb7b0-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="cb7b0-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="cb7b0-104">Uma subclasse de [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) que fornece um método de retorno de chamada que usa o common language runtime para notificar o criador de perfil que o fluxo de símbolo associado a um módulo de memória está atualizado.</span><span class="sxs-lookup"><span data-stu-id="cb7b0-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb7b0-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="cb7b0-105">Methods</span></span>  
  
|<span data-ttu-id="cb7b0-106">Método</span><span class="sxs-lookup"><span data-stu-id="cb7b0-106">Method</span></span>|<span data-ttu-id="cb7b0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb7b0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb7b0-108">Método ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="cb7b0-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="cb7b0-109">Notifica o criador de perfil que o fluxo de símbolo associado a um módulo de memória está atualizado.</span><span class="sxs-lookup"><span data-stu-id="cb7b0-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb7b0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb7b0-110">Requirements</span></span>  
 <span data-ttu-id="cb7b0-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb7b0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb7b0-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb7b0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb7b0-113">**Versões do .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb7b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb7b0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb7b0-114">See Also</span></span>  
 [<span data-ttu-id="cb7b0-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="cb7b0-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
