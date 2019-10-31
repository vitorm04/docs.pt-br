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
ms.openlocfilehash: f8c2fb544cf9fd6642bd0581211e0e4e49633221
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139766"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="eadba-102">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="eadba-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="eadba-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="eadba-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="eadba-104">Uma subclasse de [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) que fornece um método de retorno de chamada que o Common Language Runtime usa para notificar o criador de perfil de que o fluxo de símbolos associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="eadba-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eadba-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="eadba-105">Methods</span></span>  
  
|<span data-ttu-id="eadba-106">Método</span><span class="sxs-lookup"><span data-stu-id="eadba-106">Method</span></span>|<span data-ttu-id="eadba-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eadba-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eadba-108">Método ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="eadba-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="eadba-109">Notifica o criador de perfil de que o fluxo de símbolos associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="eadba-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eadba-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eadba-110">Requirements</span></span>  
 <span data-ttu-id="eadba-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eadba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eadba-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eadba-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eadba-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eadba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eadba-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eadba-114">See also</span></span>

- [<span data-ttu-id="eadba-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="eadba-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
