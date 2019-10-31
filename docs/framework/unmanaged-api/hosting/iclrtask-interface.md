---
title: Interface ICLRTask
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
ms.openlocfilehash: c4f27a73022b0495b2772c0485c14a1b007dc883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132641"
---
# <a name="iclrtask-interface"></a>Interface ICLRTask
Fornece métodos que permitem ao host fazer solicitações do Common Language Runtime (CLR) ou fornecer notificação ao CLR sobre a tarefa associada.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Abort](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Solicita que o CLR anule a tarefa que a instância de `ICLRTask` atual representa.|  
|[Método ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Notifica o CLR que a tarefa associada à instância de `ICLRTask` atual está terminando e tenta desligar a tarefa normalmente.|  
|[Método GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Obtém informações estatísticas sobre o uso de recursos de memória pela tarefa representada pela instância de `ICLRTask` atual.|  
|[Método LocksHeld](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Obtém o número de bloqueios atualmente mantidos na tarefa.|  
|[Método NeedsPriorityScheduling](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Obtém um valor que indica se o host deve atribuir uma prioridade alta para reagendar a tarefa representada pela instância de `ICLRTask` atual.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informa ao CLR que o host concluiu uma tarefa e permite que o CLR reutilize a instância de `ICLRTask` atual para representar outra tarefa.|  
|[Método RudeAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Faz com que o CLR anule a tarefa representada pela instância de `ICLRTask` atual imediatamente, sem uma garantia de que os finalizadores serão executados.|  
|[Método SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Define um identificador exclusivo para a tarefa representada pela instância de `ICLRTask` atual, para uso na depuração.|  
|[Método SwitchIn](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Notifica o CLR que a tarefa representada pela instância de `ICLRTask` atual está em um estado operável.|  
|[Método SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Notifica o CLR que a tarefa representada pela instância de `ICLRTask` atual não está mais em um estado operável.|  
|[Método YieldTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Solicita que o CLR torne o tempo do processador disponível para outras tarefas. O CLR não garante que a tarefa seja colocada em um estado em que possa gerar o tempo de processamento.|  
  
## <a name="remarks"></a>Comentários  
 Uma `ICLRTask` é a representação de uma tarefa para o CLR. A qualquer momento durante a execução de código, uma tarefa pode ser descrita como em execução ou aguardando para ser executada. O host chama o método `ICLRTask::SwitchIn` para notificar o CLR que a tarefa que a instância `ICLRTask` atual representa agora está em um estado operável. Após uma chamada para `ICLRTask::SwitchIn`, o host pode agendar a tarefa em qualquer thread do sistema operacional, exceto nos casos em que o tempo de execução requer afinidade de thread, conforme especificado por chamadas para [IHostTaskManager:: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) e [IHostTaskManager:: Métodos EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) . Algum tempo depois, o sistema operacional pode decidir remover a tarefa do thread e colocá-la em um estado de não execução. Por exemplo, isso pode ocorrer sempre que a tarefa é bloqueada em primitivos de sincronização ou aguarda a conclusão de operações de e/s. O host chama o [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) para notificar o CLR que a tarefa representada pela instância de `ICLRTask` atual não está mais em um estado operável.  
  
 Normalmente, uma tarefa é encerrada no final da execução do código. Nesse momento, o host chama `ICLRTask::ExitTask` para destruir o `ICLRTask`associado. No entanto, as tarefas também podem ser recicladas usando uma chamada para `ICLRTask::Reset`, o que permite que a instância de `ICLRTask` seja usada novamente. Essa abordagem impede a sobrecarga de criar e destruir instâncias repetidamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Interface ICLRTask2](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
