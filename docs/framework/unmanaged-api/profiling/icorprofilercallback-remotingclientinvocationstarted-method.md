---
title: Método ICorProfilerCallback::RemotingClientInvocationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b452cbfc5564d98b3770c2ed97f8453296f0fc13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157684"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a>Método ICorProfilerCallback::RemotingClientInvocationStarted
Notifica o criador de perfil que uma chamada de comunicação remota foi iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a>Comentários  
 Esse evento é o mesmo para chamadas síncronas e assíncronas.  
  
 Cada um dos seguintes pares de retornos de chamada ocorrerá no mesmo thread:  
  
-   `RemotingClientInvocationStarted` e [ICorProfilerCallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)  
  
-   [ICorProfilerCallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e [ICorProfilerCallback:: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
-   [ICorProfilerCallback:: Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) e [ICorProfilerCallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)  
  
 Você deve estar ciente dos seguintes problemas com os retornos de chamada de comunicação remota:  
  
-   Execução de uma função de comunicação remota não é refletida pelo criador de perfil API, portanto, as notificações para as funções que são chamadas do cliente e executadas no servidor não são recebidas corretamente. A invocação real ocorre por meio de um objeto de proxy; o criador de perfil, parece que determinadas funções são compilados em JIT, mas nunca usados.  
  
-   O criador de perfil não recebe notificações precisas de eventos de comunicação remota assíncrona.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
