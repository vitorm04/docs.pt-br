---
title: Enumeração EPolicyAction
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80a0e8d37e834ea0a7623517e2e1228a79d9ea10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655706"
---
# <a name="epolicyaction-enumeration"></a>Enumeração EPolicyAction
Descreve as ações de política, o host pode ser definido para operações descritas pelo [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) e as falhas descritas pelo [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
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
|`eAbortThread`|Especifica que o common language runtime (CLR) deve anular o thread normalmente. Uma anulação normal inclui tentativas de executar todos `finally` bloqueia qualquer `catch` blocos relacionados a anulações de thread e finalizadores.|  
|`eDisableRuntime`|Especifica que o CLR deve entrar em um estado desabilitado. Nenhum outro código gerenciado pode ser executado no processo afetado e threads são bloqueados de inserir o CLR.|  
|`eExitProcess`|Especifica que o CLR deve tentar uma saída normal do processo, incluindo a execução de finalizadores e operações de registro em log e limpeza.|  
|`eFastExitProcess`|Especifica que o CLR deve sair do processo imediatamente, sem execução dos finalizadores ou executar a limpeza e operações de registro em log. Nowever, a notificação é enviada para o depurador.|  
|`eNoAction`|Especifica que nenhuma ação deve ser executada.|  
|`eRudeAbortThread`|Especifica que o CLR deve realizar uma anulação de thread rude. Somente aqueles `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executadas.|  
|`eRudeExitProcess`|Especifica que o CLR deve sair do processo sem execução dos finalizadores ou operações de registro em log.|  
|`eRudeUnloadAppDomain`|Especifica que o CLR deve realizar um descarregamento de rude do <xref:System.AppDomain>. Os finalizadores apenas marcado com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executadas. Da mesma forma, todos os threads com essa <xref:System.AppDomain> em sua pilha recebem um `ThreadAbortException`, mas somente os `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executadas.|  
|`eThrowException`|Especifica que uma exceção apropriada para a condição, como falta de memória, o estouro de buffer e assim por diante, deve ser gerada.|  
|`eUnloadAppDomain`|Especifica que o <xref:System.AppDomain> deve ser descarregada. O CLR tenta executar os finalizadores.|  
  
## <a name="remarks"></a>Comentários  
 O host define as ações da política chamando métodos das [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface. Para obter informações sobre as anulações rudes e normais, consulte o [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [Interface IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
