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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2134a7f12ac482b3fe79ac722684ac8601a7280b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662916"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a>Método ICorProfilerCallback::RemotingClientReceivingReply
Notifica o criador de perfil que a parte do lado do servidor de uma chamada de comunicação remota foi concluída e o cliente agora está recebendo e prestes a processar a resposta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCookie`  
 [in] Um valor que irá corresponder com o valor fornecido no [ICorProfilerCallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) sob estas condições:  
  
- Cookies GUID de comunicação remota estão ativos.  
  
- O canal é bem-sucedida na transmissão de mensagem.  
  
- Os cookies GUID são Active Directory sobre o processo do lado do servidor.  
  
 Isso permite que o emparelhamento fácil de chamadas de comunicação remota.  
  
 `fIsAsync`  
 [in] Um valor que é `true` se a chamada é assíncrona; caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
