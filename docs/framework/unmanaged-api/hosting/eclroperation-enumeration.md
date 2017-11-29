---
title: "Enumeração EClrOperation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrOperation
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrOperation
helpviewer_keywords: EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 65822c74fbbac1dccef74c976ade8ba8d38c167c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="eclroperation-enumeration"></a>Enumeração EClrOperation
Descreve o conjunto de operações para o qual um host pode aplicar as ações de política.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|O host pode especificar ações de política a ser tomada quando um <xref:System.AppDomain> é descarregado de maneira não normal (educada).|  
|`OPR_AppDomainUnload`|O host pode especificar ações de política a ser tomada quando um <xref:System.AppDomain> é descarregado.|  
|`OPR_FinalizerRun`|O host pode especificar ações de política a ser tomada quando executar finalizadores.|  
|`OPR_ProcessExit`|O host pode especificar ações de política a ser tomada quando o processo foi encerrado.|  
|`OPR_ThreadAbort`|O host pode especificar ações de política a ser tomada quando um thread é anulado.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|O host pode especificar ações de política a ser tomada quando uma anulação de thread educado ocorre em uma região crítica de código.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|O host pode especificar ações de política para ser executada quando uma anulação de thread educado ocorre em uma região não críticos do código.|  
  
## <a name="remarks"></a>Comentários  
 A infra-estrutura de confiabilidade do common language runtime (CLR) faz distinção entre recursos e anulações de falhas de alocação que ocorrem em regiões críticas de código e os que ocorrem em regiões não críticos do código. Essa distinção foi projetada para permitir que os hosts definir políticas diferentes dependendo de onde ocorrer uma falha no código.  
  
 Um *região crítica de código* qualquer espaço em que o CLR não pode garantir que anular uma tarefa ou uma falha ao concluir uma solicitação de recursos afeta apenas a tarefa atual. Por exemplo, se uma tarefa está mantendo um bloqueio e recebe um HRESULT que indica falha ao fazer uma solicitação de alocação de memória, é suficiente apenas para anular essa tarefa para garantir a estabilidade do <xref:System.AppDomain>, pois o <xref:System.AppDomain> pode conter outros tarefas em espera para o mesmo bloqueio. Para abandonar atual tarefa pode fazer com que as outras tarefas parar de responder (ou desligar) indefinidamente. Nesse caso, o host precisa da capacidade de descarregar todo o <xref:System.AppDomain> em vez de possível instabilidade de risco.  
  
 Um *região não críticos do código*, por outro lado, é uma região em que o CLR pode garantir que uma operação de anulação ou uma falha de afetará apenas a tarefa na qual o erro ocorrer.  
  
 O CLR também faz distinção entre normais e não normal anulações (educadas). Em geral, uma anulação normal ou normal faz todos os esforços para executar rotinas de manipulação de exceção e finalizadores antes de cancelar uma tarefa, enquanto uma anulação educada não garante tais.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [Enumeração EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [Interface IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
