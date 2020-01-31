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
ms.openlocfilehash: 1677798abdb8994d34c82a71e97a2c858209c18e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790385"
---
# <a name="logginglevelenum-enumeration"></a>Enumeração LoggingLevelEnum
Indica o nível de severidade de uma mensagem descritiva que é escrita no log de eventos quando um thread gerenciado registrar um evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`LTraceLevel0`|A mensagem é um nível de rastreamento 0.|  
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
|`LPanicLevel`|A mensagem é um nível de pane.|  
  
## <a name="remarks"></a>Comentários  
 O Common Language Runtime (CLR) chama o método [ICorDebugManagedCallback:: LogMessage](icordebugmanagedcallback-logmessage-method.md) para notificar o depurador de que um thread gerenciado registrou um evento. O CLR passa um valor da enumeração `LoggingLevelEnum` para indicar o nível de severidade da mensagem que o thread gerenciado gravou no log de eventos.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Diagnostics.EventLog>
- [Declarando enumerações](debugging-enumerations.md)
