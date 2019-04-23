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
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125561"
---
# <a name="icorprofilercallback8-interface"></a>Interface ICorProfilerCallback8
[Com suporte no .NET Framework 4.7 e versões posteriores]  

 Uma subclasse de [ICorProfilerCallback7](icorprofilercallback7-interface.md) que fornece métodos de retorno de chamada usados pelo common language runtime para notificar o criador de perfil que a compilação JIT de um método dinâmico foi iniciado e concluído. 
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Notifica o criador de perfil que a compilação JIT de um método dinâmico foi iniciado.|  
|[Método DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Notifica o criador de perfil que concluiu a compilação JIT de um método dinâmico.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Interface ICorProfilerCallback9](icorprofilercallback9-interface.md)
