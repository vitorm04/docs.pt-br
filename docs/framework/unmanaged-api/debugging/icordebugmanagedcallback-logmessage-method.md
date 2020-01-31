---
title: Método ICorDebugManagedCallback::LogMessage
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: 4306c4ae44b0ae1ade2bf374981492fa1a4df76f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788374"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>Método ICorDebugManagedCallback::LogMessage
Notifica o depurador de que um thread gerenciado Common Language Runtime (CLR) chamou um método na classe <xref:System.Diagnostics.EventLog> para registrar um evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado que registrou o evento.  
  
 `pThread`  
 no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.  
  
 `lLevel`  
 no Um valor da enumeração [LoggingLevelEnum](logginglevelenum-enumeration.md) que indica o nível de severidade da mensagem descritiva que foi gravada no log de eventos.  
  
 `pLogSwitchName`  
 no Um ponteiro para o nome da opção de rastreamento.  
  
 `pMessage`  
 no Um ponteiro para a mensagem que foi gravada no log de eventos.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
