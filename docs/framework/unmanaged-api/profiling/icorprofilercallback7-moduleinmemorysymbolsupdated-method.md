---
title: 'Método ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860ecde22dead112a42b6ac868e34f0e9cd3531d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916208"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="57abd-102">Método ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="57abd-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="57abd-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="57abd-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="57abd-104">Notifica o criador de perfil sempre que o fluxo de símbolos associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="57abd-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57abd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57abd-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57abd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57abd-106">Parameters</span></span>  
 <span data-ttu-id="57abd-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="57abd-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="57abd-108">O identificador do módulo na memória cujo fluxo de símbolos é atualizado.</span><span class="sxs-lookup"><span data-stu-id="57abd-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57abd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="57abd-109">Remarks</span></span>  
 <span data-ttu-id="57abd-110">Esse retorno de chamada é controlado pela definição do sinalizador de máscara de evento [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) ao chamar o método [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="57abd-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57abd-111">Esse evento não é gerado atualmente para símbolos criados implicitamente ou modificados <xref:System.Reflection.Emit> via APIs.</span><span class="sxs-lookup"><span data-stu-id="57abd-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="57abd-112">Mesmo quando os símbolos são fornecidos antecipadamente em uma chamada para uma das sobrecargas dos métodos gerenciados <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> que incluem um `rawSymbolStore` argumento para especificar os símbolos para o assembly, o tempo de execução pode, na verdade, associar os dados simbólicos ao módulo até que o retorno de chamada [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) tenha ocorrido.</span><span class="sxs-lookup"><span data-stu-id="57abd-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="57abd-113">Esse evento fornece uma oportunidade posterior para coletar símbolos para esses módulos.</span><span class="sxs-lookup"><span data-stu-id="57abd-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57abd-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57abd-114">Requirements</span></span>  
 <span data-ttu-id="57abd-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57abd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57abd-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57abd-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57abd-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57abd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57abd-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57abd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57abd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57abd-119">See also</span></span>

- [<span data-ttu-id="57abd-120">Método ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="57abd-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="57abd-121">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="57abd-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="57abd-122">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="57abd-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
