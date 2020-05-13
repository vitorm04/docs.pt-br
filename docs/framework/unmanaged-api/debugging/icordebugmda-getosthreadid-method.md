---
title: Método ICorDebugMDA::GetOSThreadId
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: c7ab77e9316023a97d2eafe8bcccc2b45e240cd0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207819"
---
# <a name="icordebugmdagetosthreadid-method"></a>Método ICorDebugMDA::GetOSThreadId
Obtém o identificador de thread do sistema operacional no qual o MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md) está em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pOsTid`  
 fora Um ponteiro para o identificador de thread do sistema operacional.  
  
## <a name="remarks"></a>Comentários  
 O thread do sistema operacional é usado em vez de um ICorDebugThread para permitir situações em que um MDA seja acionado em um thread nativo ou em um thread gerenciado que ainda não tenha inserido código gerenciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugMDA](icordebugmda-interface.md)
- [Diagnosticando erros com assistentes para depuração gerenciada](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
