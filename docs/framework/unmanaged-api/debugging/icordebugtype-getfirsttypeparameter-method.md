---
title: "Método ICorDebugType::GetFirstTypeParameter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e963553bfeac2d659de8fc460a938d2d523b53e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>Método ICorDebugType::GetFirstTypeParameter
Obtém um ponteiro de interface para um que representa a primeira ICorDebugType <xref:System.Type> parâmetro do tipo representado por esse `ICorDebugType`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value`  
 [out] Um ponteiro para o endereço de uma `ICorDebugType` objeto que representa o primeiro parâmetro.  
  
## <a name="remarks"></a>Comentários  
 `GetFirstTypeParameter`pode ser chamado em casos onde as informações adicionais sobre o tipo envolverem, no máximo, um parâmetro de tipo. Em particular, ele pode ser usado se o tipo for um ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, conforme indicado pelo [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
