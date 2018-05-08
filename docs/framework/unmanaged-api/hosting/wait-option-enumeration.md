---
title: Enumeração WAIT_OPTION
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb37394799db39baa406ef332066d5ebb2dbf19d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="waitoption-enumeration"></a>Enumeração WAIT_OPTION
Contém valores que indicam que a ação que um host deve executar se uma operação solicitada pelos blocos de runtime (CLR) de linguagem comum.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|Notifica o host que a tarefa deve ser ativada se o CLR chama o [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) método.|  
|`WAIT_MSGPUMP`|Notifica o host que ele deve bomba de mensagens no thread atual do sistema operacional se o thread fica bloqueado. O tempo de execução especifica esse valor somente em um <xref:System.Threading.ApartmentState.STA> thread.|  
|`WAIT_NOTINDEADLOCK`|Notifica o host que a solicitação de sincronização especificado não pode ser dividida por um host. Ou seja, o host não pode retornar `HOST_E_DEADLOCK`.|  
  
## <a name="remarks"></a>Comentários  
 O [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) e [Switchtotask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) ambos os métodos usam um parâmetro deste tipo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
