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
ms.openlocfilehash: 8f3697f8b193319ebb7b155ad79b8ec25a0a2266
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205272"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>Método ICorDebugManagedCallback::DebuggerError
Notifica o depurador de que ocorreu um erro ao tentar lidar com um evento do Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pProcess`  
 no Um ponteiro para um objeto "ICorDebugProcess" que representa o processo no qual o evento ocorreu.  
  
 `errorHR`  
 no O valor HRESULT que foi retornado do manipulador de eventos.  
  
 `errorCode`  
 no Um inteiro que especifica o erro CLR.  
  
## <a name="remarks"></a>Comentários  
 O processo pode ser colocado em modo de passagem, dependendo da natureza do erro.  
  
 O `DebugError` retorno de chamada indica que os serviços de depuração foram desabilitados devido a um erro, portanto, os depuradores devem tornar a mensagem de erro disponível para o usuário. [ICorDebugProcess:: GetID](icordebugprocess-getid-method.md) será seguro chamar, mas todos os outros métodos, incluindo [ICorDebug:: Terminate](icordebug-terminate-method.md), não devem ser chamados. O depurador deve usar recursos do sistema operacional para encerrar processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
