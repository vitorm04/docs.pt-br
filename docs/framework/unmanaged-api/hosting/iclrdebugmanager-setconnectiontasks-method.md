---
title: Método ICLRDebugManager::SetConnectionTasks
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85db4247ebe4a488f7907e195bb0f25f72d87e9b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951358"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>Método ICLRDebugManager::SetConnectionTasks
Associa uma lista de instâncias [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) com um identificador e um nome amigável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `id`  
 no O identificador específico do host para a conexão com a qual associar a `ppCLRTask` matriz.  
  
 `dwCount`  
 no O número de membros de `ppCLRTask`. Esse número deve ser maior que zero.  
  
 `ppCLRTask`  
 no Uma matriz de `ICLRTask` ponteiros para associar à conexão identificada `id`pelo. Essa matriz deve conter pelo menos um membro.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks`retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|A [beginconnectização](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) não foi chamada usando esse valor de `id`, `dwCount` ou ou `id` é zero, ou um dos elementos de `ppCLRTask` é nulo.|  
  
## <a name="remarks"></a>Comentários  
 O [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornece três métodos `BeginConnection`, `SetConnectionTasks`, e [EndConnect](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), para associar listas de tarefas com identificadores e nomes amigáveis.  
  
> [!IMPORTANT]
> Esses três métodos devem ser chamados em uma ordem específica para cada conjunto de tarefas. `BeginConnection`é chamado primeiro para estabelecer uma nova conexão. `SetConnectionTasks`é chamado ao lado de fornecer o conjunto de tarefas a ser associado a essa conexão. `EndConnection`é chamado por último para remover a associação entre a lista de tarefas e o identificador e o nome amigável. No entanto, as chamadas para diferentes conexões podem ser aninhadas.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Interface ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [Método BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [Método EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [Interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
