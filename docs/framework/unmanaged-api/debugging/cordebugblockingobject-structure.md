---
title: Estrutura CorDebugBlockingObject
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49521e4b4ff5f8c364827b233759e163aca43e39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542643"
---
# <a name="cordebugblockingobject-structure"></a>Estrutura CorDebugBlockingObject
Define um objeto que está bloqueando um thread e o motivo específico que o thread está bloqueado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`pBlockingObject`|O objeto no qual o thread está bloqueando. Esse objeto é válido apenas para a duração do estado atual de sincronizado. Se dois threads estiver bloqueando no mesmo objeto dentro do mesmo estado sincronizado, você pode esperar que o [icordebugvalue:: Getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) método para retornar o mesmo valor. No entanto, as interfaces podem ou não ser equivalente do ponteiro.|  
|`dwTimeout`|O número de milissegundos antes da operação de bloqueio atingirá o tempo limite ou o valor infinito, o que indica que ele não terá tempo limite. O valor de tempo limite Especifica o comprimento total do tempo para a operação de bloqueio, não a hora em que ainda resta.|  
|`blockingReason`|O motivo pelo qual que o thread é bloqueado neste objeto.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
