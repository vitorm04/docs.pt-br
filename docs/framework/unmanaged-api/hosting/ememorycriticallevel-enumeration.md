---
title: Enumeração EMemoryCriticalLevel
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acf4f3f582e417c5e7b814622986427f996796ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432517"
---
# <a name="ememorycriticallevel-enumeration"></a>Enumeração EMemoryCriticalLevel
Contém valores que indicam o impacto de uma falha quando uma alocação de memória específica foi solicitada, mas não pode ser atendida.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`eAppDomainCritical`|Indica que a alocação é fundamental para a execução de código gerenciado no domínio que solicitou a alocação. Se não é possível alocar a memória, o CLR não pode garantir que o domínio é utilizável. O host decide qual ação a ser tomada quando a alocação não pode ser atendida. Ele pode instruir o CLR para anular o `AppDomain` automaticamente, ou permitir que ele seja executado chamando métodos na [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Indica que a alocação é fundamental para a execução de código gerenciado no processo. Esse valor é usado durante a inicialização e ao executar finalizadores. Se não é possível alocar a memória, o CLR não pode operar no processo. Se a alocação falhar, o CLR está desativado. Todas as chamadas subsequentes para o CLR falharem com HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Indica que a alocação é fundamental para a execução da tarefa que solicitou a alocação. Se não é possível alocar a memória, o CLR não pode garantir que a tarefa pode ser executada. No caso de falha, o CLR gera um <xref:System.Threading.ThreadAbortException> no thread de operação física do sistema.|  
  
## <a name="remarks"></a>Comentários  
 Os métodos de alocação de memória definidos a [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) e [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces usam um parâmetro deste tipo. Dependendo da gravidade de falha, um host pode decidir se falhar a solicitação de alocação imediatamente ou aguardar até que ele pode ser atendido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
