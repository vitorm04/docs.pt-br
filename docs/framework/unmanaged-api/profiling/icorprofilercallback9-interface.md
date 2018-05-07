---
title: Interface ICorProfilerCallback9
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback9-interface"></a>Interface ICorProfilerCallback9
[Com suporte nas versões posteriores e 4.7.2 do .NET Framework]  

 Uma subclasse de [ICorProfilerCallback8](icorprofilercallback8-interface.md) que fornece um método de retorno de chamada usado pelo common language runtime para notificar o criador de perfil que um método dinâmico foi limpos e subsequentemente descarregado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DynamicMethodUnloaded](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Notifica o criador de perfil que um método dinâmico foi limpos e subsequentemente descarregado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
**Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Consulte também  
[Interfaces de criação de perfil](profiling-interfaces.md)   
[Interface ICorProfilerCallback8](icorprofilercallback9-interface.md)   
[Método ICorProfilerCallback8.DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)   
[Método ICorProfilerCallback8.DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
