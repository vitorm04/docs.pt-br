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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d66e010340d186eed2222ae2ba8cfb24b8e8d7b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658566"
---
# <a name="eclrevent-enumeration"></a>Enumeração EClrEvent
Descreve os eventos de runtime (CLR) de linguagem comum para o qual o host pode registrar retornos de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`Event_ClrDisabled`|Especifica um erro fatal do CLR.|  
|`Event_DomainUnload`|Especifica o descarregamento de um determinado <xref:System.AppDomain>.|  
|`Event_MDAFired`|Especifica que uma mensagem de Managed Debugging Assistant (MDA) foi gerada.|  
|`Event_StackOverflow`|Especifica que ocorreu um erro de estouro de pilha.|  
  
## <a name="remarks"></a>Comentários  
 O host pode registrar retornos de chamada para qualquer um dos tipos de evento descritos por `EClrEvent` chamando métodos das [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface. O host obtém um ponteiro para essa interface por meio da chamada a [iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método.  
  
 O `Event_CLRDisabled` e `Event_DomainUnload` eventos podem ser gerados, mais de uma vez e de diversos threads para sinalizar um descarregamento ou a desabilitação do CLR.  
  
 O `Event_MDAFired` evento dispara a criação de um [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instância que contém os detalhes da mensagem MDA. Para obter mais informações sobre MDAs, consulte [diagnosticando erros com assistentes para depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
