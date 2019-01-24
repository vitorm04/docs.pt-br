---
title: Método ICorDebugManagedCallback::DebuggerError
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31a554fc57611f4abd5322fdc0c147e5dc110fb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654939"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>Método ICorDebugManagedCallback::DebuggerError
Notifica o depurador que ocorreu um erro durante a tentativa de manipular um evento do common language runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Um ponteiro para um objeto de "ICorDebugProcess" que representa o processo no qual o evento ocorreu.  
  
 `errorHR`  
 [in] O valor HRESULT retornado pelo manipulador de eventos.  
  
 `errorCode`  
 [in] Um inteiro que especifica o erro CLR.  
  
## <a name="remarks"></a>Comentários  
 O processo pode ser colocado no modo de passagem, dependendo da natureza do erro.  
  
 O `DebugError` retorno de chamada indica que serviços de depuração foram desabilitados devido a um erro, portanto, os depuradores devem disponibilizar a mensagem de erro para o usuário. [Icordebugprocess:: GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) estarão seguros para a chamada, mas todos os outros métodos, incluindo [icordebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), não deve ser chamado. O depurador deve usar os recursos de sistema operacional para encerrar processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
