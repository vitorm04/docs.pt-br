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
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991985"
---
# <a name="icorprofilercallback9-interface"></a>Interface ICorProfilerCallback9
[Com suporte no .NET Framework 4.7.2 e versões posteriores]  

 Uma subclasse de [ICorProfilerCallback8](icorprofilercallback8-interface.md) que fornece um método de retorno de chamada usado pelo common language runtime para notificar o criador de perfil que um método dinâmico tiver sido limpos e, subsequentemente, foi descarregado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DynamicMethodUnloaded](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Notifica o criador de perfil que um método dinâmico tiver sido limpos e, subsequentemente, foi descarregado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Interface ICorProfilerCallback8](icorprofilercallback9-interface.md)
- [Método ICorProfilerCallback8.DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [Método ICorProfilerCallback8.DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
