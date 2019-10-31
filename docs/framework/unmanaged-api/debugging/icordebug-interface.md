---
title: Interface ICorDebug
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: ee6bcbc9f3377735ed289d52afddb6efa755b16d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134069"
---
# <a name="icordebug-interface"></a>Interface ICorDebug
Fornece métodos que permitem aos desenvolvedores depurar aplicativos no ambiente Common Language Runtime (CLR).  
  
> [!NOTE]
> Não há suporte para depuração de modo misto (código gerenciado e nativo) no Windows 95, Windows 98 ou Windows ME ou em plataformas não x86 (como IA64 e AMD64).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CanLaunchOrAttach](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Determina se é possível iniciar um novo processo ou anexá-lo ao processo fornecido no contexto da máquina atual e da configuração de tempo de execução.|  
|[Método CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Inicia um processo e seu thread principal sob o controle do depurador.|  
|[Método DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Anexa o depurador a um processo existente.|  
|[Método EnumerateProcesses](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Obtém um enumerador para os processos que estão sendo depurados.|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Retorna o objeto "ICorDebugProcess" com a ID de processo fornecida.|  
|[Método Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Inicializa o objeto `ICorDebug`.|  
|[Método SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Especifica o objeto manipulador de eventos para eventos gerenciados.|  
|[Método SetUnmanagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Especifica o objeto do manipulador de eventos para eventos não gerenciados.|  
|[Método Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Encerra o objeto `ICorDebug`.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebug` representa um loop de processamento de eventos para um processo do depurador. O depurador deve aguardar o retorno de chamada [ICorDebugManagedCallback:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) de todos os processos que estão sendo depurados antes de liberar essa interface.  
  
 O objeto `ICorDebug` é o objeto inicial para controlar toda a depuração gerenciada adicional. No .NET Framework versões 1,0 e 1,1, esse objeto era um objeto `CoClass` criado a partir de COM. No .NET Framework versão 2,0, esse objeto não é mais um objeto `CoClass`. Ele deve ser criado pela função [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) , que tem mais reconhecimento de versão. Essa nova função de criação permite que os clientes obtenham uma implementação específica do `ICorDebug`, que também emula uma versão específica da API de depuração.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
