---
title: Método ICorDebugArrayValue::GetCount
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa72f82d2fc78110fc2bee8edd265916996aa884
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403140"
---
# <a name="icordebugarrayvaluegetcount-method"></a>Método ICorDebugArrayValue::GetCount
Obtém o número total de elementos na matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pnCount`  
 [out] Um ponteiro para o número total de elementos na matriz.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
