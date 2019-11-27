---
title: Enumeração COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: fc0251624738a06d1be7081ebd099e97f7278a15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283137"
---
# <a name="cor_prf_high_monitor-enumeration"></a>Enumeração COR_PRF_HIGH_MONITOR

[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
Fornece sinalizadores além daqueles encontrados na enumeração de [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) que o criador de perfil pode especificar para o método [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) quando ele está sendo carregado.  
  
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
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Nenhum sinalizador está definido.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Controla o retorno de chamada [ICorProfilerCallback6:: GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) para adicionar referências de assembly durante a movimentação de fechamento de referência do assembly CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Controla o retorno de chamada [ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) para atualizações para o fluxo de símbolos associado a um módulo na memória.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Controla o retorno de chamada [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) para indicar quando um método dinâmico foi coletado pelo lixo e descarregado. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|Somente .NET Core 3,0 e versões posteriores: desabilita a [compilação em camadas](../../../core/whats-new/dotnet-core-3-0.md) para os profileres.|
|`COR_PRF_HIGH_BASIC_GC`|Somente o .NET Core 3,0 e versões posteriores: fornece uma opção de criação de perfil de GC leve em comparação com [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md). Controla somente os retornos de chamada [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)e [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) . Ao contrário do sinalizador de `COR_PRF_MONITOR_GC`, `COR_PRF_HIGH_BASIC_GC` não desabilita a coleta de lixo simultânea.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|Somente o .NET Core 3,0 e versões posteriores: habilita os retornos de chamada [MovedReferences](icorprofilercallback-movedreferences-method.md) e [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) apenas para os GCS de compactação.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|Somente o .NET Core 3,0 e versões posteriores: semelhante a [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), mas fornece informações sobre alocações de objeto somente para o LOH (heap de objeto grande).|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que necessitam de imagens aprimoradas por perfil. Ele corresponde ao sinalizador `COR_PRF_REQUIRE_PROFILE_IMAGE` na enumeração [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos apenas durante a inicialização. Tentar alterar qualquer um desses sinalizadores em outro lugar resulta em um valor de `HRESULT` que indica falha.|  
  
## <a name="remarks"></a>Comentários

Os sinalizadores de `COR_PRF_HIGH_MONITOR` são usados com o parâmetro `pdwEventsHigh` dos métodos [ICorProfilerInfo5:: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) e [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .  
  
Começando com o .NET Framework 4.6.1, o valor da `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` alterado de 0 para `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Começando com o .NET Framework 4.7.2, seu valor mudou de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` para `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` se destina a ser um bitmask que representa todos os sinalizadores que só podem ser definidos durante a inicialização. A tentativa de alterar qualquer um desses sinalizadores em outro lugar resulta em um `HRESULT`com falha.

## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
**Cabeçalho:** CorProf. idl, CorProf. h  
  
**Biblioteca:** CorGuids.lib  
  
**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [Enumeração COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [Interface ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
