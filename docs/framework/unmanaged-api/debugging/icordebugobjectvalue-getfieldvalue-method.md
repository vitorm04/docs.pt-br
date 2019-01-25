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
ms.openlocfilehash: 72a504d23b7b15ad3de72995a632843874cc7c5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631732"
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
  
#### <a name="parameters"></a>Parâmetros  
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


