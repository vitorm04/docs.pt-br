---
title: Enumeração COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175207"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="0b300-102">Enumeração COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="0b300-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="0b300-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="0b300-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="0b300-104">Fornece sinalizadores além daqueles encontrados na enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) que o profiler pode especificar para o método [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) quando ele está carregando.</span><span class="sxs-lookup"><span data-stu-id="0b300-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b300-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b300-105">Syntax</span></span>  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED |
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="0b300-106">Membros</span><span class="sxs-lookup"><span data-stu-id="0b300-106">Members</span></span>  
  
|<span data-ttu-id="0b300-107">Membro</span><span class="sxs-lookup"><span data-stu-id="0b300-107">Member</span></span>|<span data-ttu-id="0b300-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b300-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="0b300-109">Nenhum sinalizador está definido.</span><span class="sxs-lookup"><span data-stu-id="0b300-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="0b300-110">Controla o [iCorProfilerCallback6::GetAssemblyRetornoRetorno](icorprofilercallback6-getassemblyreferences-method.md) de referência para adicionar referências de montagem durante a caminhada de encerramento de referência do conjunto CLR.</span><span class="sxs-lookup"><span data-stu-id="0b300-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="0b300-111">Controla o [ICorProfilerCallback7::ModuleInMemorySymbolsRetorno atualizado](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) para atualizações ao fluxo de símbolos associado a um módulo de memória.</span><span class="sxs-lookup"><span data-stu-id="0b300-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="0b300-112">Controla o retorno de chamada [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) para indicar quando um método dinâmico foi coletado e descarregado.</span><span class="sxs-lookup"><span data-stu-id="0b300-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="0b300-113">.NET Core 3.0 e apenas versões posteriores: [desabilita compilação hierárquica](../../../core/whats-new/dotnet-core-3-0.md) para profilers.</span><span class="sxs-lookup"><span data-stu-id="0b300-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="0b300-114">.NET Core 3.0 e apenas versões posteriores: [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)fornece uma opção de criação de perfil GC leve em comparação com .</span><span class="sxs-lookup"><span data-stu-id="0b300-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="0b300-115">Controla apenas os retornos de [callbacks GarbageCollectionStarted,](icorprofilercallback2-garbagecollectionstarted-method.md) [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)e [GetGenerationBounds.](icorprofilerinfo2-getgenerationbounds-method.md)</span><span class="sxs-lookup"><span data-stu-id="0b300-115">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="0b300-116">Ao `COR_PRF_MONITOR_GC` contrário `COR_PRF_HIGH_BASIC_GC` da bandeira, não desabilita a coleta de lixo simultânea.</span><span class="sxs-lookup"><span data-stu-id="0b300-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="0b300-117">.NET Core 3.0 e apenas versões posteriores: Habilita as [referências movediças](icorprofilercallback-movedreferences-method.md) e as chamadas [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) para compactar apenas GCs.</span><span class="sxs-lookup"><span data-stu-id="0b300-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="0b300-118">.NET Core 3.0 e apenas [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)versões posteriores: Semelhante a , mas fornece informações sobre alocações de objetos apenas para o heap de objeto grande (LOH).</span><span class="sxs-lookup"><span data-stu-id="0b300-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="0b300-119">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que necessitam de imagens aprimoradas por perfil.</span><span class="sxs-lookup"><span data-stu-id="0b300-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="0b300-120">Corresponde à `COR_PRF_REQUIRE_PROFILE_IMAGE` bandeira na [enumeração COR_PRF_MONITOR.](cor-prf-monitor-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="0b300-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="0b300-121">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="0b300-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="0b300-122">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos apenas durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="0b300-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="0b300-123">Tentar alterar qualquer um desses sinalizadores em outro lugar resulta em um valor de `HRESULT` que indica falha.</span><span class="sxs-lookup"><span data-stu-id="0b300-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b300-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b300-124">Remarks</span></span>

<span data-ttu-id="0b300-125">Os `COR_PRF_HIGH_MONITOR` sinalizadores são `pdwEventsHigh` usados com o parâmetro dos métodos [ICorProfilerInfo5:GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) e [ICorProfilerInfo5::SetEventMask2.](icorprofilerinfo5-seteventmask2-method.md)</span><span class="sxs-lookup"><span data-stu-id="0b300-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="0b300-126">A partir do Quadro .NET 4.6.1, o valor do `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` alterado de 0 para `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="0b300-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="0b300-127">A partir do Quadro .NET 4.7.2, seu valor mudou de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` . `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`</span><span class="sxs-lookup"><span data-stu-id="0b300-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>

<span data-ttu-id="0b300-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE`destina-se a ser uma máscara de bitque representa todas as bandeiras que só podem ser definidas durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="0b300-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="0b300-129">Tentar mudar qualquer uma dessas bandeiras `HRESULT`em outro lugar resulta em uma falha .</span><span class="sxs-lookup"><span data-stu-id="0b300-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="0b300-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b300-130">Requirements</span></span>

<span data-ttu-id="0b300-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b300-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="0b300-132">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0b300-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="0b300-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b300-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="0b300-134">**.NET Framework Versions:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b300-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b300-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="0b300-135">See also</span></span>

- [<span data-ttu-id="0b300-136">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="0b300-136">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="0b300-137">Enumeração COR_PRF_MONITOR</span><span class="sxs-lookup"><span data-stu-id="0b300-137">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="0b300-138">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="0b300-138">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
