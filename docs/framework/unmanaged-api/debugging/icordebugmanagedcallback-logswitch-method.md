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
ms.openlocfilehash: 3d5284cf6072aa5c1c11cc83355a3e9fa5c96837
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>Método ICorDebugManagedCallback::LogSwitch
Notifica o depurador um thread de runtime (CLR) gerenciado de linguagem comum chamou um método em de <xref:System.Diagnostics.Switch> classe para criar, modificar ou excluir um comutador/rastreamento de depuração.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `PAppDomain`  
 [in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o thread gerenciado que são criados, modificados ou excluídos de um comutador/rastreamento de depuração.  
  
 `pThread`  
 [in] Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.  
  
 `lLevel`  
 [in] Um valor que indica o nível de severidade da mensagem descritiva que foram gravado no log de eventos.  
  
 `ulReason`  
 [in] Um valor de [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeração que indica a operação executada no comutador/rastreamento de depuração.  
  
 `pLogSwitchName`  
 [in] Um ponteiro para o nome do comutador/rastreamento de depuração.  
  
 `pParentName`  
 [in] Um ponteiro para o nome do pai do comutador/rastreamento de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
