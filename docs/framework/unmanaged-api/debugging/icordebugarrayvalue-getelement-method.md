---
title: Método ICorDebugArrayValue::GetElement
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: adcb7b5a27f3b8c63dbbb660a23b5c891f84ac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179004"
---
# <a name="icordebugarrayvaluegetelement-method"></a>Método ICorDebugArrayValue::GetElement
Obtém o valor do elemento damatriz dado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cdim`  
 [em] O número de dimensões deste `ICorDebugArrayValue` objeto.  
  
 Este valor também é `indices` o tamanho da matriz porque seu tamanho `ICorDebugArrayValue` é igual ao número de dimensões do objeto.  
  
 `indices`  
 [em] Uma matriz de valores de índice, cada um `ICorDebugArrayValue` dos quais especifica uma posição dentro de uma dimensão do objeto.  
  
 Este valor não deve ser nulo.  
  
 `ppValue`  
 [fora] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do elemento especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
