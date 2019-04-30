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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8778edf9ac6e32d5dab3a53a6d9cc643a8df13b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994546"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>Método ICorDebugObjectValue::GetFieldValue
Obtém o valor do campo especificado da classe especificada para o valor desse objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pClass`  
 [in] Um ponteiro para um objeto de "ICorDebugClass" que representa a classe para o qual obter o valor do campo.  
  
 `fieldDef`  
 [in] Um `mdFieldDef` token que referencia os metadados que descrevem o campo.  
  
 `ppValue`  
 [out] Um ponteiro para um objeto de "ICorDebugValue" que representa o valor do campo especificado.  
  
## <a name="remarks"></a>Comentários  
 A classe especificada no `pClass` parâmetro, deve estar na hierarquia de classe do valor do objeto e o campo deve ser um campo de classe.  
  
 O `GetFieldValue` método ainda será bem-sucedida para objetos genéricos e as classes genéricas. Por exemplo, se MyDictionary\<V > herda de dicionário\<de cadeia de caracteres, V >, e o valor do objeto é do tipo MyDictionary\<int32 >, passando o `ICorDebugClass` objeto de dicionário\<K, V > será obter com êxito um campo de dicionário\<string, int32 >.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
