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
# <a name="cor_prf_high_monitor-enumeration"></a>Enumeração COR_PRF_HIGH_MONITOR

[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
Fornece sinalizadores além daqueles encontrados na enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) que o profiler pode especificar para o método [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) quando ele está carregando.  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Nenhum sinalizador está definido.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Controla o [iCorProfilerCallback6::GetAssemblyRetornoRetorno](icorprofilercallback6-getassemblyreferences-method.md) de referência para adicionar referências de montagem durante a caminhada de encerramento de referência do conjunto CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Controla o [ICorProfilerCallback7::ModuleInMemorySymbolsRetorno atualizado](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) para atualizações ao fluxo de símbolos associado a um módulo de memória.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Controla o retorno de chamada [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) para indicar quando um método dinâmico foi coletado e descarregado. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3.0 e apenas versões posteriores: [desabilita compilação hierárquica](../../../core/whats-new/dotnet-core-3-0.md) para profilers.|
|`COR_PRF_HIGH_BASIC_GC`|.NET Core 3.0 e apenas versões posteriores: [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)fornece uma opção de criação de perfil GC leve em comparação com . Controla apenas os retornos de [callbacks GarbageCollectionStarted,](icorprofilercallback2-garbagecollectionstarted-method.md) [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)e [GetGenerationBounds.](icorprofilerinfo2-getgenerationbounds-method.md) Ao `COR_PRF_MONITOR_GC` contrário `COR_PRF_HIGH_BASIC_GC` da bandeira, não desabilita a coleta de lixo simultânea.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET Core 3.0 e apenas versões posteriores: Habilita as [referências movediças](icorprofilercallback-movedreferences-method.md) e as chamadas [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) para compactar apenas GCs.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET Core 3.0 e apenas [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)versões posteriores: Semelhante a , mas fornece informações sobre alocações de objetos apenas para o heap de objeto grande (LOH).|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que necessitam de imagens aprimoradas por perfil. Corresponde à `COR_PRF_REQUIRE_PROFILE_IMAGE` bandeira na [enumeração COR_PRF_MONITOR.](cor-prf-monitor-enumeration.md)|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos apenas durante a inicialização. Tentar alterar qualquer um desses sinalizadores em outro lugar resulta em um valor de `HRESULT` que indica falha.|  
  
## <a name="remarks"></a>Comentários

Os `COR_PRF_HIGH_MONITOR` sinalizadores são `pdwEventsHigh` usados com o parâmetro dos métodos [ICorProfilerInfo5:GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) e [ICorProfilerInfo5::SetEventMask2.](icorprofilerinfo5-seteventmask2-method.md)  
  
A partir do Quadro .NET 4.6.1, o valor do `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` alterado de 0 para `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). A partir do Quadro .NET 4.7.2, seu valor mudou de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` . `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`

`COR_PRF_HIGH_MONITOR_IMMUTABLE`destina-se a ser uma máscara de bitque representa todas as bandeiras que só podem ser definidas durante a inicialização. Tentar mudar qualquer uma dessas bandeiras `HRESULT`em outro lugar resulta em uma falha .

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
**Cabeçalho:** CorProf.idl, CorProf.h  
  
**Biblioteca:** CorGuids.lib  
  
**.NET Framework Versions:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Criando perfil de enumerações](profiling-enumerations.md)
- [Enumeração COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)
- [Interface ICorProfilerInfo5](icorprofilerinfo5-interface.md)
