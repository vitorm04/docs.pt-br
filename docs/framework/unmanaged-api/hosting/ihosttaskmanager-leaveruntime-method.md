---
title: "Método IHostTaskManager::LeaveRuntime"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4c168cffba44a21d6705e8abd921ecbf8a9da6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>Método IHostTaskManager::LeaveRuntime
Notifica o host que a tarefa em execução no momento está prestes a deixar o common language runtime (CLR) e insira o código não gerenciado.  
  
> [!IMPORTANT]
>  Uma chamada correspondente para [Enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifica o host que a tarefa em execução no momento é precisar reinserir o código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `target`  
 [in] O endereço dentro do arquivo executável portátil mapeado de função não gerenciada a ser chamado.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não há memória suficiente está disponível para concluir a alocação solicitada.|  
  
## <a name="remarks"></a>Comentários  
 Sequências de chamada de código não gerenciado e podem ser aninhadas. Por exemplo, a lista a seguir descreve uma situação hipotética no qual a sequência de chamadas para `LeaveRuntime`, [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), e `IHostTaskManager::EnterRuntime` permite que o host identificar as camadas aninhadas.  
  
|Ação|Chamada de método correspondente|  
|------------|-------------------------------|  
|Invocação de uma função não gerenciada, escrita em C usando a plataforma um chamadas executável gerenciado do Visual Basic.|`IHostTaskManager::LeaveRuntime`|  
|A função não gerenciada de C chama um método em uma DLL gerenciada, escrita em c#.|`IHostTaskManager::ReverseEnterRuntime`|  
|A função c# gerenciada chama outra função não gerenciada, escrita em C, também usando invocação de plataforma.|`IHostTaskManager::LeaveRuntime`|  
|A segunda função não gerenciada retorna a execução para a função c#.|`IHostTaskManager::EnterRuntime`|  
|A função c# retorna a execução para a primeira função não gerenciada.|`IHostTaskManager::ReverseLeaveRuntime`|  
|A função não gerenciada primeiro retorna a execução para o programa do Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
