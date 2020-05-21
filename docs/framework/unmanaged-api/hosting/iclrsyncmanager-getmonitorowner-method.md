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
ms.openlocfilehash: 77debe047f5b379237022f44ef8f9d96718b227d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762494"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>Método ICLRSyncManager::GetMonitorOwner
Obtém a instância de [IHostTask](ihosttask-interface.md) que possui o monitor identificado pelo cookie especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cookie`  
 no O cookie associado ao monitor.  
  
 `ppOwnerHostTask`  
 fora Um ponteiro para o `IHostTask` que atualmente possui o monitor ou nulo se nenhuma tarefa tiver propriedade.  
  
## <a name="return-value"></a>Valor Retornado  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner`retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O host normalmente chama `GetMonitorOwner` como parte de um mecanismo de detecção de deadlock. O cookie é associado a um monitor quando ele é criado usando uma chamada para [IHostSyncManager:: CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).  
  
> [!NOTE]
> Uma chamada para liberar o evento subjacente ao monitor pode bloquear — mas não trava — se uma chamada para esse método estiver atualmente em vigor no cookie associado a esse monitor. Outras tarefas também podem bloquear se tentarem adquirir esse monitor.  
  
 `GetMonitorOwner`sempre retorna imediatamente e pode ser chamado a qualquer momento após uma chamada para `CreateMonitorEvent` . O host não precisa aguardar até que uma tarefa esteja aguardando o evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRSyncManager](iclrsyncmanager-interface.md)
- [Interface IHostSyncManager](ihostsyncmanager-interface.md)
