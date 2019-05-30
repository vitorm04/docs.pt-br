---
title: Enumeração COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e365dff7c56ddca1d05f2e16605078ef46e4e2af
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251151"
---
# <a name="corprfhighmonitor-enumeration"></a>Enumeração COR_PRF_HIGH_MONITOR
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Fornece sinalizadores além dos encontrados na [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração que o criador de perfil pode especificar para o [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método quando ele está sendo carregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Nenhum sinalizador está definido.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Controles de [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada para adicionar referências de assembly durante o exame de fechamento de referência de assembly CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Controles de [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) retorno de chamada para as atualizações para o fluxo de símbolo associado a um módulo na memória.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Controles de [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) retorno de chamada para indicar quando um método dinâmico tiver sido lixo coletado e descarregado. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que necessitam de imagens aprimoradas por perfil. Ele corresponde a `COR_PRF_REQUIRE_PROFILE_IMAGE` sinalizador na [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos apenas durante a inicialização. Tentar alterar qualquer um desses sinalizadores em outro lugar resulta em um valor de `HRESULT` que indica falha.|  
  
## <a name="remarks"></a>Comentários  
 O `COR_PRF_HIGH_MONITOR` sinalizadores são usados com o `pdwEventsHigh` parâmetro do [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) e [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) métodos.  
  
Começando com o .NET Framework 4.6.1, o valor de `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` alterada de 0 a `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Começando com o .NET Framework 4.7.2, seu valor alterado de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` para `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` destina-se a ser um bitmask que representa todos os sinalizadores que só podem ser definidos durante a inicialização. Tentativa de alterar qualquer um desses sinalizadores em outro lugar resulta em uma falha `HRESULT`.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [Enumeração COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [Interface ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
