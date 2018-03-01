---
title: "Método ICLRSyncManager::GetMonitorOwner"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b998a26056aec739587b77c1b1b39f0e9392a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>Método ICLRSyncManager::GetMonitorOwner
Obtém o [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que possui o monitor identificado pelo cookie especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cookie`  
 [in] O cookie associado ao monitor.  
  
 `ppOwnerHostTask`  
 [out] Um ponteiro para o `IHostTask` que atualmente possui o monitor ou nulo se nenhuma tarefa tem a propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O host normalmente chama `GetMonitorOwner` como parte de um mecanismo de detecção de deadlock. O cookie é associado um monitor quando ela é criada usando uma chamada para [Ihostsyncmanager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).  
  
> [!NOTE]
>  Pode impedir que uma chamada para liberar o evento subjacente do monitor — mas não será bloqueada, se uma chamada para esse método está atualmente em vigor no cookie associado a esse monitor. Outras tarefas também podem bloquear se tentar adquirir o monitor.  
  
 `GetMonitorOwner`sempre retorna imediatamente e pode ser chamado a qualquer momento após uma chamada para `CreateMonitorEvent`. O host não precisa esperar até que uma tarefa está aguardando o evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
