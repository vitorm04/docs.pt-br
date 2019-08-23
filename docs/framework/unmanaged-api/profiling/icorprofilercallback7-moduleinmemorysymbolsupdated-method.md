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
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>Método ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated
[Com suporte no .NET Framework 4.6.1 e versões posteriores]  
  
 Notifica o criador de perfil sempre que o fluxo de símbolos associado a um módulo na memória é atualizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 [in] `moduleId`  
 O identificador do módulo na memória cujo fluxo de símbolos é atualizado.  
  
## <a name="remarks"></a>Comentários  
 Esse retorno de chamada é controlado pela definição do sinalizador de máscara de evento [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) ao chamar o método [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
> [!NOTE]
> Esse evento não é gerado atualmente para símbolos criados implicitamente ou modificados <xref:System.Reflection.Emit> via APIs.  
  
 Mesmo quando os símbolos são fornecidos antecipadamente em uma chamada para uma das sobrecargas dos métodos gerenciados <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> que incluem um `rawSymbolStore` argumento para especificar os símbolos para o assembly, o tempo de execução pode, na verdade, associar os dados simbólicos ao módulo até que o retorno de chamada [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) tenha ocorrido. Esse evento fornece uma oportunidade posterior para coletar símbolos para esses módulos.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [Método SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [Interface ICorProfilerCallback7](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
