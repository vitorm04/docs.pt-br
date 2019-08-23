---
title: Método IHostTaskManager::LeaveRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b2e8e636915b3921fcd727fc78a3fb18fc69104
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959037"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>Método IHostTaskManager::LeaveRuntime
Notifica o host de que a tarefa em execução no momento está prestes a sair do Common Language Runtime (CLR) e inserir código não gerenciado.  
  
> [!IMPORTANT]
> Uma chamada correspondente para [IHostTaskManager:: EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifica o host que a tarefa em execução no momento está reinserindo o código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `target`  
 no O endereço dentro do arquivo executável portátil mapeado da função não gerenciada a ser chamada.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime`retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não há memória suficiente disponível para concluir a alocação solicitada.|  
  
## <a name="remarks"></a>Comentários  
 Seqüências de chamadas de e para código não gerenciado podem ser aninhadas. Por exemplo, a lista a seguir descreve uma situação hipotética na qual a sequência de chamadas para `LeaveRuntime`, [IHostTaskManager:: ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)e `IHostTaskManager::EnterRuntime` permite que o host Identifique as camadas aninhadas.  
  
|Ação|Chamada de método correspondente|  
|------------|-------------------------------|  
|Um executável gerenciado Visual Basic chama uma função não gerenciada escrita em C usando a invocação de plataforma.|`IHostTaskManager::LeaveRuntime`|  
|A função C não gerenciada chama um método em uma DLL gerenciada gravada no C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|A função C# gerenciada chama outra função não gerenciada escrita em C, também usando a invocação de plataforma.|`IHostTaskManager::LeaveRuntime`|  
|A segunda função não gerenciada retorna a execução para C# a função.|`IHostTaskManager::EnterRuntime`|  
|A C# função retorna a execução para a primeira função não gerenciada.|`IHostTaskManager::ReverseLeaveRuntime`|  
|A primeira função não gerenciada retorna a execução para o programa de Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
