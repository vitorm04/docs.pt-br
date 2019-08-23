---
title: Interface ICLRDebugManager
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a408995793caf879f8d5624ab727102c4859195
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959610"
---
# <a name="iclrdebugmanager-interface"></a>Interface ICLRDebugManager
Fornece métodos que permitem que um host associe um conjunto de tarefas a um identificador e um nome amigável.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Estabelece uma nova conexão entre o host e o depurador para associar tarefas a um identificador e um nome amigável.|  
|[Método EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.|  
|[Método GetDacl](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Este método não está implementado.|  
|[Método IsDebuggerAttached](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Obtém um valor que indica se um depurador está anexado ao processo.|  
|[Método SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Associa uma lista de instâncias [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) com um identificador e um nome amigável.|  
|[Método SetDacl](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Este método não está implementado.|  
|[Método SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Define a política para ler arquivos de banco de dados do programa (PDB). A política determina se as informações sobre números de linha e arquivos estão incluídas em pilhas de chamadas.|  
  
## <a name="remarks"></a>Comentários  
 Em cenários de depuração, um host pode querer agrupar tarefas de acordo com sua própria lógica de programação. Por exemplo, um agrupamento permitiria que um desenvolvedor vêsse apenas as tarefas exigidas pelas APIs do desenvolvedor, em vez de ver cada tarefa em execução no processo. `ICLRDebugManager`permite que o host implemente esse tipo de agrupamento.  
  
> [!IMPORTANT]
> Três `ICLRDebugManager` métodos `BeginConnection` ,e`EndConnection`,dependem uns dos outros. `SetConnectionTasks` Eles devem ser chamados na ordem especificada para funcionar conforme o esperado.  
  
 O agrupamento e os identificadores e nomes amigáveis que o host atribui ao agrupamento não têm significado para o Common Language Runtime (CLR). O CLR simplesmente passa as informações ao depurador.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
