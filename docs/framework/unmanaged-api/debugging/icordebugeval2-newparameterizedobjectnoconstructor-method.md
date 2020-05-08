---
title: Método ICorDebugEval2::NewParameterizedObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 90fce1710f97341fb49be1d07f7af2edf8cb848c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976077"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>Método ICorDebugEval2::NewParameterizedObjectNoConstructor
Cria uma instância de um novo objeto de tipo com parâmetros da classe especificada sem tentar chamar um método de construtor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pClass`  
 no Um ponteiro para um objeto ICorDebugClass que representa a classe do objeto a ser instanciado.  
  
 `nTypeArgs`  
 no O número de argumentos de tipo passado.  
  
 `ppTypeArgs`  
 no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugType que representa um argumento de tipo para o objeto que está sendo instanciado.  
  
## <a name="remarks"></a>Comentários  
 O `NewParameterizedObjectNoConstructor` método falhará se um número incorreto de argumentos de tipo ou os tipos incorretos de argumentos de tipo forem passados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
