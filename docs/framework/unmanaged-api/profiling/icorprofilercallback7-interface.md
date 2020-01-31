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
ms.openlocfilehash: e61f6a104b8b9613db32ed6912395fd07c18dcff
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864811"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="00e18-102">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="00e18-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="00e18-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="00e18-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="00e18-104">Uma subclasse de [ICorProfilerCallback6](icorprofilercallback6-interface.md) que fornece um método de retorno de chamada que o Common Language Runtime usa para notificar o criador de perfil de que o fluxo de símbolos associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="00e18-104">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00e18-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="00e18-105">Methods</span></span>  
  
|<span data-ttu-id="00e18-106">Método</span><span class="sxs-lookup"><span data-stu-id="00e18-106">Method</span></span>|<span data-ttu-id="00e18-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="00e18-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00e18-108">Método ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="00e18-108">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="00e18-109">Notifica o criador de perfil de que o fluxo de símbolos associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="00e18-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00e18-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="00e18-110">Requirements</span></span>  
 <span data-ttu-id="00e18-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00e18-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e18-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="00e18-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00e18-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00e18-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e18-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="00e18-114">See also</span></span>

- [<span data-ttu-id="00e18-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="00e18-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
