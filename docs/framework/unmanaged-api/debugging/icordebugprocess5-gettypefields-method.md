---
title: Método ICorDebugProcess5::GetTypeFields
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178596"
---
# <a name="icordebugprocess5gettypefields-method"></a>Método ICorDebugProcess5::GetTypeFields
Fornece informações sobre os campos que pertencem a um tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `id`  
 [em] O identificador do tipo cujas informações de campo são recuperadas.  
  
 `celt`  
 [em] O número de [objetos COR_FIELD](cor-field-structure.md) cujas informações de campo devem ser recuperadas.  
  
 `fields`  
 [fora] Uma série de [objetos COR_FIELD](cor-field-structure.md) que fornecem informações sobre os campos que pertencem ao tipo.  
  
 `pceltNeeded`  
 [fora] Um ponteiro para o número `fields`de [objetos COR_FIELD](cor-field-structure.md) incluídos em .  
  
## <a name="remarks"></a>Comentários  
 O `celt` parâmetro, que especifica o número de campos cujas `fields`informações de campo o `COR_TYPE_LAYOUT::numFields` método usa para preencher, deve corresponder ao valor do campo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugProcess5](icordebugprocess5-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
