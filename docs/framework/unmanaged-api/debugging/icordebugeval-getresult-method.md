---
title: "Método ICorDebugEval::GetResult"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.GetResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7379237c73d79d9e8c66112a101edadca357cb10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalgetresult-method"></a>Método ICorDebugEval::GetResult
Obtém os resultados dessa avaliação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppResult`  
 [out] Ponteiro para o endereço de um objeto ICorDebugValue que representa os resultados dessa avaliação, se a avaliação for concluída normalmente.  
  
## <a name="remarks"></a>Comentários  
 O `GetResult` método é válido somente depois que a avaliação é concluída.  
  
 Se a avaliação for concluída normalmente, `ppResult` Especifica os resultados. Se ele termina com uma exceção, o resultado é a exceção é gerada. Se a avaliação de um novo objeto, o resultado é a referência ao novo objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
