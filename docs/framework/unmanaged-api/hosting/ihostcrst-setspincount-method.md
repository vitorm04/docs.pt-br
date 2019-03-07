---
title: Método IHostCrst::SetSpinCount
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf83c7755bc099275c02ff0049f663573c582faf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469555"
---
# <a name="ihostcrstsetspincount-method"></a>Método IHostCrst::SetSpinCount
Define a contagem de rotação atual [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instância.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwSpinCount`  
 [in] A nova contagem de rotação atual `IHostCrst` instância.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetSpinCount` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 Em sistemas com vários processadores, se a seção crítica representado pelo atual `IHostCrst` instância não estiver disponível, um thread de chamada gira `dwSpinCount` vezes antes de chamar [ihostsemaphore:: wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) em um semáforo associado com a seção crítica. Se a seção crítica ficar livre durante a operação de rotação, o thread de chamada evita a operação de espera.  
  
 O uso de `dwSpinCount` é idêntica ao uso do parâmetro do mesmo nome no Win32 `InitializeCriticalSectionAndSpinCount` função.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [Interface IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
