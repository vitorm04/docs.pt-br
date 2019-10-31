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
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129467"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>Método ICorDebugModule2::SetJMCStatus
Define o status de Apenas Meu Código (JMC) de todos os métodos de todas as classes nesse ICorDebugModule2 para o valor especificado, exceto aqueles na matriz `pTokens`, que ele define para o valor oposto.  
  
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
 no Defina como `true` se o código deve ser depurado; caso contrário, defina como `false`.  
  
 `cTokens`  
 no O tamanho da matriz de `pTokens`.  
  
 `pTokens`  
 no Uma matriz de valores `mdToken`, cada um dos quais se refere a um método que terá seu status JMC definido como!`bIsJustMycode`.  
  
## <a name="remarks"></a>Comentários  
 O status de JMC de cada método especificado na matriz de `pTokens` é definido como o oposto do valor de `bIsJustMycode`. O status de todos os outros métodos neste módulo é definido como o valor `bIsJustMycode`.  
  
 O método `SetJMCStatus` apaga todas as configurações de JMC anteriores neste módulo.  
  
 O método `SetJMCStatus` retorna um erro S_OK HRESULT se todas as funções foram definidas com êxito. Ele retornará um HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE se algumas funções marcadas `true` não forem depurável.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
