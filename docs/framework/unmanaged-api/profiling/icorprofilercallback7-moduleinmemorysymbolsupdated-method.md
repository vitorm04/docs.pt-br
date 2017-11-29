---
title: "Método ICorProfilerCallback7::ModuleInMemorySymbolsUpdated"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfiler7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 088749195165039639f58f4eb6444fb640ab4cec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="8ef4a-102">Método ICorProfilerCallback7::ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="8ef4a-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="8ef4a-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="8ef4a-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="8ef4a-104">Notifica o criador de perfil sempre que o fluxo de símbolo associado a um módulo de memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="8ef4a-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef4a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ef4a-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ef4a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ef4a-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8ef4a-107">O identificador do módulo de memória cujo fluxo de símbolo é atualizado.</span><span class="sxs-lookup"><span data-stu-id="8ef4a-107">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ef4a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ef4a-108">Remarks</span></span>  
 <span data-ttu-id="8ef4a-109">Esse retorno de chamada é controlado pela configuração de [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) sinalizador de máscara de evento ao chamar o [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8ef4a-109">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ef4a-110">Esse evento não é gerado no momento para símbolos implicitamente criado ou modificado por meio de <xref:System.Reflection.Emit> APIs.</span><span class="sxs-lookup"><span data-stu-id="8ef4a-110">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="8ef4a-111">Mesmo quando símbolos são fornecidos com antecedência em uma chamada para uma das sobrecargas de gerenciado <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> métodos que inclui um `rawSymbolStore` argumento para especificar os símbolos para o assembly, o tempo de execução pode realmente associar dados simbólicos o módulo até depois que o [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) ocorreu o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="8ef4a-111">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="8ef4a-112">Esse evento fornece uma oportunidade posteriormente para coletar os símbolos para esses módulos.</span><span class="sxs-lookup"><span data-stu-id="8ef4a-112">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef4a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ef4a-113">Requirements</span></span>  
 <span data-ttu-id="8ef4a-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef4a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef4a-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ef4a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ef4a-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ef4a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ef4a-117">**Versões do .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef4a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef4a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ef4a-118">See Also</span></span>  
 [<span data-ttu-id="8ef4a-119">Método ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="8ef4a-119">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="8ef4a-120">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="8ef4a-120">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [<span data-ttu-id="8ef4a-121">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="8ef4a-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
