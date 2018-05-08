---
title: Método ICorDebugArrayValue::GetElementAtPosition
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 580c7b4dcd63f83e113a5317c242b7e66cfb3f5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a>Método ICorDebugArrayValue::GetElementAtPosition
Obtém o elemento na posição determinada, tratando a matriz como uma matriz unidimensional com base em zero.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nPosition`  
 [in] A posição do elemento a ser recuperado.  
  
 `ppValue`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do elemento.  
  
## <a name="remarks"></a>Comentários  
 O layout de uma matriz de multi-dimensão segue o estilo de C++ de layout de matriz.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
