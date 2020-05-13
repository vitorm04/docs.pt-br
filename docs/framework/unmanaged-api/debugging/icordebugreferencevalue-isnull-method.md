---
title: Método ICorDebugReferenceValue::IsNull
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: e8b778c0880040f5ffd639a445fd5663ce493219
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379090"
---
# <a name="icordebugreferencevalueisnull-method"></a>Método ICorDebugReferenceValue::IsNull
Obtém um valor que indica se este ICorDebugReferenceValue é um valor nulo; nesse caso, o `ICorDebugReferenceValue` não aponta para um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pbNull`  
 fora Um ponteiro para um valor booliano que é `true` se esse `ICorDebugReferenceValue` objeto for nulo; caso contrário, `pbNull` será `false` .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
