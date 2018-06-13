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
ms.openlocfilehash: ed0d2ff3b64bab026087e13d54314eca86181d8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438802"
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
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
