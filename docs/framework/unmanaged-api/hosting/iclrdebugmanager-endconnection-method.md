---
title: Método ICLRDebugManager::EndConnection
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2af6970907eb9895750ca58065b2e0cb735cea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969404"
---
# <a name="iclrdebugmanagerendconnection-method"></a>Método ICLRDebugManager::EndConnection
Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwConnectionId`  
 no O identificador específico do host para a conexão e a lista associada de tarefas de Common Language Runtime (CLR).  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`EndConnection`retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|A [beginconnectização](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nunca foi chamada `dwConnectionId`de using `dwConnectionId` ou era zero.|  
  
## <a name="remarks"></a>Comentários  
 O [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornece três métodos `BeginConnection`,, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), `EndConnection`e, para associar listas de tarefas com identificadores e nomes amigáveis.  
  
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
- [Método SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [Interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
