---
title: Método ICorProfilerCallback::RuntimeSuspendFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
ms.openlocfilehash: 8bad09ddb2b821d0e02d43c1e3d1585b3473ec98
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446968"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a>Método ICorProfilerCallback::RuntimeSuspendFinished
Notifica o criador de perfil que o tempo de execução concluiu a suspensão de todos os threads de tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a>Comentários  
 Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar em execução até tentarem inserir novamente o tempo de execução. Nesse ponto, eles também serão suspensos até que o tempo de execução seja retomado. Isso também se aplica a novos threads que entram no tempo de execução. Todos os threads no tempo de execução serão suspensos imediatamente se já estiverem no código passível de interrupção ou se forem solicitados a suspender quando acessarem o código passível de interrupção.  
  
 É garantido que o retorno de chamada de `RuntimeSuspendFinished` ocorrerá no mesmo thread que o retorno de chamada [ICorProfilerCallback:: RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) .  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
