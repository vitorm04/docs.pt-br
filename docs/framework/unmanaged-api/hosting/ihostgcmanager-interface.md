---
title: Interface IHostGCManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager
helpviewer_keywords: IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0927b236af094b964261a9b2a49a33d1ea2b9391
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanager-interface"></a>Interface IHostGCManager
Fornece métodos que notificam o host de eventos no mecanismo de coleta de lixo implementado pelo common language runtime (CLR).  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|[Método SuspensionEnding](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|Notifica o host que o CLR está continuando a execução de tarefas em threads que foi suspenso para uma coleta de lixo.|  
|[Método SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|Notifica o host que o CLR é suspender a execução de tarefas para executar uma coleta de lixo.|  
|[Método ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|Notifica o host que o thread do qual foi feita a chamada do método está prestes a bloquear uma coleta de lixo.|  
  
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
 [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
