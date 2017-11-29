---
title: "Método ICorDebugNativeFrame2::IsChild"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsChild Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 006543e473ca3b7cc1818b2b4641567ce37f6f0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2ischild-method"></a>Método ICorDebugNativeFrame2::IsChild
Determina se o quadro atual é um quadro filho.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pIsChild`  
 [out] Um valor booleano que especifica se o quadro atual é um quadro filho.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O status de filho foi retornado com êxito.|  
|E_FAIL|Não foi possível retornar o status do filho.|  
|E_INVALIDARG|`pIsChild` é nulo.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O `IsChild` método retorna `true` se o objeto de quadro no qual você chamar o método é um filho de outro quadro. Se esse for o caso, use o [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) método para verificar se um quadro é seu pai.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugNativeFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
