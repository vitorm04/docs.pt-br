---
title: "Método ICorDebugObjectValue::IsValueClass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.IsValueClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b504a9fe28ee72ae8a394359f1f1ef51e7d9d3af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectvalueisvalueclass-method"></a>Método ICorDebugObjectValue::IsValueClass
Obtém um valor que indica se o valor desse objeto é um tipo de valor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbIsValueClass`  
 [out] Um ponteiro para um valor booliano que é `true` se o valor do objeto representado por esse "ICorDebugObjectValue", é um tipo de valor em vez de um tipo de referência; caso contrário, `pbIsValueClass` é `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
    
 
