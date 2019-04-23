---
title: Método ICorDebugInternalFrame2::IsCloserToLeaf
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30a9d26283d4f544bdd865e40cfc1c1c625ae462
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120894"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>Método ICorDebugInternalFrame2::IsCloserToLeaf
Verifica se o `this` quadro interno está mais próximo da folha que o objeto ICorDebugFrame especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFrameToCompare`  
 [in] Um ponteiro para a comparação `ICorDebugFrame` objeto.  
  
 `pIsCloser`  
 [out] `true` se o `this` quadro interno está mais próximo da folha que o quadro especificado por `pFrameToCompare`; caso contrário, `false`.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A comparação foi realizada com êxito.|  
|E_FAIL|A comparação não pôde ser executada.|  
|E_INVALIDARG|`pFrameToCompare` ou `pIsCloser` é nulo.|  
  
## <a name="remarks"></a>Comentários  
 `IsCloserToLeaf` pode ser usado para implementar uma política de intercalação quadros internos com outros quadros na pilha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
