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
ms.openlocfilehash: 982af81f8f3886ae26b56114cc36374279c07593
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656343"
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
 [out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o <xref:System.Type> do valor representado por esse objeto de "ICorDebugValue2".  
  
## <a name="remarks"></a>Comentários  
 O reconhecimento de genéricos `GetExactType` método substitui ambos o [icordebugobjectvalue:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) e o [icordebugvalue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) métodos, cada um dos quais retornar informações sobre o tipo de um valor .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

