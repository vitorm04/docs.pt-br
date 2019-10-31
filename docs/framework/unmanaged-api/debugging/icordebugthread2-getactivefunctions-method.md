---
title: Método ICorDebugThread2::GetActiveFunctions
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
ms.openlocfilehash: 9b9a301714ea60b4e3220eb75721e56e39bd9659
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139939"
---
# <a name="icordebugthread2getactivefunctions-method"></a>Método ICorDebugThread2::GetActiveFunctions
Obtém informações sobre a função ativa em cada um dos quadros deste thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cFunctions`  
 no O tamanho da matriz de `pFunctions`.  
  
 `pcFunctions`  
 fora Um ponteiro para o número de objetos retornados na matriz de `pFunctions`. O número de objetos retornados será igual ao número de quadros gerenciados na pilha.  
  
 `pFunctions`  
 [entrada, saída] Uma matriz de objetos COR_ACTIVE_FUNCTION, cada um dos quais contém informações sobre as funções ativas nos quadros deste thread.  
  
 O primeiro elemento será usado para o quadro folha e assim por diante de volta para a raiz da pilha.  
  
## <a name="remarks"></a>Comentários  
 Se `pFunctions` for nulo na entrada, `GetActiveFunctions` retornará apenas o número de funções que estão na pilha. Ou seja, se `pFunctions` for nulo na entrada, `GetActiveFunctions` retornará um valor somente em `pcFunctions`.  
  
 O método `GetActiveFunctions` é destinado como uma otimização ao obter as mesmas informações de quadros em um rastreamento de pilha e inclui apenas quadros que teriam um objeto ICorDebugILFrame para eles no rastreamento de pilha completo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
