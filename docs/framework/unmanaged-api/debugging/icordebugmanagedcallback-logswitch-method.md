---
title: Método ICorDebugManagedCallback::LogSwitch
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 040c7dea7f751accb801f8fda190e9387c7aede1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466161"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>Método ICorDebugManagedCallback::LogSwitch
Notifica o depurador um thread de runtime (CLR) gerenciado de linguagem comum chamou um método no <xref:System.Diagnostics.Switch> classe para criar, modificar ou excluir um comutador de depuração/rastreamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `PAppDomain`  
 [in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o thread gerenciado que criados, modificados ou excluídos de um comutador de depuração/rastreamento.  
  
 `pThread`  
 [in] Um ponteiro para um objeto de ICorDebugThread que representa o thread gerenciado.  
  
 `lLevel`  
 [in] Um valor que indica o nível de severidade da mensagem descritiva que foi gravado no log de eventos.  
  
 `ulReason`  
 [in] Um valor igual a [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) a enumeração que indica a operação realizada no comutador/rastreamento de depuração.  
  
 `pLogSwitchName`  
 [in] Um ponteiro para o nome do comutador/rastreamento de depuração.  
  
 `pParentName`  
 [in] Um ponteiro para o nome do pai do comutador/rastreamento de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
