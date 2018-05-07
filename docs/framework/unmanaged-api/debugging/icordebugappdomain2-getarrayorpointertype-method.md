---
title: Método ICorDebugAppDomain2::GetArrayOrPointerType
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3f0ca6d930b22f30fe9bbc5b5a04bf1e034f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>Método ICorDebugAppDomain2::GetArrayOrPointerType
Obtém uma matriz do tipo especificado, ou um ponteiro ou referência ao tipo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `elementType`  
 [in] Um valor da enumeração CorElementType que especifica o tipo nativo subjacente (uma matriz, ponteiro ou referência) a ser criado.  
  
 `nRank`  
 [in] A classificação (ou seja, o número de dimensões) da matriz. Esse valor deve ser 0 se `elementType` Especifica um tipo de ponteiro ou referência.  
  
 `pTypeArg`  
 [in] Um ponteiro para um objeto ICorDebugType que representa o tipo de matriz, um ponteiro ou uma referência a ser criado.  
  
 `ppType`  
 [out] Um ponteiro para o endereço de um `ICorDebugType` tipo de objeto que representa a matriz construído, tipo de ponteiro ou referência.  
  
## <a name="remarks"></a>Comentários  
 O valor de *elementType* deve ser um dos seguintes:  
  
-   ELEMENT_TYPE_PTR  
  
-   ELEMENT_TYPE_BYREF  
  
-   ELEMENT_TYPE_ARRAY ou ELEMENT_TYPE_SZARRAY  
  
 Se o valor de *elementType* é ELEMENT_TYPE_PTR ou ELEMENT_TYPE_BYREF, *nRank* devem ser zero.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
