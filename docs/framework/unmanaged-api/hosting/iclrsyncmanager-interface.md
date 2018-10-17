---
title: Interface ICLRSyncManager
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21295268ba5c230062fadddc9c61217f3574551b
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49370975"
---
# <a name="iclrsyncmanager-interface"></a>Interface ICLRSyncManager
Define métodos que permitem que o host para obter informações sobre tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)|Solicita que o common language runtime (CLR) cria um iterador para o host a usar para determinar o conjunto de tarefas aguardando um bloqueio de leitor-gravador.|  
|[Método DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md)|Solicita que o CLR destrua um iterador que foi criado por uma chamada para `CreateRWLockOwnerIterator`.|  
|[Método GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md)|Obtém a tarefa que possui o monitor especificado.|  
|[Método GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md)|Obtém a próxima tarefa está aguardando o bloqueio de leitor-gravador atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** mscoree. H  
  
 **Biblioteca:** incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread>  
 [Interface IHostSyncManager](ihostsyncmanager-interface.md)  
 [Threading gerenciado e não gerenciado](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))  
 [Hospedagem de Interfaces](hosting-interfaces.md)
