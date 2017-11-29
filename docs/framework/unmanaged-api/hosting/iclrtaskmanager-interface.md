---
title: Interface ICLRTaskManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager
helpviewer_keywords: ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3144338ddce262aaa6772f588a4f1a652cc57e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanager-interface"></a>Interface ICLRTaskManager
Fornece métodos que permitem que o host solicitar explicitamente que o common language runtime (CLR) cria uma nova tarefa, obtém a tarefa em execução no momento e definir o idioma geográfico e a cultura para a tarefa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateTask](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Solicita explicitamente que o CLR pode criar um novo [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância.|  
|[Método GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Obtém o `ICLRTask` instância que representa a tarefa que está sendo executado.|  
|[Método GetCurrentTaskType](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Obtém o tipo de tarefa que está em execução atualmente.|  
|[Método SetLocale](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Notifica o CLR que o host tiver modificado o identificador de localidade da tarefa em execução no momento.|  
|[Método SetUILocale](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Notifica o common language runtime que o host tiver modificado o identificador de localidade de interface de usuário da tarefa em execução no momento.|  
  
## <a name="remarks"></a>Comentários  
 Cada tarefa que está em execução em um ambiente hospedado tem as duas representações no lado do host (uma instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) e no lado do CLR (uma instância de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). O host ou o CLR pode iniciar a criação de uma tarefa, mas a representação do lado do host deve ser associada uma representação de CLR lado correspondente para garantir a comunicação bem-sucedida entre o host e o CLR relativas à tarefa. Os dois objetos devem ser criados e instanciados antes de executar código gerenciado em um thread de sistema operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
