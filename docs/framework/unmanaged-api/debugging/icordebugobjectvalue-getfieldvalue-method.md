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
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207586"
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
 A classe, especificada no `pClass` parâmetro, deve estar na hierarquia da classe do valor do objeto e o campo deve ser um campo dessa classe.  
  
 O `GetFieldValue` método ainda terá sucesso para objetos genéricos e classes genéricas. Por exemplo, se MyDictionary \< V> herdar da \< cadeia de caracteres do dicionário, V> e o valor do objeto for do tipo MyDictionary \< Int32>, passando o `ICorDebugClass` objeto para o Dictionary \< K, v> receberá com êxito um campo de string de dicionário \< , Int32>.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também
