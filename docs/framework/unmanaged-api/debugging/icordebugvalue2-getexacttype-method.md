---
title: Método ICorDebugValue2::GetExactType
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1f8292a6964a6b25e228fcd07ab21a7ee5f5a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvalue2getexacttype-method"></a>Método ICorDebugValue2::GetExactType
Obtém um ponteiro de interface para um objeto de "ICorDebugType" que representa o <xref:System.Type> desse valor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppType`  
 [out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o <xref:System.Type> do valor representado pelo objeto "ICorDebugValue2".  
  
## <a name="remarks"></a>Comentários  
 O com reconhecimento de genéricos `GetExactType` método substitui ambos o [Icordebugobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) e [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) métodos, cada um dos quais retornar informações sobre o tipo de um valor .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
