---
title: Interface ICLRDebugManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e537b955524f2721868ddf5da9fccf68f9d4efd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanager-interface"></a>Interface ICLRDebugManager
Fornece métodos que permitem que um host associar um conjunto de tarefas com um identificador e um nome amigável.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Estabelece uma nova conexão entre o host e o depurador para associar tarefas com um identificador e um nome amigável.|  
|[Método EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.|  
|[Método GetDacl](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Este método não está implementado.|  
|[Método IsDebuggerAttached](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Obtém um valor que indica se um depurador está anexado ao processo.|  
|[Método SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Associa uma lista de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instâncias com um identificador e um nome amigável.|  
|[Método SetDacl](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Este método não está implementado.|  
|[Método SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Define a política para a leitura de arquivos do programa (PDB) de banco de dados. A política determina se as informações sobre números de linha e de arquivos estão incluídas em pilhas de chamadas.|  
  
## <a name="remarks"></a>Comentários  
 Em cenários de depuração, um host pode querer agrupar tarefas de acordo com sua própria lógica de programação. Por exemplo, um agrupamento permitiria que um desenvolvedor ver somente as tarefas necessárias por APIs do desenvolvedor, ao invés de fazer todas as tarefas em execução no processo. `ICLRDebugManager`permite que o host implementar esse tipo de agrupamento.  
  
> [!IMPORTANT]
>  Três `ICLRDebugManager` métodos, `BeginConnection`, `SetConnectionTasks` e `EndConnection`, são dependentes entre si. Ele devem ser chamados na ordem fornecida para funcionar como esperado.  
  
 O agrupamento e os identificadores e nomes amigáveis que atribui o host para o agrupamento não têm significado para o common language runtime (CLR). O CLR simplesmente passa as informações ao longo do depurador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
