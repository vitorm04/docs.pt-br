---
title: ICorDebugProcess Interface1
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
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6fa95d17e7ff6f857765ea2dd48f61b047a47b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess-interface1"></a>ICorDebugProcess Interface1
Representa um processo que está executando o código gerenciado. Esta interface é uma subclasse de ICorDebugController.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Limpa a exceção atual não gerenciada em um determinado thread.|  
|[Método EnableLogMessages](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Habilita e desabilita o envio de mensagens de log para o depurador.|  
|[Método EnumerateAppDomains](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Enumera todos os domínios de aplicativo no processo.|  
|[Método EnumerateObjects](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Não implementado.|  
|[Método GetHandle](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Obtém um identificador para o processo.|  
|[Método GetHelperThreadID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Obtém a ID do thread de sistema operacional (SO) para o thread de auxiliar interno do depurador.|  
|[Método GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Obtém a ID de sistema operacional (SO) do processo.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Não implementado.|  
|[Método GetThread](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Obtém a instância de ICorDebugThread que tem o thread de sistema operacional especificado ID|  
|[Método GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Obtém o contexto do thread especificado.|  
|[Método IsOSSuspended](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Determina se o thread foi suspenso como resultado o depurador ao interromper o processo.|  
|[Método IsTransitionStub](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Determina se um endereço está dentro de um stub que fará com que uma transição para código gerenciado.|  
|[Método ModifyLogSwitch](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Define o nível de severidade da opção de log especificado.|  
|[Método ReadMemory](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Ler a memória do processo.|  
|[Método SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Define o contexto de determinado thread.|  
|[Método ThreadForFiberCookie](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Preterido.|  
|[Método WriteMemory](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Grava dados em uma área da memória do processo.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
