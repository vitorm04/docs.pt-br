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
ms.openlocfilehash: b2429052173a187297b67c756213e5d27a79298b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792600"
---
# <a name="icordebugprocess-interface"></a>Interface ICorDebugProcess
Representa um processo que está executando o código gerenciado. Essa interface é uma subclasse de ICorDebugController.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearCurrentException](icordebugprocess-clearcurrentexception-method.md)|Limpa a exceção não gerenciada atual no thread determinado.|  
|[Método EnableLogMessages](icordebugprocess-enablelogmessages-method.md)|Habilita e desabilita o envio de mensagens de log para o depurador.|  
|[Método EnumerateAppDomains](icordebugprocess-enumerateappdomains-method.md)|Enumera todos os domínios de aplicativo no processo.|  
|[Método EnumerateObjects](icordebugprocess-enumerateobjects-method.md)|Não implementado.|  
|[Método GetHandle](icordebugprocess-gethandle-method.md)|Obtém um identificador para o processo.|  
|[Método GetHelperThreadID](icordebugprocess-gethelperthreadid-method.md)|Obtém a ID do thread do sistema operacional (SO) para o thread auxiliar interno do depurador.|  
|[Método GetID](icordebugprocess-getid-method.md)|Obtém a ID do sistema operacional (SO) do processo.|  
|[Método GetObject](icordebugprocess-getobject-method.md)|Não implementado.|  
|[Método GetThread](icordebugprocess-getthread-method.md)|Obtém a instância ICorDebugThread que tem a ID de thread do sistema operacional especificada.|  
|[Método GetThreadContext](icordebugprocess-getthreadcontext-method.md)|Obtém o contexto para o thread fornecido.|  
|[Método IsOSSuspended](icordebugprocess-isossuspended-method.md)|Determina se o thread foi suspenso como resultado do depurador parando o processo.|  
|[Método IsTransitionStub](icordebugprocess-istransitionstub-method.md)|Determina se um endereço está dentro de um stub que causará uma transição para o código gerenciado.|  
|[Método ModifyLogSwitch](icordebugprocess-modifylogswitch-method.md)|Define o nível de severidade da opção de log especificada.|  
|[Método ReadMemory](icordebugprocess-readmemory-method.md)|Lê a memória do processo.|  
|[Método SetThreadContext](icordebugprocess-setthreadcontext-method.md)|Define o contexto para o thread fornecido.|  
|[Método ThreadForFiberCookie](icordebugprocess-threadforfibercookie-method.md)|Preterido.|  
|[Método WriteMemory](icordebugprocess-writememory-method.md)|Grava dados em uma área de memória no processo.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebug](icordebug-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
