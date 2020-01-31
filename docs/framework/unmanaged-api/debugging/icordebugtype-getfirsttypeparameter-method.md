---
title: Método ICorDebugType::GetFirstTypeParameter
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 1a02190b595fb01bdc2df46182bfa64bfe638db4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791283"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>Método ICorDebugType::GetFirstTypeParameter
Obtém um ponteiro de interface para um ICorDebugType que representa o primeiro parâmetro <xref:System.Type> do tipo representado por esse `ICorDebugType`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `value`  
 fora Um ponteiro para o endereço de um objeto de `ICorDebugType` que representa o primeiro parâmetro.  
  
## <a name="remarks"></a>Comentários  
 `GetFirstTypeParameter` pode ser chamado em casos em que as informações adicionais sobre o tipo envolvam, no máximo, um parâmetro de tipo. Em particular, ele pode ser usado se o tipo for um ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, conforme indicado pelo método [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
