---
title: "Enumeração EPolicyAction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EPolicyAction
api_location: mscoree.dll
api_type: COM
f1_keywords: EPolicyAction
helpviewer_keywords: EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f2c3a4138adfa354de07bc6df4e51d7697598b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="epolicyaction-enumeration"></a>Enumeração EPolicyAction
Descreve as ações de política, o host pode ser definido para operações descritas por [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) e falhas descritas por [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`eAbortThread`|Especifica que o common language runtime (CLR) deve anular o thread normalmente. Uma anulação normal inclui tentativas para executar todos os `finally` bloqueia qualquer `catch` blocos relacionados a anulações de thread e finalizadores.|  
|`eDisableRuntime`|Especifica que o CLR deve entrar em um estado desabilitado. Nenhum outro código gerenciado pode ser executado no processo de afetados e threads são impedidos de inserir o CLR.|  
|`eExitProcess`|Especifica que o CLR deve tentar uma saída normal do processo, incluindo a execução de finalizadores e executar operações de registro em log e limpeza.|  
|`eFastExitProcess`|Especifica que o CLR deve sair do processo imediatamente, sem executar finalizadores ou executar limpeza e operações de log. Nowever, a notificação é enviada para o depurador.|  
|`eNoAction`|Especifica que nenhuma ação deve ser executada.|  
|`eRudeAbortThread`|Especifica que o CLR deve realizar uma anulação de thread educado. Somente os `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.|  
|`eRudeExitProcess`|Especifica que o CLR deve sair do processo sem executar finalizadores ou operações de log.|  
|`eRudeUnloadAppDomain`|Especifica que o CLR deve realizar um descarregamento educado do <xref:System.AppDomain>. Finalizadores somente marcado com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados. Da mesma forma, todos os threads com essa <xref:System.AppDomain> em sua pilha receber um `ThreadAbortException`, mas somente aqueles `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.|  
|`eThrowException`|Especifica que uma exceção apropriada para a condição, como falta de memória, estouro de buffer e assim por diante, deverá ser lançada.|  
|`eUnloadAppDomain`|Especifica que o <xref:System.AppDomain> deve ser descarregado. O CLR tentará executar finalizadores.|  
  
## <a name="remarks"></a>Comentários  
 O host define as ações de política chamando métodos do [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface. Para obter informações sobre anulações educadas e normais, consulte o [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [Interface IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
