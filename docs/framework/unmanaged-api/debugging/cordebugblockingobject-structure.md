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
ms.openlocfilehash: 12a114ea65aca544d653704cdfb01ed15d19c581
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143215"
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
