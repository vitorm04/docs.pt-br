---
title: "Método ICorDebugProcess5::GetTypeFields"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeFields
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a64e754a77c7d730d921f8a8c1547dd18b66d77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypefields-method"></a>Método ICorDebugProcess5::GetTypeFields
Fornece informações sobre os campos que pertencem a um tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 [in] O identificador do tipo cujas informações de campo são recuperadas.  
  
 `celt`  
 [in] O número de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos cujas informações de campo deve ser recuperado.  
  
 `fields`  
 [out] Uma matriz de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos que fornecem informações sobre os campos que pertencem ao tipo.  
  
 `pceltNeeded`  
 [out] Um ponteiro para o número de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos incluídos no `fields`.  
  
## <a name="remarks"></a>Comentários  
 O `celt` parâmetro, que especifica o número de campos cujas informações de campo que usa o método para preencher `fields`, deve corresponder ao valor da `COR_TYPE_LAYOUT::numFields` campo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
