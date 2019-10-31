---
title: Método ICorDebugEval::CreateValue
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: 4bb04ba090be9cab551bc39d8d9f1be974c747d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085131"
---
# <a name="icordebugevalcreatevalue-method"></a>Método ICorDebugEval::CreateValue
Cria um valor do tipo especificado, com um valor inicial de zero ou NULL.  
  
 Esse método é obsoleto no .NET Framework versão 2,0. Use [ICorDebugEval2:: CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `elementType`  
 no Um valor da enumeração [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) que especifica o tipo do valor.  
  
 `pElementClass`  
 no Ponteiro para um objeto [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) que especifica a classe do valor, se o tipo não for um tipo primitivo.  
  
 `ppValue`  
 fora Ponteiro para o endereço de um objeto "ICorDebugValue" que representa o valor.  
  
## <a name="remarks"></a>Comentários  
 `CreateValue` cria um objeto `ICorDebugValue` do tipo fornecido para o único propósito de usá-lo em uma avaliação de função. Esse objeto de valor pode ser usado para passar constantes de usuário como parâmetros.  
  
 Se o tipo do valor for um tipo primitivo, seu valor inicial será zero ou NULL. Use [ICorDebugGenericValue:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) para definir o valor de um tipo primitivo.  
  
 Se o valor de `elementType` for ELEMENT_TYPE_CLASS, você obterá um "ICorDebugReferenceValue" (retornado em `ppValue`) que representa a referência do objeto nulo. Você pode usar esse objeto para passar NULL para uma avaliação de função que tem parâmetros de referência de objeto. Não é possível definir o `ICorDebugValue` como qualquer coisa; Ele sempre permanece nulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Consulte também

- [Método CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [Interface ICorDebugEval](icordebugeval-interface.md)
