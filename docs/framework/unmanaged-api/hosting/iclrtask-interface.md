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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1baeac5db41aa64380d694ebab5419229d8adb4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088192"
---
# <a name="iclrtask-interface"></a>Interface ICLRTask
Fornece métodos que permitem que o host para fazer solicitações do common language runtime (CLR), ou para fornecer uma notificação para o CLR sobre a tarefa associada.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Abort](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Solicitações que o CLR anular a tarefa que atual `ICLRTask` instância representa.|  
|[Método ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Notifica o CLR que a tarefa associada com o atual `ICLRTask` instância está terminando e tenta desligar a tarefa normalmente.|  
|[Método GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Obtém informações estatísticas sobre o uso de recursos de memória pela tarefa representada por atual `ICLRTask` instância.|  
|[Método LocksHeld](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Obtém o número de bloqueios atualmente mantidos na tarefa.|  
|[Método NeedsPriorityScheduling](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Obtém um valor que indica se o host deve atribuir uma prioridade alta para reagendamento da tarefa representada pela atual `ICLRTask` instância.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informa ao CLR que o host tiver concluído uma tarefa e permite que o CLR reutilizar atual `ICLRTask` instância para representar outra tarefa.|  
|[Método RudeAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Faz com que o CLR anular a tarefa representada por atual `ICLRTask` instância imediatamente, sem uma garantia de que os finalizadores serão executados.|  
|[Método SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Define um identificador exclusivo para a tarefa representada por atual `ICLRTask` instância, para uso na depuração.|  
|[Método SwitchIn](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Notifica o CLR que a tarefa representada por atual `ICLRTask` instância está em um estado operacional.|  
|[Método SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Notifica o CLR que a tarefa representada por atual `ICLRTask` instância não está mais em um estado operacional.|  
|[Método YieldTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Solicita que o tempo de processador do CLR faça disponível para outras tarefas. O CLR não faz nenhuma garantia de que a tarefa será colocada em um estado em que ele pode gerar um tempo de processamento.|  
  
## <a name="remarks"></a>Comentários  
 Um `ICLRTask` é a representação de uma tarefa para o CLR. Em qualquer momento durante a execução de código, uma tarefa pode ser descrita como em execução ou aguardando para serem executados. O host chama o `ICLRTask::SwitchIn` método para notificar o CLR que a tarefa que atual `ICLRTask` instância representa agora está em um estado operacional. Após uma chamada para `ICLRTask::SwitchIn`, o host pode agendar a tarefa em qualquer thread de sistema operacional, exceto em casos em que o tempo de execução requer afinidade de thread, conforme especificado por chamadas para o [ihosttaskmanager:: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) e [Ihosttaskmanager:: EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) métodos. Algum tempo depois, o sistema operacional pode decidir remover a tarefa do thread e colocá-lo em um estado não-execução. Por exemplo, isso pode ocorrer sempre que a tarefa bloqueia em primitivos de sincronização, ou aguarda a conclusão das operações de e/s. O host chama [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) para notificar o CLR que a tarefa representada por atual `ICLRTask` instância não está mais em um estado operacional.  
  
 Normalmente, uma tarefa termina no final da execução do código. Nesse momento, o host chama `ICLRTask::ExitTask` destruir associado `ICLRTask`. No entanto, as tarefas também podem ser recicladas por meio de uma chamada para `ICLRTask::Reset`, que permite que o `ICLRTask` instância a ser usada novamente. Essa abordagem evita a sobrecarga de criação e destruição de instâncias de repetidamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Interface ICLRTask2](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
