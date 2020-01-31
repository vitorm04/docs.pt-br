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
ms.openlocfilehash: d15938e94d647fd5fded23c72bdc200d198d21a7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792699"
---
# <a name="icordebugobjectvaluegetclass-method"></a>Método ICorDebugObjectValue::GetClass
Obtém a classe desse valor de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppClass`  
 fora Um ponteiro para o endereço de um objeto "ICorDebugClass" que representa a classe do valor do objeto representado por esse objeto "ICorDebugObjectValue".  
  
## <a name="remarks"></a>Comentários  
 Os métodos `GetClass` e [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) retornam informações sobre o tipo de um valor; Eles são ambos substituídos pelo [ICorDebugValue2:: Getexatotype](icordebugvalue2-getexacttype-method.md)com reconhecimento de genéricos.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também
