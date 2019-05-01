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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d872e4a65c0556dddac468336e6a42dd7d7923c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986980"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>Método ICorDebugType::GetFirstTypeParameter
Obtém um ponteiro de interface para um que representa a primeira ICorDebugType <xref:System.Type> parâmetro do tipo representado por este `ICorDebugType`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `value`  
 [out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o primeiro parâmetro.  
  
## <a name="remarks"></a>Comentários  
 `GetFirstTypeParameter` pode ser chamado em casos onde as informações adicionais sobre o tipo envolve, no máximo, um parâmetro de tipo. Em particular, ele pode ser usado se o tipo for um ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, conforme indicado pelo [icordebugtype:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
