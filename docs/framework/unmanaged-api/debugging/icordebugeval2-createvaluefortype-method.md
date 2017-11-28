---
title: "Método ICorDebugEval2::CreateValueForType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CreateValueForType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc2760b1c303141372aed824bda71ebdae8ffe0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2createvaluefortype-method"></a>Método ICorDebugEval2::CreateValueForType
Obtém um ponteiro para um novo ICorDebugValue do tipo especificado, com um valor inicial de zero ou nulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pType`  
 [in] Ponteiro para um objeto ICorDebugType que representa o tipo.  
  
 `ppValue`  
 [out] Ponteiro para o endereço de uma `ICorDebugValue` objeto que representa o valor.  
  
## <a name="remarks"></a>Comentários  
 `CreateValueForType`generaliza [: Createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) , permitindo que você especifique um tipo de objeto arbitrário, incluindo construído tipos como `List<int>`. A única finalidade deste método é gerar um valor que pode ser passado para uma avaliação de função.  
  
 O tipo deve ser uma classe ou um tipo de valor. Você não pode usar esse método para criar valores de cadeia de caracteres ou valores de matriz.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
