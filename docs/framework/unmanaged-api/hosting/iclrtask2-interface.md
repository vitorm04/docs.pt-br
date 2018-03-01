---
title: Interface ICLRTask2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8701cff3400e46660fac90486cf5648d29aa9972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2-interface"></a>Interface ICLRTask2
Fornece toda a funcionalidade do [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; Além disso, fornece métodos que permitem cancelamentos do thread para ser atrasado no thread atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Novo thread de atrasos de anulação de solicitações no thread atual.|  
|[Método EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Permite que novos ou pendente solicitações de anulação de thread resultará em thread anulada no thread atual.|  
  
## <a name="remarks"></a>Comentários  
 O `ICLRTask2` interface herda o `ICLRTask` interface e adiciona métodos que permitem que o host atrasar anulações de thread, para proteger uma região de código que não deve falhar. Chamando `BeginPreventAsyncAbort` incrementa o contador de anulação de thread de atraso para o thread atual e chamar `EndPreventAsyncAbort` diminui-la. Chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` podem ser aninhados. Como o contador for maior que zero, anulações de thread para o thread atual estão atrasadas.  
  
 Se chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` não são emparelhados, é possível atingir um estado no qual thread anulações não podem ser entregue ao thread atual.  
  
 O atraso não é cumprido por um thread que anula a mesmo.  
  
 A funcionalidade que é exposta por este recurso é usada internamente pela máquina virtual (VM). Uso indevido dos métodos a seguir pode causar comportamento não especificado na VM. Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador para zero quando a VM foi incrementada anteriormente. Da mesma forma, o contador interno não é verificado de estouro. Se ele exceder o limite de integral porque ele é incrementado pelo host e a máquina virtual, o comportamento resultante é não especificado.  
  
 Para obter informações sobre membros herdada do `ICLRTask` e sobre outros usos dessa interface, consulte o [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
