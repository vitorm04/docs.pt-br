---
title: Método ICorDebugType::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: d403a8bfba3599a60d8af72307590f5a569480dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791291"
---
# <a name="icordebugtypegetclass-method"></a>Método ICorDebugType::GetClass
Obtém um ponteiro de interface para um ICorDebugClass que representa o tipo genérico não instanciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppClass`  
 fora Um ponteiro para o endereço de uma interface de `ICorDebugClass` que representa o tipo genérico não instanciado.  
  
## <a name="remarks"></a>Comentários  
 `GetClass` pode ser chamado somente sob determinadas condições. Chame [ICorDebugType:: GetType](icordebugtype-gettype-method.md) antes de chamar `GetClass`. Se `ICorDebugType::GetType` retornar um valor de CorElementType que seja ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` poderá ser chamado para obter o tipo não instanciado para um tipo genérico.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
