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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 516485d39f1e18a3b82886ed08cd0344c16236dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640531"
---
# <a name="icordebugmanagedcallback-interface"></a>Interface ICorDebugManagedCallback
Fornece métodos para processar retornos de chamada do depurador.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Break](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Notifica o depurador quando uma <xref:System.Reflection.Emit.OpCodes.Break> instrução no fluxo de código é executada.|  
|[Método Breakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Notifica o depurador quando um ponto de interrupção é encontrado.|  
|[Método BreakpointSetError](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Notifica o depurador que o common language runtime (CLR) não pôde associar com precisão de um ponto de interrupção foi definido antes de uma função ficou just-in-time (JIT) compilado.|  
|[Método ControlCTrap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Notifica o depurador que um CTRL + C é interceptado no processo sendo depurado.|  
|[Método CreateAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Notifica o depurador que um domínio de aplicativo foi criado.|  
|[Método CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Notifica o depurador quando um processo foi anexado ou iniciado pela primeira vez.|  
|[Método CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Notifica o depurador que um thread foi iniciado executando código gerenciado.|  
|[Método DebuggerError](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Notifica o depurador que ocorreu um erro durante a tentativa de manipular um evento do CLR.|  
|[Método EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Preterido. Notifica o depurador que um evento de remapeamento foi enviado para o IDE.|  
|[Método EvalComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Notifica o depurador que uma avaliação foi concluída.|  
|[Método EvalException](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Notifica o depurador que uma avaliação foi encerrada com uma exceção sem tratamento.|  
|[Método Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Notifica o depurador que foi lançada uma exceção do código gerenciado.|  
|[Método ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Notifica o depurador que um domínio de aplicativo foi encerrado.|  
|[Método ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Notifica o depurador que um processo foi encerrado.|  
|[Método ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Notifica o depurador que um thread que estava executando código gerenciado foi encerrado.|  
|[Método LoadAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Notifica o depurador que um assembly CLR foi carregado com êxito.|  
|[Método LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Notifica o depurador que uma classe foi carregada.|  
|[Método LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Notifica o depurador um módulo CLR foi carregado com êxito.|  
|[Método LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Notifica o depurador um thread gerenciado do CLR chamou um método no <xref:System.Diagnostics.EventLog> classe para registrar um evento.|  
|[Método LogSwitch](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Notifica o depurador um thread gerenciado do CLR chamou um método no <xref:System.Diagnostics.Switch> classe para criar, modificar ou excluir um comutador de depuração/rastreamento.|  
|[Método NameChange](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Notifica o depurador que o nome de um domínio do aplicativo ou thread foi alterado.|  
|[Método StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Notifica o depurador que uma etapa foi concluída.|  
|[Método UnloadAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Notifica o depurador que um assembly CLR foi descarregado.|  
|[Método UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Notifica o depurador que uma classe está sendo descarregada.|  
|[Método UnloadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Notifica o depurador que um módulo CLR (DLL) foi descarregado.|  
|[Método UpdateModuleSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Notifica o depurador para que os símbolos para um módulo CLR foram alterados.|  
  
## <a name="remarks"></a>Comentários  
 Todos os retornos de chamada são serializados, chamados no mesmo thread e chamados com o processo no estado sincronizado.  
  
 Cada implementação do retorno de chamada deve chamar [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para retomar a execução. Se `ICorDebugController::Continue` não é chamado antes do retorno de chamada retorna, o processo permanecerá parado e nenhum retorno de chamada do evento mais ocorrerá até `ICorDebugController::Continue` é chamado.  
  
 Um depurador deve implementar [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) se ele está depurando aplicativos do .NET Framework versão 2.0. Uma instância do `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` é passado como o objeto de retorno de chamada para [icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
