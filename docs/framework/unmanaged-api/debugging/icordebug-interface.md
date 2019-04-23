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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193232ce1006a9cf209db9330343386404948440
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168279"
---
# <a name="icordebug-interface"></a>Interface ICorDebug
Fornece métodos que permitem que os desenvolvedores depurem aplicativos em que o ambiente do common language runtime (CLR).  
  
> [!NOTE]
>  Não há suporte para a depuração mista (código gerenciado e nativo) no Windows 95, Windows 98 ou Windows ME ou em plataformas não x86 (como IA64 e AMD64).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CanLaunchOrAttach](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Determina se iniciando um novo processo ou anexando ao processo determinado é possível dentro do contexto da configuração da máquina e o tempo de execução atual.|  
|[Método CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Inicia um processo e thread primário, sob o controle do depurador.|  
|[Método DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Anexa o depurador a um processo existente.|  
|[Método EnumerateProcesses](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Obtém um enumerador para os processos que estão sendo depurados.|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Retorna o objeto "ICorDebugProcess" com a ID de processo especificado.|  
|[Método Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Inicializa o objeto `ICorDebug`.|  
|[Método SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Especifica o objeto de manipulador de eventos para eventos gerenciados.|  
|[Método SetUnmanagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Especifica o objeto de manipulador de eventos para eventos não gerenciados.|  
|[Método Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Encerra o `ICorDebug` objeto.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebug` representa um loop de processamento de eventos para um processo do depurador. O depurador deve aguardar a [icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) retorno de chamada de todos os processos que estão sendo depurados antes de liberar essa interface.  
  
 O `ICorDebug` é o objeto inicial para controlar a depuração gerenciada tudo ainda mais. Nas versões do .NET Framework 1.0 e 1.1, este objeto foi um `CoClass` objeto criado da COM. No .NET Framework versão 2.0, esse objeto não é mais um `CoClass` objeto. Ele deve ser criado o [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) função, que é mais reconhecimento de versão. Essa nova função de criação permite que os clientes receberem uma implementação específica da `ICorDebug`, que também emula uma versão específica da API de depuração.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
