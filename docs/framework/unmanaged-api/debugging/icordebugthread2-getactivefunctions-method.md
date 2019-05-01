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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed13f78d5a1f6d54b12c86613715f4878a521bfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993961"
---
# <a name="icordebugthread2getactivefunctions-method"></a>Método ICorDebugThread2::GetActiveFunctions
Obtém informações sobre a função do Active Directory em cada um dos quadros desse segmento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cFunctions`  
 [in] O tamanho do `pFunctions` matriz.  
  
 `pcFunctions`  
 [out] Um ponteiro para o número de objetos retornados no `pFunctions` matriz. O número de objetos retornados será igual ao número de quadros gerenciados na pilha.  
  
 `pFunctions`  
 [no, out] Uma matriz de objetos COR_ACTIVE_FUNCTION, cada uma delas contém informações sobre as funções do Active Directory em quadros desse segmento.  
  
 O primeiro elemento será usado para o quadro de folha e assim por diante novamente para a raiz da pilha.  
  
## <a name="remarks"></a>Comentários  
 Se `pFunctions` for nulo na entrada, `GetActiveFunctions` retorna somente o número de funções que estão na pilha. Ou seja, se `pFunctions` for nulo na entrada, `GetActiveFunctions` retorna um valor somente em `pcFunctions`.  
  
 O `GetActiveFunctions` método destina-se como uma otimização em obter as mesmas informações de quadros em um rastreamento de pilha e inclui somente os quadros que teria um objeto ICorDebugILFrame para eles no rastreamento de pilha completa.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
