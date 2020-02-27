---
title: Método IHostTaskManager::EnterRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: 94ad0073678e88e15d4b083793dca1423130f7e9
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628066"
---
# <a name="ihosttaskmanagerenterruntime-method"></a>Método IHostTaskManager::EnterRuntime
Notifica o host de que uma chamada para um método não gerenciado, como um método de invocação de plataforma, está retornando o controle de execução para o Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`EnterRuntime` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|{1&gt;E_FAIL&lt;1}|Ocorreu uma falha catastrófica desconhecida. Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
|{1&gt;E_OUTOFMEMORY&lt;1}|Não havia memória suficiente disponível para concluir a alocação solicitada.|  
  
## <a name="remarks"></a>Comentários  
 `EnterRuntime` é chamado para notificar o host de que uma função não gerenciada, para a qual uma chamada anterior para o método [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) foi feita, concluiu a execução e está retornando o controle de execução para o tempo de execução.  
  
> [!NOTE]
> [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) é chamado para notificar o host de que uma função não gerenciada, para a qual uma chamada anterior para `LeaveRuntime` foi feita, está fazendo uma chamada para código gerenciado.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interoperabilidade COM avançada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Como chamar DLLs nativas de código gerenciado usando PInvoke](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Método LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
