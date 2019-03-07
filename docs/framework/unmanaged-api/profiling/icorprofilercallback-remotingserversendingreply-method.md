---
title: Método ICorProfilerCallback::RemotingServerSendingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 655b2af2efcaba82af46e92ae94abf3a4adc349c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500402"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a>Método ICorProfilerCallback::RemotingServerSendingReply
Notifica o criador de perfil que o processo terminou de processar uma solicitação de invocação de método remoto e está prestes a transmitir a resposta por meio de um canal.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCookie`  
 [in] Um ponteiro para um GUID que irá corresponder com o valor fornecido no [ICorProfilerCallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) sob estas condições:  
  
-   Cookies GUID de comunicação remota estão ativos.  
  
-   O canal é bem-sucedida na transmissão de mensagem.  
  
-   Os cookies GUID são Active Directory sobre o processo do lado do cliente.  
  
 Isso permite que o emparelhamento fácil de chamadas de comunicação remota e a criação de uma pilha de chamadas lógicas.  
  
 `fIsAsync`  
 [in] Um valor que é `true` se a chamada é assíncrona; caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
