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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1abe307e3b9fa607912f98e456a11176eb17c56
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471501"
---
# <a name="icordebugevalnewarray-method"></a>Método ICorDebugEval::NewArray
Aloca uma nova matriz do tipo de elemento especificado e dimensões.  
  
 Este método é obsoleto no .NET Framework versão 2.0. Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] Um valor de enumeração CorElementType que especifica o tipo de elemento da matriz.  
  
 `pElementClass`  
 [in] Um ponteiro para um objeto ICorDebugClass que especifica a classe do elemento. Esse valor pode ser nulo se o tipo de elemento é um tipo primitivo.  
  
 `rank`  
 [in] O número de dimensões da matriz. No .NET Framework 2.0, esse valor deve ser 1.  
  
 `dims`  
 [in] O tamanho, em bytes, de cada dimensão da matriz.  
  
 `lowBounds`  
 [in] Opcional. O limite inferior de cada dimensão da matriz. Se esse valor for omitido, um limite inferior de zero será assumido para cada dimensão.  
  
## <a name="remarks"></a>Comentários  
 A matriz é sempre criada no domínio do aplicativo no qual o thread está em execução no momento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 1.1, 1.0
