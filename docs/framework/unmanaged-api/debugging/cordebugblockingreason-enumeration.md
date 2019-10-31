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
ms.openlocfilehash: bc488e55bf64468eb62e2dc6eaedca62ebde3310
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098979"
---
# <a name="cordebugblockingreason-enumeration"></a>Enumeração CorDebugBlockingReason
Especifica os motivos pelos quais um thread pode ficar bloqueado em um determinado objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Um thread está tentando adquirir a seção crítica associada ao bloqueio de monitor em um objeto. Normalmente, isso ocorre quando você chama um dos métodos <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ou <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>.|  
|`BLOCKING_MONITOR_EVENT`|Um thread está aguardando o evento que está associado a um bloqueio de monitor para um objeto. Normalmente, isso ocorre quando você chama um dos métodos de `Wait` <xref:System.Threading.Monitor?displayProperty=nameWithType>.|  
  
## <a name="remarks"></a>Comentários  
 Quando o membro `BLOCKING_MONITOR_CRITICAL_SECTION` ou `BLOCKING_MONITOR_EVENT` é usado em uma estrutura [CorDebugBlockingObject](cordebugblockingobject-structure.md) , o membro `pBlockingObject` da estrutura aponta para uma interface "ICorDebugValue" que representa o objeto que está sendo inserido. Também é garantido implementar a interface [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](debugging-enumerations.md)
- [Depuração](index.md)
