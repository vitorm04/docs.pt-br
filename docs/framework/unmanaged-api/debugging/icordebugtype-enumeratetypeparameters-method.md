---
title: "Método ICorDebugType::EnumerateTypeParameters"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9dd00b0a5f28821112621a54c97551c71e1acc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>Método ICorDebugType::EnumerateTypeParameters
Obtém um ponteiro de interface para um ICorDebugTypeEnum que contém o <xref:System.Type> parâmetros da classe referenciada por este ICorDebugType.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppTyParEnum`  
 [out] Um ponteiro para o endereço de um `ICorDebugTypeEnum` que contém os parâmetros do tipo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar `EnumerateTypeParameters` se o valor de CorElementType retornado por [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) é ELEMENT_TYPE_CLASS ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE _ PTR ou ELEMENT_TYPE_FNPTR. O número de parâmetros e sua ordem depende do tipo:  
  
-   ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE: O número de parâmetros de tipo dentro de `ICorDebugTypeEnum` que este método retorna, dependerá do número de parâmetros de tipo formal para a classe correspondente. Por exemplo, se o tipo é `class Dict<String,int32>`, em seguida, `EnumerateTypeParameters` retornará um `ICorDebugTypeEnum` que contém objetos que representam `String` e `int32` em sequência.  
  
-   ELEMENT_TYPE_FNPTR: O número de parâmetros de tipo contidos no `ICorDebugTypeEnum` terá um maior que o número de argumentos aceitados pela função. O primeiro parâmetro de tipo contido no `ICorDebugTypeEnum` é o tipo de retorno da função e os parâmetros de tipo subsequentes são os parâmetros da função.  
  
-   ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR: um parâmetro de tipo será retornado. Por exemplo, se o tipo é um tipo de matriz, como `int32[]`,`EnumerateTypeParameters` retornará um `ICorDebugTypeEnum` que contém um objeto que representa `int32`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
