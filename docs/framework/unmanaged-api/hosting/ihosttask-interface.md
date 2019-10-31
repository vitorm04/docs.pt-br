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
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121388"
---
# <a name="ihosttask-interface"></a>Interface IHostTask
Fornece métodos que permitem que o Common Language Runtime (CLR) se comunique com o host para gerenciar tarefas.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Solicita que o host ative a tarefa representada pela instância de `IHostTask` atual, para que a tarefa possa ser anulada.|  
|[Método GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Obtém o nível de prioridade de thread da tarefa representada pela instância de `IHostTask` atual.|  
|[Método Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Bloqueia a tarefa de chamada até que a tarefa representada pela instância de `IHostTask` atual seja concluída, o intervalo de tempo especificado decorre ou [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) seja chamado.|  
|[Método SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Associa uma instância de [interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) com a instância de `IHostTask` atual.|  
|[Método SetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Solicita que o host ajuste o nível de prioridade de thread para a tarefa representada pela instância de `IHostTask` atual.|  
|[Método Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Solicita que o host mova a tarefa representada pela instância de `IHostTask` atual de um estado suspenso para um estado ativo, no qual o código pode ser executado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR chama os métodos definidos por `IHostTask` para iniciar uma tarefa, definir seu nível de prioridade de thread e assim por diante.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
