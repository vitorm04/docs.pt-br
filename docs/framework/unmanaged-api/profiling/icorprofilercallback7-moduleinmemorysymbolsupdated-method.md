---
title: Método ICorProfilerCallback7::ModuleInMemorySymbolsUpdated
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
ms.openlocfilehash: 9aa690378a32ffee2def672f02dc8b5582647a5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>Método ICorProfilerCallback7::ModuleInMemorySymbolsUpdated
[Com suporte no .NET Framework 4.6.1 e versões posteriores]  
  
 Notifica o criador de perfil sempre que o fluxo de símbolo associado a um módulo de memória é atualizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 [in] `moduleId`  
 O identificador do módulo de memória cujo fluxo de símbolo é atualizado.  
  
## <a name="remarks"></a>Comentários  
 Esse retorno de chamada é controlado pela configuração de [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) sinalizador de máscara de evento ao chamar o [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método.  
  
> [!NOTE]
>  Esse evento não é gerado no momento para símbolos implicitamente criado ou modificado por meio de <xref:System.Reflection.Emit> APIs.  
  
 Mesmo quando símbolos são fornecidos com antecedência em uma chamada para uma das sobrecargas de gerenciado <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> métodos que inclui um `rawSymbolStore` argumento para especificar os símbolos para o assembly, o tempo de execução pode realmente associar dados simbólicos o módulo até depois que o [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) ocorreu o retorno de chamada. Esse evento fornece uma oportunidade posteriormente para coletar os símbolos para esses módulos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [Método SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [Interface ICorProfilerCallback7](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
