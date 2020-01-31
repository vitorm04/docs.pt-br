---
title: Método ICorDebugEval::NewArray
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: 13ac5379992f4e768b09a03d31591143ba9bf627
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788717"
---
# <a name="icordebugevalnewarray-method"></a>Método ICorDebugEval::NewArray
Aloca uma nova matriz do tipo e das dimensões do elemento especificado.  
  
 Esse método é obsoleto no .NET Framework versão 2,0. Use [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `elementType`  
 no Um valor da enumeração CorElementType que especifica o tipo de elemento da matriz.  
  
 `pElementClass`  
 no Um ponteiro para um objeto ICorDebugClass que especifica a classe do elemento. Esse valor pode ser nulo se o tipo de elemento for um tipo primitivo.  
  
 `rank`  
 no O número de dimensões da matriz. No .NET Framework 2,0, esse valor deve ser 1.  
  
 `dims`  
 no O tamanho, em bytes, de cada dimensão da matriz.  
  
 `lowBounds`  
 [in] Opcional. O limite inferior de cada dimensão da matriz. Se esse valor for omitido, um limite inferior de zero será assumido para cada dimensão.  
  
## <a name="remarks"></a>Comentários  
 A matriz é sempre criada no domínio do aplicativo no qual o thread está sendo executado no momento.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 1,1, 1,0
