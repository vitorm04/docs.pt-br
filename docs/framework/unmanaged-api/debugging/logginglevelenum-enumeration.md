---
title: Enumeração LoggingLevelEnum
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe8e1355382273a681e927897f4a8ff5814b8de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765421"
---
# <a name="logginglevelenum-enumeration"></a>Enumeração LoggingLevelEnum
Indica o nível de severidade de uma mensagem descritiva que é escrita no log de eventos quando um thread gerenciado registrar um evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`LTraceLevel0`|A mensagem é um nível de rastreamento, 0.|  
|`LTraceLevel1`|A mensagem é um nível de rastreamento 1.|  
|`LTraceLevel2`|A mensagem é um nível de rastreamento 2.|  
|`LTraceLevel3`|A mensagem é um nível de rastreamento 3.|  
|`LTraceLevel4`|A mensagem é um nível de rastreamento 4.|  
|`LStatusLevel0`|A mensagem é um nível de status 0.|  
|`LStatusLevel1`|A mensagem é um nível de status 1.|  
|`LStatusLevel2`|A mensagem é um nível de status 2.|  
|`LStatusLevel3`|A mensagem é um nível de status 3.|  
|`LStatusLevel4`|A mensagem é um nível de status 4.|  
|`LWarningLevel`|A mensagem é um nível de aviso.|  
|`LErrorLevel`|A mensagem é um nível de erro.|  
|`LPanicLevel`|A mensagem é um nível de pânico.|  
  
## <a name="remarks"></a>Comentários  
 O common language runtime (CLR) chama o [icordebugmanagedcallback:: Logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) método para notificar o depurador que um thread gerenciado fez um evento. O CLR passa o valor de `LoggingLevelEnum` enumeração para indicar o nível de severidade da mensagem que o thread gerenciado gravou o log de eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.EventLog>
- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
