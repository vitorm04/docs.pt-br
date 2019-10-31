---
title: Interface ICLRTask2
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124519"
---
# <a name="iclrtask2-interface"></a>Interface ICLRTask2
Fornece toda a funcionalidade da interface [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ; Além disso, o fornece métodos que permitem que as anulações de thread sejam atrasadas no thread atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Atrasa novas solicitações de anulação de thread no thread atual.|  
|[Método EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Permite solicitações de anulação de thread novas ou pendentes para resultar em anulações de thread no thread atual.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICLRTask2` herda a interface `ICLRTask` e adiciona métodos que permitem ao host atrasar anulações de thread, proteger uma região de código que não deve falhar. Chamar `BeginPreventAsyncAbort` incrementa o contador atraso-thread-anulação para o thread atual e chamar `EndPreventAsyncAbort` decrementa-lo. As chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` podem ser aninhadas. Desde que o contador seja maior que zero, as anulações de thread para o thread atual serão atrasadas.  
  
 Se as chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` não forem emparelhadas, é possível alcançar um estado no qual as anulações de thread não podem ser entregues ao thread atual.  
  
 O atraso não é respeitado para um thread que se anula.  
  
 A funcionalidade exposta por esse recurso é usada internamente pela VM (máquina virtual). O uso indevido desses métodos pode causar um comportamento não especificado na VM. Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` pode definir o contador como zero quando a VM o incrementaa anteriormente. Da mesma forma, o contador interno não é verificado quanto ao estouro. Se ele exceder seu limite integral porque é incrementado pelo host e pela VM, o comportamento resultante não é especificado.  
  
 Para obter informações sobre membros herdados de `ICLRTask` e sobre outros usos dessa interface, consulte a interface [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
