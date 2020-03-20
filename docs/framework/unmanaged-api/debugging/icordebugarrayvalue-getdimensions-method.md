---
title: Método ICorDebugArrayValue::GetDimensions
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: 35e043c56977bf644efe1dd9cee1409f50cc877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179024"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a>Método ICorDebugArrayValue::GetDimensions
Obtém o número de elementos em cada dimensão desta matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cdim`  
 [em] O número de dimensões deste objeto ICorDebugArrayValue.  
  
 Este valor também é `dims` o tamanho da matriz porque seu tamanho `ICorDebugArrayValue` é igual ao número de dimensões do objeto.  
  
 `dims`  
 [fora] Uma matriz de inteiros, cada um dos quais especifica o `ICorDebugArrayValue` número de elementos em uma dimensão neste objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
