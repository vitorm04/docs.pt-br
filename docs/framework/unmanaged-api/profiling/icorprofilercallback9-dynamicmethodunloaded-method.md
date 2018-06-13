---
title: Método ICorProfilerCallback9::DynamicMethodUnloaded
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16b3334647922f845645e6eb58db3146f4c9b936
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452397"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a>Método ICorProfilerCallback9::DynamicMethodUnloaded
[Com suporte nas versões posteriores e 4.7.2 do .NET Framework]  
  
Notifica o criador de perfil sempre que um método dinâmico é lixo coletado e subsequentemente descarregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
[in] `functionId`  
O identificador da função na memória que foram limpos e descarregado.   

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[Método ICorProfilerCallback8.DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
[Método ICorProfilerCallback8.DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
[Interface ICorProfilerCallback9](icorprofilercallback9-interface.md)   
[COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS](cor-prf-high-monitor-enumeration.md)
