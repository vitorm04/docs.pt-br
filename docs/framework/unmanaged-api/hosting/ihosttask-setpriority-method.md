---
title: Método IHostTask::SetPriority
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5382341a8c0c6455438af9e8c476348ab2467a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189034"
---
# <a name="ihosttasksetpriority-method"></a>Método IHostTask::SetPriority
Solicitações que o host de ajustar a prioridade do thread de nível para a tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `newPriority`  
 [in] Um inteiro que representa o valor de prioridade de thread solicitada para a tarefa representada por atual `IHostTask` instância.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetPriority` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 Threads de processamento são concedidas tempo usando um sistema de rodízio parcialmente com base no nível de prioridade do thread. `SetPriority` permite que o CLR definir esse nível de prioridade de thread para a tarefa atual. O seguinte `newPriority` valores têm suporte.  
  
-   THREAD_PRIORITY_ABOVE_NORMAL  
  
-   THREAD_PRIORITY_BELOW_NORMAL  
  
-   THREAD_PRIORITY_HIGHEST  
  
-   THREAD_PRIORITY_IDLE  
  
-   THREAD_PRIORITY_LOWEST  
  
-   THREAD_PRIORITY_NORMAL  
  
-   THREAD_PRIORITY_TIME_CRITICAL  
  
 O CLR chama `SetPriority` quando o valor da <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> é modificado pelo código do usuário. Um host pode definir seus próprios algoritmos para atribuição de prioridade de thread e está livre para ignorar essa solicitação.  
  
> [!NOTE]
>  `SetPriority` não relata se o nível de prioridade de thread foi alterado. Chame [ihosttask:: Getpriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) para determinar o valor do nível de prioridade do thread da tarefa.  
  
 Valores de nível de prioridade de thread são definidos pelo Win32 `SetThreadPriority` função. Para obter mais informações sobre a prioridade de thread, consulte a documentação da plataforma Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading.Thread>
- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Método GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
