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
ms.openlocfilehash: 2d865f837d38894e8449af671e2d12e7676dd040
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129130"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>Método ICorDebugUnmanagedCallback::DebugEvent
Notifica o depurador de que um evento nativo foi acionado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pDebugEvent`  
 no Um ponteiro para o evento nativo.  
  
 `fOutOfBand`  
 [in] `true`, se a interação com o estado do processo gerenciado for impossível depois que um evento não gerenciado ocorrer, até que o depurador chame [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se o thread que está sendo depurado for um Thread Win32, não use nenhum membro da interface de depuração do Win32. Você pode chamar `ICorDebugController::Continue` apenas em um Thread Win32 e apenas quando estiver continuando um evento fora de banda.  
  
 O retorno de chamada `DebugEvent` não segue as regras padrão para retornos de chamada. Quando você chama `DebugEvent`, o processo estará no estado RAW, de depuração do sistema operacional interrompido. O processo não será sincronizado. Ele inserirá automaticamente o estado SYNCHRONIZED quando necessário para atender a solicitações de informações sobre código gerenciado, o que pode resultar em outros retornos de chamada de `DebugEvent` aninhados.  
  
 Chame [ICorDebugProcess:: ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) no processo para ignorar um evento de exceção antes de continuar o processo. Chamar esse método envia DBG_CONTINUE em vez de DBG_EXCEPTION_NOT_HANDLED na solicitação de continuação e limpa automaticamente os pontos de interrupção fora de banda e as exceções de etapa única. Eventos fora de banda podem vir a qualquer momento, mesmo quando o aplicativo que está sendo depurado aparece parado e quando um evento em banda pendente já existe.  
  
 No .NET Framework versão 2,0, o depurador deve continuar imediatamente após um evento de ponto de interrupção fora de banda. O depurador deve usar os métodos [ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) e [ICorDebugProcess2:: ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) para adicionar e remover pontos de interrupção. Esses métodos ignorarão todos os pontos de interrupção fora de banda automaticamente. Portanto, os únicos pontos de interrupção fora de banda que são expedidos devem ser pontos de interrupção brutos que já estão no fluxo de instrução, como uma chamada para a função de `DebugBreak` do Win32. Não tente usar `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)ou qualquer outro membro da [API de depuração](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
