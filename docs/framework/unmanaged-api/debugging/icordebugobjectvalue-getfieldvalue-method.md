---
title: Método ICorDebugObjectValue::GetFieldValue
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
ms.openlocfilehash: 002c6cccb3ddf29b831ba5e14baa5e51f1b82433
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095890"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>Método ICorDebugObjectValue::GetFieldValue
Obtém o valor do campo especificado da classe especificada para esse valor de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pClass`  
 no Um ponteiro para um objeto "ICorDebugClass" que representa a classe para a qual obter o valor do campo.  
  
 `fieldDef`  
 no Um `mdFieldDef` token que faz referência aos metadados que descrevem o campo.  
  
 `ppValue`  
 fora Um ponteiro para um objeto "ICorDebugValue" que representa o valor do campo especificado.  
  
## <a name="remarks"></a>Comentários  
 A classe, especificada no parâmetro `pClass`, deve estar na hierarquia da classe do valor do objeto e o campo deve ser um campo dessa classe.  
  
 O método `GetFieldValue` ainda terá sucesso para objetos genéricos e classes genéricas. Por exemplo, se MyDictionary\<V > herda do Dictionary\<cadeia de caracteres, V > e o valor do objeto for do tipo MyDictionary\<Int32 >, passando o objeto `ICorDebugClass` para o Dictionary\<K, V > obterá com êxito um campo de Dicionário\<cadeia de caracteres, Int32 >.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
