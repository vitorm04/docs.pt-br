---
title: "Método ICorProfilerCallback::RemotingClientInvocationFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientInvocationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77f86d12d3a19f1b02ece35c8b717e78802f74f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a>Método ICorProfilerCallback::RemotingClientInvocationFinished
Notifica o criador de perfil que uma chamada de comunicação remota foi executado para conclusão no cliente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a>Comentários  
 Se a chamada de comunicação remota síncrona, ele também foi executada até a conclusão no servidor. Se a chamada de comunicação remota assíncrona, uma resposta ainda poderia ser esperada quando a chamada é manipulada. Se uma resposta é esperada, ocorrerá uma chamada para [: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e uma chamada adicional para `RemotingClientInvocationFinished` para indicar o processamento necessário secundário de uma chamada assíncrona.  
  
 Cada um dos seguintes pares de retornos de chamada ocorrerá no mesmo thread:  
  
-   `RemotingClientInvocationStarted`e [: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)  
  
-   [: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) e [: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
-   [Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) e [: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)  
  
 Você deve estar ciente dos problemas a seguir com os retornos de chamada de comunicação remota:  
  
-   Execução de uma função de comunicação remota não é refletida pela API, o criador de perfil para que as notificações para as funções que são chamadas do cliente e executadas no servidor não são recebidas corretamente. A invocação real ocorre por meio de um objeto de proxy. o criador de perfil, parece que determinadas funções são compilados JIT, mas nunca é usado.  
  
-   O criador de perfil não recebe notificações precisas para eventos de comunicação remota assíncrona.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
