---
title: Método ICorDebugNativeFrame2::IsChild
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
ms.openlocfilehash: 22722e4d602bdb9df9877b2199b4d4271a4d3105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792727"
---
# <a name="icordebugnativeframe2ischild-method"></a>Método ICorDebugNativeFrame2::IsChild
Determina se o quadro atual é um quadro filho.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pIsChild`  
 fora Um valor booliano que especifica se o quadro atual é um quadro filho.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O status filho foi retornado com êxito.|  
|{1&gt;E_FAIL&lt;1}|Não foi possível retornar o status filho.|  
|{1&gt;E_INVALIDARG&lt;1}|`pIsChild` é nulo.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O método `IsChild` retorna `true` se o objeto de quadro no qual você chama o método é filho de outro quadro. Se esse for o caso, use o método [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) para verificar se um quadro é seu pai.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
