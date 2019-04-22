---
title: Interface IHostTask
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081496"
---
# <a name="ihosttask-interface"></a>Interface IHostTask
Fornece métodos que permitem que o common language runtime (CLR) para se comunicar com o host para gerenciar tarefas.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Solicitações que o host ativar a tarefa representada por atual `IHostTask` da instância, portanto, a tarefa pode ser anulada.|  
|[Método GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Obtém o nível de prioridade do thread da tarefa representada por atual `IHostTask` instância.|  
|[Método Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Bloqueia a tarefa de chamada até que a tarefa representada por atual `IHostTask` instância é concluída, o intervalo de tempo especificado tenha decorrido, ou [ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) é chamado.|  
|[Método SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Associa um [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância com o atual `IHostTask` instância.|  
|[Método SetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Solicitações que o host de ajustar a prioridade do thread de nível para a tarefa representada por atual `IHostTask` instância.|  
|[Método Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Solicitações que o host de move a tarefa representada por atual `IHostTask` instância de um estado suspenso para um estado ativo, no qual o código pode ser executado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR chama os métodos definidos pela `IHostTask` para iniciar uma tarefa, defina sua prioridade de thread, nível, e assim por diante.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
