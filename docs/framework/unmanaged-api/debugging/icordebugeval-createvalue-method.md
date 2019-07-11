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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ada3a06a2beb8f21c3e24665c0f1f8e7c48515f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752951"
---
# <a name="icordebugevalcreatevalue-method"></a>Método ICorDebugEval::CreateValue
Cria um valor do tipo especificado, com um valor inicial de zero ou nulo.  
  
 Este método é obsoleto no .NET Framework versão 2.0. Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) em vez disso.  
  
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
 [in] Um valor igual a [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeração que especifica o tipo do valor.  
  
 `pElementClass`  
 [in] Ponteiro para um [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) objeto que especifica a classe de valor, se o tipo não for um tipo primitivo.  
  
 `ppValue`  
 [out] Ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor.  
  
## <a name="remarks"></a>Comentários  
 `CreateValue` cria um `ICorDebugValue` objeto do tipo especificado para o único propósito de usá-lo em uma avaliação de função. Esse objeto de valor pode ser usado para passar constantes do usuário como parâmetros.  
  
 Se o tipo do valor for um tipo primitivo, seu valor inicial é zero ou nulo. Use [icordebuggenericvalue:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) para definir o valor de um tipo primitivo.  
  
 Se o valor de `elementType` é ELEMENT_TYPE_CLASS, você obtém "ICorDebugReferenceValue" (retornados em `ppValue`) que representa a referência de objeto nulo. Você pode usar esse objeto passar null para uma avaliação de função que tem parâmetros de referência de objeto. Não é possível definir o `ICorDebugValue` para qualquer coisa; ele sempre permanecerá nulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Consulte também

- [Método CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [Interface ICorDebugEval](icordebugeval-interface.md)
