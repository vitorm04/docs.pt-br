---
title: Método ICorProfilerCallback::RuntimeThreadSuspended
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: c8645bf828d0ad99bd25c1909cbee3314a11abf9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865864"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>Método ICorProfilerCallback::RuntimeThreadSuspended
Notifica o criador de perfil de que o thread especificado foi suspenso ou está prestes a ser suspenso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadId`  
 no A ID do thread que foi suspenso.  
  
## <a name="remarks"></a>Comentários  
 A notificação de `RuntimeThreadSuspended` pode ocorrer a qualquer momento entre o [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) e os retornos de chamada [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) associados. As notificações que ocorrem entre [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) e `RuntimeResumeStarted` são para threads que estavam sendo executados em código não gerenciado e foram suspensos na entrada para o tempo de execução.  
  
 Geralmente, esse retorno de chamada ocorre apenas depois que um thread é suspenso. No entanto, se o thread atualmente em execução (o thread que chamou esse retorno de chamada) for aquele que está sendo suspenso, esse retorno de chamada ocorrerá logo antes de o thread ser suspenso.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md)
