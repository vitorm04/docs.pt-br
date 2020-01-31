---
title: Método ICorDebugValue::GetType
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 7def2bd2c0f3ab501fdb918a0e9a7ee154159b78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791151"
---
# <a name="icordebugvaluegettype-method"></a>Método ICorDebugValue::GetType
Obtém o tipo primitivo desse objeto "ICorDebugValue".  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pType`  
 fora Um ponteiro para um valor da enumeração "CorElementType" que indica o tipo do valor.  
  
## <a name="remarks"></a>Comentários  
 Se o objeto for um tipo de tempo de execução complexo, esse tipo poderá ser examinado por meio das subclasses apropriadas da interface `ICorDebugValue`. Por exemplo, "ICorDebugObjectValue", que herda de `ICorDebugValue`, representa um tipo complexo.  
  
 Os métodos `GetType` e [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) retornam informações sobre o tipo de um valor. Eles são ambos substituídos pelo método [ICorDebugValue2:: Getexatotype](icordebugvalue2-getexacttype-method.md) com reconhecimento de genéricos.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também
