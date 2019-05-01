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
ms.openlocfilehash: 12414064bf0651eab443951bde2a50dcff7b2291
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992089"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>Método ICorProfilerCallback7::ModuleInMemorySymbolsUpdated
[Com suporte no .NET Framework 4.6.1 e versões posteriores]  
  
 Notifica o criador de perfil sempre que o fluxo de símbolo associado a um módulo na memória for atualizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 [in] `moduleId`  
 O identificador do módulo na memória cujos símbolos de fluxo é atualizado.  
  
## <a name="remarks"></a>Comentários  
 Esse retorno de chamada é controlado pela configuração de [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) sinalizador de máscara de evento ao chamar o [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método.  
  
> [!NOTE]
>  Esse evento não é gerado no momento para símbolos implicitamente criado ou modificado por meio do <xref:System.Reflection.Emit> APIs.  
  
 Até mesmo quando símbolos são fornecidos com antecedência em uma chamada para uma das sobrecargas de gerenciados <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> métodos que inclui um `rawSymbolStore` argumento para especificar os símbolos para o assembly, o tempo de execução pode não realmente associar simbólicos dados com o módulo até depois que o [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada tenha ocorrido. Este evento oferece uma oportunidade posterior para coletar os símbolos para esses módulos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [Método SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [Interface ICorProfilerCallback7](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
