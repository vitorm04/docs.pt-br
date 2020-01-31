---
title: Método ICorProfilerCallback::RuntimeSuspendStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865877"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>Método ICorProfilerCallback::RuntimeSuspendStarted
Notifica o criador de perfil que o tempo de execução está prestes a suspender todos os threads de tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `suspendReason`  
 no Um valor da enumeração [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) que indica o motivo da suspensão.  
  
## <a name="remarks"></a>Comentários  
 Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar em execução até tentarem inserir novamente o tempo de execução. Nesse ponto, eles também serão suspensos até que o tempo de execução seja retomado. Isso também se aplica a novos threads que entram no tempo de execução. Todos os threads no tempo de execução serão suspensos imediatamente se já estiverem no código passível de interrupção ou se forem solicitados a suspender quando acessarem o código passível de interrupção.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método RuntimeSuspendAborted](icorprofilercallback-runtimesuspendaborted-method.md)
- [Método RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)
