---
title: "Enumeração LoggingLevelEnum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoggingLevelEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: LoggingLevelEnum
helpviewer_keywords: LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f6041f429c057cea9607df34ec5691be84e2d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 O common language runtime (CLR) chama o [Logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) método para notificar o depurador que um thread gerenciado registrou um evento. O CLR transmite um valor da `LoggingLevelEnum` enumeração para indicar o nível de severidade da mensagem que o thread gerenciado foram gravado no log de eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.EventLog>  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
