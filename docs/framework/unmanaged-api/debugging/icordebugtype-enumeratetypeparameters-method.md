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
ms.openlocfilehash: b2c381d093069f5ee86be1b19d75f5c2d69ad9fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791305"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>Método ICorDebugType::EnumerateTypeParameters
Obtém um ponteiro de interface para um ICorDebugTypeEnum que contém os parâmetros de <xref:System.Type> da classe referenciada por este ICorDebugType.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppTyParEnum`  
 fora Um ponteiro para o endereço de um `ICorDebugTypeEnum` que contém os parâmetros do tipo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar `EnumerateTypeParameters` se o valor CorElementType retornado por [ICorDebugType:: GetType](icordebugtype-gettype-method.md) for ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR ou ELEMENT_TYPE_FNPTR. O número de parâmetros e sua ordem depende do tipo:  
  
- ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE: o número de parâmetros de tipo contidos no `ICorDebugTypeEnum` que esse método retorna, dependerá do número de parâmetros de tipo formal para a classe correspondente. Por exemplo, se o tipo for `class Dict<String,int32>`, `EnumerateTypeParameters` retornará um `ICorDebugTypeEnum` que contém objetos que representam `String` e `int32` em sequência.  
  
- ELEMENT_TYPE_FNPTR: o número de parâmetros de tipo contidos na `ICorDebugTypeEnum` será maior que o número de argumentos aceitos pela função. O primeiro parâmetro de tipo contido no `ICorDebugTypeEnum` é o tipo de retorno para a função, e os parâmetros de tipo subsequentes são os parâmetros da função.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR: um parâmetro de tipo será retornado. Por exemplo, se o tipo for um tipo de matriz, como `int32[]`,`EnumerateTypeParameters` retornará um `ICorDebugTypeEnum` que contém um objeto que representa `int32`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
