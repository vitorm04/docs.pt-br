---
title: iCorProfilerCallback9::DynamicMethodDes Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177027"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a>iCorProfilerCallback9::DynamicMethodDes Method
[Suportado nas versões .NET Framework 4.7.2 e posteriores]  
  
Notifica o profiler sempre que um método dinâmico é coletado e posteriormente descarregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a>parâmetros  
[in] `functionId`  
O identificador da função in-memory que foi coletado e descarregado lixo.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [Interface ICorProfilerCallback9](icorprofilercallback9-interface.md)
- [COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS](cor-prf-high-monitor-enumeration.md)
