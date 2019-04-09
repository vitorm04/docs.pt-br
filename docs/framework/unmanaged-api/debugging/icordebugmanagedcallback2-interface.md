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
ms.openlocfilehash: f1ecfea208f87f53f15fcc4cdafb58341c293e43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096082"
---
# <a name="icordebugmanagedcallback2-interface"></a>Interface ICorDebugManagedCallback2
Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs). `ICorDebugManagedCallback2` é uma extensão lógica do [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|Notifica o depurador que o conjunto de tarefas associadas com a conexão especificada foi alterado.|  
|[Método CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|Notifica o depurador que foi criada uma nova conexão.|  
|[Método DestroyConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|Notifica o depurador para que a conexão especificada foi encerrada.|  
|[Método Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|Notifica o depurador que uma pesquisa por um manipulador de exceção foi iniciada.|  
|[Método ExceptionUnwind](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|Fornece uma notificação de status durante o processo de desenrolamento de exceção.|  
|[Método FunctionRemapComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|Notifica o depurador para que a execução de código mudou para uma nova versão de uma função editada.|  
|[Método FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|Notifica o depurador para que a execução de código atingiu um ponto de sequência em uma versão mais antiga de uma função editada.|  
|[Método MDANotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|Fornece notificação de que a execução de código encontrou uma mensagem MDA (Assistente) depuração gerenciada.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugManagedCallback2` interface estende o `ICorDebugManagedCallback` interface para lidar com novos eventos de depuração introduzidos no .NET Framework versão 2.0.  
  
 Um depurador deve implementar `ICorDebugManagedCallback2` se ele está depurando aplicativos do .NET Framework 2.0. Uma instância do `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` é passado como o objeto de retorno de chamada para [icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Diagnosticando erros com assistentes de depuração gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
