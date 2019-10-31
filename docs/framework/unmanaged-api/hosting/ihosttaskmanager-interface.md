---
title: Interface IHostTaskManager
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: 470e2ac06f433dc12d66f6cac97337a6de1d8183
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133014"
---
# <a name="ihosttaskmanager-interface"></a>Interface IHostTaskManager
Fornece métodos que permitem que o Common Language Runtime (CLR) trabalhe com tarefas por meio do host em vez de usar as funções de fibra ou de Threading do sistema operacional padrão.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Notifica o host de que o código gerenciado está entrando em um período no qual a tarefa atual não deve ser anulada.|  
|[Método BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Notifica o host de que o código gerenciado está entrando em um período no qual a tarefa atual não deve ser movida para outro thread do sistema operacional.|  
|[Método CallNeedsHostHook](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Permite que o host especifique se o Common Language Runtime pode embutir a chamada especificada para uma função não gerenciada.|  
|[Método CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|Solicita que o host crie uma nova tarefa.|  
|[Método EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Notifica o host de que o código gerenciado está saindo do período em que a tarefa atual não deve ser anulada, seguindo uma chamada anterior para `BeginDelayAbort`.|  
|[Método EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Notifica o host de que o código gerenciado está saindo do período no qual a tarefa atual não deve ser movida para outro thread do sistema operacional, seguindo uma chamada anterior para `BeginThreadAffinity`.|  
|[Método EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Notifica o host de que uma chamada para um método não gerenciado, como um método de invocação de plataforma, está retornando o controle de execução para o CLR.|  
|[Método GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Obtém um ponteiro de interface para a tarefa que está atualmente em execução no thread do sistema operacional do qual essa chamada é feita.|  
|[Método GetStackGuarantee](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Obtém a quantidade de espaço de pilha que tem garantia de disponibilidade após a conclusão de uma operação de pilha, mas antes do fechamento de um processo.|  
|[Método LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Notifica o host que o código gerenciado está prestes a fazer uma chamada para uma função não gerenciada.|  
|[Método ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Notifica o host de que uma chamada está sendo feita no Common Language Runtime (CLR) de código não gerenciado.|  
|[Método ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Notifica o host que o controle está deixando o CLR e inserindo uma função não gerenciada que, por sua vez, foi chamada a partir do código gerenciado.|  
|[Método SetCLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Fornece ao host um ponteiro de interface para uma instância [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) implementada pelo CLR.|  
|[Método SetLocale](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Notifica o host de que o CLR alterou a localidade na tarefa atual.|  
|[Método SetStackGuarantee](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Reservado apenas para uso interno.|  
|[Método SetUILocale](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Notifica o host de que a localidade da interface do usuário foi alterada na tarefa atual.|  
|[Método Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Notifica o host que a tarefa atual vai suspender.|  
|[Método SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Notifica o host de que ele deve desativar a tarefa atual.|  
  
## <a name="remarks"></a>Comentários  
 `IHostTaskManager` permite que o CLR crie e gerencie tarefas, para fornecer ganchos para que o host execute uma ação quando o controle transfere do código gerenciado para o não gerenciado e vice-versa, e para especificar determinadas ações que o host pode e não pode executar durante a execução do código.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
