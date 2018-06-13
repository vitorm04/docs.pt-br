---
title: Interface ICorDebugManagedCallback2
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22f4b2cb1bafefefaf3a3fc207af76c80c0c9798
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420336"
---
# <a name="icordebugmanagedcallback2-interface"></a>Interface ICorDebugManagedCallback2
Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs). `ICorDebugManagedCallback2` é uma extensão lógica do [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|Notifica o depurador que o conjunto de tarefas associadas a conexão especificada foi alterado.|  
|[Método CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|Notifica o depurador que foi criada uma nova conexão.|  
|[Método DestroyConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|Notifica o depurador a conexão especificada foi encerrada.|  
|[Método Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|Notifica o depurador que uma pesquisa para um manipulador de exceção foi iniciada.|  
|[Método ExceptionUnwind](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|Fornece uma notificação de status durante o processo de desenrolamento da exceção.|  
|[Método FunctionRemapComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|Notifica o depurador que a execução de código alternou para uma nova versão de uma função editada.|  
|[Método FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|Notifica o depurador que a execução de código atingiu um ponto de sequência em uma versão anterior de uma função editada.|  
|[Método MDANotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|Fornece notificação de que a execução de código encontrou uma mensagem de (MDA) do Assistente de depuração gerenciada.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugManagedCallback2` interface estende o `ICorDebugManagedCallback` interface para lidar com os novos eventos de depuração, introduzidos no .NET Framework versão 2.0.  
  
 Um depurador deve implementar `ICorDebugManagedCallback2` se depurar aplicativos do .NET Framework 2.0. Uma instância de `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` é passado como o objeto de retorno de chamada para [: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
