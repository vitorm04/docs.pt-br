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
ms.openlocfilehash: df1fb24c4003f77523ef01a4029fd19cc55a3fef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttask-interface"></a>Interface IHostTask
Fornece métodos que permitem que o common language runtime (CLR) para se comunicar com o host para gerenciar as tarefas.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Solicitações que o host de ativação da tarefa representada pela atual `IHostTask` instância, para que a tarefa pode ser anulada.|  
|[Método GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Obtém o nível de prioridade de thread da tarefa representada por atual `IHostTask` instância.|  
|[Método Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Bloqueia a tarefa chamada até que a tarefa representada por atual `IHostTask` instância for concluída, o intervalo de tempo especificado expira, ou [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) é chamado.|  
|[Método SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Associa um [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância com a atual `IHostTask` instância.|  
|[Método SetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Nível de solicitações que o host de ajustar a prioridade de thread para a tarefa representada por atual `IHostTask` instância.|  
|[Método Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|O host de move a tarefa representada por atual de solicitações `IHostTask` instância de um estado suspenso para um estado ativo, no qual o código pode ser executado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR chama métodos definidos pelo `IHostTask` para iniciar uma tarefa, defina a prioridade de thread nível, e assim por diante.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
