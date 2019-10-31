---
title: Interface ICorDebugManagedCallback
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
ms.openlocfilehash: 96dedcd27e87c5afc504e7840100eb121410675e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130755"
---
# <a name="icordebugmanagedcallback-interface"></a>Interface ICorDebugManagedCallback
Fornece métodos para processar retornos de chamada do depurador.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Break](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Notifica o depurador quando uma instrução <xref:System.Reflection.Emit.OpCodes.Break> no fluxo de código é executada.|  
|[Método Breakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Notifica o depurador quando um ponto de interrupção é encontrado.|  
|[Método BreakpointSetError](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Notifica o depurador de que o Common Language Runtime (CLR) não pôde associar com precisão um ponto de interrupção que foi definido antes de uma função ser compilada por JIT (just-in-time).|  
|[Método ControlCTrap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Notifica o depurador de que um CTRL + C é interceptado no processo que está sendo depurado.|  
|[Método CreateAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Notifica o depurador de que um domínio de aplicativo foi criado.|  
|[Método CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Notifica o depurador quando um processo foi anexado ou iniciado pela primeira vez.|  
|[Método CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Notifica o depurador de que um thread iniciou a execução de código gerenciado.|  
|[Método DebuggerError](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Notifica o depurador de que ocorreu um erro ao tentar lidar com um evento do CLR.|  
|[Método EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Preterido. Notifica o depurador de que um evento de remapeamento foi enviado para o IDE.|  
|[Método EvalComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Notifica o depurador de que uma avaliação foi concluída.|  
|[Método EvalException](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Notifica o depurador de que uma avaliação foi encerrada com uma exceção sem tratamento.|  
|[Método Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Notifica o depurador de que uma exceção foi lançada do código gerenciado.|  
|[Método ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Notifica o depurador de que um domínio de aplicativo foi encerrado.|  
|[Método ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Notifica o depurador de que um processo foi encerrado.|  
|[Método ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Notifica o depurador de que um thread que estava executando código gerenciado foi encerrado.|  
|[Método LoadAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Notifica o depurador de que um assembly CLR foi carregado com êxito.|  
|[Método LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Notifica o depurador de que uma classe foi carregada.|  
|[Método LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Notifica o depurador de que um módulo CLR foi carregado com êxito.|  
|[Método LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Notifica o depurador de que um thread gerenciado pelo CLR chamou um método na classe <xref:System.Diagnostics.EventLog> para registrar um evento.|  
|[Método LogSwitch](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Notifica o depurador de que um thread gerenciado pelo CLR chamou um método na classe <xref:System.Diagnostics.Switch> para criar, modificar ou excluir uma opção de depuração/rastreamento.|  
|[Método NameChange](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Notifica o depurador de que o nome de um domínio de aplicativo ou thread foi alterado.|  
|[Método StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Notifica o depurador de que uma etapa foi concluída.|  
|[Método UnloadAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Notifica o depurador de que um assembly CLR foi descarregado.|  
|[Método UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Notifica o depurador de que uma classe está sendo descarregada.|  
|[Método UnloadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Notifica o depurador de que um módulo CLR (DLL) foi descarregado.|  
|[Método UpdateModuleSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Notifica o depurador de que os símbolos de um módulo CLR foram alterados.|  
  
## <a name="remarks"></a>Comentários  
 Todos os retornos de chamada são serializados, chamados no mesmo thread e chamados com o processo no estado SYNCHRONIZED.  
  
 Cada implementação de retorno de chamada deve chamar [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para retomar a execução. Se `ICorDebugController::Continue` não for chamado antes que o retorno de chamada seja retornado, o processo permanecerá parado e nenhum mais retornos de chamada de evento ocorrerá até que `ICorDebugController::Continue` seja chamado.  
  
 Um depurador deve implementar [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) se estiver depurando .NET Framework aplicativos da versão 2,0. Uma instância de `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` é passada como o objeto de retorno de chamada para [ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
