---
title: "Método ICorProfilerCallback::RemotingServerReceivingMessage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e4542f5362d83bc5c0419b9f1ff389c9a21aad29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>Método ICorProfilerCallback::RemotingServerReceivingMessage
Notifica o criador de perfil que o processo recebeu uma solicitação de ativação ou invocação de método remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCookie`  
 [in] Um valor que irá corresponder com o valor fornecido no [: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) sob estas condições:  
  
-   Cookies GUID de comunicação remota estão ativos.  
  
-   O canal tem sucesso na transmissão de mensagem.  
  
-   Cookies GUID estão ativos no processo de cliente.  
  
 Isso permite que o emparelhamento fácil de chamadas de comunicação remota e a criação de uma pilha de chamadas lógicas.  
  
 `fIsAsync`  
 [in] Um valor que é `true` se a chamada for assíncrona; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se a solicitação de mensagem é assíncrona, a solicitação pode ser atendida por qualquer thread arbitrário.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
