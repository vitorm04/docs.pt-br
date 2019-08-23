---
title: Interface ICorDebugProcess
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b99630ba60cd84254024b91dba9ef9922fd7e041
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943312"
---
# <a name="icordebugprocess-interface"></a>Interface ICorDebugProcess
Representa um processo que está executando o código gerenciado. Essa interface é uma subclasse de ICorDebugController.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Limpa a exceção não gerenciada atual no thread determinado.|  
|[Método EnableLogMessages](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Habilita e desabilita o envio de mensagens de log para o depurador.|  
|[Método EnumerateAppDomains](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Enumera todos os domínios de aplicativo no processo.|  
|[Método EnumerateObjects](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Não implementado.|  
|[Método GetHandle](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Obtém um identificador para o processo.|  
|[Método GetHelperThreadID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Obtém a ID do thread do sistema operacional (SO) para o thread auxiliar interno do depurador.|  
|[Método GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Obtém a ID do sistema operacional (SO) do processo.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Não implementado.|  
|[Método GetThread](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Obtém a instância ICorDebugThread que tem a ID de thread do sistema operacional especificada.|  
|[Método GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Obtém o contexto para o thread fornecido.|  
|[Método IsOSSuspended](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Determina se o thread foi suspenso como resultado do depurador parando o processo.|  
|[Método IsTransitionStub](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Determina se um endereço está dentro de um stub que causará uma transição para o código gerenciado.|  
|[Método ModifyLogSwitch](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Define o nível de severidade da opção de log especificada.|  
|[Método ReadMemory](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Lê a memória do processo.|  
|[Método SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Define o contexto para o thread fornecido.|  
|[Método ThreadForFiberCookie](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Preterido.|  
|[Método WriteMemory](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Grava dados em uma área de memória no processo.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
