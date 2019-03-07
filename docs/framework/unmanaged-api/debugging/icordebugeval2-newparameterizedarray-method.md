---
title: Método ICorDebugEval2::NewParameterizedArray
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c639204fa207774b0e362f1ba8fe71937494ae2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487676"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>Método ICorDebugEval2::NewParameterizedArray
Aloca uma nova matriz do tipo de elemento especificado e dimensões.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pElementType`  
 [in] Um ponteiro para um objeto ICorDebugType que representa o tipo de elemento armazenado na matriz.  
  
 `rank`  
 [in] O número de dimensões da matriz. No .NET Framework versão 2.0, esse valor deve ser 1.  
  
 `dims`  
 [in] O tamanho, em bytes, de cada dimensão da matriz.  
  
 `lowBounds`  
 [in] Opcional. O limite inferior de cada dimensão da matriz. Se esse valor for omitido, um limite inferior de zero será assumido para cada dimensão.  
  
## <a name="remarks"></a>Comentários  
 Os elementos da matriz podem ser instâncias de um tipo genérico. A matriz é sempre criada no domínio do aplicativo no qual o thread está em execução. No .NET Framework 2.0, o valor de `rank` deve ser 1.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
