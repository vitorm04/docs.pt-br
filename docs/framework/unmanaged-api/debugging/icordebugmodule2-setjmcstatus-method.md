---
title: Método ICorDebugModule2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d438123dcefb901098954845596c210e5b76cea6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764110"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>Método ICorDebugModule2::SetJMCStatus
Define o status de apenas My Code (JMC) de todos os métodos de todas as classes nesse ICorDebugModule2 ao valor especificado, exceto aqueles no `pTokens` matriz, que define como o valor oposto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bIsJustMycode`  
 [in] Definido como `true` se o código deve ser depurado; caso contrário, definido como `false`.  
  
 `cTokens`  
 [in] O tamanho do `pTokens` matriz.  
  
 `pTokens`  
 [in] Uma matriz de `mdToken` valores, cada um deles se refere a um método que terá o status JMC definido como!`bIsJustMycode`.  
  
## <a name="remarks"></a>Comentários  
 O status JMC de cada método que é especificado na `pTokens` matriz é definida como o oposto do `bIsJustMycode` valor. O status de todos os outros métodos neste módulo é definido como o `bIsJustMycode` valor.  
  
 O `SetJMCStatus` método apaga todas as configurações anteriores de JMC neste módulo.  
  
 O `SetJMCStatus` método retornará um S_OK HRESULT se todas as funções foram definidas com êxito. Ele retorna um HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE se algumas funções que são marcados `true` não são depurável.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
