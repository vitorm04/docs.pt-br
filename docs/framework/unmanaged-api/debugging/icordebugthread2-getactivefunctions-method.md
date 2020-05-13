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
ms.openlocfilehash: e064a7db131a671adc4d0b6df522f3456e3a31d5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377161"
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
 no O tamanho da `pFunctions` matriz.  
  
 `pcFunctions`  
 fora Um ponteiro para o número de objetos retornados na `pFunctions` matriz. O número de objetos retornados será igual ao número de quadros gerenciados na pilha.  
  
 `pFunctions`  
 [entrada, saída] Uma matriz de objetos COR_ACTIVE_FUNCTION, cada um dos quais contém informações sobre as funções ativas nos quadros deste thread.  
  
 O primeiro elemento será usado para o quadro folha e assim por diante de volta para a raiz da pilha.  
  
## <a name="remarks"></a>Comentários  
 Se `pFunctions` for NULL na entrada, `GetActiveFunctions` retornará apenas o número de funções que estão na pilha. Ou seja, se `pFunctions` for NULL na entrada, `GetActiveFunctions` retornará um valor somente no `pcFunctions` .  
  
 O `GetActiveFunctions` método é projetado como uma otimização sobre como obter as mesmas informações de quadros em um rastreamento de pilha e inclui apenas quadros que teriam um objeto ICorDebugILFrame para eles no rastreamento de pilha completo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
