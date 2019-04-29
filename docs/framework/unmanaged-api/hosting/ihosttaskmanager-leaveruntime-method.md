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
ms.openlocfilehash: 81da8052b79047933b4afc6d5686029465d83eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796689"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>Método IHostTaskManager::LeaveRuntime
Notifica o host que a tarefa atualmente em execução está prestes a deixar o common language runtime (CLR) e insira o código não gerenciado.  
  
> [!IMPORTANT]
>  Uma chamada correspondente para [ihosttaskmanager:: Enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifica o host que a tarefa em execução no momento é reinserção de código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `target`  
 [in] O endereço dentro do arquivo executável portátil mapeado da função não gerenciada a ser chamado.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não há memória suficiente está disponível para concluir a alocação solicitada.|  
  
## <a name="remarks"></a>Comentários  
 Sequências de chamada de código não gerenciado e podem ser aninhadas. Por exemplo, a lista a seguir descreve uma situação hipotética em que a sequência de chamadas para `LeaveRuntime`, [ihosttaskmanager:: Reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [ihosttaskmanager:: Reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), e `IHostTaskManager::EnterRuntime` permite que o host identificar as camadas aninhadas.  
  
|Ação|Chamada de método correspondente|  
|------------|-------------------------------|  
|Invocação de uma função não gerenciada, escrita em C usando a plataforma um chamadas executável gerenciado do Visual Basic.|`IHostTaskManager::LeaveRuntime`|  
|A função C não gerenciada chama um método em uma DLL gerenciada escrita em C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Gerenciado C# função chama outra função não gerenciada escrita em C, também usando invocação de plataforma.|`IHostTaskManager::LeaveRuntime`|  
|A segunda função não gerenciada retorna a execução para o C# função.|`IHostTaskManager::EnterRuntime`|  
|O C# função retorna a execução para a primeira função não gerenciada.|`IHostTaskManager::ReverseLeaveRuntime`|  
|A primeira função não gerenciada retorna a execução para o programa em Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
