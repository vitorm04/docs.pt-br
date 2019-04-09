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
ms.openlocfilehash: 81477010b22edee71098edfc1b8557db08b6038f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178627"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="67d1b-102">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="67d1b-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="67d1b-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="67d1b-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="67d1b-104">Uma subclasse de [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) que fornece um método de retorno de chamada que o common language runtime usa para notificar o criador de perfil que o fluxo de símbolo associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="67d1b-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67d1b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="67d1b-105">Methods</span></span>  
  
|<span data-ttu-id="67d1b-106">Método</span><span class="sxs-lookup"><span data-stu-id="67d1b-106">Method</span></span>|<span data-ttu-id="67d1b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="67d1b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67d1b-108">Método ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="67d1b-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="67d1b-109">Notifica o criador de perfil que o fluxo de símbolo associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="67d1b-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67d1b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67d1b-110">Requirements</span></span>  
 <span data-ttu-id="67d1b-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67d1b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67d1b-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67d1b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="67d1b-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="67d1b-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="67d1b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67d1b-114">See also</span></span>

- [<span data-ttu-id="67d1b-115">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="67d1b-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
