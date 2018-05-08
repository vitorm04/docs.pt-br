---
title: Interface ICorProfilerCallback8
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8-interface"></a>Interface ICorProfilerCallback8
[Com suporte nas versões posteriores e 4.7 do .NET Framework]  

 Uma subclasse de [ICorProfilerCallback7](icorprofilercallback7-interface.md) que fornece métodos de retorno de chamada usados pelo common language runtime para notificar o criador de perfil que a compilação JIT de um método dinâmico foi iniciado e concluído. 
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Notifica o criador de perfil que a compilação JIT de um método dinâmico foi iniciado.|  
|[Método DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Notifica o criador de perfil que concluiu a compilação JIT de um método dinâmico.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
**Versões do .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também  
[Interfaces de criação de perfil](profiling-interfaces.md)   
[Interface ICorProfilerCallback9](icorprofilercallback9-interface.md)
