---
title: Interface ICLRSyncManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager
helpviewer_keywords: ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e47f02a5a84b909b03c6be4e0a43c7166a1ddc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanager-interface"></a>Interface ICLRSyncManager
Define métodos que permitem que o host para obter informações sobre tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|Solicita que o common language runtime (CLR) criar um iterador para o host a ser usado para determinar o conjunto de tarefas que esperam por um bloqueio de leitor / gravador.|  
|[Método DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|Solicita que o CLR destruir um iterador que foi criado por uma chamada para `CreateRWLockOwnerIterator`.|  
|[Método GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|Obtém a tarefa que tem o monitor de especificados.|  
|[Método GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|Obtém a próxima tarefa está aguardando o bloqueio de leitor-gravador atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread>  
 [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Threading gerenciado e não gerenciado](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
