---
title: Interface ICorDebugThread2
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82648714c375998e9daa1bb59cd9ebd9802b5794
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153927"
---
# <a name="icordebugthread2-interface"></a>Interface ICorDebugThread2
Serve como uma extensão lógica para a interface ICorDebugThread.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Obtém uma matriz de instâncias COR_ACTIVE_FUNCTION que contêm dados sobre as funções do Active Directory em quadros de um thread.|  
|[Método GetConnectionID](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Obtém um identificador de conexão para este `ICorDebugThread2`.|  
|[Método GetTaskID](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Obtém um identificador de tarefa para este `ICorDebugThread2`.|  
|[Método GetVolatileOSThreadID](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Obtém o identificador de thread do sistema operacional para este `ICorDebugThread2`.|  
|[Método InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Permite que um depurador interceptar a exceção atual em um thread.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
