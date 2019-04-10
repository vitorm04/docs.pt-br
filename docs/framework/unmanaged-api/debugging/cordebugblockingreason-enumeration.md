---
title: Enumeração CorDebugBlockingReason
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54652727b4684d71068a19eb5eeb2e862f413f25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215073"
---
# <a name="cordebugblockingreason-enumeration"></a>Enumeração CorDebugBlockingReason
Especifica os motivos pelos quais um thread pode ficar bloqueado em um determinado objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`BLOCKING_NONE`|Apenas para uso interno.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Um thread está tentando adquirir a seção crítica que está associada com o bloqueio do monitor em um objeto. Normalmente, isso ocorre quando você chama um dos <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ou <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> métodos.|  
|`BLOCKING_MONITOR_EVENT`|Um thread está aguardando o evento que está associado com um bloqueio de monitor para um objeto. Normalmente, isso ocorre quando você chama um do <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` métodos.|  
  
## <a name="remarks"></a>Comentários  
 Quando o `BLOCKING_MONITOR_CRITICAL_SECTION` ou `BLOCKING_MONITOR_EVENT` membro é usado em uma [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estrutura, o `pBlockingObject` membro dos pontos de estrutura para uma interface de "ICorDebugValue" que representa o objeto que está sendo inserido . Também é garantido para implementar o [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
