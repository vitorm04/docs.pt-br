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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cbd627eff9318fce38ec238e5fa686cc9d759b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627181"
---
# <a name="iclrtask2-interface"></a>Interface ICLRTask2
Fornece a funcionalidade dos [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; Além disso, fornece métodos que permitem que as anulações de thread para ser atrasado no thread atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Novo thread de atrasos de anulação de solicitações no thread atual.|  
|[Método EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Permite que novos ou thread anulação solicitações pendentes para resultar em thread anula no thread atual.|  
  
## <a name="remarks"></a>Comentários  
 O `ICLRTask2` interface herda o `ICLRTask` de interface e adiciona métodos que permitem que o host atrasar as anulações de thread, para proteger uma região de código que não deve falhar. Chamando `BeginPreventAsyncAbort` incrementa o contador de anulação de thread de atraso para o thread atual e chamar `EndPreventAsyncAbort` diminui-lo. Chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` podem ser aninhados. Desde que o contador for maior que zero, as anulações de thread para o thread atual são atrasadas.  
  
 Se chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` não são emparelhadas, é possível atingir um estado no qual thread anulações não podem ser entregues ao thread atual.  
  
 O atraso é respeitado para um thread que anula a mesmo.  
  
 A funcionalidade que é exposta por esse recurso é usada internamente pela máquina virtual (VM). Uso indevido desses métodos pode causar comportamento não especificado na VM. Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador como zero quando a VM é incrementado anteriormente. Da mesma forma, o contador interno não é verificado para estouro. Se ele exceder seu limite de integral porque ele é incrementado pelo host e a VM, o comportamento resultante é especificado.  
  
 Para obter informações sobre membros herdada de `ICLRTask` e sobre outros usos dessa interface, consulte a [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
