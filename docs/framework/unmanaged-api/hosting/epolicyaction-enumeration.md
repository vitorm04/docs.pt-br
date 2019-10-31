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
ms.openlocfilehash: eaba6b2166a82cfe825ffb98db515e24d4656462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138226"
---
# <a name="epolicyaction-enumeration"></a>Enumeração EPolicyAction
Descreve as ações de política que o host pode definir para operações descritas por [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) e falhas descritas por [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`eAbortThread`|Especifica que o Common Language Runtime (CLR) deve abortar o thread normalmente. Uma anulação normal inclui tentativas de executar todos os blocos de `finally`, quaisquer blocos de `catch` relacionados a anulações de thread e finalizadores.|  
|`eDisableRuntime`|Especifica que o CLR deve entrar em um estado desabilitado. Nenhum código gerenciado adicional pode ser executado no processo afetado e os threads são impedidos de entrar no CLR.|  
|`eExitProcess`|Especifica que o CLR deve tentar uma saída normal do processo, incluindo a execução de finalizadores e a execução de operações de limpeza e registro em log.|  
|`eFastExitProcess`|Especifica que o CLR deve sair do processo imediatamente, sem executar finalizadores ou executar operações de limpeza e registro em log. No entanto, a notificação é enviada ao depurador.|  
|`eNoAction`|Especifica que nenhuma ação deve ser executada.|  
|`eRudeAbortThread`|Especifica que o CLR deve executar uma anulação de thread rude. Somente os blocos `catch` e `finally` marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.|  
|`eRudeExitProcess`|Especifica que o CLR deve sair do processo sem executar finalizadores ou operações de registro em log.|  
|`eRudeUnloadAppDomain`|Especifica que o CLR deve executar um descarregamento rude do <xref:System.AppDomain>. Somente finalizadores marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados. Da mesma forma, todos os threads com esse <xref:System.AppDomain> em sua pilha recebem um `ThreadAbortException`, mas somente os blocos `catch` e `finally` marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.|  
|`eThrowException`|Especifica que uma exceção apropriada para a condição, como memória insuficiente, estouro de buffer e assim por diante, deve ser lançada.|  
|`eUnloadAppDomain`|Especifica que o <xref:System.AppDomain> deve ser descarregado. O CLR tenta executar finalizadores.|  
  
## <a name="remarks"></a>Comentários  
 O host define as ações de política chamando métodos da interface [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) . Para obter informações sobre anulações rudes e normais, consulte a enumeração [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [Interface IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
