---
title: "Método ICorDebugObjectValue::GetFieldValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33c3f368d9b78b899f54c989427ea1f660346487
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
 [in] Um ponteiro para um objeto de "ICorDebugClass" que representa a classe para a qual obter o valor do campo.  
  
 `fieldDef`  
 [in] Um `mdFieldDef` token que referencia os metadados que descrevem o campo.  
  
 `ppValue`  
 [out] Um ponteiro para um objeto de "ICorDebugValue" que representa o valor do campo especificado.  
  
## <a name="remarks"></a>Comentários  
 A classe especificada no `pClass` , deve ser na hierarquia de classe do valor do objeto, e o campo deve ser um campo da classe.  
  
 O `GetFieldValue` método ainda funcionará para objetos genéricos e classes genéricas. Por exemplo, se MyDictionary\<V > herda de dicionário\<de cadeia de caracteres, V >, e o valor do objeto é do tipo MyDictionary\<int32 >, passando o `ICorDebugClass` o objeto de dicionário\<K, V > será obtido com êxito um campo do dicionário\<cadeia de caracteres, int32 >.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
    
 
