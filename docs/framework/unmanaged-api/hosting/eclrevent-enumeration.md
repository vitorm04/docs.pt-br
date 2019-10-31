---
title: Enumeração EClrEvent
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131130"
---
# <a name="eclrevent-enumeration"></a>Enumeração EClrEvent
Descreve os eventos de Common Language Runtime (CLR) para os quais o host pode registrar retornos de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`Event_ClrDisabled`|Especifica um erro fatal de CLR.|  
|`Event_DomainUnload`|Especifica o descarregamento de um determinado <xref:System.AppDomain>.|  
|`Event_MDAFired`|Especifica que uma mensagem do MDA (Assistente de depuração gerenciada) foi gerada.|  
|`Event_StackOverflow`|Especifica que ocorreu um erro de estouro de pilha.|  
  
## <a name="remarks"></a>Comentários  
 O host pode registrar retornos de chamada para qualquer um dos tipos de evento descritos por `EClrEvent` chamando métodos da interface [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) . O host obtém um ponteiro para essa interface chamando o método [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .  
  
 Os eventos `Event_CLRDisabled` e `Event_DomainUnload` podem ser gerados mais de uma vez e de threads diferentes para sinalizar um descarregamento ou desabilitar o CLR.  
  
 O evento `Event_MDAFired` gera a criação de uma instância [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) que contém os detalhes da mensagem do MDA. Para obter mais informações sobre MDAs, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
