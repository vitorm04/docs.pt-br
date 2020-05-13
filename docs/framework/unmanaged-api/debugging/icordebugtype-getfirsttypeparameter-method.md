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
ms.openlocfilehash: da0097daea183c76f97f0b1966b313e1cb5a557b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379946"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>Método ICorDebugType::GetFirstTypeParameter
Obtém um ponteiro de interface para um ICorDebugType que representa o primeiro <xref:System.Type> parâmetro do tipo representado por isso `ICorDebugType` .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `value`  
 fora Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o primeiro parâmetro.  
  
## <a name="remarks"></a>Comentários  
 `GetFirstTypeParameter`pode ser chamado em casos em que as informações adicionais sobre o tipo envolvam, no máximo, um parâmetro de tipo. Em particular, ele pode ser usado se o tipo for um ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, conforme indicado pelo método [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
