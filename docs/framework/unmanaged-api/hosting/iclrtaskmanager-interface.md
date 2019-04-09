---
title: Interface ICLRTaskManager
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ef7cb78791496de76e5741f8254ee88563c776
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134648"
---
# <a name="iclrtaskmanager-interface"></a>Interface ICLRTaskManager
Fornece métodos que permitem que o host para solicitar explicitamente que o common language runtime (CLR), crie uma nova tarefa obtém a tarefa em execução no momento e definir o idioma geográfico e a cultura para a tarefa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateTask](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Solicita explicitamente que o CLR cria um novo [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância.|  
|[Método GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Obtém o `ICLRTask` instância que representa a tarefa que está sendo executado.|  
|[Método GetCurrentTaskType](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Obtém o tipo da tarefa que está sendo executado.|  
|[Método SetLocale](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Notifica o CLR que o host tiver modificado o identificador de localidade da tarefa em execução no momento.|  
|[Método SetUILocale](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Notifica o common language runtime que o host tiver modificado o identificador de localidade de interface do usuário da tarefa em execução no momento.|  
  
## <a name="remarks"></a>Comentários  
 Cada tarefa que está em execução em um ambiente hospedado tem as duas representações no lado do host (uma instância do [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) e no lado do CLR (uma instância do [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). O host ou o CLR pode iniciar a criação de uma tarefa, mas a representação do lado do host deve ser associada uma representação de CLR lado correspondente para garantir uma comunicação bem-sucedida entre o host e o CLR relativas à tarefa. Os dois objetos devem ser criados e instanciados antes de executar código gerenciado em um thread de sistema operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
