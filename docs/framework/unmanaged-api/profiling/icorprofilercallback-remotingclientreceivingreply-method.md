---
title: Método ICorProfilerCallback::RemotingClientReceivingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: f7a943627e2087e6b8c78ced9fc32824843d44fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175129"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a>Método ICorProfilerCallback::RemotingClientReceivingReply
Notifica o profiler que a parte do lado do servidor de uma chamada remoting foi concluída e o cliente está recebendo e prestes a processar a resposta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a>parâmetros  
 `pCookie`  
 [em] Um valor que corresponderá ao valor fornecido no [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) nessas condições:  
  
- Os cookies GUID de remoção estão ativos.  
  
- O canal consegue transmitir a mensagem.  
  
- Os cookies GUID estão ativos no processo do lado do servidor.  
  
 Isso permite um emparelhamento fácil de chamadas remoting.  
  
 `fIsAsync`  
 [em] Um valor `true` que é se a chamada for assíncrona; caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
