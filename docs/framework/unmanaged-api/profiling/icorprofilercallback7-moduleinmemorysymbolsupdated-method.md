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
ms.openlocfilehash: f6dd10d196ffd3a653584e1bc8d1a5643850bc33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136605"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="203ee-102">Método ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="203ee-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="203ee-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="203ee-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="203ee-104">Notifica o criador de perfil sempre que o fluxo de símbolos associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="203ee-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203ee-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="203ee-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="203ee-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="203ee-106">Parameters</span></span>  
 <span data-ttu-id="203ee-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="203ee-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="203ee-108">O identificador do módulo na memória cujo fluxo de símbolos é atualizado.</span><span class="sxs-lookup"><span data-stu-id="203ee-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="203ee-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="203ee-109">Remarks</span></span>  
 <span data-ttu-id="203ee-110">Esse retorno de chamada é controlado pela definição do sinalizador de máscara de evento [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) ao chamar o método [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="203ee-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="203ee-111">Esse evento não é gerado atualmente para símbolos criados implicitamente ou modificados por meio de APIs de <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="203ee-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="203ee-112">Mesmo quando os símbolos são fornecidos antecipadamente em uma chamada para uma das sobrecargas dos métodos de <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> gerenciados que incluem um argumento `rawSymbolStore` para especificar os símbolos para o assembly, o tempo de execução pode não associar realmente os dados simbólicos ao módulo até depois do O retorno de chamada [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) ocorreu.</span><span class="sxs-lookup"><span data-stu-id="203ee-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="203ee-113">Esse evento fornece uma oportunidade posterior para coletar símbolos para esses módulos.</span><span class="sxs-lookup"><span data-stu-id="203ee-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="203ee-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="203ee-114">Requirements</span></span>  
 <span data-ttu-id="203ee-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="203ee-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="203ee-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="203ee-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="203ee-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="203ee-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="203ee-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="203ee-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203ee-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="203ee-119">See also</span></span>

- [<span data-ttu-id="203ee-120">Método ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="203ee-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="203ee-121">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="203ee-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="203ee-122">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="203ee-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
