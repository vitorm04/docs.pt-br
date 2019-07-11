---
title: Método ICLRSyncManager::GetMonitorOwner
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1c986de068cd79ae3662c82ed24906d42bf2780
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759040"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>Método ICLRSyncManager::GetMonitorOwner
Obtém o [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que detém o monitor identificado pelo cookie especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cookie`  
 [in] O cookie associado ao monitor.  
  
 `ppOwnerHostTask`  
 [out] Um ponteiro para o `IHostTask` que atualmente possui o monitor ou nulo se nenhuma tarefa tem a propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O host normalmente chama `GetMonitorOwner` como parte de um mecanismo de detecção de deadlock. O cookie é associado um monitor quando ele é criado usando uma chamada para [ihostsyncmanager:: Createmonitorevent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).  
  
> [!NOTE]
>  Uma chamada para liberar o evento subjacente o monitor pode bloquear — mas não será bloqueada — se uma chamada para esse método está atualmente em vigor no cookie associado a esse monitor. Outras tarefas também podem bloquear se eles tentam adquirir o monitor.  
  
 `GetMonitorOwner` sempre retorna imediatamente e pode ser chamado a qualquer momento após uma chamada para `CreateMonitorEvent`. O host não precisa esperar até que uma tarefa está esperando o evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
