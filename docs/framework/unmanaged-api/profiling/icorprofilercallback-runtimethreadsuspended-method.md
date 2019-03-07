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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54d297f6915af59ad5a24dfdad9dca9397489edb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468163"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>Método ICorProfilerCallback::RuntimeThreadSuspended
Notifica o criador de perfil que o thread especificado foi suspenso ou está prestes a ser suspenso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadId`  
 [in] A ID do thread que foi suspenso.  
  
## <a name="remarks"></a>Comentários  
 O `RuntimeThreadSuspended` notificação pode ocorrer a qualquer momento entre os [ICorProfilerCallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) e os respectivos [ICorProfilerCallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retornos de chamada. As notificações que ocorrem entre [ICorProfilerCallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) e `RuntimeResumeStarted` são de threads que estavam sendo executados em código não gerenciado e foram suspensos durante a entrada para o tempo de execução.  
  
 Em geral, esse retorno de chamada ocorre depois que um thread é suspenso. No entanto, se o thread em execução no momento (o thread que chamou esse retorno de chamada) é aquele que está sendo suspenso, esse retorno de chamada ocorrerá antes que o thread está suspenso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
