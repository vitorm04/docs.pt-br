---
title: Método ICorDebugObjectValue::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dff7a42cac7002e170e8da3c3505fe37bd5eb85f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugobjectvaluegetclass-method"></a>Método ICorDebugObjectValue::GetClass
Obtém a classe de valor desse objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppClass`  
 [out] Um ponteiro para o endereço de um objeto de "ICorDebugClass" que representa a classe do valor do objeto representado pelo objeto "ICorDebugObjectValue".  
  
## <a name="remarks"></a>Comentários  
 O `GetClass` e [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) métodos retornam informações sobre o tipo de um valor; elas são substituídas pelas com reconhecimento de genéricos [Icordebugvalue2](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
    
 
