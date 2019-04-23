---
title: Enumeração EClrOperation
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d5f24d7415ff7ecceba6b0a5fbd3098d70dcd0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190347"
---
# <a name="eclroperation-enumeration"></a>Enumeração EClrOperation
Descreve o conjunto de operações para o qual um host pode aplicar ações de política.  
  
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
|`OPR_AppDomainRudeUnload`|O host pode especificar ações de política a ser tomada quando um <xref:System.AppDomain> é descarregada de forma não-amigável (rude).|  
|`OPR_AppDomainUnload`|O host pode especificar ações de política a ser tomada quando um <xref:System.AppDomain> é descarregado.|  
|`OPR_FinalizerRun`|O host pode especificar ações de política a ser tomada quando a execução de finalizadores.|  
|`OPR_ProcessExit`|O host pode especificar ações de política a ser tomada quando o processo é encerrado.|  
|`OPR_ThreadAbort`|O host pode especificar ações de política a ser tomada quando um thread é anulado.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|O host pode especificar ações de política a ser tomada quando uma anulação de thread rude ocorre em uma região crítica de código.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|O host pode especificar ações de política para ser executada quando uma anulação de thread rude ocorre em uma região não-críticas do código.|  
  
## <a name="remarks"></a>Comentários  
 A infraestrutura de confiabilidade do common language runtime (CLR) faz distinção entre recursos e anulações de falhas de alocação que ocorrem em regiões críticas de código e aqueles que ocorrem em regiões de não-críticas do código. Essa distinção é projetada para permitir que os hosts definir diretivas diferentes, dependendo de onde ocorre uma falha no código.  
  
 Um *região crítica de código* é qualquer espaço em que o CLR não garante que anular uma tarefa ou uma falha ao concluir uma solicitação para recursos afetará apenas a tarefa atual. Por exemplo, se uma tarefa está mantendo um bloqueio e recebe um HRESULT que indica falha depois de fazer uma solicitação de alocação de memória, é suficiente simplesmente para anular essa tarefa para garantir a estabilidade do <xref:System.AppDomain>, pois o <xref:System.AppDomain> pode conter outros tarefas aguardando o mesmo bloqueio. Abandonar atual tarefa pode fazer com que as outras tarefas parar de responder (ou parar de responder) indefinidamente. Nesse caso, o host precisa da capacidade de descarregar todo o <xref:System.AppDomain> em vez de instabilidade de potencial de risco.  
  
 Um *região não-críticas do código*, por outro lado, é uma região em que o CLR pode garantir uma anulação ou uma falha afeta apenas a tarefa na qual o erro ocorre.  
  
 O CLR também faz distinção entre anulações (rudes) normais e não normal. Em geral, uma anulação normal ou normal todos os esforços para executar rotinas de manipulação de exceção e finalizadores antes de cancelar uma tarefa, enquanto uma anulação rude não faz com que nenhuma dessas garantias.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [Enumeração EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [Interface IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
