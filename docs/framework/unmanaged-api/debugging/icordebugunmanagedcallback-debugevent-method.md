---
title: "Método ICorDebugUnmanagedCallback::DebugEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback.DebugEvent
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49c3386fcda0bc731935ec9db7d029d0e619ef14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>Método ICorDebugUnmanagedCallback::DebugEvent
Notifica o depurador que um evento nativo foi acionado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDebugEvent`  
 [in] Um ponteiro para o evento nativo.  
  
 `fOutOfBand`  
 [in] `true`, se a interação com o estado do processo gerenciado é impossível quando ocorre um evento de não gerenciado, até que as chamadas do depurador [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se o thread está sendo depurado é um thread do Win32, não use nenhum membro do Win32 na interface de depuração. Você pode chamar `ICorDebugController::Continue` somente em um thread do Win32 e somente quando continuar após um evento de fora da banda.  
  
 O `DebugEvent` retorno de chamada não segue as regras padrão para retornos de chamada. Quando você chama `DebugEvent`, será o processo no raw, estado de parado de depuração do sistema operacional. O processo não será sincronizado. Ele inserirá automaticamente o estado sincronizado quando necessário para atender a solicitações para obter informações sobre o código gerenciado, o que pode resultar em outros aninhados `DebugEvent` retornos de chamada.  
  
 Chamar [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) sobre o processo de ignorar um evento de exceção antes de continuar o processo. Chamar esse método envia a solicitação continue DBG_CONTINUE em vez de DBG_EXCEPTION_NOT_HANDLED e limpa automaticamente os pontos de interrupção de fora de banda e exceções de única etapa. Eventos fora de banda podem vir a qualquer momento, mesmo quando o aplicativo está sendo depurado aparece interrompido e quando um evento em banda pendente já existe.  
  
 No .NET Framework versão 2.0, o depurador imediatamente deve continuar após um evento de ponto de interrupção de fora da banda. O depurador deve estar usando o [Icordebugprocess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) e [Icordebugprocess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) métodos para adicionar e remover pontos de interrupção. Esses métodos ignorará os pontos de interrupção de fora da banda automaticamente. Portanto, os pontos de interrupção somente fora de banda expedidos devem ser brutos pontos de interrupção que já estão no fluxo de instrução, como uma chamada para o Win32 `DebugBreak` função. Não tente usar `ICorDebugProcess::ClearCurrentException`, [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), ou qualquer outro membro do [depuração da API](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
