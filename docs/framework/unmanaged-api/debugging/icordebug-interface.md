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
ms.openlocfilehash: 74c5036bdc8a4a75e5711c6dc1d34d8f2c21128f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebug-interface"></a>Interface ICorDebug
Fornece métodos que permitem aos desenvolvedores depurar aplicativos no ambiente do common language runtime (CLR).  
  
> [!NOTE]
>  Não há suporte para a depuração (código gerenciado e nativo) de modo misto no Windows 95, Windows 98 ou Windows ME ou em plataformas x86 não (como IA64 e AMD64).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CanLaunchOrAttach](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Determina se iniciar um novo processo ou anexar ao processo determinado é possíveis dentro do contexto da configuração do computador e o tempo de execução atual.|  
|[Método CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Inicia um processo e o thread principal sob o controle do depurador.|  
|[Método DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Anexa o depurador a um processo existente.|  
|[Método EnumerateProcesses](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Obtém um enumerador para os processos que estão sendo depurados.|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Retorna o objeto "ICorDebugProcess" com a ID de processo especificado.|  
|[Método Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Inicializa o objeto `ICorDebug`.|  
|[Método SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Especifica o objeto do manipulador de eventos para eventos gerenciados.|  
|[Método SetUnmanagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Especifica o objeto do manipulador de eventos para eventos não gerenciados.|  
|[Método Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Encerra o `ICorDebug` objeto.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebug` representa um loop de processamento de eventos para um processo do depurador. O depurador deve aguardar o [: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) retorno de chamada de todos os processos que está sendo depurado antes de liberar esta interface.  
  
 O `ICorDebug` é o objeto inicial para controlar a depuração gerenciada tudo mais. Nas versões do .NET Framework 1.0 e 1.1, este objeto foi uma `CoClass` objeto criado pela COM. No .NET Framework versão 2.0, esse objeto não é mais um `CoClass` objeto. Ele deve ser criado pelo [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) função, que tem mais suporte a versão. Essa nova função de criação permite que os clientes obter uma implementação específica de `ICorDebug`, que emula também uma versão específica da API de depuração.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
