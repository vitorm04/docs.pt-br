---
title: Enumeração CorDebugUserState
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f489ab29726292f6c55151169ad9efc6f0fbfbcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407788"
---
# <a name="cordebuguserstate-enumeration"></a>Enumeração CorDebugUserState
Indica o estado do usuário de um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>Membros  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|Foi solicitado o encerramento do thread.|  
|`USER_SUSPEND_REQUESTED`|Foi solicitada uma suspensão do thread.|  
|`USER_BACKGROUND`|O thread está em execução em segundo plano.|  
|`USER_UNSTARTED`|O thread não iniciou a execução.|  
|`USER_STOPPED`|O thread foi encerrado.|  
|`USER_WAIT_SLEEP_JOIN`|O thread está aguardando outro thread para concluir uma tarefa.|  
|`USER_SUSPENDED`|O thread foi suspenso.|  
|`USER_UNSAFE_POINT`|O thread está em um ponto desprotegido. Ou seja, o thread está em um ponto na execução de onde ele pode bloquear a coleta de lixo.<br /><br /> Depurar eventos podem ser distribuídos de pontos não seguros, mas a suspensão de um thread em um ponto desprotegido muito provavelmente causará um deadlock até que o thread seja retomado. Os pontos seguros e são determinados pela implementação de coleta de lixo e just-in-time (JIT).|  
|`USER_THREADPOOL`|É o thread do pool de threads.|  
  
## <a name="remarks"></a>Comentários  
 O estado do usuário de um thread é o estado em que o thread tem quando o depurador examina a ele. Um thread pode ter uma combinação de estados do usuário.  
  
 Use o [Getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) método para recuperar o estado do usuário do thread.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
