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
ms.openlocfilehash: 2c2eb7d0dc04d813b1ce91fb1acf4b171f244592
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445755"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>Método ICorProfilerCallback::RemotingServerReceivingMessage
Notifies the profiler that the process has received a remote method invocation or activation request.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCookie`  
 [in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:  
  
- Remoting GUID cookies are active.  
  
- The channel succeeds in transmitting the message.  
  
- GUID cookies are active on the client-side process.  
  
 This allows easy pairing of remoting calls and the creation of a logical call stack.  
  
 `fIsAsync`  
 [in] A value that is `true` if the call is asynchronous; otherwise, `false`.  
  
## <a name="remarks"></a>Comentários  
 If the message request is asynchronous, the request can be serviced by any arbitrary thread.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
