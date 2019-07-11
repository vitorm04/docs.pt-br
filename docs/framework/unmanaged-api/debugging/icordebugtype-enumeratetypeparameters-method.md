---
title: Método ICorDebugType::EnumerateTypeParameters
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16cf17d43fcad3c4f7a710678bbdc056f840eaca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736814"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>Método ICorDebugType::EnumerateTypeParameters
Obtém um ponteiro de interface para um ICorDebugTypeEnum que contém o <xref:System.Type> parâmetros da classe referenciada por este ICorDebugType.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppTyParEnum`  
 [out] Um ponteiro para o endereço de um `ICorDebugTypeEnum` que contém os parâmetros do tipo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar `EnumerateTypeParameters` se o valor de CorElementType retornado por [icordebugtype:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) é ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE _ PTR ou ELEMENT_TYPE_FNPTR. O número de parâmetros e sua ordem depende do tipo:  
  
- ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE: O número de parâmetros de tipo contidos no `ICorDebugTypeEnum` que esse método retorna, dependerá do número de parâmetros de tipo formal para a classe correspondente. Por exemplo, se o tipo é `class Dict<String,int32>`, em seguida, `EnumerateTypeParameters` retornará uma `ICorDebugTypeEnum` que contém objetos que representam `String` e `int32` na sequência.  
  
- ELEMENT_TYPE_FNPTR: O número de parâmetros de tipo contidos no `ICorDebugTypeEnum` será um maior que o número de argumentos aceitados pela função. O primeiro parâmetro de tipo contido no `ICorDebugTypeEnum` é o tipo de retorno da função e os parâmetros de tipo subsequentes são os parâmetros da função.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR: Um parâmetro de tipo será retornado. Por exemplo, se o tipo é um tipo de matriz, como `int32[]`,`EnumerateTypeParameters` retornará uma `ICorDebugTypeEnum` que contém um objeto que representa `int32`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
