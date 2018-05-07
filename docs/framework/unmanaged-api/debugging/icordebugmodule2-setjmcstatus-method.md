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
ms.openlocfilehash: a56b5c31c26dbe5c5371fdb7a10c13ad11847117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2setjmcstatus-method"></a>Método ICorDebugModule2::SetJMCStatus
Define o status de apenas meu código (JMC) de todos os métodos de todas as classes neste ICorDebugModule2 ao valor especificado, exceto aqueles na `pTokens` matriz, que define como o valor oposto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bIsJustMycode`  
 [in] Definido como `true` se o código é depurado; caso contrário, defina como `false`.  
  
 `cTokens`  
 [in] O tamanho do `pTokens` matriz.  
  
 `pTokens`  
 [in] Uma matriz de `mdToken` valores, cada um deles se refere a um método que terá seu status de JMC!`bIsJustMycode`.  
  
## <a name="remarks"></a>Comentários  
 O status JMC de cada método é especificado no `pTokens` matriz é definida como o oposto do `bIsJustMycode` valor. O status de todos os outros métodos neste módulo é definido como o `bIsJustMycode` valor.  
  
 O `SetJMCStatus` método apaga todas as configurações anteriores do JMC neste módulo.  
  
 O `SetJMCStatus` método retorna um HRESULT S_OK se todas as funções foram definidas com êxito. Ele retorna um HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE se algumas funções que são marcados `true` não são depurável.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
