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
ms.openlocfilehash: f8eb370e4f16212c536c252661163b7eca6f74d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="a10b9-102">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="a10b9-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="a10b9-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="a10b9-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a10b9-104">Uma subclasse de [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) que fornece um método de retorno de chamada que usa o common language runtime para notificar o criador de perfil que o fluxo de símbolo associado a um módulo de memória está atualizado.</span><span class="sxs-lookup"><span data-stu-id="a10b9-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a10b9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a10b9-105">Methods</span></span>  
  
|<span data-ttu-id="a10b9-106">Método</span><span class="sxs-lookup"><span data-stu-id="a10b9-106">Method</span></span>|<span data-ttu-id="a10b9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a10b9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a10b9-108">Método ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="a10b9-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="a10b9-109">Notifica o criador de perfil que o fluxo de símbolo associado a um módulo de memória está atualizado.</span><span class="sxs-lookup"><span data-stu-id="a10b9-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a10b9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a10b9-110">Requirements</span></span>  
 <span data-ttu-id="a10b9-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a10b9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a10b9-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a10b9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a10b9-113">**Versões do .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a10b9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10b9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a10b9-114">See Also</span></span>  
 [<span data-ttu-id="a10b9-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a10b9-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
