---
title: Interface IHostCrst
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34a911668db09b255282833cec3e6272b315373b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618653"
---
# <a name="ihostcrst-interface"></a>Interface IHostCrst
Serve como a representação do host de uma seção crítica para threading.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Enter](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Entrar na seção crítica.|  
|[Método Leave](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Deixa a seção crítica.|  
|[Método SetSpinCount](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Define a contagem de rotação para a seção crítica.|  
|[Método TryEnter](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Tentativas de inserir a seção crítica e relatórios de êxito ou falha imediatamente.|  
  
## <a name="remarks"></a>Comentários  
 `IHostCrst` permite que o common language runtime (CLR) para se comunicar diretamente com a representação do host de uma seção crítica, em vez de usar as funções do Win32, como `EnterCriticalSection` ou `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
