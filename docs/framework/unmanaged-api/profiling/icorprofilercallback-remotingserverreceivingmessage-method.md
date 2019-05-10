---
title: Método ICorProfilerCallback::RemotingServerReceivingMessage
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec6f7cf8c70292d586e58b5b6d8251aa4700dbac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662892"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>Método ICorProfilerCallback::RemotingServerReceivingMessage
Notifica o criador de perfil que o processo tenha recebido uma solicitação de ativação ou invocação de método remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCookie`  
 [in] Um valor que irá corresponder com o valor fornecido no [ICorProfilerCallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) sob estas condições:  
  
- Cookies GUID de comunicação remota estão ativos.  
  
- O canal é bem-sucedida na transmissão de mensagem.  
  
- Os cookies GUID são Active Directory sobre o processo do lado do cliente.  
  
 Isso permite que o emparelhamento fácil de chamadas de comunicação remota e a criação de uma pilha de chamadas lógicas.  
  
 `fIsAsync`  
 [in] Um valor que é `true` se a chamada é assíncrona; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se a solicitação de mensagem é assíncrona, a solicitação pode ser atendida por qualquer thread arbitrário.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
