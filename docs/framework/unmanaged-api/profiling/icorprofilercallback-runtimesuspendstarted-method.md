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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29d57f4ff2584ca6444f09d4e66c4ba36e3fff67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517793"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>Método ICorProfilerCallback::RuntimeSuspendStarted
Notifica o criador de perfil que o tempo de execução está prestes a suspender todos os segmentos de tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `suspendReason`  
 [in] Um valor igual a [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeração que indica o motivo para a suspensão.  
  
## <a name="remarks"></a>Comentários  
 Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar a execução até que eles tentarem inserir novamente o tempo de execução. Nesse ponto que eles serão também suspensos até que o tempo de execução é retomada. Isso também se aplica a novos threads que insira o tempo de execução. Todos os threads no tempo de execução são que seja suspenso imediatamente se eles já estão no código passível de interrupção, ou eles são solicitados a suspender quando atingem código passível de interrupção.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
- [Método RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
