---
title: Método ICorDebugUnmanagedCallback::DebugEvent
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1c75e1844fca4e592faa924a55432dd42fa7355
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772626"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>Método ICorDebugUnmanagedCallback::DebugEvent
Notifica o depurador que um evento nativo foi disparado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pDebugEvent`  
 [in] Um ponteiro para o evento nativo.  
  
 `fOutOfBand`  
 [in] `true`, se a interação com o estado do processo gerenciado é impossível quando ocorre um evento de não gerenciado, até que as chamadas do depurador [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se o thread que está sendo depurado é um thread do Win32, não use nenhum membro do Win32 na interface de depuração. Você pode chamar `ICorDebugController::Continue` somente em um thread do Win32 e somente quando continuar após um evento de fora da banda.  
  
 O `DebugEvent` retorno de chamada não segue as regras padrão para retornos de chamada. Quando você chama `DebugEvent`, o processo estará em bruto, o estado de parado de depuração do sistema operacional. O processo não será sincronizado. Entrará automaticamente o estado sincronizado quando necessário para atender a solicitações para obter informações sobre o código gerenciado, que pode resultar em outros aninhados `DebugEvent` retornos de chamada.  
  
 Chame [icordebugprocess:: Clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) sobre o processo de ignorar um evento de exceção antes de continuar o processo. Chamar esse método envia a solicitação para continuar DBG_CONTINUE em vez de DBG_EXCEPTION_NOT_HANDLED e limpa automaticamente os pontos de interrupção de out-of-band e exceções do passo a passo. Eventos fora de banda podem vir a qualquer momento, mesmo quando o aplicativo que está sendo depurado aparece interrompido e quando um evento em banda pendente já existe.  
  
 No .NET Framework versão 2.0, o depurador imediatamente deve continuar após um evento de ponto de interrupção de out-of-band. O depurador deve estar usando o [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) e [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) métodos para adicionar e remover pontos de interrupção. Esses métodos ignorará qualquer ponto de interrupção de out-of-band automaticamente. Assim, os pontos de interrupção somente out-of-band expedidos devem ser brutos pontos de interrupção que já estão no fluxo de instruções, como uma chamada para o Win32 `DebugBreak` função. Não tente usar `ICorDebugProcess::ClearCurrentException`, [icordebugprocess:: Getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [icordebugprocess:: Setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), ou qualquer outro membro do [API de depuração](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
