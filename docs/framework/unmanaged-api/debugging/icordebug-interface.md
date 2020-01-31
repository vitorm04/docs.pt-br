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
ms.openlocfilehash: 0ca66f001d04bc86b64e0fe2d1cd37559e4fc633
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785111"
---
# <a name="icordebug-interface"></a>Interface ICorDebug
Fornece métodos que permitem aos desenvolvedores depurar aplicativos no ambiente Common Language Runtime (CLR).  
  
> [!NOTE]
> Não há suporte para depuração de modo misto (código gerenciado e nativo) no Windows 95, Windows 98 ou Windows ME ou em plataformas não x86 (como IA64 e AMD64).  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CanLaunchOrAttach](icordebug-canlaunchorattach-method.md)|Determina se é possível iniciar um novo processo ou anexá-lo ao processo fornecido no contexto da máquina atual e da configuração de tempo de execução.|  
|[Método CreateProcess](icordebug-createprocess-method.md)|Inicia um processo e seu thread principal sob o controle do depurador.|  
|[Método DebugActiveProcess](icordebug-debugactiveprocess-method.md)|Anexa o depurador a um processo existente.|  
|[Método EnumerateProcesses](icordebug-enumerateprocesses-method.md)|Obtém um enumerador para os processos que estão sendo depurados.|  
|[Método GetProcess](icordebug-getprocess-method.md)|Retorna o objeto "ICorDebugProcess" com a ID de processo fornecida.|  
|[Método Initialize](icordebug-initialize-method.md)|Inicializa o objeto `ICorDebug`.|  
|[Método SetManagedHandler](icordebug-setmanagedhandler-method.md)|Especifica o objeto manipulador de eventos para eventos gerenciados.|  
|[Método SetUnmanagedHandler](icordebug-setunmanagedhandler-method.md)|Especifica o objeto do manipulador de eventos para eventos não gerenciados.|  
|[Método Terminate](icordebug-terminate-method.md)|Encerra o objeto `ICorDebug`.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebug` representa um loop de processamento de eventos para um processo do depurador. O depurador deve aguardar o retorno de chamada [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) de todos os processos que estão sendo depurados antes de liberar essa interface.  
  
 O objeto `ICorDebug` é o objeto inicial para controlar toda a depuração gerenciada adicional. No .NET Framework versões 1,0 e 1,1, esse objeto era um objeto `CoClass` criado a partir de COM. No .NET Framework versão 2,0, esse objeto não é mais um objeto `CoClass`. Ele deve ser criado pela função [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) , que tem mais reconhecimento de versão. Essa nova função de criação permite que os clientes obtenham uma implementação específica do `ICorDebug`, que também emula uma versão específica da API de depuração.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
